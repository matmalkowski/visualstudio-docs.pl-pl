---
title: "setDate — metoda (Data) (JavaScript) | Dokumentacja firmy Microsoft"
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
- setDate
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- setDate method
- dates, setting
ms.assetid: a84b9b01-a6d0-489f-8a13-e7af9e9630b2
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8d74340287b3a7348419d302f79775eb610c6983
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="setdate-method-date-javascript"></a>setDate — Metoda (Data) (JavaScript)
Ustawia wartość liczbową dnia miesiąca `Date` przy użyciu czasu lokalnego.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
dateObj.setDate(numDate)   
```  
  
## <a name="parameters"></a>Parametry  
 `dateObj`  
 Wymagany. Wszelkie `Date` obiektu.  
  
 `numDate`  
 Wymagany. Liczbowa wartość równą dzień miesiąca.  
  
## <a name="remarks"></a>Uwagi  
 Aby ustawić wartość dnia miesiąca przy użyciu uniwersalnego czasu koordynowanego (UTC), użyj `setUTCDate` metody.  
  
 Jeśli wartość `numDate` jest większa niż liczba dni w miesiącu przedstawia datę za pośrednictwem do nowszej miesiąca lub roku. Na przykład, jeśli data przechowywanych jest 5 stycznia 1996 i `setDate(32)` jest nazywany zmiany daty 1 lutego 1996. Jeśli `numDate` jest liczbą ujemną, przedstawia datę powrót do wcześniejszej miesiąca lub roku. Na przykład, jeśli data przechowywanych jest 5 stycznia 1996 i `setDate(-32)` jest nazywany 29 listopada 1995 r. zmiany daty.  
  
 [SetFullYear — metoda (Data)](../../javascript/reference/setfullyear-method-date-javascript.md) można ustawić rok, miesiąc i dzień miesiąca.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `setDate` metody.  
  
```JavaScript  
var date = new Date("12/15/1990");  
date.setDate(30);  
document.write(date);  
  
// Output (for the PST time zone): Sun Dec 30 00:00:00 PST 1990  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Dotyczy**: [obiekt Date](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [getDate — metoda (Data)](../../javascript/reference/getdate-method-date-javascript.md)   
 [setFullYear — metoda (Data)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [setMonth — metoda (Data)](../../javascript/reference/setmonth-method-date-javascript.md)   
 [setUTCDate — metoda (Data)](../../javascript/reference/setutcdate-method-date-javascript.md)