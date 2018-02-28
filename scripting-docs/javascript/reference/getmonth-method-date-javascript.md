---
title: "getMonth — metoda (Data) (JavaScript) | Dokumentacja firmy Microsoft"
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
- getMonth
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Date object
- dates, month value
- Month method
- GetMonth method
ms.assetid: c20dd8ba-1d78-42f1-8717-ed3dfd2362dd
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eeffd7ffc7bee5fa63607e342a9a9dced7088d35
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="getmonth-method-date-javascript"></a>getMonth — Metoda (Data) (JavaScript)
Pobiera miesiąca, przy użyciu czasu lokalnego.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
dateObj.getMonth()   
```  
  
#### <a name="parameters"></a>Parametry  
 Wymagane `dateObj` odwołanie jest `Date` obiektu.  
  
## <a name="return-value"></a>Wartość zwracana  
 `getMonth` Metoda zwraca liczbę całkowitą od 0 (styczeń) do 11 (grudzień). Aby uzyskać `Date` skonstruowany przy "5 stycznia 1996", `getMonth` zwraca wartość 0.  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać wartość miesiąca przy użyciu uniwersalnego czasu koordynowanego (UTC), należy użyć `getUTCMonth` metody.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `getMonth` metody.  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getMonth());  
  
// Output: 0  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Dotyczy**: [obiekt Date](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [getUTCMonth — metoda (Data)](../../javascript/reference/getutcmonth-method-date-javascript.md)   
 [setMonth — metoda (Data)](../../javascript/reference/setmonth-method-date-javascript.md)   
 [setUTCMonth — metoda (Data)](../../javascript/reference/setutcmonth-method-date-javascript.md)