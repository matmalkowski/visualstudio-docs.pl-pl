---
title: LINQ do XML właściwości dynamicznych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-designers
ms.topic: conceptual
ms.assetid: 0455f47c-4a68-4f2e-a3f8-dd1d85b99012
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0d54a37b58f46d8c3d1de145cc623ac3138621da
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="linq-to-xml-dynamic-properties"></a>LINQ do XML właściwości dynamicznych
Ta sekcja zawiera informacje na temat właściwości dynamicznych w składniku LINQ do XML. W szczególności te właściwości są udostępniane przez <xref:System.Xml.Linq.XAttribute> i <xref:System.Xml.Linq.XElement> klasy, które znajdują się w <xref:System.Xml.Linq> przestrzeni nazw.  
  
 Zgodnie z objaśnieniem w temacie [Omówienie programu WPF powiązania danych za pomocą LINQ do XML](../designers/wpf-data-binding-with-linq-to-xml-overview.md), każdy z właściwości dynamicznych jest odpowiednikiem standardowego publicznej właściwości lub metody w tej samej klasy. Te standardowe elementów członkowskich należy używać w większości przypadków; właściwości dynamiczne są dostępne w szczególności dla składnika LINQ to scenariusze wiązania danych XML. Aby uzyskać więcej informacji dotyczących standardowych członków z tych klas, zobacz <xref:System.Xml.Linq.XAttribute> i <xref:System.Xml.Linq.XElement> tematy referencyjne.  
  
 W odniesieniu do ich rozwiązane wartości właściwości dynamicznych w tej sekcji można podzielić na dwie kategorie:  
  
-   Te proste, takie jak `Value` właściwości w <xref:System.Xml.Linq.XAttribute> i <xref:System.Xml.Linq.XElement> klasy, które rozwiązanie do pojedynczej wartości.  
  
-   Indeksowana wartości, takich jak [elementy](../designers/elements-xelement-dynamic-property.md) i [elementy podrzędne](../designers/descendants-xelement-dynamic-property.md) właściwości <xref:System.Xml.Linq.XElement>, które rozwiązanie do indeksatora typu. W przypadku typów indeksatora jest rozpoznawana żądaną wartość lub kolekcji rozwiniętą nazwą parametru muszą być przekazywane do nich.  
  
 Wszystkie właściwości dynamiczne, które zwracają wartość indeksowanego typu <xref:System.Collections.Generic.IEnumerable%601> Użyj deffered wykonywania. Aby uzyskać więcej informacji o wykonanie odroczone, zobacz [wprowadzenie do kwerend LINQ (C#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries).  
  
## <a name="in-this-section"></a>W tej sekcji  
  
|Temat|Opis|  
|-----------|-----------------|  
|[Właściwości dynamiczne klasy XAttribute](../designers/xattribute-class-dynamic-properties.md)|Szczegółowe informacje na temat właściwości dynamicznych udostępnianych przez <xref:System.Xml.Linq.XAttribute> klasy.|  
|[Właściwości dynamiczne klasy XElement](../designers/xelement-class-dynamic-properties.md)|Szczegółowe informacje na temat właściwości dynamicznych udostępnianych przez <xref:System.Xml.Linq.XElement> klasy.|  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Xml.Linq>  
  
 <xref:System.Xml.Linq.XElement?displayProperty=fullName>  
  
 <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>  
  
## <a name="see-also"></a>Zobacz też  
 [Powiązanie danych WPF za pomocą LINQ do XML](../designers/wpf-data-binding-with-linq-to-xml.md)   
 [Powiązanie danych WPF za pomocą LINQ do XML-Przegląd](../designers/wpf-data-binding-with-linq-to-xml-overview.md)   
 [Wprowadzenie do kwerend LINQ (C#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries)