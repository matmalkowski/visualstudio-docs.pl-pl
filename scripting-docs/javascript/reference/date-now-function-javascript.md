---
title: Date.now — funkcja (JavaScript) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- now method
ms.assetid: 41beda89-1a40-4fb1-88b0-38c090af739b
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 41a098c55b8ced3c630d3724615835301b6f00c8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24790426"
---
# <a name="datenow-function-javascript"></a>Date.now — Funkcja (JavaScript)
Pobiera bieżącą datę i godzinę.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
Date.now()  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Liczba milisekund między północy, 1 stycznia 1970 i aktualnej daty i godziny.  
  
## <a name="remarks"></a>Uwagi  
 [GetTime — metoda](../../javascript/reference/gettime-method-date-javascript.md) zwraca liczbę milisekund między 1 stycznia 1970 i określonej daty.  
  
 Uzyskać informacji o tym, jak można obliczyć czas i porównywanie dat, zobacz [obliczanie dat i godzin (JavaScript)](../../javascript/calculating-dates-and-times-javascript.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `now` metody.  
  
```JavaScript  
var start = Date.now();  
var response = prompt("What is your name?", "");  
var end = Date.now();  
var elapsed = (end - start) / 1000;  
document.write("You took " + elapsed + " seconds" + " to type: " + response);  
  
// Output:  
// You took <seconds> seconds to type: <name>  
```  
  
## <a name="requirements"></a>Wymagania  
 Nie jest obsługiwane w zainstalowanej wersji starszych niż program Internet Explorer 9. Jednak jest obsługiwane w następujących trybach dokumentu: Osobliwości, Standardy programu Internet Explorer 6, Standardy programu Internet Explorer 7, Standardy programu Internet Explorer 8, Standardy programu Internet Explorer 9, Standardy programu Internet Explorer 10. Również obsługiwane w [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [getTime — metoda (Data)](../../javascript/reference/gettime-method-date-javascript.md)   
 [Date — obiekt](../../javascript/reference/date-object-javascript.md)   
 [Obliczanie dat i godzin (JavaScript)](../../javascript/calculating-dates-and-times-javascript.md)   
 [JavaScript — metody](../../javascript/reference/javascript-methods.md)