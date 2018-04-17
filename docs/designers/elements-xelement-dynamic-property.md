---
title: Elementy (właściwość klasy XElement dynamiczny) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-designers
ms.topic: conceptual
apiname:
- XElement.Elements
apitype: Assembly
ms.assetid: 3d5737f2-d2ed-410a-821c-349dbb2b574f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d7c68611dc8377d9fc32f6eedbbfd0114959cf08
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="elements-xelement-dynamic-property"></a>Elementy (właściwość klasy XElement dynamiczny)
Pobiera indeksatora używane do pobierania elementy podrzędne bieżącego elementu, które odpowiada określonym rozwiniętą nazwą.  
  
## <a name="syntax"></a>Składnia  
  
```  
elem.Elements[{namespaceName}localName]   
```  
  
## <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość  
 Indeksatora typu `IEnumerable<XElement> Item(String expandedName)`. Ten indeksator pobiera nazwę rozwinięte wymaganymi podrzędnymi elementami i zwraca zgodnych elementów podrzędnych w <xref:System.Collections.IEnumerable> `<` <xref:System.Xml.Linq.XElement> `>` kolekcji.  
  
## <a name="remarks"></a>Uwagi  
 Ta właściwość jest odpowiednikiem <xref:System.Xml.Linq.XContainer.Elements(System.Xml.Linq.XName)?displayProperty=fullName> metody <xref:System.Xml.Linq.XContainer> klasy.  
  
 Elementy w zwracanej kolekcji znajdują się w kolejności dokumentu XML źródła.  
  
 Wykonanie odroczone korzysta z tej właściwości.  
  
## <a name="see-also"></a>Zobacz też  
 [Właściwości dynamiczne klasy XElement — klasa](../designers/xelement-class-dynamic-properties.md)   
 [Element](../designers/element-xelement-dynamic-property.md)   
 [Elementy podrzędne](../designers/descendants-xelement-dynamic-property.md)