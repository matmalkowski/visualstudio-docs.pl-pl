---
title: Date.Parse — funkcja (JavaScript) | Dokumentacja firmy Microsoft
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
- parse
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- parse function [JavaScript]
- Date.parse function [JavaScript]
ms.assetid: ed737e50-6398-4462-8779-2af3c03f8325
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0a73fda66ef24df17a5213a182c04667fc4dfabf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24790351"
---
# <a name="dateparse-function-javascript"></a>Date.parse — Funkcja (JavaScript)
Analizuje ciąg zawierający daty i zwraca liczbę milisekund między tą datą a północy, 1 stycznia 1970.  
  
## <a name="syntax"></a>Składnia  
  
```  
Date.parse(dateVal)   
```  
  
## <a name="remarks"></a>Uwagi  
 Wymagane `dateVal` argument jest ciąg zawierający datę lub wartość VT_DATE pobierana z obiektu ActiveX lub innego obiektu. Dla ciągów informacje o dacie, które `Date.parse` można analizować funkcji. zobacz [ciągów daty i godziny](../../javascript/date-and-time-strings-javascript.md).  
  
 `Date.parse` Funkcja zwraca wartość całkowitą reprezentującą liczbę milisekund między północy, 1 stycznia 1970 i data podana w `dateVal`.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `Date.parse` funkcji.  
  
```JavaScript  
var dateString = "November 1, 1997 10:15 AM";  
var mSec = Date.parse(dateString);  
document.write(mSec);  
// Output: 878404500000  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zwraca różnicę między datą podana a 1/1/1970.  
  
```JavaScript  
var minMilli = 1000 * 60;  
var hrMilli = minMilli * 60;  
var dyMilli = hrMilli * 24;  
  
var testDate = new Date("June 1, 1990");  
var ms = Date.parse(testDate);  
var days = Math.round(ms / dyMilli);  
  
var dateStr = "";  
dateStr += "There are " + days + " days ";  
dateStr += "between 01/01/1970 and " + testDate;  
document.write(dateStr);  
  
// Output: There are 7456 days between 01/01/1970 and Fri Jun 1 00:00:00 PDT 1990  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [getDate — metoda (Data)](../../javascript/reference/getdate-method-date-javascript.md)