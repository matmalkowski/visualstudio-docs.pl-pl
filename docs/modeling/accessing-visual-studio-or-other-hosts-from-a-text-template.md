---
title: Dostęp do Visual Studio lub innych hostów z szablonu tekstowego
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 171b3d3060ea00cc5adc9ca1220cb86148f8d883
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="access-visual-studio-or-other-hosts-from-a-text-template"></a>Dostęp do programu Visual Studio lub innych hostów z szablonu tekstowego

W szablonie tekstu można użyć metody i właściwości, które są udostępniane przez hosta, która wykonuje szablonu. Program Visual Studio jest przykładem hosta.

> [!NOTE]
> W szablonach zwykłym tekstem, ale nie można użyć właściwości i metod hosta *wstępnie przetworzony* szablonów tekstowych.

## <a name="obtain-access-to-the-host"></a>Uzyskaj dostęp do hosta

Aby uzyskać dostęp do hosta, należy ustawić `hostspecific="true"` w `template` dyrektywy. Teraz można używać `this.Host`, który ma typ <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>. <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost> Typ ma elementów członkowskich, które umożliwia, na przykład, rozpoznawanie nazw plików i dziennika błędów.

### <a name="resolve-file-names"></a>Rozpoznawanie nazw plików

Aby znaleźć Pełna ścieżka pliku względem szablonu tekstowego, należy użyć `this.Host.ResolvePath()`.

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

### <a name="display-error-messages"></a>Wyświetlane komunikaty o błędach

W tym przykładzie rejestruje komunikaty podczas transformacji szablonu. Jeśli host znajduje się programu Visual Studio, błędy są dodawane do **listy błędów**.

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

## <a name="use-the-visual-studio-api"></a>Za pomocą programu Visual Studio interfejsu API

Jeśli szablonu tekstowego są wykonywane w programie Visual Studio, możesz użyć `this.Host` dostęp do usług świadczonych przez Visual Studio oraz pakiety lub rozszerzenia, które zostały załadowane.

Wartość hostspecific = "true" i rzutowania `this.Host` do <xref:System.IServiceProvider>.

W tym przykładzie pobiera Visual Studio interfejsu API, <xref:EnvDTE.DTE>, jako usługa:

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

## <a name="use-hostspecific-with-template-inheritance"></a>HostSpecific za pomocą szablonu dziedziczenia

Określ `hostspecific="trueFromBase"` Jeśli używasz również `inherits` atrybutu, i w razie dziedziczyć szablon, który określa `hostspecific="true"`. Jeśli nie, można otrzymać kompilatora, ostrzeżenie, że właściwość `Host` została zadeklarowana dwa razy.