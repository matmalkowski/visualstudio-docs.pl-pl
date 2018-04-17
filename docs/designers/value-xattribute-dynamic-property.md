---
title: Wartość (właściwość XAttribute dynamiczny) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-designers
ms.topic: conceptual
apiname:
- XAttribute.Value
apitype: Assembly
ms.assetid: 019733d2-e050-4120-b537-831cd3fc008e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a0ca01f5d7aec5807343b98a3c402a89678fbe88
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
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
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=fullName>   
 [Właściwości dynamiczne XAttribute — klasa](../designers/xattribute-class-dynamic-properties.md)   
 [Atrybut](../designers/attribute-xelement-dynamic-property.md)