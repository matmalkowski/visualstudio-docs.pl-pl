---
title: "Wartość (właściwość XAttribute dynamiczny) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
apiname: XAttribute.Value
apitype: Assembly
ms.assetid: 019733d2-e050-4120-b537-831cd3fc008e
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 4807a84b9e1de5186e72cbe138f0f54e2f33525e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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