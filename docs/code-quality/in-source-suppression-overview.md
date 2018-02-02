---
title: "Pomijanie ostrzeżeń analizy kodu w programie Visual Studio przy użyciu atrybutu SuppressMessage | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/29/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.topic: article
helpviewer_keywords:
- source suppression, code analysis
- code analysis, source suppression
author: gewarren
ms.author: gewarren
manager: ghogen
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: 4cd3800e082673e9478eb32c6ae5627eef4d7e81
ms.sourcegitcommit: d6327b978661c0a745bf4b59f32d8171607803a3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2018
---
# <a name="suppressing-code-analysis-warnings"></a>Pomijanie ostrzeżeń analizy kodu

Często jest to przydatne w celu wskazania, że ostrzeżenie nie dotyczy. Oznacza to, aby członkowie zespołu, który kodu zostało sprawdzone i można pominąć to ostrzeżenie. Pomijanie (ISS) używa źródła <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> atrybutu w celu pominięcia ostrzeżenia. Ten atrybut można umieścić blisko segment kodu, który wygenerował ostrzeżenia. Możesz dodać <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> atrybutu w pliku źródłowym, wpisując je, lub za pomocą menu skrótów na ostrzeżenie w **listy błędów** dodać ją automatycznie.

<xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> Jest atrybutem warunkowego uwzględniony w metadanych z zestawu zarządzanego kodu IL tylko wtedy, gdy CODE_ANALYSIS symbol kompilacji jest definiowany w czasie kompilacji.

W języku C + +/ CLI, użyj makra urzędu certyfikacji\_POMIŃ\_wiadomości lub urzędu certyfikacji\_GLOBAL\_SUPPRESS_MESSAGE w pliku nagłówka, aby dodać ten atrybut.

> [!NOTE]
> Nie należy używać pominięć w źródła w kompilacjach wydania, aby uniknąć przypadkowego wysyłania metadanych pomijanie w źródła. Ponadto z powodu przetwarzania pomijania-source, może być niższa wydajność aplikacji.

## <a name="suppressmessage-attribute"></a>SuppressMessage — atrybut

Po wybraniu **Pomiń** menu kontekstowe lub kliknij prawym przyciskiem myszy ostrzeżenia analizy kodu w **listy błędów**, <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> w kodzie lub pominięć globalnych projektu jest dodawany atrybut plik.

<xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> Atrybut ma następujący format:

```vb
<Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")>
```

```csharp
[Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")]
```

```cpp
CA_SUPPRESS_MESSAGE("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")
```

Właściwości atrybutu obejmują:

- **Reguły kategorii** -kategorii, w którym zdefiniowana jest reguła. Aby uzyskać więcej informacji o kategoriach reguł analizy kodu, zobacz [ostrzeżenia kodu zarządzanego](../code-quality/code-analysis-for-managed-code-warnings.md).

- **Identyfikator reguły** — identyfikator reguły. Obsługa obejmuje zarówno nazwę krótkich i długich identyfikatorem reguły. Krótka nazwa jest CAXXXX; długa nazwa jest CAXXXX:FriendlyTypeName.

- **Justowanie** — tekst, który jest używany do dokumentu Przyczyna pomijanie wiadomości.

- **Identyfikator wiadomości** — Unikatowy identyfikator problemu dla każdego komunikatu.

- **Zakres** — element docelowy, na którym pomijane jest ostrzeżenie. Jeśli element docelowy nie zostanie określony, ustawiono element docelowy atrybutu. Zakresy obsługiwane są następujące:

    - Moduł

    - Przestrzeń nazw

    - Zasób

    - Typ

    - Element członkowski

- **Docelowy** — identyfikator, który służy do określania docelowych, na którym pomijane jest ostrzeżenie. Musi zawierać element w pełni kwalifikowaną nazwę.

## <a name="suppressmessage-usage"></a>Użycie SuppressMessage

Ostrzeżenia analizy kodu są pomijane na poziomie, do którego <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> atrybut jest stosowany. Na przykład można zastosować atrybutu poziomie zestawu, modułu, typu, elementu członkowskiego lub parametru. Celem tego jest ściśle połączenie informacji pomijania kod gdzie występuje naruszenie.

Ogólny kształt pomijania obejmuje kategoria reguł i identyfikator reguły, który zawiera opcjonalne reprezentacja zrozumiałą dla użytkownika nazwa reguły. Na przykład:

`[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`

Jeśli ze względu na wydajność strict dla minimalizując pomijanie w źródła metadanych, można pominąć nazwę reguły. Kategoria reguł wraz z jego identyfikator reguły stanowić wystarczająco Unikatowy identyfikator reguły. Na przykład:

`[SuppressMessage("Microsoft.Design", "CA1039")]`

Ze względu na łatwość pominięcie Nazwa reguły nie jest zalecane.

## <a name="suppressing-selective-violations-within-a-method-body"></a>Pomijanie selektywnego naruszeń w treści metody

Atrybuty do pomijania można zastosować do metody, ale nie może być osadzony w treści metody. Oznacza to, że wszystkie naruszenia określonej reguły są pomijane, jeśli dodasz <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> atrybut do metody.

