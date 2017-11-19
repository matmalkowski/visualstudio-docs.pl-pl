---
title: "isfinite — funkcja (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: isFinite
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- finite numbers
- isFinite method
ms.assetid: ea9287d2-892f-496b-86b7-f9196868d5cf
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ce78afe59190a03fb079841e7691f84c01eebedd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="isfinite-function-javascript"></a>isFinite — Funkcja (JavaScript)
Określa, czy podany numer jest jednak ograniczona.  
  
## <a name="syntax"></a>Składnia  
  
```  
isFinite(number)   
```  
  
## <a name="remarks"></a>Uwagi  
 Wymagane `number` argument ma wartość liczbową.  
  
 `isFinite` Funkcja zwraca `true` Jeśli `number` jest wartością innego niż `NaN`, nieskończoności ujemnej lub nieskończoności dodatniej. W takich przypadkach trzy zwraca **false**.  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Dotyczy**: [obiekt globalny](../../javascript/reference/global-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [isNaN — funkcja](../../javascript/reference/isnan-function-javascript.md)