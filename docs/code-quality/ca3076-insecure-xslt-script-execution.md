---
title: 'CA3076: Wykonywanie skryptu niezabezpieczonych XSLT | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9793d0af1c2207b5201cb9e0e7bebe0d7bf4ef1c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="ca3076-insecure-xslt-script-execution"></a>CA3076: Wykonywanie skryptu niezabezpieczonych XSLT

|||  
|-|-|  
|TypeName|InsecureXSLTScriptExecution|  
|CheckId|CA3076|  
|Kategoria|Microsoft.Security|  
|Zmiana kluczowa|Bez podziału|  

## <a name="cause"></a>Przyczyna

Jeśli nimi wykonane arkusze stylów języka przekształcenia XSLT (Extensible) w aplikacjach .NET, procesor może rozwiązać niezaufanych odwołań do identyfikatora URI, które można ujawnić poufne informacje do osoby atakujące, co może prowadzić do odmowy usługi i Cross-Site ataki. Aby uzyskać więcej informacji, zobacz [Considerations(.NET Guide) zabezpieczeń XSLT](/dotnet/standard/data/xml/xslt-security-considerations).

## <a name="rule-description"></a>Opis reguły

**XSLT** jest standardem sieci World Wide Web konsorcjum W3C do transformacji danych XML. XSLT jest zwykle używana podczas zapisu arkusze stylów do transformacji danych XML w innych formatach, takich jak HTML, stała długość tekstu, tekst rozdzielany przecinkami lub innego formatu XML. Mimo że zabronione domyślnie, możesz ją włączyć dla projektu.

Aby upewnić się, nie jest ujawniany ataku, ta zasada wyzwala po każdej zmianie XslCompiledTransform.<xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> odbiera wystąpień niezabezpieczonych kombinacja <xref:System.Xml.Xsl.XsltSettings> i <xref:System.Xml.XmlResolver>, która pozwala na przetwarzanie złośliwy skrypt.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

- Zastąp niezabezpieczonych argument XsltSettings XsltSettings.<xref:System.Xml.Xsl.XsltSettings.Default%2A> lub z wystąpieniem, które ma wyłączone dokumentu wykonywania funkcji i skryptów.

- Zastąp <xref:System.Xml.XmlResolver> argument o wartości null lub <xref:System.Xml.XmlSecureResolver> wystąpienia.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Jeśli nie masz pewności, czy dane wejściowe jest znany jako z zaufanego źródła, nie Pomijaj reguły z to ostrzeżenie.

## <a name="pseudo-code-examples"></a>Przykłady pseudo-kodu

### <a name="violationmdashuses-xsltsettingstrustedxslt"></a>Naruszenie&mdash;używa XsltSettings.TrustedXslt

```csharp
using System.Xml;  
using System.Xml.Xsl;  
  
namespace TestNamespace   
{   
    class TestClass   
    {  
         void TestMethod()
        {    
             XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();
             var settings = XsltSettings.TrustedXslt;
             var resolver = new XmlUrlResolver();
             xslCompiledTransform.Load("testStylesheet", settings, resolver); // warn   
        }  
    }
} 
```

### <a name="solutionmdashuse-xsltsettingsdefault"></a>Rozwiązanie&mdash;Użyj XsltSettings.Default

```csharp
using System.Xml;
using System.Xml.Xsl;

namespace TestNamespace
{
    class TestClass
    {
        void TestMethod()
        {
            XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();
            var settings = XsltSettings.Default;
            var resolver = new XmlUrlResolver();
            xslCompiledTransform.Load("testStylesheet", settings, resolver);
        }
    }
}
```

### <a name="violationmdashdocument-function-and-script-execution-not-disabled"></a>Naruszenie&mdash;dokumentu wykonywania funkcji i skryptów nie jest wyłączone

```csharp
using System.Xml;
using System.Xml.Xsl;
  
namespace TestNamespace   
{   
    class TestClass   
    {   
        private static void TestMethod(XsltSettings settings)
        {   
            try   
            {   
                XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();
                var resolver = new XmlUrlResolver();
                xslCompiledTransform.Load("testStylesheet", settings, resolver); // warn
            }
            catch { throw; }
            finally { }
        }
    }
}
```

### <a name="solutionmdashdisable-document-function-and-script-execution"></a>Rozwiązanie&mdash;wyłączyć wykonanie funkcji i skryptów dokumentu

```csharp
using System.Xml;
using System.Xml.Xsl;

namespace TestNamespace
{
    class TestClass
    {
        private static void TestMethod(XsltSettings settings)
        {
            try
            {
                XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();
                settings.EnableDocumentFunction = false;
                settings.EnableScript = false;
                var resolver = new XmlUrlResolver();
                xslCompiledTransform.Load("testStylesheet", settings, resolver);
            }
            catch { throw; }
            finally { }
        }
    }
}
```

## <a name="see-also"></a>Zobacz także

[Zagadnienia dotyczące zabezpieczeń XSLT (Przewodnik .NET)](/dotnet/standard/data/xml/xslt-security-considerations)