---
title: "Ostrzeżenia i błędy | Narzędzie Test Microsoft IntelliTest dewelopera | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IntelliTest, Warnings and errors
ms.author: gewarren
manager: ghogen
ms.workload: multiple
author: gewarren
ms.openlocfilehash: 77f47c2d18b43c3ab08dac5fec6281892072ab36
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2018
---
# <a name="warnings-and-errors"></a>Ostrzeżenia i błędy

## <a name="warnings-and-errors-by-category"></a>Ostrzeżenia i błędy według kategorii

* **Granice**
  * [Przekroczono MaxBranches](#maxbranches-exceeded)
  * [Przekroczono MaxConstraintSolverTime](#maxconstraintsolvertime-exceeded)
  * [Przekroczono MaxConditions](#maxconditions-exceeded)
  * [Przekroczono MaxCalls](#maxcalls-exceeded)
  * [Przekroczono MaxStack](#maxstack-exceeded)
  * [Przekroczono MaxRuns](#maxruns-exceeded)
  * [Przekroczono MaxRunsWithoutNewTests](#maxrunswithoutnewtests-exceeded)<p />

* **Ograniczenia rozwiązania**
  * [Nie można skonkretyzować rozwiązania](#cannot-concretize-solution)<p />

* **Domen**
  * [Potrzebna pomoc do konstruowania obiektu](#help-construct)
  * [Potrzebujesz pomocy w celu odnalezienia typów](#help-types)
  * [Można używać typu odgadnąć](#usable-type-guessed)<p />

* **Wykonanie**
  * [Nieoczekiwany błąd podczas eksploracji](#unexpected-exploration)
  * [TargetInvocationException](#targetinvocationexception)<p />

* **Instrumentacji**
  * [Niezinstrumentowanej metody o nazwie](#uninstrumented-method-called)
  * [Wywołano metodę zewnętrznych](#external-method-called)
  * [Wywołuje metody niemożliwej](#uninstrumentable-method-called)
  * [Problem testowania](#testability-issue)
  * [Ograniczenia](#limitation)<p />

* **Interpreter**
  * [Zaobserwowano niezgodność wywołań](#observed-call-mismatch)
  * [Wartość przechowywana w polu statycznym](#value-static-field)

<a name="maxbranches-exceeded"></a>
## <a name="maxbranches-exceeded"></a>Przekroczono MaxBranches

IntelliTest ogranicza długość dowolną ścieżkę wykonywania, który pokazuje go podczas [wejściowych generowania](input-generation.md). Ta funkcja zapobiega IntelliTest przestanie odpowiadać, gdy program przechodzi w pętli nieskończonej.

Co warunkowe i bezwarunkowe gałęzi wykonane i monitorowanych kodu jest liczony kierunku ten limit, gałęzie, które nie są zależne od danych wejściowych z tym [sparametryzowanego testu jednostkowego](test-generation.md#parameterized-unit-testing).

Na przykład następujący kod zużywa gałęzie kolejności 100:

```
for (int i=0; i<100; i++) { }
```

Można edytować **MaxBranches** opcji atrybutu pochodną **PexSettingsAttributeBase**, takich jak [PexClass](attribute-glossary.md#pexclass) lub [PexMethod](attribute-glossary.md#pexmethod) . Poniższy przykład usunięcie to powiązane:

```
[PexMethod(MaxBranches=int.MaxValue)]
public void MyTest(...) {
    // ....
}
```

Można również ustawić **TestExcludePathBoundsExceeded** opcję, aby poinformować IntelliTest jak ogólnie radzenia sobie z tych problemów.

W kodzie testu, można użyć [PexSymbolicValue](static-helper-classes.md#pexsymbolicvalue) ignoruje wygenerowany przez warunek pętli ograniczenia:

```
for (int i=0; 
    PexSymbolicValue.Ignore(i<100); // IntelliTest will 'forget' about this path condition
    i++) 
{ }
```

<a name="maxconstraintsolvertime-exceeded"></a>
## <a name="maxconstraintsolvertime-exceeded"></a>Przekroczono MaxConstraintSolverTime

Używa IntelliTest [moduł rozwiązywania ograniczeń](input-generation.md#constraint-solver) do obliczenia nowe dane wejściowe testu. Ograniczenia rozwiązywania może być procesem bardzo czasochłonne, więc IntelliTest umożliwia konfigurowanie granic — w szczególności **MaxConstraintSolverTime**.

W wielu aplikacjach znaczne zwiększenie limitu czasu nie spowoduje lepsze pokrycia. Przyczyną jest większość limitów czasu są spowodowane ograniczenia systemów, które są dostępne nie rozwiązania. Jednak program IntelliTest nie może być możliwe ustalenie, czy jest on niezgodny bez próby wszystkie możliwe rozwiązania, które spowoduje przekroczenie limitu czasu.

<a name="maxconditions-exceeded"></a>
## <a name="maxconditions-exceeded"></a>Przekroczono MaxConditions

IntelliTest ogranicza długość dowolną ścieżkę wykonywania, który pokazuje go podczas [wejściowych generowania](input-generation.md). Ta funkcja zapobiega IntelliTest przestanie odpowiadać, gdy wprowadzany Pętla nieskończona.

Każda gałąź warunkowego, która zależy od wejść z [sparametryzowanego testu jednostkowego](test-generation.md#parameterized-unit-testing) jest liczony kierunku ten limit.

Na przykład wykorzystuje każda ścieżka w poniższym kodzie **n + 1** warunki:

```
[PexMethod]
void ParameterizedTest(int n) {
    // conditions are "0<n", "1<n", ..., "!(n<n)"
    for (int i=0; i<n; i++)
    { ... }

    // irrelevant for MaxConditions, since conditions do not depend on input
    for (int i=0; i<100; i++) 
    { ... }
}
```

Można edytować **MaxConditions** opcji atrybutu pochodną **PexSettingsAttributeBase**, takich jak [PexClass](attribute-glossary.md#pexclass) lub [PexMethod](attribute-glossary.md#pexmethod). Na przykład:

```
[PexMethod(MaxConditions=10000)]
void ParameterizedTest(int n) {
    // ...
}
```

Można również ustawić **TestExcludePathBoundsExceeded** opcję, aby poinformować IntelliTest jak ogólnie rozwiązać te problemy.

Można użyć [PexSymbolicValue](static-helper-classes.md#pexsymbolicvalue) ignoruje wygenerowany przez warunek pętli ograniczenia:

```
[PexMethod]
void ParameterizedTest(int n) {
    int nshadow = PexSymbolicValue.Ignore(n); // IntelliTest looses track of 'n'

    // irrevelant for MaxConditions, since nshadow is not related to input
    for (int i=0; i<nshadow; i++)  
    {...}
}
```

<a name="maxcalls-exceeded"></a>
## <a name="maxcalls-exceeded"></a>Przekroczono MaxCalls

IntelliTest ogranicza długość dowolną ścieżkę wykonywania, który pokazuje go podczas [wejściowych generowania](input-generation.md). Ta funkcja zapobiega IntelliTest przestanie odpowiadać, gdy program rozpocznie nieskończoną pętlę.

Każde wywołanie (bezpośrednie, pośrednie, wirtualne lub przejść) kodu wykonane i monitorowanych zliczane kierunku ten limit.

Można edytować **MaxCalls** opcji atrybutu pochodną **PexSettingsAttributeBase**, takich jak [PexClass](attribute-glossary.md#pexclass) lub [PexMethod](attribute-glossary.md#pexmethod). Poniższy przykład usunięcie to powiązane:

```
[PexMethod(MaxCalls=int.MaxValue)]
public void MyTest(...) {
    // ....
}
```

Można również ustawić **TestExcludePathBoundsExceeded** opcję, aby poinformować IntelliTest jak ogólnie rozwiązać te problemy.

<a name="maxstack-exceeded"></a>
## <a name="maxstack-exceeded"></a>Przekroczono MaxStack

IntelliTest ogranicza rozmiar stosu wywołań z dowolną ścieżkę wykonywania, który pokazuje go podczas [wejściowych generowania](input-generation.md). Ta funkcja zapobiega IntelliTest przerywanie, gdy wystąpi przepełnienie stosu.

Można edytować **MaxStack** opcji atrybutu pochodną **PexSettingsAttributeBase**, takich jak [PexClass](attribute-glossary.md#pexclass) lub [PexMethod](attribute-glossary.md#pexmethod). Poniższy przykład usunięcie tego granica (niezalecane):

```
[PexMethod(MaxStack=int.MaxValue)]
public void MyTest(...) {
    // ....
}
```

Można również ustawić **TestExcludePathBoundsExceeded** opcję, aby poinformować IntelliTest jak ogólnie rozwiązać te problemy.

<a name="maxruns-exceeded"></a>
## <a name="maxruns-exceeded"></a>Przekroczono MaxRuns

IntelliTest ogranicza liczbę ścieżek wykonywania, które go Eksploruje podczas [wejściowych generowania](input-generation.md). Ta funkcja zapewnia, że IntelliTest kończy działanie, gdy program ma pętli lub rekursji.

Nie może być to, że w każdym uruchomieniu IntelliTest test sparametryzowany z konkretnym dane wejściowe, emituje nowy przypadek testowy. Zobacz [TestEmissionFilter](exploration-bounds.md#testemissionfilter) Aby uzyskać więcej informacji.

Można edytować **MaxRuns** opcji atrybutu pochodną **PexSettingsAttributeBase**, takich jak [PexClass](attribute-glossary.md#pexclass) lub [PexMethod](attribute-glossary.md#pexmethod). Poniższy przykład usunięcie tego granica (niezalecane):

```
[PexMethod(MaxRuns=2000)]
public void MyTest(...) {
    // ....
}
```

<a name="maxrunswithoutnewtests-exceeded"></a>
## <a name="maxrunswithoutnewtests-exceeded"></a>Przekroczono MaxRunsWithoutNewTests

IntelliTest ogranicza liczbę ścieżek wykonywania, które go Eksploruje podczas [wejściowych generowania](input-generation.md). Ta funkcja zapewnia, że IntelliTest kończy działanie, gdy program ma pętli lub rekursji.

Nie może być to, że w każdym uruchomieniu IntelliTest test sparametryzowany z konkretnym dane wejściowe, emituje nowy przypadek testowy. Zobacz [TestEmissionFilter](exploration-bounds.md#testemissionfilter) Aby uzyskać więcej informacji.

Gdy IntelliTest znajdzie często dużo interesujące dane wejściowe testu początkowo, go może — po chwili - Emituj żadnych więcej testów. Ta opcja decyduje o tym, jak długo IntelliTest może próbować znaleźć innego testu odpowiednich danych wejściowych.

Można edytować **MaxRunsWithoutNewTests** opcji atrybutu pochodną **PexSettingsAttributeBase**, takich jak [PexClass](attribute-glossary.md#pexclass) lub [PexMethod](attribute-glossary.md#pexmethod). Poniższy przykład usunięcie tego granica (niezalecane):

```
[PexMethod(MaxRunsWithoutNewTests=2000)]
public void MyTest(...) {
    // ....
}
```

<a name="cannot-concretize-solution"></a>
## <a name="cannot-concretize-solution"></a>Nie można skonkretyzować rozwiązania

Ten błąd jest często konsekwencją wcześniejszego błędu. Używa IntelliTest [moduł rozwiązywania ograniczeń](input-generation.md#constraint-solver) ustalenie nowe dane wejściowe testu. Czasami test proponowane przez dane wejściowe [moduł rozwiązywania ograniczeń](input-generation.md#constraint-solver) są nieprawidłowe. To może się zdarzyć, gdy:

* Niektóre ograniczenia nie są znane.
* Jeśli wartości są tworzone w sposób zdefiniowane przez użytkownika, powodując błędów w kodzie użytkownika
* Niektóre typy mają logiki inicjowania nie są kontrolowane przez program IntelliTest (na przykład klasy COM)

<a name="help-construct"></a>
## <a name="need-help-to-construct-object"></a>Potrzebujesz pomocy do konstruowania obiektu

IntelliTest [generuje dane wejściowe testu](input-generation.md), a niektóre dane wejściowe mogą być obiekty z polami. W tym miejscu IntelliTest próbuje wygenerować wystąpienia klasy, która ma pole prywatne i przyjęto założenie, że interesujące zachowanie programu wystąpią, gdy to pole prywatne ma określoną wartość. 

Jednak gdy jest to możliwe za pomocą odbicia, IntelliTest nie produkcji obiekty z dowolnego pola wartości. Zamiast tego w tych przypadkach go zależy od użytkownika podania wskazówki dotyczące korzystania z publicznej metody klasy do utworzenia obiektu i włączenie go w stanie, w których jej pole prywatne ma wymaganą wartość.

Odczyt [tworzenia wystąpienia istniejących klas](input-generation.md#existing-classes) Aby dowiedzieć się, jak możesz pomóc IntelliTest skonstruować interesujące obiektów. 

<a name="help-types"></a>
## <a name="need-help-to-find-types"></a>Potrzebujesz pomocy w celu odnalezienia typów

IntelliTest [generuje dane wejściowe testu](input-generation.md) dla dowolnego typu .NET. W tym miejscu IntelliTest próbuje utworzyć wystąpienie, które pochodzi z klasy abstrakcyjnej lub implementuje interfejs abstrakcyjna i IntelliTest nie zna żadnego typu spełniającego ograniczenia. 

Możesz pomóc IntelliTest, wskazując jeden lub więcej typów, które pasują do ograniczeń. Zazwyczaj jedną z następujących atrybutów pomoże:

* **PexUseTypeAttribute**, który wskazuje określonego typu.

  Na przykład, jeśli IntelliTest zgłasza, że "nie ma żadnych typów, które można przypisać do **System.Collections.IDictionary**", można ułatwić poprzez dołączenie następujące **PexUseTypeAttribute** testu (lub do klasy osprzętu):

  ```
  [PexMethod]
  [PexUseType(typeof(System.Collections.Hashtable))]
  public void MyTest(IDictionary[] dictionaries) { ... }
  ```

* **Atrybut poziomu zestawu**

  ```
  [assembly: PexUseType(typeof(System.Collections.Hashtable))]
  ```

<a name="usable-type-guessed"></a>
## <a name="usable-type-guessed"></a>Można używać typu odgadnąć

IntelliTest [generuje dane wejściowe testu](input-generation.md) dla wszystkich typów .NET. Jeśli typ jest abstrakcyjny lub interfejsu, IntelliTest należy wybrać określoną implementację tego typu. Można wybrać tego musi wiedzieć, jakie typy istnieje. 

Jeśli to ostrzeżenie jest wyświetlane, it indiicates czy IntelliTest przeglądał niektóre zestawy występujące w odwołaniach i znaleźć typu implementacji, ale nie jest pewności, czy go należy użyć tego typu lub jeśli są bardziej odpowiednie typy dostępnych w innym miejscu. IntelliTest po prostu wybierz typ, która zawierała obietnicy.

Aby uniknąć tego ostrzeżenia, możesz zaakceptować wybór typu IntelliTest w, lub ułatwienie IntelliTest za pomocą innych typów, dodając odpowiednią [PexUseType](attribute-glossary.md#pexusetype).

<a name="unexpected-exploration"></a>
## <a name="unexpected-failure-during-exploration"></a>Nieoczekiwany błąd podczas eksploracji

Wystąpił nieoczekiwany wyjątek podczas eksploracji testu.

Sprawdź [zgłosić ten błąd](#report-bug).

<a name="targetinvocationexception"></a>
## <a name="targetinvocationexception"></a>TargetInvocationException

Wystąpił wyjątek w kodzie użytkownika. Sprawdź ślad stosu i Usuń usterki w kodzie.

<a name="uninstrumented-method-called"></a>
## <a name="uninstrumented-method-called"></a>Niezinstrumentowanej metody o nazwie

IntelliTest [generuje dane wejściowe testu](input-generation.md) przez monitorowanie wykonywania programu. Istotne jest odpowiedni kod prawidłowo został zinstrumentowany tak, aby IntelliTest można monitorować swoje działanie.

To ostrzeżenie jest wyświetlane, gdy instrumentowanych kod wywołuje metody w zestawie innym, niezinstrumentowanej. Jeśli chcesz IntelliTest, aby eksplorować interakcji obu musi również Instrumentacja innych zestawu (lub jej części).

<a name="external-method-called"></a>
## <a name="external-method-called"></a>Wywołano metodę zewnętrznych

IntelliTest [generuje dane wejściowe testu](input-generation.md) przez monitorowanie wykonywania aplikacji .NET. IntelliTest nie można wygenerować dane wejściowe testu zrozumiały dla kodu, który nie jest napisany w języku .NET.

To ostrzeżenie jest wyświetlane, gdy instrumentowanych kod wywołuje metodę niezarządzane, natywnego IntelliTest nie można przeanalizować. Jeśli chcesz IntelliTest, aby eksplorować interakcji obu musi mock niezarządzane — metoda.

<a name="uninstrumentable-method-called"></a>
## <a name="uninstrumentable-method-called"></a>Wywołuje metody niemożliwej

IntelliTest [generuje dane wejściowe testu](input-generation.md) przez monitorowanie wykonywania aplikacji .NET. Istnieją jednak w przypadku niektórych metod, z przyczyn technicznych IntelliTest nie można monitorować. Na przykład IntelliTest nie można monitorować Konstruktor statyczny.

To ostrzeżenie jest wyświetlane, gdy instrumentowanych kod wywołuje metodę IntelliTest nie można monitorować. 

<a name="testability-issue"></a>
## <a name="testability-issue"></a>Problem testowania

IntelliTest [generuje dane wejściowe testu](input-generation.md) przez monitorowanie wykonywania programu. Dane wejściowe testu odpowiednich może generować tylko wtedy, gdy program jest deterministyczna, a odpowiednie zachowanie jest kontrolowane przez dane wejściowe testu.

To ostrzeżenie pojawia się, ponieważ, podczas wykonywania przypadku testowego, metoda została wywołana albo działa w sposób niejednoznaczny, lub współdziała ze środowiskiem. Przykłady są metody **System.Random** i **System.IO.File**. Jeśli chcesz IntelliTest, aby utworzyć dane wejściowe testu znaczący musi mock metody, które IntelliTest flagi jako pola problemy.

<a name="limitation"></a>
## <a name="limitation"></a>Ograniczenia

IntelliTest [generuje dane wejściowe testu](input-generation.md) za pomocą [moduł rozwiązywania ograniczeń](input-generation.md#constraint-solver).
Istnieją jednak niektóre operacje, które wykraczają poza zakres [moduł rozwiązywania ograniczeń](input-generation.md#constraint-solver).
Obecnie w tym:

* operacje najbardziej zmiennoprzecinkowe (tylko działania arytmetyczne, liniowego jest obsługiwany na liczby zmiennoprzecinkowe)
* konwersje między liczby zmiennoprzecinkowe i całkowite
* wszystkie operacje na **System.Decimal** typu

To ostrzeżenie jest wyświetlane, gdy kod wykonywany wykonuje operację lub wywołuje metodę, która nie może zinterpretować IntelliTest. 

<a name="observed-call-mismatch"></a>
## <a name="observed-call-mismatch"></a>Zaobserwowano niezgodność wywołań

IntelliTest [generuje dane wejściowe testu](input-generation.md) przez monitorowanie wykonywania programu. Jednak program IntelliTest nie może być monitorować wszystkie instrukcje. Na przykład nie można monitorować kodu macierzystego i nie można monitorować kodu, która nie została zinstrumentowana.

Gdy program IntelliTest nie można monitorować kodu, nie może generować dane wejściowe testu, które mają zastosowanie do tego kodu.
Często IntelliTest nie są znane fakt, że nie można go monitorować metody do momentu zwraca wywołanie tej metody. Jednak przyczyna to ostrzeżenie jest:

* IntelliTest monitorowane kod, który zainicjował wywołanie niezinstrumentowanej metody
* Niezinstrumentowanej metody wywołuje metodę, która jest instrumentowany
* IntelliTest monitoruje instrumentowanych metodę, która została wywołana 

IntelliTest nie zna co zostało niezinstrumentowanej metody pośrednie, więc może być mogą generować dane wejściowe testu istotnych zagnieżdżone wywołania Instrumentacją.

<a name="value-static-field"></a>
## <a name="value-stored-in-static-field"></a>Wartość przechowywana w polu statycznym

IntelliTest systematycznie można określić [dane wejściowe testu odpowiednich](input-generation.md) tylko podczas testu jednostkowego jest deterministyczna; innymi słowy, zawsze działa ten sam sposób dla tych samych wejściach testu. W szczególności oznacza to, test należy pozostawić system w stanie, który umożliwia ponowne wykonanie tego testu.
W idealnym przypadku testu jednostkowego nie należy zmieniać żadnego globalnego stanu, ale powinien być mocked wszystkie interakcje z globalne.

To ostrzeżenie oznacza, że pola statycznego został zmieniony; może to uniemożliwić testu zachowują się w sposób niejednoznaczny.

W niektórych sytuacjach zmiana pola statycznego jest dopuszczalne:

* gdy dane wejściowe testu powoduje, że ustawienia lub czyszczenia kod cofnąć zmianę
* gdy pole jest inicjowane tylko raz, a wartość nie ulega zmianie później

<a name="report-bug"></a>

## <a name="got-feedback"></a>Masz opinię?

Publikowania własnych pomysłów i funkcji żądań na  **[UserVoice](https://visualstudio.uservoice.com/forums/121579-visual-studio-2015/category/157869-test-tools?query=IntelliTest)**.
