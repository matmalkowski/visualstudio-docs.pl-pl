---
title: "Elementy podrzędne (właściwość klasy XElement dynamiczny) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9611d00f-23bf-444b-ab0c-f30701bfc13d
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 12d50f38d8f8d907ddb663a03db459851f1e14e2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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