W niektórych przypadkach można pominąć konkretnego wystąpienia naruszenia, na przykład, dzięki czemu kod przyszłości nie jest automatycznie wykluczony z reguł analizy kodu. Niektórych reguł analizy kodu można to zrobić przy użyciu `MessageId` właściwość <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> atrybutu. Ogólnie rzecz biorąc, starsze reguły naruszeń w zakresie określonego symbolu (zmienną lokalną ani parametrem) `MessageId` właściwości. [CA1500:VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500-variable-names-should-not-match-field-names.md) jest przykładem takich reguły. Jednak nie przestrzega starsze reguły za naruszenia na kod wykonywalny (z systemem innym niż symbol) `MessageId` właściwości. Ponadto nie przestrzega analizatorów Roslyn `MessageId` właściwości.

Aby pominąć to naruszenie określonego symbolu regułę, określ nazwę symbolu `MessageId` właściwość <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> atrybutu. W poniższym przykładzie pokazano kod z dwóch naruszeń [CA1500:VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500-variable-names-should-not-match-field-names.md)&mdash;jeden dla `name` zmienną i jeden dla `age` zmiennej. Naruszenie dla `age` symbol jest pomijane.

```vb
Public Class Animal
    Dim age As Integer
    Dim name As String

    <CodeAnalysis.SuppressMessage("Microsoft.Maintainability", "CA1500:VariableNamesShouldNotMatchFieldNames", MessageId:="age")>
    Sub PrintInfo()
        Dim age As Integer = 5
        Dim name As String = "Charlie"

        Console.WriteLine("Age {0}, Name {1}", age, name)
    End Sub

End Class
```

```csharp
public class Animal
{
    int age;
    string name;

    [System.Diagnostics.CodeAnalysis.SuppressMessage("Microsoft.Maintainability", "CA1500:VariableNamesShouldNotMatchFieldNames", MessageId = "age")]
    private void PrintInfo()
    {
        int age = 5;
        string name = "Charlie";

        Console.WriteLine($"Age {age}, Name {name}");
    }
}
```

## <a name="generated-code"></a>Wygenerowany kod

Kompilatory kodu zarządzanego i niektóre narzędzia innych firm generowanie kodu w celu ułatwienia kodu szybkie programowanie. Kod wygenerowany przez kompilator pojawia się w plikach źródłowych jest zwykle oznaczony atrybutem `GeneratedCodeAttribute` atrybutu.

Można wybrać, czy pominąć kod analizy ostrzeżenia i błędy dla wygenerowanego kodu. Informacje o sposobie Pomiń tych ostrzeżeń i błędów, zobacz [porady: pomijanie ostrzeżeń dla wygenerowany kod](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md).

> [!NOTE]
> Analiza kodu ignoruje `GeneratedCodeAttribute` gdy jest stosowany do całego zestawu lub jeden parametr.

## <a name="global-level-suppressions"></a>Pominięcia na poziomie Global

Sprawdza, czy narzędzie do analizy kodu zarządzanego `SuppressMessage` atrybuty, które są stosowane na poziomie zestawu, modułu, typu, elementu członkowskiego lub parametr. On również generowane naruszeń względem zasobów i przestrzenie nazw. Naruszenia należy zastosować na poziomie globalnym zakresie i docelowe. Na przykład następujący komunikat pomija naruszenie przestrzeni nazw:

`[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`

> [!NOTE]
> Pomijaj ostrzeżenia o zakresie przestrzeni nazw, powoduje pominięcie ostrzeżenie przed przestrzeni nazw, do samej siebie. Odrzuca ostrzeżenie przed typy w przestrzeni nazw.

Wszelkie pomijania można wyrazić, określając zakres jawnego. Te pominięć musi istnieć na poziomie globalnym. Pomijanie poziom elementu członkowskiego nie można określić przez dekoracji typu.

Pominięcia na poziomie globalnych są jedynym sposobem na wyświetlanie komunikatów, które odwołują się do kod wygenerowany przez kompilator, który nie został zmapowany do źródła jawnie podany użytkownik. Na przykład następujący kod pomija naruszenie względem konstruktora wysyłanego kompilatora:

`[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`

> [!NOTE]
> `Target`zawsze zawiera nazwę elementu w pełni kwalifikowana.

## <a name="global-suppression-file"></a>Plik pominięć globalnych

Plik pominięć globalnych przechowuje pominięć pominięcia na poziomie globalnym lub ograniczeń, które nie określają elementu docelowego. Na przykład pominięcia na poziomie zestawu naruszeń są przechowywane w tym pliku. Ponadto niektóre pominięć ASP.NET są przechowywane w tego pliku, ponieważ ustawienia na poziomie projektu nie są dostępne dla kod związany z formularzem. Plik pominięć globalnych jest tworzony i dodawany do projektu po raz pierwszy należy wybrać **w pliku pominięć projektu** opcji **Pomiń** w **listy błędów**okna.

## <a name="see-also"></a>Zobacz także

<xref:System.Diagnostics.CodeAnalysis>