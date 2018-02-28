---
title: "setSeconds — metoda (Data) (JavaScript) | Dokumentacja firmy Microsoft"
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
- setSeconds
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- setSeconds method
- seconds method
ms.assetid: 986ffa54-1db6-4af2-ab8b-8353f64f0b57
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6b8d545307f6aac3506310c868a2860a6159a106
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="setseconds-method-date-javascript"></a>setSeconds — Metoda (Data) (JavaScript)
Ustawia wartość w ciągu sekund `Date` przy użyciu czasu lokalnego.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
dateObj  
.setSeconds(  
numSeconds[, numMilli])   
```  
  
## <a name="parameters"></a>Parametry  
 `dateObj`  
 Wymagany. Wszelkie `Date` obiektu.  
  
 *numSeconds*  
 Wymagany. Wartość liczbowa wartość sekund.  
  
 `numMilli`  
 Opcjonalny. Wartość liczbowa wartość w milisekundach.  
  
## <a name="remarks"></a>Uwagi  
 Wszystkie **ustawić** metody biorąc Argumenty opcjonalne używać wartość zwracana z odpowiadającego **uzyskać** metody, jeśli nie zostanie określony opcjonalny argument. Na przykład jeśli `numMilli` argument nie zostanie określony, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] używa wartość zwracana z **getMilliseconds** metody.  
  
 Aby ustawić wartość przy użyciu uniwersalnego czasu koordynowanego (UTC) sekund, użyj `setUTCSeconds` metody.  
  
 Jeśli wartość argumentu jest większa niż jego zakres lub wartość ujemną, inne wartości przechowywane są odpowiednio zmienione. Na przykład, jeśli jest przechowywane daty "5 stycznia 1996 00:00:00" i **setSeconds(150)** jest nazywane, data została zmieniona na "5 stycznia 1996 00:02:30."  
  
 `setHours` Metody można użyć do ustawienia godziny, minuty, w sekundach i milisekundach.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `setSeconds` metody.  
  
```JavaScript  
function SetSecondsDemo(nsec){  
   var d = new Date();         //Create Date object.  
   d.setSeconds(nsec);         //Set seconds.  
   var s = "Current setting is ";  
   s += d.toLocaleString();  
   return(s);                  //Return new setting.  
}  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Dotyczy**: [obiekt Date](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [getSeconds — metoda (Data)](../../javascript/reference/getseconds-method-date-javascript.md)   
 [getUTCSeconds — metoda (Data)](../../javascript/reference/getutcseconds-method-date-javascript.md)   
 [setUTCSeconds — metoda (Data)](../../javascript/reference/setutcseconds-method-date-javascript.md)