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
ms.openlocfilehash: 0fd01945c2a33f3929f59e66a02a1d08a39c3cc7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
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