---
title: Generowanie tekstu czasu wykonywania przy użyciu szablonów tekstowych T4
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- Preprocessed Text Template project item
- TextTemplatingFilePreprocessor custom tool
- text templates, TransformText() method
- text templates, generating files at run time
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 91d232a4eaac7aa9f7a624ecfcc4168659347d8f
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37117657"
---
# <a name="run-time-text-generation-with-t4-text-templates"></a>Generowanie tekstu czasu wykonywania przy użyciu szablonów tekstowych T4

Przy użyciu szablonów tekstowych środowiska wykonawczego Visual Studio można wygenerować ciągów tekstowych w aplikacji w czasie wykonywania. Komputer, gdzie aplikacja wykonuje nie muszą mieć programu Visual Studio. Środowisko uruchomieniowe szablony czasami są nazywane "wstępnie przetworzony szablonów tekstowych", ponieważ w czasie kompilacji szablon generuje kod, który jest wykonywany w czasie wykonywania.

Każdy szablon jest mieszaniną tekstu, jak będzie wyglądać w wygenerowanym ciągu i fragmentów kodu programu. Fragmenty program Podaj wartości dla zmiennej części ciągu i również sterować części warunkowe i powtórzony.

Następujący szablon można na przykład w aplikacji, która tworzy raport HTML.

```html
<#@ template language="C#" #>
<html><body>
<h1>Sales for Previous Month</h2>
<table>
    <# for (int i = 1; i <= 10; i++)
       { #>
         <tr><td>Test name <#= i #> </td>
             <td>Test value <#= i * i #> </td> </tr>
    <# } #>
 </table>
This report is Company Confidential.
</body></html>
```

Zwróć uwagę, że szablon jest strona HTML, w którym zostały zastąpione zmiennej części kodu programu. Można rozpocząć projektu strony sieci pisząc statycznych prototypu strony HTML. Następnie można zastąpić tabeli i innymi częściami zmiennej z kodem program, który generuje zawartość, która różni się od jednokrotnie do następnego.

W usłudze ułatwia aplikacji przy użyciu szablonu jest widoczność końcowego formularza danych wyjściowych nie może w, na przykład długich serię instrukcji zapisu. Zmiany wprowadzone w formie danych wyjściowych jest łatwiejsze i bardziej niezawodny.

## <a name="creating-a-run-time-text-template-in-any-application"></a>Tworzenie szablonu tekstowego Run-Time w dowolnej aplikacji

### <a name="to-create-a-run-time-text-template"></a>Aby utworzyć szablon tekstu czasu wykonywania

1. W Eksploratorze rozwiązań, w menu skrótów projektu, wybierz **Dodaj** > **nowy element**.

2. W **Dodaj nowy element** okno dialogowe, wybierz opcję **szablonu tekstowego środowiska uruchomieniowego**. (W języku Visual Basic, sprawdź w obszarze **wspólne elementy** > **ogólne**.)

3. Wpisz nazwę pliku szablonu.

    > [!NOTE]
    > Nazwa pliku szablonu będzie służyć jako nazwy klasy w wygenerowanym kodzie. W związku z tym nie ma on spacji ani znaków interpunkcyjnych.

4. Wybierz **dodać**.

    Utworzony nowy plik ma rozszerzenie **.TT —**. Jego **narzędzie niestandardowe** właściwość jest ustawiona na **texttemplatingfilepreprocessor —**. Ten przewodnik zawiera następujące wiersze:

    ```
    <#@ template language="C#" #>
    <#@ assembly name="System.Core" #>
    <#@ import namespace="System.Linq" #>
    <#@ import namespace="System.Text" #>
    <#@ import namespace="System.Collections.Generic" #>
    ```

## <a name="converting-an-existing-file-to-a-run-time-template"></a>Konwertowanie istniejącego pliku do szablonu środowiska wykonawczego

Sposób tworzenia szablonu jest przekonwertować istniejące przykład danych wyjściowych. Na przykład jeśli aplikacja generuje pliki HTML, można uruchomić, tworząc zwykły plik HTML. Upewnij się, że działa prawidłowo i czy jej wygląd jest poprawna. Następnie dołącz ją do projektu programu Visual Studio i przekonwertować go do szablonu.

### <a name="to-convert-an-existing-text-file-to-a-run-time-template"></a>Aby przekonwertować istniejącego pliku tekstowego do szablonu środowiska wykonawczego

1. Dołączyć plik do projektu programu Visual Studio. W Eksploratorze rozwiązań, w menu skrótów projektu, wybierz **Dodaj** > **istniejący element**.

