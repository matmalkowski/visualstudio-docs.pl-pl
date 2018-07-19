---
title: Atrybut (właściwość dynamiczna XElement)
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
ms.openlocfilehash: caacdd787f1765721d281db885364aafc36c5183
ms.sourcegitcommit: 522ba712c0d625e51352506146b0556414681964
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37890012"
---
# <a name="attribute-xelement-dynamic-property"></a>Atrybut (właściwość dynamiczna XElement)

Pobiera indeksatora używane do pobierania wystąpienia atrybutu, który odpowiada określony rozwiniętej nazwy.

## <a name="syntax"></a>Składnia

```xaml
elem.Attribute[{namespaceName}attribName]
```

## <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość

Indeksator typu `XAttribute Item(String expandedName)`. Ten indeksator rozwiniętą nazwę określonego atrybutu przyjmuje i zwraca odpowiedni <xref:System.Xml.Linq.XAttribute>, lub `null` Jeśli istnieje atrybut o określonej nazwie.

## <a name="remarks"></a>Uwagi

Ta właściwość jest równoważna <xref:System.Xml.Linq.XElement.Attribute%2A> metody <xref:System.Xml.Linq.XElement?displayProperty=fullName> klasy.

## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName>
- [Właściwości dynamiczne klasy XElement](../designers/xelement-class-dynamic-properties.md)
- [Wartość](../designers/value-xattribute-dynamic-property.md)