---
title: "setUTCDate — metoda (Data) (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: setUTCDate
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dates, UTC
- dates, setting
- UTC dates, setting
- setUTCDate method
ms.assetid: e6c3b876-70fe-4103-b197-6c84c078ce10
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5631a36c8b1c4f1ee50dcadb39f0f21ae5aa28e3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="setutcdate-method-date-javascript"></a>setUTCDate — Metoda (Data) (JavaScript)
Ustawia liczbą dzień miesiąca w `Date` przy użyciu uniwersalnego czasu koordynowanego (UTC).  
  
## <a name="syntax"></a>Składnia  
  
```  
  
dateObj.setUTCDate(numDate)   
```  
  
## <a name="parameters"></a>Parametry  
 `dateObj`  
 Wymagany. Wszelkie `Date` obiektu.  
  
 *numDate*  
 Wymagany. Liczbowa wartość równą dzień miesiąca.  
  
## <a name="remarks"></a>Uwagi  
 Aby ustawić dzień miesiąca przy użyciu czasu lokalnego, należy użyć `setDate` metody.  
  
 Jeśli wartość *numDate* jest większa niż liczba dni w miesiącu przechowywane w **data** obiektu lub jest liczbą ujemną, data jest ustawiona na datę równa *numDate* minus Liczba dni w miesiącu przechowywane. Na przykład, jeśli data przechowywanych jest 5 stycznia 1996 i **setUTCDate(32)** jest nazywany zmiany daty 1 lutego 1996. Wartości ujemne zachowują się podobnie.  
  
 **SetUTCFullYear** metody można użyć do ustawienia rok, miesiąc i dzień miesiąca.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `setUTCDate` metody.  
  
```JavaScript  
function SetUTCDateDemo(newdayofmonth){  
   var d = new Date();           // Create Date object.  
   d.setUTCDate(newdayofmonth);  // Set UTC day of month.  
   var s = "Current setting is ";  
   s += d.toUTCString();   
   return(s);                    // Return new setting.  
}  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Dotyczy**: [obiekt Date](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [getDate — metoda (Data)](../../javascript/reference/getdate-method-date-javascript.md)   
 [getUTCDate — metoda (Data)](../../javascript/reference/getutcdate-method-date-javascript.md)   
 [setDate — metoda (Data)](../../javascript/reference/setdate-method-date-javascript.md)