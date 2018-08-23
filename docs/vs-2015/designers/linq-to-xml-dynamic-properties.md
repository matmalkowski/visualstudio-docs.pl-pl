---
title: Właściwości LINQ to XML dynamiczne | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0455f47c-4a68-4f2e-a3f8-dd1d85b99012
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f5153740a93a60bd89b193ae398008541d06bc46
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42690173"
---
# <a name="linq-to-xml-dynamic-properties"></a>LINQ to XML właściwości dynamiczne
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [XML właściwości dynamiczne LINQ to](https://docs.microsoft.com/visualstudio/designers/linq-to-xml-dynamic-properties).  
  
Ta sekcja zawiera informacje na temat właściwości dynamicznych w składniku LINQ to XML. W szczególności te właściwości są udostępniane przez <xref:System.Xml.Linq.XAttribute> i <xref:System.Xml.Linq.XElement> klasy, które znajdują się w <xref:System.Xml.Linq> przestrzeni nazw.  
  
 Zgodnie z opisem w temacie [Omówienie programu WPF powiązanie danych za pomocą LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml-overview.md), każdy z właściwości dynamicznych jest odpowiednikiem standardowa publiczna właściwość lub metoda w tej samej klasy. Te składniki standardowe należy używać w przypadku większości celów; właściwości dynamiczne znajdują się w szczególności dla programu LINQ to scenariusze powiązania danych XML. Aby uzyskać więcej informacji na temat standardowych elementów członkowskich w ramach tych zajęć, zobacz <xref:System.Xml.Linq.XAttribute> i <xref:System.Xml.Linq.XElement> tematy referencyjne.  
  
 W odniesieniu do ich rozwiązane wartości właściwości dynamicznych w tej sekcji można podzielić na dwie kategorie:  
  
-   Te proste, takie jak `Value` właściwości w <xref:System.Xml.Linq.XAttribute> i <xref:System.Xml.Linq.XElement> klas, które nawiązują do pojedynczej wartości.  
  
-   Indeksowane wartości, takich jak [elementy](../designers/elements-xelement-dynamic-property.md) i [elementy podrzędne](../designers/descendants-xelement-dynamic-property.md) właściwości <xref:System.Xml.Linq.XElement>, który rozpoznać jako typ indeksatora. W przypadku typów indeksatora jest rozpoznawana przez żądaną wartość lub kolekcję parametrem rozwiniętej nazwy muszą być przekazywane do nich.  
  
 Wszystkie właściwości dynamicznych, które zwracają indeksowanej wartości typu <xref:System.Collections.Generic.IEnumerable%601> Użyj deffered wykonywania. Aby uzyskać więcej informacji na temat odroczonego wykonania zobacz [wprowadzenie do zapytań LINQ (C#)](http://msdn.microsoft.com/library/37895c02-268c-41d5-be39-f7d936fa88a8).  
  
## <a name="in-this-section"></a>W tej sekcji  
  
|Temat|Opis|  
|-----------|-----------------|  
|[Właściwości dynamiczne klasy XAttribute](../designers/xattribute-class-dynamic-properties.md)|Szczegółowe informacje na temat właściwości dynamicznych, udostępnianych przez <xref:System.Xml.Linq.XAttribute> klasy.|  
|[Właściwości dynamiczne klasy XElement](../designers/xelement-class-dynamic-properties.md)|Szczegółowe informacje na temat właściwości dynamicznych, udostępnianych przez <xref:System.Xml.Linq.XElement> klasy.|  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Xml.Linq>  
  
 <xref:System.Xml.Linq.XElement?displayProperty=fullName>  
  
 <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>  
  
## <a name="see-also"></a>Zobacz też  
 [Powiązanie danych WPF za pomocą LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml.md)   
 [Powiązanie danych WPF za pomocą LINQ to XML — Przegląd](../designers/wpf-data-binding-with-linq-to-xml-overview.md)   
 [Wprowadzenie do zapytań LINQ (C#)](http://msdn.microsoft.com/library/37895c02-268c-41d5-be39-f7d936fa88a8)



