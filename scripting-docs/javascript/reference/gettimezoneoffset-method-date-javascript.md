---
title: "getTimezoneOffset — metoda (Data) (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: getTimeZoneOffset
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- getTimezoneOffset method
- time zones [Visual Studio]
ms.assetid: 58ee22b0-4688-45bd-a337-cc23119b09ce
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e49a3c8b7060e6097300f8aaf99b2ef869833018
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="gettimezoneoffset-method-date-javascript"></a>getTimezoneOffset — Metoda (Data) (JavaScript)
Pobiera różnicę w minutach czas na komputerze lokalnym i uniwersalny czas koordynowany (UTC).  
  
## <a name="syntax"></a>Składnia  
  
```  
  
dateObj.getTimezoneOffset()   
```  
  
#### <a name="parameters"></a>Parametry  
 Wymagane `dateObj` odwołanie jest `Date` obiektu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca liczbę minut między czasem na bieżącym komputerze (komputer kliencki lub, jeśli ta metoda jest wywoływana ze skryptu serwera z maszyną serwera) i czas UTC. Jest dodatnia, jeśli czas lokalny komputera bieżącego jest za UTC (np. czas pacyficzny letni) i wartość ujemną, jeśli czas lokalny komputera bieżącego jest wcześniejsze UTC (np., Japonia). Jeśli w Nowym Jorku jest skontaktować się z serwerem przez klienta w Warszawie 1 grudnia `getTimezoneOffset` zwraca 480, jeśli wykonywane po stronie klienta lub 300, jeśli wykonywane na serwerze.  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `getTimezoneOffset` metody.  
  
```JavaScript  
var date =  new Date();  
var minutes = date.getTimezoneOffset();  
  
if (minutes < 0)  
    document.write(minutes / 60 + " hours after UTC");  
else  
    document.write(minutes / 60 + " hours before UTC");  
  
// Output (for example, where local time is PST):   
7 hours before UTC  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Dotyczy**: [obiekt Date](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [getTime — metoda (Data)](../../javascript/reference/gettime-method-date-javascript.md)