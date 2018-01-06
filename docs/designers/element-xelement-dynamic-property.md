---
title: "Element (właściwość klasy XElement dynamiczny) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
apiname: XElement.Element
apitype: Assembly
ms.assetid: c6c25b8d-a1da-41ff-aeff-867ff1dcf749
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: ec02b03188ea0fd1fa7c15ea03878bdec12890f6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=fullName>   
 [Właściwości dynamiczne klasy XElement — klasa](../designers/xelement-class-dynamic-properties.md)   
 [Elements](../designers/elements-xelement-dynamic-property.md)