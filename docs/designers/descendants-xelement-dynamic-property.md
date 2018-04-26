---
title: Elementy podrzędne (właściwość klasy XElement dynamiczny)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: reference
ms.assetid: 9611d00f-23bf-444b-ab0c-f30701bfc13d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7c1b0aa0c55c0da2a6f9af58f5d54ff607a409ce
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
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

## <a name="see-also"></a>Zobacz także

- [Właściwości dynamiczne klasy XElement](../designers/xelement-class-dynamic-properties.md)
- [Elements](../designers/elements-xelement-dynamic-property.md)