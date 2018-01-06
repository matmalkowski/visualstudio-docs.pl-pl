---
title: "Analizatory Roslyn i obsługujących kod biblioteki ImmutableArrays | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b0afa22-3fca-4d59-908e-352464c1d903
caps.latest.revision: "5"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 6870f1733d507f2cf46d196b2bba027b998b5ba4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="roslyn-analyzers-and-code-aware-library-for-immutablearrays"></a>Analizatory Roslyn i obsługujących kod biblioteki ImmutableArrays

[Platformy kompilatora .NET](https://github.com/dotnet/roslyn) ("Roslyn") pomaga w utworzeniu obsługujący kod biblioteki.  Obsługujący kod biblioteki zawiera funkcje, których można używać i narzędzi (Roslyn analizatorów), aby ułatwić korzystanie z biblioteki w najlepszy sposób, lub aby uniknąć błędów.  W tym temacie przedstawiono sposób tworzenia analizator Roslyn rzeczywistych, aby wykryć typowych błędów, korzystając z [System.Collections.Immutable](https://www.nuget.org/packages/System.Collections.Immutable) pakietu NuGet.  W przykładzie pokazano także jak zapewnić poprawkę kod problemu kodu znaleziono przez analizatora.  Użytkownicy widzą poprawki kodu w Visual Studio żarówkę interfejsu użytkownika i można automatycznie zastosować poprawkę dla kodu.

## <a name="getting-started"></a>Wprowadzenie

Potrzebne do tworzenia w tym przykładzie:

* Visual Studio 2015 (nie Express Edition) lub nowszy.  Można korzystać z BEZPŁATNEJ [programu Visual Studio Community Edition](https://www.visualstudio.com/products/visual-studio-community-vs)
* [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  Można także podczas instalowania programu Visual Studio, sprawdzić rozszerzalności programu Visual Studio Tools w obszarze narzędziom do instalowania zestawu SDK, w tym samym czasie.  Jeśli zainstalowano program Visual Studio można także zainstalować zestaw SDK, przechodząc do menu głównego **plik &#124; Nowy &#124; Projekt...** , wybierając C# w lewym okienku nawigacji, a następnie wybierając rozszerzalności.  Po wybraniu "**Zainstaluj narzędzia rozszerzalności programu Visual Studio**" szablonu projektu nawigacją, monituje użytkownika o pobranie i zainstalowanie zestawu SDK.
* [Platforma kompilatora .NET ("Roslyn") zestawu SDK](http://aka.ms/roslynsdktemplates).  Można także zainstalować zestaw SDK, przechodząc do menu głównego **plik &#124; Nowy &#124; Projekt...** , wybierając pozycję **C#** w lewym okienku nawigacji, a następnie wybierając **rozszerzalności**.  Po wybraniu "**Pobierz zestaw SDK platformy .NET kompilatora**" szablonu projektu nawigacją, monituje użytkownika o pobranie i zainstalowanie zestawu SDK.  Ten zestaw SDK zawiera [wizualizatora składni Roslyn](https://github.com/dotnet/roslyn/wiki/Syntax%20Visualizer).  Pomaga to bardzo przydatne narzędzie możesz dowiedzieć się, jakie typy modelu kodu należy szukać w Twojej analizatora.  Wywołania infrastruktury analizatora do kodu dla typów modelu określonego kodu, dzięki czemu kod tylko wykonuje się, gdy jest to konieczne i mogą skupić się tylko na analizowanie odpowiedni kod.

## <a name="whats-the-problem"></a>Co to jest Problem?

Wyobraź sobie zapewnia biblioteki element ImmutableArray (na przykład <xref:System.Collections.Immutable.ImmutableArray%601?displayProperty=fullName>) obsługuje.  C# mogą korzystać doświadczonych z tablicami .NET.  Jednak ze względu na specyfikę technik ImmutableArrays i optymalizacji zastosowany w implementacji intuitions developer C#, że użytkownicy biblioteki do pisania kodu, uszkodzony, jak wyjaśniono poniżej.  Ponadto nie jest wyświetlany ich błędów czasu wykonywania, nie są one używane do programu Visual Studio z platformą .NET doświadczeniu jakości.

Użytkownicy zapoznali się z pisanie kodu podobne do poniższych:

```csharp
var a1 = new int[0];
Console.WriteLine("a1.Length = { 0}", a1.Length);
var a2 = new int[] { 1, 2, 3, 4, 5 };
Console.WriteLine("a2.Length = { 0}", a2.Length);
```

Tworzenie puste tablice, aby wypełnić się przy użyciu kolejnych wierszy kodu i przy użyciu składni inicjatora kolekcji są bardzo znane deweloperom C#.  Jednak kod element ImmutableArray zapisywania takie same ulega awarii w czasie wykonywania:

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = { 0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = { 0}", b2.Length);
```

Pierwszy błąd wynika z implementacji element ImmutableArray przy użyciu struktury opakowywać źródłowy magazyn danych. Struktury musi mieć konstruktorów bez parametrów, aby `default(T)` wyrażenia może zwrócić struktury ze wszystkimi zero lub wartość null elementów członkowskich.  Gdy kod uzyskuje dostęp do `b1.Length`, jest wartość null w czasie wykonywania wyłuskania błąd, ponieważ nie istnieje żadna podstawowej macierz magazynowa w strukturze element ImmutableArray.  Jest prawidłowy sposób, aby utworzyć pusty element ImmutableArray `ImmutableArray<int>.Empty`.

Błąd inicjatory kolekcji odbywa się, ponieważ metoda ImmutableArray.Add zwraca nowe wystąpienia zawsze należy wywołać.  Ponieważ ImmutableArrays nigdy nie ulegną zmianie, podczas dodawania nowego elementu, można odzyskać nowy obiekt element ImmutableArray (która może udostępniać magazynu ze względu na wydajność istniejących element ImmutableArray).  Ponieważ `b2` wskazuje pierwszy element ImmutableArray przed wywołaniem `Add()` pięć razy `b2` jest domyślny element ImmutableArray.  Wywoływanie długości w nim również awarii (Crash) z wartością null wyłuskania błąd.  Prawidłowy sposób zainicjować element ImmutableArray bez wywoływania ręcznie Dodaj jest użycie `ImmutableArray.CreateRange(new int[] {1, 2, 3, 4, 5})`.

## <a name="finding-relevant-syntax-node-types-to-trigger-your-analyzer"></a>Wyszukiwanie składni odpowiednie typy węzłów do wyzwolenia z analizatora

 Aby rozpocząć tworzenie analizatora, najpierw dowiedzieć się, jakiego rodzaju SyntaxNode potrzebne do wyszukania. Uruchamianie wizualizatora składni z menu **widoku &#124; Inne okna &#124; Składnia Roslyn wizualizatora**.

Umieść karetka edytora w wierszu, który deklaruje `b1`.  Zobaczysz wizualizatora składni pokazuje znajdują się w `LocalDeclarationStatement` węzeł drzewa składni.  Ten węzeł zawiera `VariableDeclaration`, który z kolei ma `VariableDeclarator`, który z kolei ma `EqualsValueClause`, a na koniec istnieje `ObjectCreationExpression`.  Kliknij w drzewie składni wizualizatora węzłów składni w oknie edytora prezentuje pokazanie kod reprezentowany przez ten węzeł.  Nazwy typów sub SyntaxNode są zgodne z nazw używanych w gramatyce C#.

## <a name="creating-the-analyzer-project"></a>Tworzenie projektu analizatora

W menu głównym wybierz **plik &#124; Nowy &#124; Projekt...** .  W **nowy projekt** okna dialogowego, w obszarze **C#** projekty na pasku nawigacyjnym po lewej stronie wybierz rozszerzeń, a w okienku po prawej stronie wybierz **analizatora z kodu** projektu szablon.  Wprowadź nazwę i Potwierdź okna dialogowego.

Szablon zostanie otwarty plik DiagnosticAnalyzer.cs.  Wybierz kartę buforu tego edytora.  Ten plik zawiera klasę analyzer (sformułowany niż nazwa nadana projektu) która pochodzi z `DiagnosticAnalyzer` (typ Roslyn interfejsu API).  Ma nowej klasie `DiagnosticAnalyzerAttribute` deklarowanie analizatora użytkownika jest istotne dla języka C#, aby kompilator umożliwia odnalezienie i ładuje z analizatora.

```csharp
[DiagnosticAnalyzer(LanguageNames.CSharp)]
public class ImmutableArrayAnalyzerAnalyzer : DiagnosticAnalyzer
{}
```

Można zaimplementować analizator kodu języka Visual Basic, przeznaczonego dla kodu C# i na odwrót.  Jest większe znaczenie w DiagnosticAnalyzerAttribute, aby wybrać, czy Twoje Analizator jest przeznaczony dla jednego języka lub oba.  Bardziej złożone analizatorów, które wymagają szczegółowe modelowania języka można kierować tylko jeden język.  Twoje analizatora, na przykład tylko sprawdza nazwy typu lub publicznego elementu członkowskiego, może być możliwe wspólnego modelu języka Roslyn oferowanych w Visual Basic i C#.  Na przykład programu FxCop ostrzega, że klasa implementuje <xref:System.Runtime.Serialization.ISerializable>, ale nie ma klasy <xref:System.SerializableAttribute> atrybut jest niezależny od języka i działa w przypadku kodu zarówno Visual Basic i C#.

## <a name="initalizing-the-analyzer"></a>Initalizing analizatora

 Przewiń w dół nieco w `DiagnosticAnalyzer` klasy, aby wyświetlić `Initialize` metody.  Kompilator wywołuje tę metodę, gdy aktywacja analizatora.  Metoda korzysta z `AnalysisContext` obiekt, który umożliwia z analizatora, aby uzyskać informacje o kontekście i rejestrowania wywołań zwrotnych dla zdarzeń dla typów kodu do przeanalizowania.

```csharp
public override void Initialize(AnalysisContext context) {}

```

Otwórz nowy wiersz w tym metody i typu "kontekście." Aby wyświetlić listę uzupełniania IntelliSense.  Widać na liście uzupełniania wiele `Register...` metod obsługi różnych rodzajów zdarzeń.  Na przykład pierwsza z nich, `RegisterCodeBlockAction`, kod w bloku, który zazwyczaj znajduje się kod między nawiasy klamrowe wywołań.  Rejestrowanie w bloku również wywołuje kodu dla inicjatora pola, podana wartość atrybutu lub wartość parametr opcjonalny.

Inny przykład `RegisterCompilationStartAction`, wywołania do kodu na początku kompilacji, co jest przydatne, gdy trzeba gromadzenia stanów w wielu lokalizacjach.  Można utworzyć struktury danych, powiedz, aby zbierać wszystkie symbole używane, i każdym razem, gdy Twoje Analizator jest wywołanie zwrotne dla niektórych składni lub symbol, można zapisać informacji o każdej lokalizacji w strukturze danych.  Kiedy jest ponownie wywoływana ze względu na zakończenie kompilacji, można analizować wszystkich zostały zapisane, na przykład, aby zgłosić symbole, jaki kod korzysta z każdej lokalizacji `using` instrukcji.

Przy użyciu **wizualizatora składni**, wiesz, że chcesz można wywołać, gdy kompilator przetwarza ObjectCreationExpression.  Konfigurowanie wywołania zwrotnego przy użyciu tego kodu:

```csharp
context.RegisterSyntaxNodeAction(c => AnalyzeObjectCreation(c),
                                 SyntaxKind.ObjectCreationExpression);
```

Możesz zarejestrować węzeł składni i filtr tylko obiekt tworzenie składni węzłów.  Konwencja autorzy analizatora używać wyrażenia lambda, podczas rejestrowania akcji, które pomaga chronić analizatorów bezstanowych.  Funkcja Visual Studio **Generowanie z użycia** utworzyć `AnalyzeObjectCreation` metody.  Spowoduje to wygenerowanie poprawny typ parametru kontekstowego można zbyt.

## <a name="setting-properties-for-users-of-your-analyzer"></a>Ustawianie właściwości dla użytkowników z analizatora

Tak, aby Twoje analizatora zostaną wyświetlone w Visual Studio UI odpowiednio, Znajdź i zmodyfikuj następujący wiersz kodu do identyfikowania użytkownika analizatora:

```csharp
internal const string Category = "Naming";
```

Zmień `"Naming"` do `"API Guidance"`.

Następnie Znajdowanie i otwieranie `Resources.resx` pliku w projekcie za pomocą **Eksploratora rozwiązań**.  Możesz umieścić w opisie z analizatora, tytuł itd.  Można zmienić wartości dla wszystkich tych do `"Don't use ImmutableArray<T> constructor"` teraz.  Ciąg formatowania argumenty w ciągu ({0}, {1}, itp.), można umieścić i nowszym, jeśli wywołujesz `Diagnostic.Create()`, możesz podać `params` tablicy argumenty do przekazania.

## <a name="analyzing-an-object-creation-expression"></a>Analizowanie wyrażenie Tworzenie obiektu

`AnalyzeObjectCreation` Metoda ma inny typ kontekstu dostarczanych przez platformę analizator kodu.  Metoda inicjowania `AnalysisContext` służy do rejestrowania wywołań zwrotnych akcji, aby skonfigurować Twoje analizatora.  `SyntaxNodeAnalysisContext`, Na przykład `CancellationToken` przekazywaną wokół.  Jeśli użytkownik uruchamia, wpisując w edytorze, Roslyn spowoduje anulowanie uruchomionych analizatorów, aby zapisać pracę i zwiększyć wydajność.  Inny przykład tego kontekstu ma właściwość węzła, która zwraca węzeł składni tworzenia obiektu.

Pobierz węzeł, który można założyć, jest to typ, dla którego filtrowana Akcja węzeł składni:

```csharp
var objectCreation = (ObjectCreationExpressionSyntax)context.Node;
```

### <a name="launching-visual-studio-with-your-analyzer-the-first-time"></a>Uruchamianie programu Visual Studio z Twojej analizator po raz pierwszy

Uruchom program Visual Studio po utworzeniu i wykonywanie programu analyzer (naciśnij klawisz **F5**).  Ponieważ uruchamianie projektu w **Eksploratora rozwiązań** jest projektu VSIX, systemem kompilacji kodu w kodzie i pliku VSIX, a następnie uruchamia program Visual Studio z tym VSIX zainstalowane.  Po uruchomieniu programu Visual Studio w ten sposób uruchamia z gałęzi rejestru distinct, aby głównej korzystanie z programu Visual Studio nie wpłynie swoich wystąpień testowych podczas kompilowania analizatorów.  Po raz pierwszy w ten sposób możesz uruchomić program Visual Studio nie kilka operacji inicjowania, podobnie jak podczas należy najpierw uruchomić Visual Studio po jego zainstalowaniu.

Utwórz projekt konsoli, a następnie wprowadź kod tablicy do metody Main aplikacji z konsoli:

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = {0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = {0}", b2.Length);
```

Wiersze kodu z `ImmutableArray` mieć zygzaki, ponieważ należy pobrać pakiet NuGet niezmienne i Dodaj `using` instrukcji w kodzie.  Naciśnij przycisk prawo wskaźnika na węzeł projektu w **Eksploratora rozwiązań** i wybierz polecenie **Zarządzaj pakietami NuGet...** .  W Menedżerze programu NuGet, w polu wyszukiwania wpisz "Immutable", a następnie wybierz pozycję "System.Collections.Immutable" (nie wybierzesz "Microsoft.Bcl.Immutable") w okienku po lewej stronie i kliknij przycisk Zainstaluj w okienku po prawej stronie.  Instalowanie pakietu dodaje odwołanie do odwołania projektu.

Nadal zobaczysz czerwony zygzaki w obszarze `ImmutableArray`, umieszczają karetki w tym identyfikator i naciśnij klawisz **CTRL +.** (okres), aby wyświetlić menu sugerowanej poprawki i wybierz opcję Dodaj odpowiednie `using` instrukcji.

**Zapisz wszystkie i Zamknij** drugie wystąpienie programu Visual Studio teraz możesz umieścić w stanu czystego, aby kontynuować.

## <a name="finishing-the-analyzer-using-edit-and-continue"></a>Kończenie przy użyciu analizatora Edytuj i Kontynuuj

W pierwszym wystąpieniu programu Visual Studio, ustaw punkt przerwania na początku Twojej `AnalyzeObjectCreation` metody naciskając **F9** z karetki w pierwszym wierszu.

Uruchamianie z analizatora ponownie, podając **F5**i w drugie wystąpienie programu Visual Studio, otwórz ponownie utworzono ostatniego aplikacji konsoli.

Zwraca pierwsze wystąpienie programu Visual Studio na punkt przerwania ponieważ kompilatora Roslyn był wyświetlany wyrażeniu tworzenia obiektów i wywołać do Twojej analizatora.

**Pobierz węzeł tworzenia obiektu.** Przekrocz nad wiersza, który ustawia `objectCreation` zmiennej naciskając **F10**i w **oknie bezpośrednim** oszacować wyrażenia `"objectCreation.ToString()"`.  Węzeł składni wskazuje zmienna jest kod `"new ImmutableArray<int>()"`, po prostu co szukasz.

**Pobierz element ImmutableArray < T\> typu obiektu.** Należy sprawdzić, czy typ tworzony jest element ImmutableArray.  Najpierw pobierz jest obiekt, który reprezentuje tego typu.  Możesz sprawdzić, aby upewnić się, ma nieprawidłowy typ, a nie porównanie ciągu z ToString() przy użyciu modelu semantycznego.  Wprowadź następujący wiersz kodu na końcu funkcji:

```csharp
var immutableArrayOfTType =
    context.SemanticModel
           .Compilation
           .GetTypeByMetadataName("System.Collections.Immutable.ImmutableArray`1");
```

Możesz określić typy ogólne w metadanych z backquotes (') i liczba parametrów ogólnych.  Dlatego nie widać "... Element ImmutableArray\<T > "w nazwie metadanych.

Model semantyczny znajdują się wiele przydatne czynności umożliwiające zadać pytania dotyczące symboli, przepływu danych, okres istnienia zmiennej itp.  Roslyn oddziela składni węzłów z modelu semantycznego z różnych powodów engineering (wydajność, modelowania błędnego kodu itp.).  Ma model kompilacji do wyszukiwania informacji zawartych w odwołaniach do dokładność porównania.

Wskaźnik żółty wykonywania można przeciągnąć po lewej stronie okna edytora.  Przeciągnij go do wiersza, który ustawia `objectCreation` zmienną i Przekrocz Twojej nowy wiersz kodu za pomocą **F10**.  Jeśli umieść wskaźnik myszy nad zmiennej `immutableArrayOfType`, zobaczysz, że znaleziono dokładnego typu w modelu semantycznego.

**Pobierz typ wyrażenia tworzenia obiektu.** "Type" jest używany na kilka sposobów, w tym artykule, ale oznacza to, czy masz "Foo nowe" wyrażenie, należy uzyskać modelu Foo.  Należy uzyskać typ wyrażenia tworzenia obiektu, aby sprawdzić, czy jest element ImmutableArray\<T > typu.  Ponownie użyj modelu semantycznego można pobrać informacji o symbolach dla typu symbolu (element ImmutableArray) w wyrażeniu tworzenia obiektów.  Wprowadź następujący wiersz kodu na końcu funkcji:

```csharp
var symbolInfo = context.SemanticModel.GetSymbolInfo(objectCreation.Type).Symbol as INamedTypeSymbol;
```

Ponieważ Twoje analizator musi obsługiwać niekompletne lub niepoprawne kodu w edytorze buforów (na przykład brakuje `using` instrukcji), należy sprawdzić, czy `symbolInfo` jest `null`.  Należy pobrać typu o nazwie (INamedTypeSymbol) z obiektu informacji symbol do zakończenia analizy.

**Porównanie typów.** Ponieważ jest to otwarty typ ogólny, t, który czekamy na, a konkretnego typu ogólnego jest typem w kodzie, kwerendy informacji o symbolach dla jakiego typu jest tworzony z (otwartym typem ogólnym) i porównać wynik z `immutableArrayOfTType`.  Wprowadź następujące na końcu metody:

```csharp
if (symbolInfo != null &&
    symbolInfo.ConstructedFrom.Equals(immutableArrayOfTType))
{}
```

**Raport dane diagnostyczne.** Raportowanie dane diagnostyczne jest dość proste.  W przypadku użycia reguły, utworzona w programie szablonu projektu, który jest zdefiniowany przed wywołaniem metody Initialize.  Ponieważ w tej sytuacji kod jest błąd, można zmienić wiersza, który zainicjowany regułę, aby zastąpić `DiagnosticSeverity.Warning` (zielony wężyk) z `DiagnosticSeverity.Error` (czerwona falista).  Inicjuje pozostałe reguły z zasoby, które można edytowane na początku tego przewodnika.  Należy również zgłosić lokalizację wężyk, który znajduje się wyrażenie tworzenia obiektu specyfikacji typu.  Wprowadź ten kod w `if` bloku:

```csharp
context.ReportDiagnostic(Diagnostic.Create(Rule, objectCreation.Type.GetLocation()));
```

Funkcja powinna wyglądać następująco (być może format inny):

```csharp
private void AnalyzeObjectCreation(SyntaxNodeAnalysisContext context)
{
    var objectCreation = (ObjectCreationExpressionSyntax)context.Node;
    var immutableArrayOfTType =
        context.SemanticModel
               .Compilation
               .GetTypeByMetadataName(
                   "System.Collections.Immutable.ImmutableArray`1");
    var symbolInfo = context.SemanticModel.GetSymbolInfo(objectCreation.Type).Symbol as
        INamedTypeSymbol;
    if (symbolInfo != null &&
        symbolInfo.ConstructedFrom.Equals(immutableArrayOfTType))
    {
        context.ReportDiagnostic(
            Diagnostic.Create(Rule, objectCreation.Type.GetLocation()));
    }
}
```

Usuń punkt przerwania, można przejrzeć pracy analizator (i zatrzymać, wracając do pierwszego wystąpienia programu Visual Studio).  Przeciągnij wskaźnik wykonywania na początku metody i naciśnij klawisz **F5** do kontynuowania wykonywania.  Po przełączeniu do drugiego wystąpienia programu Visual Studio, kompilator rozpocznie się zbadanie kodu i zostanie wywołany z analizatora.  Zostanie wyświetlony wężyk w obszarze `ImmutableType<int>`.

## <a name="adding-a-code-fix-for-the-code-issue"></a>Dodawanie "Napraw kodu" problemu kodu

Przed rozpoczęciem należy zamknąć drugie wystąpienie programu Visual Studio i Zatrzymaj debugowanie w pierwszej kolejności programu Visual Studio (gdy tworzysz analizatora).

**Dodaj nową klasę.** Użyj menu skrótów (wskaźnik myszy w prawy przycisk) w węźle projekt w Eksploratorze rozwiązań i wybierz opcję Dodaj nowy element.  Dodaj klasę o nazwie `BuildCodeFixProvider`.  Ta klasa musi pochodzić od `CodeFixProvider`, i będą musieli używać **CTRL +.** (okres), aby wywołać poprawka kodu, który dodaje poprawny `using` instrukcji.  Ta klasa również musi być adnotowany przy `ExportCodeFixProvider` atrybut i konieczne będzie dodanie `using` instrukcji, aby rozwiązać `LanguageNames` wyliczenia.  Plik klasy następującym kodem w nim powinny mieć:

```csharp
using Microsoft.CodeAnalysis;
using Microsoft.CodeAnalysis.CodeFixes;

namespace ImmutableArrayAnalyzer
{
    [ExportCodeFixProvider(LanguageNames.CSharp)]
    class BuildCodeFixProvider : CodeFixProvider
    {}

```

**Stub limit pochodnych elementów członkowskich.** Teraz umieść karetka edytora w identyfikatorze `CodeFixProvider` i naciśnij klawisz **CTRL +.** (okres) można zastąpić klasą zastępczą limit implementację to abstrakcyjna klasa podstawowa.  Spowoduje to wygenerowanie właściwości i metody dla Ciebie.

**Implementowanie właściwości.** Wypełnij `FixableDiagnosticIds` właściwości `get` treści następującym kodem:

```csharp
return ImmutableArray.Create(ImmutableArrayAnalyzerAnalyzer.DiagnosticId);
```

Roslyn zgromadzono diagnostyki i rozwiązuje się przez dopasowanie tych identyfikatorów, które są tylko ciągi.  Szablon projektu wygenerowany identyfikator diagnostyczny i mogą je zmienić.  Kodu we właściwości właśnie zwraca identyfikator klasy analizatora.

**Metoda RegisterCodeFixAsync pobierającej kontekst.** Kontekst jest ważne, ponieważ poprawki kodu można stosować do wielu diagnostyki lub może być problem z więcej niż jeden na wiersz kodu.  Jeśli wpiszesz "context". w treści metody na liście uzupełniania IntelliSense opisano niektóre elementy członkowskie są użyteczne.  Brak elementu członkowskiego CancellationToken, który można sprawdzić, jeśli coś chce anulować tę poprawkę.  Brak elementu członkowskiego dokumentu, który ma wiele elementów członkowskich przydatne i umożliwi użytkownikowi uzyskanie dostępu do obiektów modelu projektu i rozwiązania.  Brak elementu członkowskiego zakresu, który jest początek i koniec lokalizacji kodu określić, kiedy zgłaszane dane diagnostyczne.

**Utwórz metodę być asynchroniczne.** Najpierw należy wykonać jest deklaracja metody wygenerowanego należy naprawić `async` metody.  Nie zawiera kodu poprawkę stubbing limit implementacji klasy abstrakcyjnej `async` — słowo kluczowe nawet wtedy, gdy metoda zwraca `Task`.

**Pobierz korzeń drzewa składni.** Aby zmodyfikować kod potrzebne do tworzenia nowego drzewa składni ze zmianami dokonanych zmian kodu sprawia, że.  Należy `Document` z kontekstu do wywołania `GetSyntaxRootAsync`.  Jest to metoda asynchroniczna, ponieważ jest nieznany pracy można pobrać drzewa składni, prawdopodobnie w tym pobierania pliku z dysku, jego analizowanie i budowania model kodu programu Roslyn.  W tym czasie, w którym przy użyciu interfejsu użytkownika programu Visual Studio powinien być dynamiczne `async` umożliwia.  Zastąp linię kod w metodzie następujące czynności:

```csharp
var root = await context.Document
                        .GetSyntaxRootAsync(context.CancellationToken);
```

**Znaleźć węzła o problem.** Możesz przekazać zakres kontekstu, ale węzła, które być może nie być kod, który trzeba zmienić.  Zgłoszona Diagnostyka tylko podany zakres dla identyfikatora typu (gdzie wężyk należały), ale należy zastąpić wyrażeniem tworzenia całego obiektu, w tym `new` — słowo kluczowe na początku i nawiasów na końcu.  Dodaj następujący kod do metody (i użyj **CTRL +.** Aby dodać `using` instrukcji dla `ObjectCreationExpressionSyntax`):

```csharp
var objectCreation = root.FindNode(context.Span)
                         .FirstAncestorOrSelf<ObjectCreationExpressionSyntax>();
```

**Zarejestruj Twoje poprawki kodu żarówki interfejsu użytkownika.** Po zarejestrowaniu Twojego poprawki kodu Roslyn podłącza się do programu Visual Studio żarówkę interfejsu użytkownika automatycznie.  Użytkownicy zobaczą, mogą używać **CTRL +.** (okresów), gdy Twoje analizatora squiggles zły `ImmutableArray<T>` Użyj konstruktora.  Ponieważ dostawcą poprawki kodu jest wykonywana tylko wtedy, gdy występuje problem, można założyć, że masz wyrażeniem tworzenia obiektu, którego szukasz.  W parametrze kontekstowym można zarejestrować nowy kod poprawka przez dodanie poniższego kodu do końca `RegisterCodeFixAsync` metody:

```csharp
context.RegisterCodeFix(
            CodeAction.Create("Use ImmutableArray<T>.Empty",
                              c => ChangeToImmutableArrayEmpty(objectCreation,
                                                               context.Document,
                                                               c)),
            context.Diagnostics[0]);
```

Trzeba umieścić karetka edytora w identyfikatorze, `CodeAction`, następnie użyć **CTRL +.** (okres), aby dodać odpowiedni `using` instrukcji dla tego typu.

Umieść punkt wstawiania edytora w `ChangeToImmutableArrayEmpty` identyfikator i użyj **CTRL +.** ponownie, aby wygenerować ten szkieletu metody dla Ciebie.

Ten ostatni fragment kodu dodano rejestruje poprawka kodu przez przekazanie `CodeAction` i Identyfikator diagnostyczny dla rodzaju Napotkano problem.  W tym przykładzie tylko jedno jest naprawia diagnostycznych identyfikator, który zawiera ten kod, tak można po prostu Przekaż pierwszy element tablicy identyfikatorów diagnostycznych.  Po utworzeniu `CodeAction`, przekazać w tekście, która ma być używana jako Opis poprawki kodu żarówki interfejsu użytkownika.  Należy również przekazać w funkcji, która przyjmuje CancellationToken i zwraca nowy dokument.  Nowy dokument ma nowe drzewo składni, zawierające kodzie poprawioną, która wywołuje `ImmutableArray.Empty`.  Następujący fragment kodu używa wyrażenia lambda, można zamknąć przez węzeł objectCreation i kontekstu dokumentu.

**Utworzyć nowe drzewa składni.** W `ChangeToImmutableArrayEmpty` metody, których stub wygenerowanego wcześniej, wprowadź w wierszu kodu: `ImmutableArray<int>.Empty;`.  Jeśli ponownie wyświetlić wizualizatora składni okna narzędzia można zauważyć, że ta składnia jest węzłem SimpleMemberAccessExpression.  To jest ta metoda wymaga utworzenia i zwróć nowy dokument.

Pierwsza zmiana do `ChangeToImmutableArrayEmpty` jest dodanie `async` przed `Task<Document>` ponieważ generatory kodu nie założono, metoda powinna być asynchroniczne.

Wypełnij treści następującym kodem, aby metodę wygląda podobnie do następującego:

```csharp
private async Task<Document> ChangeToImmutableArrayEmpty(
    ObjectCreationExpressionSyntax objectCreation, Document document,
    CancellationToken c)
{
    var generator = SyntaxGenerator.GetGenerator(document);
    var memberAccess =
        generator.MemberAccessExpression(objectCreation.Type, "Empty");
    var oldRoot = await document.GetSyntaxRootAsync(c);
    var newRoot = oldRoot.ReplaceNode(objectCreation, memberAccess);
    return document.WithSyntaxRoot(newRoot);
}
```

Należy wprowadzić karetka edytora w `SyntaxGenerator` identyfikator i użyj **CTRL +.** (okres), aby dodać odpowiedni `using` instrukcji dla tego typu.

Ten kod zawiera `SyntaxGenerator`, który jest typem przydatne do tworzenia nowego kodu.  Po pierwsze generator dla dokumentu, który ma problem kodu `ChangeToImmutableArrayEmpty` wywołania `MemberAccessExpression`, przekazywanie typ, który ma chcemy, aby uzyskać dostęp do elementu członkowskiego i przekazując nazwy elementu członkowskiego jako ciąg.

Następnie metoda pobiera głównego dokumentu, a ponieważ może to obejmować dowolnego pracy w przypadku ogólnych, kod oczekujące na to wywołanie i przekazuje token anulowania.  Modele kodu Roslyn są niezmienne, tak jak w przypadku ciąg .NET. Podczas aktualizacji ciągu otrzymasz nowy obiekt ciągu w zamian.  Podczas wywoływania `ReplaceNode`, wrócić nowego węzła głównego.  Większość drzewa składni jest udostępniana (ponieważ jest niezmienialny), ale `objectCreation` węzła jest zastępowany `memberAccess` węzeł, a także wszystkich węzłów nadrzędnych do katalogu głównego drzewa składni.

## <a name="trying-your-code-fix"></a>W trakcie dokonanych zmian kodu

Teraz możesz nacisnąć **F5** można wykonać z analizatora w drugie wystąpienie programu Visual Studio.  Otwórz projekt konsoli używane przed.  Teraz powinien zostać wyświetlony żarówki pojawiają się nowe wyrażenie utworzenia obiektu w przypadku dla `ImmutableArray<int>`.  Jeśli naciśniesz **CTRL +.** (kropka) zostanie wyświetlona Usuń kod i będzie wyświetlany podgląd różnica automatycznie wygenerowany kod w żarówki interfejsu użytkownika.  Roslyn tworzy to dla Ciebie.

**Porady Pro:** Jeśli Uruchom drugie wystąpienie programu Visual Studio i nie widzisz żarówkę z Twojej poprawki kodu, a następnie należy wyczyścić pamięć podręczną składnika programu Visual Studio.  Wyczyszczenie pamięci podręcznej wymusza Visual Studio, aby ponownie bada składników, więc programu Visual Studio należy następnie podnieś składnika najnowszego.  Najpierw zamknij drugie wystąpienie programu Visual Studio.  W Eksploratorze Windows przejdź do katalogu użytkownika (c:\users\\< userid\>) i Znajdź AppData\Local\Microsoft\VisualStudio\14.0Roslyn\\.  W tym katalogu Usuń katalog sub ComponentModelCache.  "14" zmiany wersji do wersji z programem Visual Studio.

## <a name="talk-video-and-finish-code-project"></a>Rozmowa wideo i Zakończ kodu projektu

Widać, w tym przykładzie opracowany i omówione w [tego poproś](http://channel9.msdn.com/events/Build/2015/3-725).  Poproś przedstawia analizatora pracy oraz przeprowadzi Cię przez skompilowanie go.

Można wyświetlić kod zakończenia [tutaj](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers).  Podfoldery DoNotUseImmutableArrayCollectionInitializer, jak i DoNotUseImmutableArrayCtor ma pliku C# do znajdowania problemy i pliku C#, który implementuje poprawki kodu, które są widoczne w Visual Studio żarówkę interfejsu użytkownika.  Uwaga: kod zakończenia ma nieco więcej abstrakcji, aby uniknąć pobierania element ImmutableArray\<T > samodzielnego typu object.  Używa zagnieżdżonych zarejestrowanych akcji można zapisać obiektu typu w kontekście, który jest dostępny zawsze, gdy akcje sub (analizowanie tworzenia obiektów i analizować Inicjowanie zbierania) wykonania.

## <a name="see-also"></a>Zobacz też

* [\\Poproś \Build 2015](http://channel9.msdn.com/events/Build/2015/3-725)
* [Kompletny kod w witrynie GitHub](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers)
* [Kilka przykładów w witrynie GitHub, podzielone na trzy rodzaje analizatorów](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)
* [Inne dokumentów w witrynie GitHub OSS](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
* [Zasady programu FxCop realizowana za pomocą analizatorów Roslyn w witrynie GitHub](https://github.com/dotnet/roslyn/tree/master/src/Diagnostics/FxCop)
