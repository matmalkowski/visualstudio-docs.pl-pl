---
title: setHours — metoda (Data) (JavaScript) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- setHours
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- hours
- setHours method
- dates, setting
ms.assetid: 460f742d-f8d2-4874-9d07-2fb969fef066
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f9757f8416953eaf756dba96b91100527606cf9c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791800"
---
# <a name="sethours-method-date-javascript"></a>setHours — Metoda (Data) (JavaScript)
Ustawia wartość godziny w `Date` przy użyciu czasu lokalnego.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
dateObj.setHours(numHours[, numMin[, numSec[, numMilli]]])   
```  
  
## <a name="parameters"></a>Parametry  
 `dateObj`  
 Wymagany. Wszelkie `Date` obiektu.  
  
 `numHours`  
 Wymagany. Wartość liczbowa wartość godziny.  
  
 `numMin`  
 Opcjonalny. Wartość liczbowa wartość minut. Musi zostać dostarczona, jeśli jeden z następujących argumentów jest używany.  
  
 `numSec`  
 Opcjonalny. Wartość liczbowa wartość sekund. Należy podać Jeśli następujący argument jest używany.  
  
 `numMilli`  
 Opcjonalny. Wartość liczbowa wartość w milisekundach.  
  
## <a name="remarks"></a>Uwagi  
 Wszystkie **ustawić** metody biorąc Argumenty opcjonalne używać wartość zwracana z odpowiadającego **uzyskać** metody, jeśli nie zostanie określony opcjonalny argument. Na przykład jeśli `numMinutes` argument nie zostanie określony, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] używa wartość zwracana z `getMinutes` metody.  
  
 Aby ustawić wartość godziny przy użyciu uniwersalnego czasu koordynowanego (UTC), użyj `setUTCHours` metody.  
  
 Jeśli wartość argumentu jest większa niż jego zakres lub wartość ujemną, inne wartości przechowywane są odpowiednio zmienione. Na przykład, jeśli jest przechowywane daty "5 stycznia 1996 00:00:00", i **setHours(30)** jest nazywane, data została zmieniona na "6 stycznia 1996 06:00:00." Wartości ujemne zachowują się podobnie.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `setHours` metody.  
  
```JavaScript  
function SetHoursDemo(nhr, nmin, nsec){  
   var d, s;                     //Declare variables.  
   d = new Date();               //Create Date object.  
   d.setHours(nhr, nmin, nsec);  //Set hours, minutes, & seconds.  
   s = "Current setting is " + d.toLocaleString()   
   return(s);                    //Return new date setting.  
}  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Dotyczy**: [obiekt Date](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [getHours — metoda (Data)](../../javascript/reference/gethours-method-date-javascript.md)   
 [getUTCHours — metoda (Data)](../../javascript/reference/getutchours-method-date-javascript.md)   
 [setUTCHours — metoda (Data)](../../javascript/reference/setutchours-method-date-javascript.md)