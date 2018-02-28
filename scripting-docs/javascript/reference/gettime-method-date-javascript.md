---
title: "getTime — metoda (Data) (JavaScript) | Dokumentacja firmy Microsoft"
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
- getTime
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- GetTime method
- time method
ms.assetid: f0da1d4e-337c-497d-9205-093defbc6d3d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a31e542445e89a0e2f3364d36ae44f8d2d4cf9bb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="gettime-method-date-javascript"></a>getTime — Metoda (Data) (JavaScript)
Pobiera wartość czasu w milisekundach.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
dateObj.getTime()   
```  
  
#### <a name="parameters"></a>Parametry  
 Wymagane `dateObj` odwołanie jest `Date` obiektu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca liczbę milisekund między północy, 1 stycznia 1970 i wartość czasu w `Date` obiektu. Zakres dat wynosi około 285,616 lat z obu stron północy, 1 stycznia 1970. Wartości ujemne wskazać daty przed rokiem 1970.  
  
## <a name="remarks"></a>Uwagi  
 Podczas wykonywania wielu obliczeń daty i czasu, można zdefiniować zmienne równa Liczba milisekund, dzień, godzina lub minutę. Na przykład:  
  
```JavaScript  
var minute = 1000 * 60;  
var hour = minute * 60;  
var day = hour * 24;  
```  
  
 Zobacz [obliczanie dat i godzin (JavaScript)](../../javascript/calculating-dates-and-times-javascript.md) Aby uzyskać więcej informacji o sposobie używania `getTime` metody.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `getTime` metody.  
  
```JavaScript  
var minute = 1000 * 60;  
var hour = minute * 60;  
var day = hour * 24;  
  
date = new Date("1/1/2001");  
var time = date.getTime();  
  
document.write(Math.round(time / day) + " days from 1/1/1970 to 1/1/2001");  
  
// Output: 11323 days from 1/1/1970 to 1/1/2001  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Dotyczy**: [obiekt Date](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [setTime — metoda (Data)](../../javascript/reference/settime-method-date-javascript.md)