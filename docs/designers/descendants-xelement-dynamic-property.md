---
title: Elementy podrzędne (właściwość klasy XElement dynamiczny) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-designers
ms.topic: conceptual
ms.assetid: 9611d00f-23bf-444b-ab0c-f30701bfc13d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8520ae91e2a4983e2cc8bcf0e04562255bf4fc1d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="descendants-xelement-dynamic-property"></a>Elementy podrzędne (właściwość klasy XElement dynamiczny)
Pobiera indeksatora używane do pobierania wszystkie elementy zależne bieżącego elementu spełniających określony rozwiniętą nazwą.  
  
## <a name="syntax"></a>Składnia  
  
```  
elem.Descendants[{namespaceName}localName]  
```  
  
## <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość  
 Indeksatora typu `IEnumerable<XElement> Item(String expandedName)`. Ten indeksator ma rozwiniętą nazwę określone elementy podrzędne i zwraca zgodnych elementów podrzędnych w <xref:System.Collections.IEnumerable> `<` <xref:System.Xml.Linq.XElement> `>` kolekcji.  
  
## <a name="remarks"></a>Uwagi  
 Ta właściwość jest odpowiednikiem <xref:System.Xml.Linq.XContainer.Descendants(System.Xml.Linq.XName)?displayProperty=fullName> metody <xref:System.Xml.Linq.XContainer> klasy.  
  
 Elementy w zwracanej kolekcji znajdują się w kolejności dokumentu XML źródła.  
  
 Wykonanie odroczone korzysta z tej właściwości.  
  
## <a name="see-also"></a>Zobacz też  
 [Właściwości dynamiczne klasy XElement — klasa](../designers/xelement-class-dynamic-properties.md)   
 [Elements](../designers/elements-xelement-dynamic-property.md)