2. Pliku zestawu **narzędzia niestandardowe** właściwości **texttemplatingfilepreprocessor —**. W Eksploratorze rozwiązań, pliku, w menu skrótów wybierz **właściwości**.

    > [!NOTE]
    > Jeśli właściwość została już ustawiona, upewnij się, że jest **texttemplatingfilepreprocessor —** i nie **texttemplatingfilegenerator —**. Może się to zdarzyć, jeśli zawiera plik, który ma już rozszerzenie **.TT —**.

3. Zmień rozszerzenie nazwy pliku na **.TT —**. Mimo że ten krok jest opcjonalny, pomaga uniknąć otworzyć plik w edytorze niepoprawne.

4. Usuń wszystkie spacje lub znaki interpunkcyjne z głównej części nazwy pliku. Na przykład "Mój Page.tt sieci Web" jest nieprawidłowa, ale "MyWebPage.tt" jest poprawna. Nazwa pliku będzie służyć jako nazwy klasy w wygenerowanym kodzie.

5. Wstaw następujący wiersz na początku pliku. Jeśli pracujesz w projektach Visual Basic, zastąp "C#" z "VB".

    `<#@ template language="C#" #>`

## <a name="the-content-of-the-run-time-template"></a>Zawartość szablonu środowiska wykonawczego

### <a name="template-directive"></a>Dyrektywy szablonu

Zachowaj pierwszy wiersz szablonu, jak w momencie tworzenia pliku:

`<#@ template language="C#" #>`

Parametr język będzie zależeć od język projektu.

### <a name="plain-content"></a>Zwykły zawartości

Edytuj **.TT —** plik zawierający tekst, który ma być aplikację do wygenerowania. Na przykład:

```html
<html><body>
<h1>Sales for January</h2>
<!-- table to be inserted here -->
This report is Company Confidential.
</body></html>
```

### <a name="embedded-program-code"></a>Osadzony kod programów

Możesz wstawić kod programu między `<#` i `#>`. Na przykład:

```csharp
<table>
    <# for (int i = 1; i <= 10; i++)
       { #>
         <tr><td>Test name <#= i #> </td>
             <td>Test value <#= i * i #> </td> </tr>
    <# } #>
 </table>
```

```vb
<table>
<#
    For i As Integer = 1 To 10
#>
    <tr><td>Test name <#= i #> </td>
      <td>Test value <#= i*i #> </td></tr>
<#
    Next
#>
</table>
```

Należy zauważyć, że instrukcje są wstawiane `<# ... #>` i wyrażenia są wstawiane `<#= ... #>`. Aby uzyskać więcej informacji, zobacz [pisanie szablonu tekstowego T4](../modeling/writing-a-t4-text-template.md).

## <a name="using-the-template"></a>Przy użyciu szablonu

### <a name="the-code-built-from-the-template"></a>Kod zbudowane na podstawie szablonu

Po zapisaniu **.TT —** pliku zależnej **.cs** lub **.vb** plik został wygenerowany. Aby wyświetlić ten plik w Eksploratorze rozwiązań, rozwiń węzeł **.TT —** węzła plików. W projektach Visual Basic, należy najpierw wybrać **Pokaż wszystkie pliki** na pasku narzędzi Eksplorator rozwiązań.

Powiadomienie, że pomocniczy plik zawiera częściowej klasy, która zawiera metodę o nazwie `TransformText()`. Ta metoda jest wywoływana z poziomu aplikacji.

### <a name="generating-text-at-run-time"></a>Generowanie tekstu w czasie wykonywania

W kodzie aplikacji można wygenerować zawartość szablonu przy użyciu wywołania następująco:

```csharp
MyWebPage page = new MyWebPage();
String pageContent = page.TransformText();
System.IO.File.WriteAllText("outputPage.html", pageContent);
```

```vb
Dim page = New My.Templates.MyWebPage
Dim pageContent = page.TransformText()
System.IO.File.WriteAllText("outputPage.html", pageContent)
```

Aby umieścić wygenerowanej klasy w określonej przestrzeni nazw, należy ustawić **Namespace narzędzie niestandardowe** właściwości pliku szablonu tekstowego.

### <a name="debugging-runtime-text-templates"></a>Szablony tekstowe środowiska uruchomieniowego debugowania

Debugowania i testowania szablonów tekstowych środowiska uruchomieniowego w taki sam sposób jak zwykłe kodu.

Można ustawić punktu przerwania w szablonu tekstowego. Po uruchomieniu aplikacji w trybie debugowania w programie Visual Studio można wykonywać krokowo kodu i ocenić Czujka wyrażeń w zwykły sposób.

### <a name="passing-parameters-in-the-constructor"></a>Przekazywanie parametrów w Konstruktorze

