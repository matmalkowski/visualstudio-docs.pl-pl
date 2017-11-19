---
title: 'CA3076: Wykonywanie skryptu niezabezpieczonych XSLT | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 53cb7a46-c564-488f-bc51-0e210a7853c9
caps.latest.revision: "5"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5bf7da81e41a00bd0d673e3522f944dc17a549c9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ca3076-insecure-xslt-script-execution"></a>CA3076: Wykonywanie skryptu niezabezpieczonych XSLT
|||  
|-|-|  
|TypeName|InsecureXSLTScriptExecution|  
|CheckId|CA3076|  
|Kategoria|Microsoft.Security|  
|Zmiana kluczowa|Bez podziału|  
  
## <a name="cause"></a>Przyczyna  
 Jeśli zostanie wykonana [arkusze stylów języka przekształcenia XSLT (Extensible)](https://support.microsoft.com/en-us/kb/313997) w aplikacjach .NET nimi, procesor może [rozwiązać niezaufanych odwołuje się do identyfikatora URI](http://msdn.microsoft.com/en-us/ba3e4d4f-1ee7-4226-a51a-78a1f1b5bd8a) który można ujawnić poufne informacje na ataki, co może prowadzić do ataków typu "odmowa usługi" i Cross-Site.  
  
## <a name="rule-description"></a>Opis reguły  
 [XSLT](http://msdn.microsoft.com/en-us/6377ce5f-3c45-42a6-b7a9-ec8da588b60c) jest standardem sieci World Wide Web konsorcjum W3C do transformacji danych XML. XSLT jest zwykle używana podczas zapisu arkusze stylów do transformacji danych XML w innych formatach, takich jak HTML, stała długość tekstu, tekst rozdzielany przecinkami lub innego formatu XML. Mimo że zabronione domyślnie, możesz ją włączyć dla projektu.  
  
 Aby upewnić się, nie jest ujawniany ataku, ta zasada wyzwala po każdej zmianie XslCompiledTransform. <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> odbiera wystąpień niezabezpieczonych kombinacja <xref:System.Xml.Xsl.XsltSettings> i <xref:System.Xml.XmlResolver>, która pozwala na przetwarzanie złośliwy skrypt.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
  
-   Zastąp niezabezpieczonych argument XsltSettings XsltSettings. <xref:System.Xml.Xsl.XsltSettings.Default%2A> lub przy użyciu wystąpienia wyłączonego dokumentu wykonywania funkcji i skryptów.  
  
-   Zastąp <xref:System.Xml.XmlResolver> argument o wartości null lub <xref:System.Xml.XmlSecureResolver> wystąpienia.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Jeśli nie masz pewności, czy dane wejściowe jest znany jako z zaufanego źródła, nie Pomijaj reguły z to ostrzeżenie.  
  
## <a name="pseudo-code-examples"></a>Przykłady pseudo-kodu  
  
### <a name="violation"></a>Naruszenie  
  
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
  
### <a name="solution"></a>Rozwiązanie  
  
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
  
### <a name="violation"></a>Naruszenie  
  
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
  
### <a name="solution"></a>Rozwiązanie  
  
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