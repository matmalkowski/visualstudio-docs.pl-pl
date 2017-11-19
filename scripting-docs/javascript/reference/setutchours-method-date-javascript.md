---
title: "setUTCHours — metoda (Data) (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: setUTCHours
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dates, UTC
- UTC times, setting
- setUTCHours method
ms.assetid: 257e36fd-fb06-4a4d-8634-d66a020a1511
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9fe83735028f86d38ef270beac6c44dfa4caae7f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="setutchours-method-date-javascript"></a>setUTCHours — Metoda (Data) (JavaScript)
Ustawia wartość godziny w `Date` przy użyciu uniwersalnego czasu koordynowanego (UTC).  
  
## <a name="syntax"></a>Składnia  
  
```  
  
dateObj.setUTCHours(numHours[, numMin[, numSec[, numMilli]]])   
```  
  
## <a name="parameters"></a>Parametry  
 `dateObj`  
 Wymagany. Wszelkie `Date` obiektu.  
  
 `numHours`  
 Wymagany. Wartość liczbowa wartość godziny.  
  
 `numMin`  
 Opcjonalny. Wartość liczbowa wartość minut. Musi być dostarczona, jeśli albo `numSec` lub `numMilli` są używane.  
  
 `numSec`  
 Opcjonalny. Wartość liczbowa wartość sekund. Musi być dostarczona, jeśli `numMilli` argument jest używany.  
  
 `numMilli`  
 Opcjonalny. Wartość liczbowa wartość w milisekundach.  
  
## <a name="remarks"></a>Uwagi  
 Wszystkie **ustawić** metody biorąc Argumenty opcjonalne używać wartość zwracana z odpowiadającego **uzyskać** metody, jeśli nie zostanie określony opcjonalny argument. Na przykład jeśli `numMin` argument nie zostanie określony, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] używa wartość zwracana z `getUTCMinutes` metody.  
  
 Aby ustawić wartość godziny przy użyciu czasu lokalnego, należy użyć `setHours` metody.  
  
 Wartość argumentu jest większa niż jego zakres, czy jest to liczba ujemna, inne wartości przechowywane są odpowiednio zmienione. Na przykład, jeśli data przechowywanych jest "5 stycznia 1996 00:00:00.00" i **setUTCHours(30)** jest nazywane, data została zmieniona na "06:00:00.00 6 stycznia 1996".  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `setUTCHours` metody.  
  
```JavaScript  
function SetUTCHoursDemo(nhr, nmin, nsec){     
   var d, s;                        // Declare variables.  
   d = new Date();                  // Create Date object.  
   d.setUTCHours(nhr, nmin, nsec);  // Set UTC hours, minutes, seconds.  
   s = "Current setting is " + d.toUTCString()   
   return(s);                       // Return new setting.  
}  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Dotyczy**: [obiekt Date](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [getHours — metoda (Data)](../../javascript/reference/gethours-method-date-javascript.md)   
 [getUTCHours — metoda (Data)](../../javascript/reference/getutchours-method-date-javascript.md)   
 [setHours — metoda (Data)](../../javascript/reference/sethours-method-date-javascript.md)