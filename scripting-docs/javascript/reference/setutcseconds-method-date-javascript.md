---
title: "setUTCSeconds — metoda (Data) (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: setUTCSeconds
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dates, UTC
- setUTCSeconds method
- UTC times, setting
- seconds method
ms.assetid: e035e282-b39d-4d1d-8771-c17542fd6493
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f3df010cd84332d8957f1c08c41c4543dec36e4a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="setutcseconds-method-date-javascript"></a>setUTCSeconds — Metoda (Data) (JavaScript)
Ustawia wartość w ciągu sekund `Date` przy użyciu uniwersalnego czasu koordynowanego (UTC).  
  
## <a name="syntax"></a>Składnia  
  
```  
  
dateObj.setUTCSeconds(numSeconds[, numMilli])   
```  
  
## <a name="parameters"></a>Parametry  
 `dateObj`  
 Wymagany. Wszelkie `Date` obiektu.  
  
 *numSeconds*  
 Wymagany. Wartość liczbowa wartość sekund.  
  
 `numMilli`  
 Opcjonalny. Wartość liczbowa wartość w milisekundach.  
  
## <a name="remarks"></a>Uwagi  
 Wszystkie **ustawić** metody biorąc Argumenty opcjonalne używać wartość zwracana z odpowiadającego **uzyskać** metody, jeśli nie zostanie określony opcjonalny argument. Na przykład jeśli `numMilli` argument nie zostanie określony, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] używa wartość zwracana z `getUTCMilliseconds` metody.  
  
 Aby ustawić sekund wartość przy użyciu czasu lokalnego, należy użyć `setSeconds` metody.  
  
 Jeśli wartość argumentu jest większa niż jego zakres lub wartość ujemną, inne wartości przechowywane są odpowiednio zmienione. Na przykład, jeśli data przechowywanych jest "5 stycznia 1996 00:00:00.00" i **setSeconds(150)** jest nazywane, data została zmieniona na "5 stycznia 1996 00:02:30.00."  
  
 **SetUTCHours** metody można użyć do ustawienia godziny, minuty, w sekundach i milisekundach.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `setUTCSeconds` metody.  
  
```JavaScript  
function SetUTCSecondsDemo(nsec){  
// Create Date object.  
    var d = new Date();       
// Set UTC seconds.  
    d.setUTCSeconds(nsec);    
    var s = "Current setting is ";  
    s += d.toUTCString();  
// Return new setting.  
    return(s);                
}  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Dotyczy**: [obiekt Date](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [getSeconds — metoda (Data)](../../javascript/reference/getseconds-method-date-javascript.md)   
 [getUTCSeconds — metoda (Data)](../../javascript/reference/getutcseconds-method-date-javascript.md)   
 [setSeconds — metoda (Data)](../../javascript/reference/setseconds-method-date-javascript.md)