---
title: "getUTCMilliseconds — metoda (Data) (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: getUTCMilliseconds
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- milliseconds
- UTC times, returning
- getUTCMilliseconds method
ms.assetid: 7491d387-7b6a-40df-89e5-55c64795ef70
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3fb7cf202c8511bec00c10dc5b8c23bd198d8700
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="getutcmilliseconds-method-date-javascript"></a>getUTCMilliseconds — Metoda (Data) (JavaScript)
Pobiera milisekund z `Date` przy użyciu uniwersalnego czasu koordynowanego (UTC).  
  
## <a name="syntax"></a>Składnia  
  
```  
  
dateObj.getUTCMilliseconds()   
```  
  
#### <a name="parameters"></a>Parametry  
 Wymagane `dateObj` odwołanie jest `Date` obiektu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość milisekund, które mogą należeć do zakresu od 0 do 999.  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać liczbę milisekund według czasu lokalnego, należy użyć `getMilliseconds` metody.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `getUTCMilliseconds` metody.  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getUTCMilliseconds());  
document.write("<br/>");  
  
date.setMilliseconds(34);  
document.writedate.getUTCMilliseconds());  
  
// Output:  
// 0   
// 34   
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Dotyczy**: [obiekt Date](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [getMilliseconds — metoda (Data)](../../javascript/reference/getmilliseconds-method-date-javascript.md)   
 [setMilliseconds — metoda (Data)](../../javascript/reference/setmilliseconds-method-date-javascript.md)   
 [setUTCMilliseconds — metoda (Data)](../../javascript/reference/setutcmilliseconds-method-date-javascript.md)