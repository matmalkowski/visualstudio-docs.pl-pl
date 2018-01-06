---
title: "Uzyskiwanie dostępu do programu Visual Studio lub innych hostów z szablonu tekstowego | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a68886da-7416-4785-8145-3796bb382cba
caps.latest.revision: "5"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: cc0f756637921b9f470e744ec8875ba3a2b54012
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="accessing-visual-studio-or-other-hosts-from-a-text-template"></a>Dostęp do Visual Studio lub innych hostów z szablonu tekstowego
W szablonie tekstu, można użyć metody i właściwości udostępniane przez hosta, która wykonuje szablonu, takie jak [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Dotyczy to szablony zwykłego tekstu, szablony nieprzetworzony tekstu.  
  
## <a name="obtaining-access-to-the-host"></a>Uzyskiwanie dostępu do hosta  
 Ustaw `hostspecific="true"` w `template` dyrektywy. Dzięki temu można używać `this.Host`, który ma typ <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>. Ten typ ma elementów członkowskich, które, na przykład do rozpoznawania nazw plików i służy do rejestrowania błędów.  
  
### <a name="resolving-file-names"></a>Rozpoznawanie nazw plików  
 Aby znaleźć Pełna ścieżka pliku względem szablonu tekstowego, użyj tego. Host.ResolvePath().  
  
```csharp  
<#@ template hostspecific="true" language="C#" #>  
<#@ output extension=".txt" #>  
<#@ import namespace="System.IO" #>  
<#  
 // Find a path within the same project as the text template:  
 string myFile = File.ReadAllText(this.Host.ResolvePath("MyFile.txt"));  
#>  
Content of myFile is:  
<#= myFile #>  
  
```  
  
### <a name="displaying-error-messages"></a>Wyświetlanie komunikatów o błędach  
 W tym przykładzie rejestruje komunikaty podczas transformacji szablonu. Jeśli host znajduje się [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], są one dodawane do okna błędu.  
  
```csharp  
<#@ template hostspecific="true" language="C#" #>  
<#@ output extension=".txt" #>  
<#@ import namespace="System.CodeDom.Compiler" #>  
<#  
  string message = "test message";  
  this.Host.LogErrors(new CompilerErrorCollection()   
    { new CompilerError(  
       this.Host.TemplateFile, // Identify the source of the error.  
       0, 0, "0",   // Line, column, error ID.  
       message) }); // Message displayed in error window.  
#>  
  
```  
  
## <a name="using-the-visual-studio-api"></a>Za pomocą programu Visual Studio interfejsu API  
 Jeśli wykonujesz kompilację szablonu tekstowego w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], można użyć `this.Host` dostęp do usług świadczonych przez [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] oraz pakiety lub rozszerzenia, które zostały załadowane.  
  
 Wartość hostspecific = "true" i rzutowania `this.Host` do <xref:System.IServiceProvider>.  
  
 W tym przykładzie pobiera [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] interfejsu API, <xref:EnvDTE.DTE>, jako usługa:  
  
```csharp  
<#@ template hostspecific="true" language="C#" #>  
<#@ output extension=".txt" #>  
<#@ assembly name="EnvDTE" #>  
<#@ import namespace="EnvDTE" #>  
<#   
 IServiceProvider serviceProvider = (IServiceProvider)this.Host;  
 DTE dte = serviceProvider.GetService(typeof(DTE)) as DTE;    
#>  
Number of projects in this solution: <#=  dte.Solution.Projects.Count #>  
  
```  
  
## <a name="using-hostspecific-with-template-inheritance"></a>Przy użyciu hostSpecific z dziedziczenia szablonu  
 Określ `hostspecific="trueFromBase"` Jeśli używasz również `inherits` atrybutu, i w razie dziedziczyć szablon, który określa `hostspecific="true"`. Dzięki temu można uniknąć ostrzeżenia kompilatora efekt który właściwość `Host` została zadeklarowana dwa razy.