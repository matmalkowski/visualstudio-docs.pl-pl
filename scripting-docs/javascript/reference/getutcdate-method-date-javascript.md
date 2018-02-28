---
title: "getUTCDate — metoda (Data) (JavaScript) | Dokumentacja firmy Microsoft"
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
- getUTCDate
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Date object
- dates, UTC
- UTC dates, returning
- getUTCDate method
ms.assetid: 9e4c763f-c94c-44c9-9684-cb632d75b62e
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e4c38244e989027139329ae6aab762fd9fbabb3a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="getutcdate-method-date-javascript"></a>getUTCDate — Metoda (Data) (JavaScript)
Pobiera dzień miesiąca, przy użyciu uniwersalnego czasu koordynowanego (UTC).  
  
## <a name="syntax"></a>Składnia  
  
```  
  
dateObj.getUTCDate()   
```  
  
#### <a name="parameters"></a>Parametry  
 Wymagane `dateObj` odwołanie jest `Date` obiektu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca liczbę całkowitą od 1 do 31 reprezentująca dzień miesiąca.  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać dzień miesiąca przy użyciu czasu lokalnego, należy użyć `getDate` metody.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `getUTCDate` metody.  
  
```JavaScript  
var date = new Date("1/23/2001");  
document.write(date.getUTCDate());  
  
// Output: 23  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Dotyczy**: [obiekt Date](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [getDate — metoda (Data)](../../javascript/reference/getdate-method-date-javascript.md)   
 [setDate — metoda (Data)](../../javascript/reference/setdate-method-date-javascript.md)   
 [setUTCDate — metoda (Data)](../../javascript/reference/setutcdate-method-date-javascript.md)