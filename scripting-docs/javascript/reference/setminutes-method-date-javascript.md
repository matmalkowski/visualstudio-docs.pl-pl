---
title: "setMinutes — metoda (Data) (JavaScript) | Dokumentacja firmy Microsoft"
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
- setMinutes
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- minutes
- setMinutes method
ms.assetid: 34c959cd-cd29-4cee-8e04-9061cf6d42f3
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1ce40cb3ebf769cdd8f668e246e272833780434d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="setminutes-method-date-javascript"></a>setMinutes — Metoda (Data) (JavaScript)
Ustawia wartość minut w **data** przy użyciu czasu lokalnego.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
dateObj.setMinutes(numMinutes[, numSeconds[, numMilli]])   
```  
  
## <a name="parameters"></a>Parametry  
 `dateObj`  
 Wymagany. Wszelkie `Date` obiektu.  
  
 `numMinutes`  
 Wymagany. Wartość liczbowa wartość minut. Musi zostać dostarczona, jeśli jeden z następujących argumentów jest używany.  
  
 *numSeconds*  
 Opcjonalny. Wartość liczbowa wartość sekund. Musi być dostarczona, jeśli `numMilli` argument jest używany.  
  
 `numMilli`  
 Opcjonalny. Wartość liczbowa wartość w milisekundach.  
  
## <a name="remarks"></a>Uwagi  
 Wszystkie **ustawić** metody biorąc Argumenty opcjonalne używać wartość zwracana z odpowiadającego **uzyskać** metody, jeśli nie zostanie określony opcjonalny argument. Na przykład jeśli *numSeconds* nie określono argumentu [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] używa wartość zwracana z `getSeconds` metody.  
  
 Aby ustawić wartość minut przy użyciu uniwersalnego czasu koordynowanego (UTC), użyj `setUTCMinutes` metody.  
  
 Jeśli wartość argumentu jest większa niż jego zakres lub wartość ujemną, inne wartości przechowywane są odpowiednio zmienione. Na przykład, jeśli jest przechowywane daty "5 stycznia 1996 00:00:00" i **setMinutes(90)** jest nazywane, data została zmieniona na "5 stycznia 1996 01:30:00." Wartości ujemne zachowują się podobnie.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `setMinutes` metody.  
  
```JavaScript  
function SetMinutesDemo(nmin, nsec){  
   var d, s;                     // Declare variables.  
   d = new Date();               // Create Date object.  
   d.setMinutes(nmin, nsec);     // Set minutes.  
   s = "Current setting is " + d.toLocaleString()   
   return(s);                    // Return new setting.  
}  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Dotyczy**: [obiekt Date](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [getMinutes — metoda (Data)](../../javascript/reference/getminutes-method-date-javascript.md)   
 [getUTCMinutes — metoda (Data)](../../javascript/reference/getutcminutes-method-date-javascript.md)   
 [setUTCMinutes — metoda (Data)](../../javascript/reference/setutcminutes-method-date-javascript.md)