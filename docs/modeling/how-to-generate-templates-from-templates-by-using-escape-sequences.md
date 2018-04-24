---
title: 'Porady: generowanie szablonów z szablonów przy użyciu sekwencji unikowych'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, generating templates from templates
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: d7c53657faa23b57e3aef45ff8c404f2d326e489
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="how-to-generate-templates-from-templates-by-using-escape-sequences"></a>Porady: generowanie szablonów z szablonów przy użyciu sekwencji unikowych
Można utworzyć szablon tekst, który tworzy innego szablonu tekstowego jako dane wyjściowe wygenerowane tekstu. Aby to zrobić, możesz korzystać sekwencji unikowych do odróżniać znaczniki szablonu tekstowego. Jeśli nie używasz sekwencji unikowych, szablon wygenerowanego tekstu ma wstępnie zdefiniowane znaczenie. Aby uzyskać więcej informacji o użyciu sekwencji unikowych w szablonach tekstowych, zobacz [przy użyciu sekwencji unikowych w szablonach tekstowych](../modeling/using-escape-sequences-in-text-templates.md).

### <a name="to-generate-a-text-template-from-within-a-text-template"></a>Aby wygenerować szablonu tekstowego z szablonu tekstowego

-   Użyj kreska ułamkowa odwrócona (\\) jako znaku ucieczki tworzy niezbędne znaczników w szablonie tekst dyrektywy instrukcje, wyrażenia i funkcji w pliku tekstowym oddzielnego szablonu klasy.

    ```
    \<#@ directive \#>
    \<# statement \#>
    \<#= expression \#>
    \<#+ classfeature \#>
    ```

## <a name="example"></a>Przykład
 W poniższym przykładzie użyto znaki specjalne w celu utworzenia szablonu tekstowego z szablonu tekstowego. `output` Dyrektywa określa typ pliku docelowego na typ pliku szablonu tekstowego (.TT —).

```csharp
\<#@ output extension=".tt" \#>
\<#@ assembly name="System.Xml.dll" \#>
\<#@ import namespace="System.Xml" \#>
\<#
XmlDocument xDoc = new XmlDocument();
//System.Diagnostics.Debugger.Break();
    xDoc.Load(@"E:\CSharp\Overview.xml");
    XmlAttributeCollection attributes = xDoc.Attributes;
    if (attributes != null)
    {
       foreach (XmlAttribute attr in attributes)
       {\#>
           \<#= attr.Name \#>
       \<#}
     }
\#>
```

 Wygenerowany tekst wyjściowy jest szablonu tekstowego.

```
<#@ output extension=".tt" #>
<#@ assembly name="System.Xml.dll" #>
<#@ import namespace="System.Xml" #>
<#
XmlDocument xDoc = new XmlDocument();
//System.Diagnostics.Debugger.Break();
    xDoc.Load(@"E:\CSharp\Overview.xml");
    XmlAttributeCollection attributes = xDoc.Attributes;
    if (attributes != null)
    {
       foreach (XmlAttribute attr in attributes)
       {#>
           <#= attr.Name #>
       <#}
     }
#>
```