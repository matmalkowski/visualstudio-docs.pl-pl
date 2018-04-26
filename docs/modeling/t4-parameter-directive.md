---
title: Dyrektywa T4 dotycząca parametru
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 1f12363af0d0b26aa72c5478df5da82c6d4fd02a
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="t4-parameter-directive"></a>Dyrektywa T4 dotycząca parametru

W [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] szablonu tekstowego `parameter` dyrektywy deklaruje właściwości w kodzie szablonu, które są inicjowane z wartości przekazane z zewnętrznego kontekstu. Te wartości można ustawić podczas pisania kodu, który wywołuje transformacji tekstu.

## <a name="using-the-parameter-directive"></a>Użycie dyrektywy parametru

```
<#@ parameter type="Full.TypeName" name="ParameterName" #>
```

 `parameter` Dyrektywy deklaruje właściwości w kodzie szablonu, które są inicjowane z wartości przekazane z zewnętrznego kontekstu. Te wartości można ustawić podczas pisania kodu, który wywołuje transformacji tekstu. Wartości mogą być przekazywane w `Session` słownika, lub w <xref:System.Runtime.Remoting.Messaging.CallContext>.

 Można zadeklarować parametrów dowolnego typu może być zastosowana zdalnie. Oznacza to, typ musi być zadeklarowany ze <xref:System.SerializableAttribute>, lub musi pochodzić od <xref:System.MarshalByRefObject>. Dzięki temu wartości parametrów do przekazania do elementu AppDomain, w którym szablon jest przetwarzany.

 Na przykład można zapisać szablonu tekstowego o następującej treści:

```
<#@ template language="C#" #>

<#@ parameter type="System.Int32" name="TimesToRepeat" #>

<# for (int i = 0; i < TimesToRepeat; i++) { #>
Line <#= i #>
<# } #>

```

## <a name="passing-parameter-values-to-a-template"></a>Przekazywanie wartości parametrów szablonu
 Jeśli piszesz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rozszerzenia takich jak polecenie menu, program obsługi zdarzeń, może przetwarzać szablonu za pomocą usługi tworzenia szablonów tekstowych:

```csharp
// Get a service provider - how you do this depends on the context:
IServiceProvider serviceProvider = dte; // or dslDiagram.Store, for example
// Get the text template service:
ITextTemplating t4 = serviceProvider.GetService(typeof(STextTemplating)) as ITextTemplating;
ITextTemplatingSessionHost host = t4 as ITextTemplatingSessionHost;
// Create a Session in which to pass parameters:
host.Session = host.CreateSession();
// Add parameter values to the Session:
session["TimesToRepeat"] = 5;
// Process a text template:
string result = t4.ProcessTemplate("MyTemplateFile.t4",
  System.IO.File.ReadAllText("MyTemplateFile.t4"));

```

## <a name="passing-values-in-the-call-context"></a>Przekazywanie wartości w kontekście wywołania
 Można również dane można przekazać wartości logicznych w <xref:System.Runtime.Remoting.Messaging.CallContext>.

 Poniższy przykład przekazuje wartości za pomocą obu metod:

```csharp
ITextTemplating t4 = this.Store.GetService(typeof(STextTemplating)) as ITextTemplating;
ITextTemplatingSessionHost host = t4 as ITextTemplatingSessionHost;
host.Session = host.CreateSession();
// Pass a value in Session:
host.Session["p1"] = 32;
// Pass another value in CallContext:
System.Runtime.Remoting.Messaging.CallContext.LogicalSetData("p2", "test");

// Process a small template inline:
string result = t4.ProcessTemplate("",
   "<#@parameter type=\"System.Int32\" name=\"p1\"#>"
 + "<#@parameter type=\"System.String\" name=\"p2\"#>"
 + "Test <#=p1#> <#=p2#>");

// Result value is:
//     Test 32 test

```

## <a name="passing-values-to-a-run-time-preprocessed-text-template"></a>Przekazanie wartości do szablonu tekstowego Run-Time (preprocesora)
 Nie jest to zazwyczaj koniecznych do używania `<#@parameter#>` dyrektywy z szablonów tekstowych (wstępnie przetworzonych) środowiska wykonawczego. Zamiast tego można zdefiniować dodatkowe konstruktora lub ustawialnej właściwości dla wygenerowanego kodu za pomocą którego można podać wartości parametrów. Aby uzyskać więcej informacji, zobacz [Generowanie tekstu czasu wykonywania z szablonów tekstowych T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

 Jednak jeśli chcesz użyć `<#@parameter>` w szablonie środowiska wykonawczego, można przekazać wartości do niej przy użyciu słownika sesji. Na przykład załóżmy, że plik został utworzony jako szablon wstępnie przetworzonych o nazwie `PreTextTemplate1`. Szablon w programie można wywołać przy użyciu następującego kodu.

```csharp
PreTextTemplate1 t = new PreTextTemplate1();
t.Session = new Microsoft.VisualStudio.TextTemplating.TextTemplatingSession();
t.Session["TimesToRepeat"] = 5;
// Add other parameter values to t.Session here.
t.Initialize(); // Must call this to transfer values.
string resultText = t.TransformText();

```

## <a name="obtaining-arguments-from-texttemplateexe"></a>Uzyskiwanie argumenty w TextTemplate.exe

> [!IMPORTANT]
>  `parameter` Dyrektywy nie pobiera wartości `-a` parametr `TextTransform.exe` narzędzia. Aby uzyskać te wartości, należy ustawić `hostSpecific="true"` w `template` dyrektywy i użyj `this.Host.ResolveParameterValue("","","argName")`.