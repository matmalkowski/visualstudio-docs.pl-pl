---
title: Elementy (właściwość klasy XElement dynamiczny)
ms.date: 11/04/2016
ms.technology: vs-ide-designers
ms.topic: reference
apiname:
- XElement.Elements
apitype: Assembly
ms.assetid: 3d5737f2-d2ed-410a-821c-349dbb2b574f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 614914b5ff2a71cbca06b957ea381b9926a10574
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
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

## <a name="see-also"></a>Zobacz także

- [Właściwości dynamiczne klasy XElement](../designers/xelement-class-dynamic-properties.md)
- [Element](../designers/element-xelement-dynamic-property.md)
- [Elementy podrzędne](../designers/descendants-xelement-dynamic-property.md)