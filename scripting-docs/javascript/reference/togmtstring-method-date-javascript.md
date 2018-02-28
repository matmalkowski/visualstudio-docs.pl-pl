---
title: "toGMTString — metoda (Data) (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- toGMTString
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toGMTString method
ms.assetid: 9dc1e722-5722-4b8c-a213-a2650f55f207
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cef8a61e04fbb5ada6e03fa946f434327422d9d7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="togmtstring-method-date-javascript"></a>toGMTString — Metoda (Data) (JavaScript)
Zwraca datę, konwertowana na ciąg przy użyciu Time(GMT) oznacza Greenwich.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
dateObj.toGMTString()   
```  
  
## <a name="remarks"></a>Uwagi  
 Wymagane `dateObj` odwołanie jest dowolne `Date` obiektu.  
  
 `toGMTString` Metoda jest przestarzała i jest zgodne ze starszymi wersjami. Zaleca się, że używasz `toUTCString` metody zamiast tego.  
  
 `toGMTString` Metoda zwraca `String` obiekt, który zawiera daty sformatowane przy użyciu konwencji GMT. Format wartości zwracanej jest następujący: "GMT 00:00:00: 05 Jan 1996".  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Dotyczy**: [obiekt Date](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [toUTCString — metoda (Data)](../../javascript/reference/toutcstring-method-date-javascript.md)