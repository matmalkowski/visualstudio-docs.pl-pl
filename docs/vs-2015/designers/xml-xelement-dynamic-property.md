---
title: XML (właściwość dynamiczna XElement) | Dokumentacja firmy Microsoft
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
- XElement.Xml
ms.assetid: 69ab2a33-4fe7-4cfa-97f8-eaf063decb18
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 74fdfa59e791fb8e0262df04b1e45f3b867fbd02
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42680572"
---
# <a name="xml-xelement-dynamic-property"></a>XML (właściwość dynamiczna XElement)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [Xml (właściwość dynamiczna XElement)](https://docs.microsoft.com/visualstudio/designers/xml-xelement-dynamic-property).  
  
Pobiera niesformatowany XML zawartości elementu.  
  
## <a name="syntax"></a>Składnia  
  
```  
elem.Xml  
```  
  
## <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość  
 A <xref:System.String> reprezentujący niesformatowany zawartość XML elementu.  
  
## <a name="remarks"></a>Uwagi  
 Ta właściwość jest równoważna <xref:System.Xml.Linq.XNode.ToString%28System.Xml.Linq.SaveOptions%29> metody <xref:System.Xml.Linq.XNode?displayProperty=fullName> klasy, za pomocą `SaveOptions` parametr <xref:System.Xml.Linq.SaveOptions>.  
  
## <a name="see-also"></a>Zobacz też  
 [Właściwości dynamiczne klasy XElement](../designers/xelement-class-dynamic-properties.md)   
 [Wartość](../designers/value-xelement-dynamic-property.md)



