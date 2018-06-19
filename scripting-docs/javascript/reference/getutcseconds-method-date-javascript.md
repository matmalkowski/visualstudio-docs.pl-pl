---
title: getUTCSeconds — metoda (Data) (JavaScript) | Dokumentacja firmy Microsoft
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
- getUTCSeconds
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- UTC times, returning
- seconds method
- getUTCSeconds method
ms.assetid: 2d8ea7dc-79f8-4a9b-b2ab-732db2bcd5fd
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4f398145f8e31ed633bf3215de7d5a5ef669b7ef
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24790558"
---
# <a name="getutcseconds-method-date-javascript"></a>getUTCSeconds — Metoda (Data) (JavaScript)
Pobiera sekund z `Date` przy użyciu uniwersalnego czasu koordynowanego (UTC).  
  
## <a name="syntax"></a>Składnia  
  
```  
  
dateObj.getUTCSeconds()   
```  
  
#### <a name="parameters"></a>Parametry  
 Wymagane `dateObj` odwołanie jest `Date` obiektu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca liczbę całkowitą od 0 do 59. Zero jest zwracana w odpowiednim czasie krótszym niż jedna sekunda w ciągu bieżącej minuty. Jeśli `Date` obiekt został utworzony bez określania czasu, domyślnie UTC sekund, wartość jest równa 0.  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać liczbę sekund czasu lokalnego, należy użyć `getSeconds` metody.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `getUTCSeconds` metody.  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date. getUTCSeconds());  
  
// Output: 0  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Dotyczy**: [obiekt Date](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [getSeconds — metoda (Data)](../../javascript/reference/getseconds-method-date-javascript.md)   
 [setSeconds — metoda (Data)](../../javascript/reference/setseconds-method-date-javascript.md)   
 [setUTCSeconds — metoda (Data)](../../javascript/reference/setutcseconds-method-date-javascript.md)