Zazwyczaj szablonu należy zaimportować niektóre dane z innych części aplikacji. Aby ułatwić to, kod utworzony przez szablon jest klasy częściowej. Można utworzyć inną część tej samej klasy w innym pliku w projekcie. Ten plik może zawierać konstruktora z parametrami, właściwości i funkcje, które mogą być dostępne zarówno kod, który jest osadzony w szablonie i w pozostałej części aplikacji.

Na przykład można utworzyć oddzielny plik **MyWebPageCode.cs**:

```csharp
partial class MyWebPage
{
    private MyData m_data;
    public MyWebPage(MyData data) { this.m_data = data; }}
```

W pliku szablonu **MyWebPage.tt**, można zapisać:

```html
<h2>Sales figures</h2>
<table>
<# foreach (MyDataItem item in m_data.Items)
   // m_data is declared in MyWebPageCode.cs
   { #>
      <tr><td> <#= item.Name #> </td>
          <td> <#= item.Value #> </td></tr>
<# } // end of foreach
#>
</table>
```

Aby użyć tego szablonu w aplikacji:

```csharp
MyData data = ...;
MyWebPage page = new MyWebPage(data);
String pageContent = page.TransformText();
System.IO.File.WriteAllText("outputPage.html", pageContent);
```

#### <a name="constructor-parameters-in-visual-basic"></a>Parametry Konstruktora w języku Visual Basic

W języku Visual Basic, oddzielny plik **MyWebPageCode.vb** zawiera:

```vb
Namespace My.Templates
  Partial Public Class MyWebPage
    Private m_data As MyData
    Public Sub New(ByVal data As MyData)
      m_data = data
    End Sub
  End Class
End Namespace
```

Plik szablonu może zawierać:

```html
<#@ template language="VB" #>
<html><body>
<h1>Sales for January</h2>
<table>
<#
    For Each item In m_data.Items
#>
    <tr><td>Test name <#= item.Name #> </td>
      <td>Test value <#= item.Value #> </td></tr>
<#
    Next
#>
</table>
This report is Company Confidential.
</body></html>
```

Szablon może być wywoływany przez przekazanie parametru w Konstruktorze:

```vb
Dim data = New My.Templates.MyData
    ' Add data values here ....
Dim page = New My.Templates.MyWebPage(data)
Dim pageContent = page.TransformText()
System.IO.File.WriteAllText("outputPage.html", pageContent)
```

#### <a name="passing-data-in-template-properties"></a>Przekazywanie danych we właściwościach szablonu

Alternatywna metoda przekazywanie danych do szablonu jest pozwala dodać właściwości publicznej klasy szablonu w definicji klasy częściowej. Aplikację można ustawić właściwości przed wywołaniem `TransformText()`.

Można również dodać pola do klasy szablonu w definicji częściowej. Umożliwia przekazywanie danych pomiędzy kolejnymi wykonaniami szablonu.

### <a name="use-partial-classes-for-code"></a>Klasy częściowe używany dla kodu

Wielu deweloperów wolą unikać pisania dużych jednostek kodu w szablonach. Zamiast tego można zdefiniować metody w klasie częściowej, który ma taką samą nazwę jak plik szablonu. Wywołania tych metod z szablonu. W ten sposób więcej pokazuje szablonu wyraźnie jakie ciąg wyjście docelowego będzie wyglądać. Dyskusjach na temat wygląd wynik mogą być oddzielone od logiki tworzenia danych, który jest wyświetlany.

### <a name="assemblies-and-references"></a>Zestawy i odwołań

Jeśli chcesz, aby kod szablonu do odwołania .NET lub inne zestaw takich jak **System.Xml.dll**, dodaj go do projektu **odwołania** w zwykły sposób.

Jeśli chcesz zaimportować przestrzeni nazw w taki sam sposób jak `using` instrukcji, można to zrobić z `import` dyrektywy:

```
<#@ import namespace="System.Xml" #>
```

Dyrektywy te muszą znajdować się na początku pliku, natychmiast po `<#@template` dyrektywy.

### <a name="shared-content"></a>Zawartość udostępniona

Jeśli masz tekst, który jest współużytkowany kilku szablonów, można umieścić w osobnym pliku i dołączyć go w każdym pliku, w którym powinna zostać wyświetlona:

```
<#@include file="CommonHeader.txt" #>
```

Dołączonej zawartości może zawierać kombinację kodu programu i zwykły tekst i może zawierać inne obejmują dyrektywy i innych dyrektyw.

Dyrektywa include może służyć dowolne miejsce w tekście pliku szablonu lub dołączanego pliku.

### <a name="inheritance-between-run-time-text-templates"></a>Dziedziczenie między szablonami tekstu czasu wykonywania

