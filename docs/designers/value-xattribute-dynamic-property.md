---
title: Wartość (właściwość XAttribute dynamiczny)
ms.date: 11/04/2016
ms.technology: vs-ide-designers
ms.topic: reference
apiname:
- XAttribute.Value
apitype: Assembly
ms.assetid: 019733d2-e050-4120-b537-831cd3fc008e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3b98272fe2c86137eb925a54924e1b0e8411ed0e
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="value-xattribute-dynamic-property"></a>Wartość (właściwość XAttribute dynamiczny)

Pobiera lub ustawia wartość atrybutu XML.

## <a name="syntax"></a>Składnia

```
attrib.Value
```

## <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość

A <xref:System.String> zawierający wartość tego atrybutu.

## <a name="exceptions"></a>Wyjątki

|Typ wyjątku|Warunek|
|--------------------|---------------|
|<xref:System.ArgumentNullException>|Podczas ustawiania, `value` jest `null`.|

## <a name="remarks"></a>Uwagi

Ta właściwość jest odpowiednikiem <xref:System.Xml.Linq.XAttribute.Value%2A> właściwość <xref:System.Xml.Linq.XAttribute?displayProperty=fullName> klasy, ale ta właściwość dynamiczna obsługuje również powiadomienia o zmianie.

## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=fullName>
- [Właściwości dynamiczne klasy XAttribute](../designers/xattribute-class-dynamic-properties.md)
- [Atrybut](../designers/attribute-xelement-dynamic-property.md)