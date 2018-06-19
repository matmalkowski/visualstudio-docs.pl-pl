---
title: setMilliseconds — metoda (Data) (JavaScript) | Dokumentacja firmy Microsoft
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
- setMilliseconds
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- milliseconds
- setMilliseconds method
ms.assetid: 6c398961-130e-4f60-802f-6c30e1ef4de4
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f0cd339e1352511312ef9a9abf9a7ff02955c986
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791449"
---
# <a name="setmilliseconds-method-date-javascript"></a>setMilliseconds — Metoda (Data) (JavaScript)
Ustawia wartość w milisekundach `Date` przy użyciu czasu lokalnego.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
dateObj.  
setMilliseconds(  
numMilli  
)   
```  
  
## <a name="parameters"></a>Parametry  
 `dateObj`  
 Wymagany. Wszelkie `Date` obiektu.  
  
 `numMilli`  
 Wymagany. Wartość liczbowa wartość milisekund.  
  
## <a name="remarks"></a>Uwagi  
 Aby ustawić milisekund wartości przy użyciu uniwersalnego czasu koordynowanego (UTC), użyj `setUTCMilliseconds` metody.  
  
 Jeśli wartość `numMilli` jest większa niż 999 lub jest liczbą ujemną, przechowywane liczba sekund (i minuty, godziny i tak dalej, jeśli to konieczne) jest zwiększany odpowiedniej ilości.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `setMilliseconds` metody.  
  
```JavaScript  
function SetMSecDemo(nmsec){  
   var d, s;                    // Declare variables.  
   d = new Date();              // Create Date object.  
   d.setMilliseconds(nmsec);    // Set milliseconds.  
   s = "Current setting is ";  
   s += d.toLocaleString();  
   s += " and " + d.getMilliseconds();  
   s += " milliseconds";  
   return(s);                   // Return new date setting.  
}  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Dotyczy**: [obiekt Date](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [getMilliseconds — metoda (Data)](../../javascript/reference/getmilliseconds-method-date-javascript.md)   
 [getUTCMilliseconds — metoda (Data)](../../javascript/reference/getutcmilliseconds-method-date-javascript.md)   
 [setUTCMilliseconds — metoda (Data)](../../javascript/reference/setutcmilliseconds-method-date-javascript.md)