---
title: "Date.UTC — funkcja (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: UTC
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- UTC function [JavaScript]
- UTC dates, returning
- Date.UTC function [JavaScript]
ms.assetid: c0d67ce1-a47e-4dfd-bbf4-21619c406a0f
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a6a7c5622b74699e3d718ceb65e96638bdb6c3c5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="dateutc-function-javascript"></a>Date.UTC — Funkcja (JavaScript)
Zwraca liczbę milisekund między północy, 1 stycznia 1970 uniwersalnego czasu koordynowanego (UTC) (lub GMT) i określonej daty.  
  
## <a name="syntax"></a>Składnia  
  
```  
Date.UTC(year, month, day[, hours[, minutes[, seconds[,ms]]]])   
```  
  
## <a name="parameters"></a>Parametry  
 `year`  
 Wymagany. Oznaczenia roku pełnego jest wymagany dla dokładność wieku między datą. Jeśli `year` zakresu od 0 do 99 jest używana, następnie `year` zakłada, że 1900 + `year`.  
  
 `month`  
 Wymagany. Miesiąc jako liczba całkowita z zakresu od 0 do 11 (od stycznia do grudnia).  
  
 `day`  
 Wymagany. Data jako liczba całkowita z przedziału od 1 do 31.  
  
 `hours`  
 Opcjonalny. Musi być dostarczona, jeśli `minutes` podano. Liczba całkowita z przedziału od 0 do 23 (północ do 23: 00) określająca godzinę.  
  
 `minutes`  
 Opcjonalny. Musi być dostarczona, jeśli `seconds` podano. Liczba całkowita z przedziału od 0 do 59 określająca minut.  
  
 `seconds`  
 Opcjonalny. Musi być dostarczona, jeśli `milliseconds` podano. Liczba całkowita z przedziału od 0 do 59 określająca sekund.  
  
 `ms`  
 Opcjonalny. Liczba całkowita z przedziału od 0 do 999 określająca milisekund.  
  
## <a name="remarks"></a>Uwagi  
 `Date.UTC` Funkcja zwraca liczbę milisekund między północy, 1 stycznia 1970 UTC i podanej daty. Ta wartość zwracany może być używana w `setTime` metody i w `Date` konstruktora obiektów. Wartość argumentu jest większa niż jego zakres, czy jest to liczba ujemna, inne wartości przechowywane są odpowiednio zmienione. Na przykład jeśli określisz 150 sekund [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] ponownie definiuje tego numeru jako dwóch minut do 30 sekund.  
  
 Różnica między `Date.UTC` funkcji i `Date` konstruktora obiektu, który akceptuje Data jest to, że `Date.UTC` funkcja przyjmuje UTC i `Date` konstruktora obiektów zakłada czasu lokalnego.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `Date.UTC` funkcji.  
  
```JavaScript  
// Determine the milliseconds per day.  
 var MinMilli = 1000 * 60;  
var HrMilli = MinMilli * 60;  
var DyMilli = HrMilli * 24;  
  
var date = new Date("June 1, 1990");  
var year = date.getFullYear();  
var month = date.getMonth();  
var day = date.getDay();  
  
var newDay = new Date("January 16, 2020");  
var yeartoday = newDay.getUTCFullYear();  
var monthtoday = newDay.getUTCMonth();  
var dayofmonthtoday = newDay.getUTCDate();  
  
// Get the milliseconds since 1/1/1970 UTC.  
var t1 = Date.UTC(year, month - 1, day)  
var t2 = Date.UTC(yeartoday, monthtoday, dayofmonthtoday);  
  
// Determine the difference in days.  
var days = (t2 - t1) / DyMilli;  
  
document.write(days);  
// Output: 10848  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [setTime — metoda (Data)](../../javascript/reference/settime-method-date-javascript.md)