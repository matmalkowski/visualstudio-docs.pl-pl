---
title: Bloki formantów szablonów tekstowych
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, template code
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: f0fa4a3848fedae642c6471dd001933ca1b7d011
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="text-template-control-blocks"></a>Bloki formantów szablonów tekstowych
Bloki kontroli umożliwiają pisanie kodu w szablonie tekst w celu różnią się dane wyjściowe. Istnieją trzy rodzaje bloków kontroli, które można rozróżnić za ich otwierające nawiasy:

-   `<# Standard control blocks #>` może zawierać instrukcji.

-   `<#= Expression control blocks #>` może zawierać wyrażenia.

-   `<#+ Class feature control blocks #>` może zawierać metod, pól i właściwości.

## <a name="standard-control-block"></a>Blok formantu standardowego
 Bloki formantu standardowego zawierają instrukcje. Na przykład następujący blok standardowe pobiera nazwy wszystkich atrybutów w dokumencie XML:

```
<#@ assembly name="System.Xml.dll" #>
<#@ import namespace="System.Xml" #>

<#
    List<string> allAttributes = new List<string>();
    XmlDocument xDoc = new XmlDocument();
    xDoc.Load(@"E:\CSharp\Overview.xml");
    XmlAttributeCollection attributes = xDoc.Attributes;
    if (attributes.Count > 0)
    {
       foreach (XmlAttribute attr in attributes)
       {
           allAtributes.Add(attr.Name);
       }
     }
#>
```

 Można osadzić zwykły tekst wewnątrz instrukcji złożonej, takich jak `if` lub `for`. Na przykład ten fragment generuje dane wyjściowe wiersza w każdej iteracji pętli:

```
<#
       foreach (XmlAttribute attr in attributes)
       {
#>
Found another one!
<#
           allAtributes.Add(attr.Name);
       }
#>
```

> [!WARNING]
>  Zawsze używaj {...} Aby ograniczyć zagnieżdżonych instrukcji, które zawierają osadzone zwykłego tekstu. Poniższy przykład może nie działać prawidłowo:
>
>  `<# if (ShouldPrint) #> Some text. -- WRONG`
>
>  Zamiast tego należy uwzględnić {nawiasów klamrowych}, w następujący sposób:

```

<#
 if (ShouldPrint)
 {   //  "{" REQUIRED
#>
Some text.
<#
 }
#>

```

## <a name="expression-control-block"></a>Blok kontroli wyrażenia
 Wyrażenie bloków sterowania są używane do kodu, który zawiera ciągi do zapisania do pliku wyjściowego. Na przykład z powyższym przykładzie można drukować nazwy atrybutów do pliku wyjściowego, zmieniając następujący blok kodu:

```
<#
    XmlDocument xDoc = new XmlDocument();
    xDoc.Load(@"E:\CSharp\Overview.xml");
    XmlAttributeCollection attributes = xDoc.Attributes;
    if (attributes != null)
    {
       foreach (XmlAttribute attr in attributes)
       {
#><#= attr.Name #><#
       }
    }
#>
```

## <a name="class-feature-control-block"></a>Blok kontroli funkcji klasy
 Bloków sterowania funkcji klasy służy do dodawania metod, właściwości, pola lub nawet zagnieżdżonych klas do szablonu tekstu. Najczęściej używane bloki funkcji klasy jest zapewnienie funkcji pomocnika dla kodu innych części szablonu tekstowego. Na przykład następujące bloku funkcji klasy zamienia pierwszą literę nazwy atrybutu na wielkie (lub, jeśli nazwa zawiera spacji, powoduje rozpoczynanie pierwszą literę każdego wyrazu):

```
<#@ import namespace="System.Globalization" #>
```

```
<#+
    private string FixAttributeName(string name)
    {
        return CultureInfo.CurrentCulture.TextInfo.ToTitleCase(name);
    }
#>
```

