---
title: setUTCMinutes — metoda (Data) (JavaScript) | Dokumentacja firmy Microsoft
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
- setUTCMinutes
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- minutes
- dates, UTC
- UTC times, setting
- setUTCMinutes method
ms.assetid: 2415e788-6d28-46dd-a103-0931a1fd1446
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 37df1bcefa358f2c9076a3da877bd642d19178b0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791776"
---
# <a name="setutcminutes-method-date-javascript"></a>setUTCMinutes — Metoda (Data) (JavaScript)
Ustawia wartość minut w `Date` przy użyciu uniwersalnego czasu koordynowanego (UTC).  
  
## <a name="syntax"></a>Składnia  
  
```  
  
dateObj.setUTCMinutes(numMinutes[, numSeconds[, numMilli]])   
```  
  
## <a name="parameters"></a>Parametry  
 `dateObj`  
 Wymagany. Wszelkie `Date` obiektu.  
  
 `numMinutes`  
 Wymagany. Wartość liczbowa wartość minut. Musi zostać dostarczona, jeśli jeden z następujących argumentów jest używany.  
  
 *numSeconds*  
 Opcjonalny. Wartość liczbowa wartość sekund. Musi być dostarczona, jeśli `numMilli` jest używany.  
  
 `numMilli`  
 Opcjonalny. Wartość liczbowa wartość w milisekundach.  
  
## <a name="remarks"></a>Uwagi  
 Wszystkie **ustawić** metody biorąc Argumenty opcjonalne używać wartość zwracana z odpowiadającego **uzyskać** metody, jeśli nie zostanie określony opcjonalny argument. Na przykład jeśli *numSeconds* argument nie zostanie określony, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] używa wartość zwracana z `getUTCSeconds` metody.  
  
 Aby zmodyfikować wartość minut przy użyciu czasu lokalnego, należy użyć `setMinutes` metody.  
  
 Wartość argumentu jest większa niż jego zakres, czy jest to liczba ujemna, inne wartości przechowywane są odpowiednio zmienione. Na przykład, jeśli data przechowywanych jest "5 stycznia 1996 00:00:00.00" i **setUTCMinutes(70)** jest nazywane, data została zmieniona na "5 stycznia 1996 01:10:00.00."  
  
 **SetUTCHours** metody można użyć do ustawienia godziny, minuty, w sekundach i milisekundach.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `setUTCMinutes` metody:  
  
```JavaScript  
function SetUTCMinutesDemo(nmin, nsec){  
   var d, s;                    // Declare variables.  
   d = new Date();              // Create Date object.  
   d.setUTCMinutes(nmin,nsec);  // Set UTC minutes.  
   s = "Current setting is " + d.toUTCString()   
   return(s);                   // Return new setting.  
}  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Dotyczy**: [obiekt Date](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [getMinutes — metoda (Data)](../../javascript/reference/getminutes-method-date-javascript.md)   
 [getUTCMinutes — metoda (Data)](../../javascript/reference/getutcminutes-method-date-javascript.md)   
 [setMinutes — metoda (Data)](../../javascript/reference/setminutes-method-date-javascript.md)