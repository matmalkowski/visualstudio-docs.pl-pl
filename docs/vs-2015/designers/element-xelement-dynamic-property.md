---
title: Element (właściwość dynamiczna XElement) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
api_name:
- XElement.Element
api_type:
- Assembly
ms.assetid: c6c25b8d-a1da-41ff-aeff-867ff1dcf749
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 56689506db04ee2aedd484093506db4a4fc7453d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42680334"
---
# <a name="element-xelement-dynamic-property"></a>Element (właściwość dynamiczna XElement)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [— Element (właściwość dynamiczna XElement)](https://docs.microsoft.com/visualstudio/designers/element-xelement-dynamic-property).  
  
Pobiera indeksatora używane do pobierania elementu podrzędnego wystąpienia elementu, który odpowiada określony rozwiniętej nazwy.  
  
## <a name="syntax"></a>Składnia  
  
```  
elem.Element[{namespaceName}localName]  
```  
  
## <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość  
 Indeksator typu `XElement Item(String expandedName)`. Ten indeksator przyjmuje parametr rozwiniętej nazwy i zwraca odpowiedni <xref:System.Xml.Linq.XElement>, lub `null` Jeśli nie ma żadnego elementu o podanej nazwie.  
  
## <a name="remarks"></a>Uwagi  
 Ta właściwość jest równoważna <xref:System.Xml.Linq.XContainer.Element%2A> metody <xref:System.Xml.Linq.XContainer?displayProperty=fullName> klasy.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=fullName>   
 [Właściwości dynamiczne klasy XElement](../designers/xelement-class-dynamic-properties.md)   
 [Elements](../designers/elements-xelement-dynamic-property.md)



