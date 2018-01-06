---
title: "Atrybut (właściwość klasy XElement dynamiczny) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8440fc7d-b3b4-4726-8ec8-492e6af79642
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: e3f373f4732aa80ac0e72f044e7a6a7f08e8a9be
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName>   
 [Właściwości dynamiczne klasy XElement — klasa](../designers/xelement-class-dynamic-properties.md)   
 [Wartość](../designers/value-xattribute-dynamic-property.md)