> [!NOTE]
>  Formant bloku funkcji klasy nie musi następować formantu standardowego bloków w tym samym pliku szablonu. Jednak to ograniczenie nie ma zastosowania do wyniku przy użyciu `<#@include#>` dyrektywy. Każdy plik dołączony może mieć standardowych bloków następuje bloki funkcji klasy.

 Można utworzyć funkcję, która generuje dane wyjściowe osadzanie tekstu i wyrażenia bloki wewnątrz bloku kontroli funkcji klasy. Na przykład:

```
<#+
    private void OutputFixedAttributeName(string name)
    {
#>
 Attribute:  <#= CultureInfo.CurrentCulture.TextInfo.ToTitleCase(name) #>
<#+  // <<< Notice that this is also a class feature block.
    }
#>
```

 Tej funkcji można wywołać z standardowego bloku lub innego bloku funkcji klasy:

```
<# foreach (Attribute attribute in item.Attributes)
{
  OutputFixedAttributeName(attribute.Name);
}
#>
```

## <a name="how-to-use-control-blocks"></a>Jak używać bloków sterowania
 Cały kod we wszystkich bloków sterowania standard i wyrażenia w jednym szablonie (w tym cały kod w szablonach uwzględnione) są łączone do formularza `TransformText()` metoda wygenerowanego kodu. (Aby uzyskać więcej informacji o tym innych szablonów tekstowych z `include` dyrektywy, zobacz [dyrektywy szablonu tekstowego T4](../modeling/t4-text-template-directives.md).)

 Użytkownik należy mieć na uwadze następujące zagadnienia dotyczące używania bloków sterowania:

-   **Język.** C# lub Visual Basic kodu można użyć w szablonie tekstu. Jest to domyślny język C#, ale można określić języka Visual Basic z `language` parametr `template` dyrektywy. (Aby uzyskać więcej informacji na temat `template` dyrektywy, zobacz [dyrektywy szablonu tekstowego T4](../modeling/t4-text-template-directives.md).)

     Język, którego używasz w blokach formantu nie ma nic wspólnego z języka lub formatu tekstu, który można wygenerować w szablonu tekstowego. Możesz wygenerować C# za pomocą języka Visual Basic kodu ani na odwrót.

     Można użyć tylko jednego języka w szablonie danego tekstu, w tym szablony tekstu uwzględnione w `include` dyrektywy.

-   **Zmienne lokalne.** Ponieważ blokuje cały kod w formancie standard i wyrażenia szablonu tekstowego jest generowane jako pojedynczej metody, należy należy upewnić się, że nie ma żadnych konfliktów nazw zmiennych lokalnych. W przypadku dołączania innych szablonów tekstowych, należy się upewnić czy zmienna nazwy są unikatowe w zawarte szablonów. Jest jednym ze sposobów zapewnienia, aby dodać parametry do każda nazwa zmiennej lokalnej identyfikowanie szablonu tekstowego, w którym został zadeklarowany.

     Jest również dobrym rozwiązaniem jest zainicjowanie zmiennych lokalnych do wartości za pośrednictwem przy deklarowaniu, zwłaszcza w przypadku dołączania wielu szablonów tekstowych.

-   **Zagnieżdżanie bloków sterowania.** Bloki kontroli nie mogą być zagnieżdżone wewnątrz siebie nawzajem. Zawsze musi wygasać bloku danego formantu, zanim otworzysz kolejnego. Na przykład poniżej przedstawiono sposób drukowania część tekstu w bloku wyrażenie jako część bloku formantu standardowego.

    ```
    <#
    int x = 10;
    while (x-- > 0)
    {
    #>
    <#= x #>
    <# } #>
    ```

-   **Refaktoryzacji.** Aby zachować szablony tekstu krótko- i łatwy do zrozumienia, zdecydowanie zaleca się unikanie kodu powtarzających się przez factoring do ponownego użycia kodu do funkcji pomocnika w blokach funkcji klasy lub tworząc własne klasy szablonu tekstu, która dziedziczy z klasy element Microsoft.VisualStudio.TextTemplating.TextTransformation.