Można udostępniać zawartość między szablonami środowiska wykonawczego, tworząc szablon klasy podstawowej, które mogą być abstrakcyjne. Użyj `inherits` parametr `<@#template#>` dyrektywy do odwołania innej klasy szablonu środowiska wykonawczego.

#### <a name="inheritance-pattern-fragments-in-base-methods"></a>Wzorzec dziedziczenia: fragmentów w podstawowej metody

We wzorcu używane w następującym przykładzie zwróć uwagę następujące kwestie:

- Klasa podstawowa `SharedFragments` definiuje metody w blokach funkcji klasy `<#+ ... #>`.

- Klasa podstawowa nie zawiera wolnych tekstu. Zamiast tego wszystkie jego bloki wystąpić wewnątrz metody funkcji klasy.

- Klasy pochodnej wywołuje metody zdefiniowane w `SharedFragments`.

- Wywołania aplikacji `TextTransform()` metody klasy pochodnej, ale nie przekształca klasy podstawowej `SharedFragments`.

- Szablony tekstowe środowiska uruchomieniowego; są klas podstawowych i pochodnych oznacza to **narzędzie niestandardowe** właściwość jest ustawiona na **texttemplatingfilepreprocessor —**.

**SharedFragments.tt:**

```
<#@ template language="C#" #>
<#+
protected void SharedText(int n)
{
#>
   Shared Text <#= n #>
<#+
}
// Insert more methods here if required.
#>
```

**MyTextTemplate1.tt:**

```
<#@ template language="C#" inherits="SharedFragments" #>
begin 1
   <# SharedText(2); #>
end 1
```

**MyProgram.cs:**

```csharp
...
MyTextTemplate1 t1  = new MyTextTemplate1();
string result = t1.TransformText();
Console.WriteLine(result);
```

**Dane wyjściowe:**

```
begin 1
    Shared Text 2
end 1
```

#### <a name="inheritance-pattern-text-in-base-body"></a>Wzorzec dziedziczenia: Tekst w podstawowej treści

W tym o innym podejściu do przy użyciu szablonu dziedziczenia zbiorczego tekst jest zdefiniowany w szablonie podstawowej. Pochodne Szablony zapewniają danych i fragmenty tekstu, który mieści się w podstawowej zawartości.

**AbstractBaseTemplate1.tt:**

```
<#@ template language="C#" #>

Here is the description for this derived template:
  <#= this.Description #>

Here is the fragment specific to this derived template:
<#
  this.PushIndent("  ");
  SpecificFragment(42);
  this.PopIndent();
#>
End of common template.
<#+
  // State set by derived class before calling TextTransform:
  protected string Description = "";
  // 'abstract' method to be defined in derived classes:
  protected virtual void SpecificFragment(int n) { }
#>
```

**DerivedTemplate1.tt:**

```
<#@ template language="C#" inherits="AbstractBaseTemplate1" #>
<#
  // Set the base template properties:
  base.Description = "Description for this derived class";

  // Run the base template:
  base.TransformText();

#>
End material for DerivedTemplate1.

<#+
// Provide a fragment specific to this derived template:

protected override void SpecificFragment(int n)
{
#>
   Specific to DerivedTemplate1 : <#= n #>
<#+
}
#>
```

**Kod aplikacji:**

```csharp
...
DerivedTemplate1 t1 = new DerivedTemplate1();
string result = t1.TransformText();
Console.WriteLine(result);
```

**Dane wyjściowe:**

```
Here is the description for this derived template:
  Description for this derived class

Here is the fragment specific to this derived template:
     Specific to DerivedTemplate1 : 42
End of common template.
End material for DerivedTemplate1.
```

## <a name="related-topics"></a>Tematy pokrewne

Podczas projektowania szablonów: Jeśli chcesz użyć szablonu, aby wygenerować kod który staje się częścią aplikacji, zobacz [generowanie kodu czasu projektowania przy użyciu szablonów tekstowych T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md).

Szablony środowiska wykonawczego mogą być używane w dowolnej aplikacji, w którym szablonów i jego zawartość są określane w czasie kompilacji. Ale jeśli chcesz zapisać rozszerzenia programu Visual Studio, które generuje tekst na podstawie szablonów, które zmieniają się w czasie wykonywania, zobacz [wywoływanie transformacji tekstu w rozszerzeniu VS](../modeling/invoking-text-transformation-in-a-vs-extension.md).

## <a name="see-also"></a>Zobacz także

- [Generowanie kodu i szablony tekstowe T4](../modeling/code-generation-and-t4-text-templates.md)
- [Pisanie szablonu tekstowego T4](../modeling/writing-a-t4-text-template.md)
- [Przybornik T4](http://olegsych.com/T4Toolbox/)
