---
title: Atrybut (właściwość klasy XElement dynamiczny)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: reference
ms.assetid: 8440fc7d-b3b4-4726-8ec8-492e6af79642
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9ac173785804ce2ed2874b9628c68d3ab78be6e1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31923268"
---
# <a name="attribute-xelement-dynamic-property"></a>Atrybut (właściwość klasy XElement dynamiczny)

Pobiera indeksatora używane do pobierania wystąpienie atrybutu odpowiadający określonej nazwie rozwinięte.

## <a name="syntax"></a>Składnia

```
elem.Attribute[{namespaceName}attribName]
```

## <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość

Indeksatora typu `XAttribute Item(String expandedName)`. Ten indeksator ma rozwiniętą nazwą określonego atrybutu i zwraca odpowiednie <xref:System.Xml.Linq.XAttribute>, lub `null` Jeśli nie istnieje atrybut o określonej nazwie.

## <a name="remarks"></a>Uwagi

Ta właściwość jest odpowiednikiem <xref:System.Xml.Linq.XElement.Attribute%2A> metody <xref:System.Xml.Linq.XElement?displayProperty=fullName> klasy.

## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName>
- [Właściwości dynamiczne klasy XElement](../designers/xelement-class-dynamic-properties.md)
- [Wartość](../designers/value-xattribute-dynamic-property.md)