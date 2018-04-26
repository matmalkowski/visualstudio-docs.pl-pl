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
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 13ca6a9aef2f0944ba1f42c849d9f8079a56a82b
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
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