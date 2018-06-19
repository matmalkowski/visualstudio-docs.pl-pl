---
title: setUTCMilliseconds — metoda (Data) (JavaScript) | Dokumentacja firmy Microsoft
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
- setUTCMilliseconds
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- milliseconds
- dates, UTC
- UTC times, setting
- setUTCMilliseconds method
ms.assetid: ed8e4486-d4b2-4b73-836b-dd1d3bb991a0
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 279d00b256b3b0763e2f15f549fdc6ee81c20254
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791533"
---
# <a name="setutcmilliseconds-method-date-javascript"></a>setUTCMilliseconds — Metoda (Data) (JavaScript)
Ustawia wartość w milisekundach `Date` przy użyciu uniwersalnego czasu koordynowanego (UTC).  
  
## <a name="syntax"></a>Składnia  
  
```  
  
dateObj.setUTCMilliseconds(numMilli)   
```  
  
## <a name="parameters"></a>Parametry  
 `dateObj`  
 Wymagany. Wszelkie `Date` obiektu.  
  
 `numMilli`  
 Wymagany. Wartość liczbowa wartość milisekund.  
  
## <a name="remarks"></a>Uwagi  
 Aby ustawić milisekund przy użyciu czasu lokalnego, należy użyć `setMilliseconds` metody.  
  
 Jeśli wartość `numMilli` jest większa niż 999 lub jest liczbą ujemną, przechowywane liczba sekund (i minuty, godziny i tak dalej, jeśli to konieczne) jest zwiększany odpowiedniej ilości.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `setUTCMilliseconds` metody.  
  
```JavaScript  
function SetUTCMSecDemo(nmsec){     
// Create Date object.  
   var d = new Date();             
// Set UTC milliseconds.  
   d.setUTCMilliseconds(nmsec);    
  
   var s = "Current setting is ";  
   s += d.toUTCString();  
   s += " and " + d.getUTCMilliseconds();  
   s += " milliseconds"  
   return(s);  
}  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Dotyczy**: [obiekt Date](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [getMilliseconds — metoda (Data)](../../javascript/reference/getmilliseconds-method-date-javascript.md)   
 [getUTCMilliseconds — metoda (Data)](../../javascript/reference/getutcmilliseconds-method-date-javascript.md)   
 [setMilliseconds — metoda (Data)](../../javascript/reference/setmilliseconds-method-date-javascript.md)