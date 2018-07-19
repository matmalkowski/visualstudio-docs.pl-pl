---
title: XML (właściwość dynamiczna XElement)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: reference
apiname:
- XElement.Xml
ms.assetid: 69ab2a33-4fe7-4cfa-97f8-eaf063decb18
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8a69245a875d0c1df1942af12afaacc5a9ffc34b
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/17/2018
ms.locfileid: "39080840"
---
# <a name="xml-xelement-dynamic-property"></a>Xml (właściwość dynamiczna XElement)

Pobiera niesformatowany XML zawartości elementu.

## <a name="syntax"></a>Składnia

```xaml
elem.Xml
```

## <a name="property-valuereturn-value"></a>Właściwość wartości/zwracana wartość

A <xref:System.String> reprezentujący niesformatowany zawartość XML elementu.

## <a name="remarks"></a>Uwagi

Ta właściwość jest równoważna <xref:System.Xml.Linq.XNode.ToString(System.Xml.Linq.SaveOptions)> metody <xref:System.Xml.Linq.XNode?displayProperty=fullName> klasy, za pomocą `SaveOptions` parametr <xref:System.Xml.Linq.SaveOptions>.

## <a name="see-also"></a>Zobacz także

- [Właściwości dynamiczne klasy XElement](../designers/xelement-class-dynamic-properties.md)
- [Wartość](../designers/value-xelement-dynamic-property.md)