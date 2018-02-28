---
title: "setTime — metoda (Data) (JavaScript) | Dokumentacja firmy Microsoft"
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
- setTime
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- SetTime method
- time method
ms.assetid: 86584748-7219-495b-bf56-e27f5782778c
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e66b1fbf5d668330eb727e8bfc50ee9d11a28be3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="settime-method-date-javascript"></a>setTime — Metoda (Data) (JavaScript)
Ustawia wartość daty i godziny w `Date` obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
dateObj.setTime(milliseconds)   
```  
  
## <a name="parameters"></a>Parametry  
 `dateObj`  
 Wymagany. Wszelkie `Date` obiektu.  
  
 *w milisekundach*  
 Wymagany. Wartość liczbowa reprezentujący liczbę milisekund, który upłynął od północy, 1 stycznia 1970 GMT.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli *milisekund* jest ujemna, wskazuje datę przed rokiem 1970. Zakres dat dostępne wynosi około 285,616 lat z obu stron rokiem 1970.  
  
 Ustawienia daty i godziny z `setTime` metody jest niezależna od strefy czasowej.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `setTime` metody.  
  
```JavaScript  
function SetTimeTest(newtime){  
   var d, s;                  //Declare variables.  
   d = new Date();            //Create Date object.  
   d.setTime(newtime);        //Set time.  
   s = "Current setting is ";  
   s += d.toUTCString();  
   return(s);                 //Return new setting.  
}  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Dotyczy**: [obiekt Date](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [getTime — metoda (Data)](../../javascript/reference/gettime-method-date-javascript.md)