---
title: Element (właściwość klasy XElement dynamiczny)
ms.date: 11/04/2016
ms.technology: vs-ide-designers
ms.topic: reference
apiname:
- XElement.Element
apitype: Assembly
ms.assetid: c6c25b8d-a1da-41ff-aeff-867ff1dcf749
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0bdcb6f4524f4f2db7f119319cbb38a09f83f201
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="element-xelement-dynamic-property"></a>Element (właściwość klasy XElement dynamiczny)

Pobiera indeksatora używane do pobierania elementu podrzędnego wystąpienie elementu, odpowiadający określonej nazwie rozwinięte.

## <a name="syntax"></a>Składnia

```
elem.Element[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość

Indeksatora typu `XElement Item(String expandedName)`. Ten indeksator przyjmuje parametr rozwiniętą nazwą i zwraca odpowiednie <xref:System.Xml.Linq.XElement>, lub `null` Jeśli brak elementów o określonej nazwie.

## <a name="remarks"></a>Uwagi

Ta właściwość jest odpowiednikiem <xref:System.Xml.Linq.XContainer.Element%2A> metody <xref:System.Xml.Linq.XContainer?displayProperty=fullName> klasy.

## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=fullName>
- [Właściwości dynamiczne klasy XElement](../designers/xelement-class-dynamic-properties.md)
- [Elements](../designers/elements-xelement-dynamic-property.md)