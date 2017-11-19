---
title: 'CA3077: Przetwarzanie niezabezpieczonych projekt interfejsu API, dokument XML i czytnika tekstu XML | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7f33771b-f3c8-4c02-bef6-f581b623c303
caps.latest.revision: "7"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6944b49626771317f1643f7ae521b0db43c2200c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ca3077-insecure-processing-in-api-design-xml-document-and-xml-text-reader"></a>CA3077: Przetwarzanie niezabezpieczonych projekt interfejsu API, dokument XML i czytnika tekstu XML
|||  
|-|-|  
|TypeName|InsecureDTDProcessingInAPIDesign|  
|CheckId|CA3077|  
|Kategoria|Microsoft.Security|  
|Zmiana kluczowa|Bez podziału|  
  
## <a name="cause"></a>Przyczyna  
 Projektowanie interfejsu API otrzymane z XMLDocument i klasy XMLTextReader, można w trosce o <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A>.  Za pomocą niezabezpieczonego DTDProcessing wystąpień, gdy odwołuje się do rozpoznawania źródeł zewnętrznej jednostki lub ustawienie niezabezpieczonych wartości w pliku XML może prowadzić do ujawnienie informacji.  
  
## <a name="rule-description"></a>Opis reguły  
 A [definicji typu dokumentu (DTD)](https://msdn.microsoft.com/en-us/library/aa468547.aspx) jest jeden z dwóch sposobów analizatora składni XML można określić ważności dokumentu, zgodnie z definicją w [sieci World Wide Web konsorcjum W3C XML Extensible Markup Language () 1.0](http://www.w3.org/TR/2008/REC-xml-20081126/). Ta reguła ma właściwości i gdzie niezaufanych danych jest akceptowany w celu ostrzegania o deweloperów o możliwości wystąpienia [ujawnienie informacji](/dotnet/framework/wcf/feature-details/information-disclosure) zagrożenia, które mogą prowadzić do [przeprowadzenie ataku typu "odmowa usługi" (DoS)](/dotnet/framework/wcf/feature-details/denial-of-service) ataków. Ta zasada wyzwala, gdy:  
  
-   <xref:System.Xml.XmlDocument>lub <xref:System.Xml.XmlTextReader> klasy użyj domyślny program rozpoznawania nazw wartości dla przetwarzanie elementu DTD.  
  
-   Żaden konstruktor nie jest zdefiniowany dla obiektu XmlDocument lub klasy pochodne klasy XmlTextReader lub nie bezpiecznego wartość jest używana w przypadku <xref:System.Xml.XmlResolver>.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
  
-   CATCH i przetwórz wszystkie wyjątki klasy XmlTextReader właściwie, aby uniknąć ścieżki ujawnienie informacji.  
  
-   Użyj <xref:System.Xml.XmlSecureResolver>zamiast element XmlResolver do ograniczenia klasy XmlTextReader mogą uzyskiwać dostęp do zasobów.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Jeśli nie masz pewności, czy dane wejściowe jest znany jako z zaufanego źródła, nie Pomijaj reguły z to ostrzeżenie.  
  
## <a name="pseudo-code-examples"></a>Przykłady pseudo-kodu  
  
### <a name="violation"></a>Naruszenie  
  
```csharp  
using System;   
using System.Xml;   
  
namespace TestNamespace   
{   
    class TestClass : XmlDocument    
    {   
        public TestClass () {} // warn   
    }   
  
    class TestClass2 : XmlTextReader    
    {       
        public TestClass2() // warn   
        {   
        }   
    }   
}  
```  
  
### <a name="solution"></a>Rozwiązanie  
  
```csharp  
using System;   
using System.Xml;   
  
namespace TestNamespace   
{   
    class TestClass : XmlDocument    
    {   
        public TestClass ()    
        {   
            XmlResolver = null;   
        }   
    }   
  
    class TestClass2 : XmlTextReader    
    {       
        public TestClass2()    
        {   
               XmlResolver = null;   
        }   
    }   
}  
```