---
title: Wywoływanie transformacji tekstu w rozszerzeniu VS
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 20c4c9e9c91fd93a190463bc35fe016be4cdf838
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="invoking-text-transformation-in-a-vs-extension"></a>Wywoływanie transformacji tekstu w rozszerzeniu VS
Jeśli piszesz rozszerzenia programu Visual Studio, takich jak polecenia menu lub [języka specyficznego dla domeny](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md), można użyć usługi tworzenia szablonów tekstowych do transformacji szablonów tekstowych. Pobierz <xref:Microsoft.VisualStudio.TextTemplating.VSHost.STextTemplating> usługi i rzutować obiekt <xref:Microsoft.VisualStudio.TextTemplating.VSHost.ITextTemplating>.

## <a name="getting-the-text-templating-service"></a>Pobieranie usługi szablonów tekstowych

```csharp
using Microsoft.VisualStudio.TextTemplating;
using Microsoft.VisualStudio.TextTemplating.VSHost;
...
// Get a service provider - how you do this depends on the context:
IServiceProvider serviceProvider = ...; // An instance of EnvDTE, for example

// Get the text template service:
ITextTemplating t4 = serviceProvider.GetService(typeof(STextTemplating)) as ITextTemplating;

// Process a text template:
string result = t4.ProcessTemplate(filePath, System.IO.File.ReadAllText(filePath));

```

## <a name="passing-parameters-to-the-template"></a>Przekazywanie parametrów do szablonu
 Parametry można przekazać do szablonu. W szablonie, można uzyskać wartości parametrów za pomocą `<#@parameter#>` dyrektywy.

 Jeśli chodzi o typ parametru należy użyć typu, który jest możliwy do serializacji lub który może być organizowany. Oznacza to, typ musi być zadeklarowany ze <xref:System.SerializableAttribute>, lub musi pochodzić od <xref:System.MarshalByRefObject>. To ograniczenie jest konieczne, ponieważ szablon tekstowy jest wykonywany w oddzielnym elemencie AppDomain. Wszystkie typy wbudowane, takie jak **System.String** i **System.Int32** jest możliwy do serializacji.

 Aby przekazać wartości parametrów, kod wywołujący może umieścić wartości albo w `Session` słownika, lub w <xref:System.Runtime.Remoting.Messaging.CallContext>.

 W poniższym przykładzie użyto obu tych metod, aby przekształcić krótki szablon tekstowy:

```
using Microsoft.VisualStudio.TextTemplating;
using Microsoft.VisualStudio.TextTemplating.VSHost;
...
// Get a service provider - how you do this depends on the context:
IServiceProvider serviceProvider = dte;

// Get the text template service:
ITextTemplating t4 = serviceProvider.GetService(typeof(STextTemplating)) as ITextTemplating;
ITextTemplatingSessionHost sessionHost = t4 as ITextTemplatingSessionHost;

// Create a Session in which to pass parameters:
sessionHost.Session = sessionHost.CreateSession();
sessionHost.Session["parameter1"] = "Hello";
sessionHost.Session["parameter2"] = DateTime.Now;

// Pass another value in CallContext:
System.Runtime.Remoting.Messaging.CallContext.LogicalSetData("parameter3", 42);

// Process a text template:
string result = t4.ProcessTemplate("",
   // This is the test template:
   "<#@parameter type=\"System.String\" name=\"parameter1\"#>"
 + "<#@parameter type=\"System.DateTime\" name=\"parameter2\"#>"
 + "<#@parameter type=\"System.Int32\" name=\"parameter3\"#>"
 + "Test: <#=parameter1#>    <#=parameter2#>    <#=parameter3#>");

// This test code yields a result similar to the following line:
//     Test: Hello    07/06/2010 12:37:45    42

```

## <a name="error-reporting-and-the-output-directive"></a>Raportowanie błędów i dyrektywa wyjściowa
 Błędów powstających podczas przetwarzania będą wyświetlane w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] okno błędów. Ponadto użytkownik może powiadamiany błędów, określając wywołania zwrotnego, który implementuje <xref:Microsoft.VisualStudio.TextTemplating.VSHost.ITextTemplatingCallback>.

 Jeśli chcesz zapisać ciąg wyniku do pliku, warto wiedzieć, jakie rozszerzenia pliku i kodowanie zostali określeni na liście `<#@output#>` dyrektywy w szablonie. Te informacje również zostaną przekazane do wywołania zwrotnego. Aby uzyskać więcej informacji, zobacz [dyrektywa T4 Output](../modeling/t4-output-directive.md).

```csharp
void ProcessMyTemplate(string MyTemplateFile)
{
  string templateContent = File.ReadAllText(MyTemplateFile);
  T4Callback cb = new T4Callback();
  // Process a text template:
  string result = t4.ProcessTemplate(MyTemplateFile, templateContent, cb);
  // If there was an output directive in the MyTemplateFile,
  // then cb.SetFileExtension() will have been called.
  // Determine the output file name:
  string resultFileName =
    Path.Combine(Path.GetDirectoryName(MyTemplateFile),
        Path.GetFileNameWithoutExtension(MyTemplateFile))
      + cb.fileExtension;
  // Write the processed output to file:
  File.WriteAllText(resultFileName, result, cb.outputEncoding);
  // Append any error messages:
  if (cb.errorMessages.Count > 0)
  {
    File.AppendAllLines(resultFileName, cb.errorMessages);
  }
}

class T4Callback : ITextTemplatingCallback
{
  public List<string> errorMessages = new List<string>();
  public string fileExtension = ".txt";
  public Encoding outputEncoding = Encoding.UTF8;

  public void ErrorCallback(bool warning, string message, int line, int column)
  { errorMessages.Add(message); }

  public void SetFileExtension(string extension)
  { fileExtension = extension; }

  public void SetOutputEncoding(Encoding encoding, bool fromOutputDirective)
  { outputEncoding = encoding; }
}

```

 Kod może być testowany z plikiem szablonu, podobnym do następującego:

```
<#@output extension=".htm" encoding="ASCII"#>
<# int unused;  // Compiler warning "unused variable"
#>
Sample text.
```

 Ostrzeżenie kompilatora będą wyświetlane w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] błędów w oknie, a także Generowanie wywołania `ErrorCallback`.

## <a name="reference-parameters"></a>Parametry odwołania
 Można przekazać wartości z szablonu tekstowego za pomocą parametru klasę, która jest pochodną <xref:System.MarshalByRefObject>.

## <a name="related-topics"></a>Tematy pokrewne
 Do generowania tekstu z szablonu tekstowego wstępnie przetworzonych: wywołanie `TransformText()` metody wygenerowanej klasy. Aby uzyskać więcej informacji, zobacz [Generowanie tekstu czasu wykonywania z szablonów tekstowych T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

 Do generowania tekstu poza [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rozszerzenia: definiowanie hosta niestandardowego. Aby uzyskać więcej informacji, zobacz [przetwarzanie szablonów tekstowych przy użyciu hosta niestandardowego](../modeling/processing-text-templates-by-using-a-custom-host.md).

 Aby wygenerować kod źródłowy, który można później można skompilować ani wykonywać: wywołanie `t4.PreprocessTemplate()` metody <xref:Microsoft.VisualStudio.TextTemplating.VSHost.ITextTemplating>.
