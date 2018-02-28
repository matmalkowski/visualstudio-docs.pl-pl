---
title: "setFullYear — metoda (Data) (JavaScript) | Dokumentacja firmy Microsoft"
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
- setFullYear
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Year method
- setFullYear method
- dates, setting
ms.assetid: 635e4f5a-0210-4c01-8152-b0da4146f6ff
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1e5e20a8486d1aefeab9b244c5f1e9d1b1e60c3f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="setfullyear-method-date-javascript"></a>setFullYear — Metoda (Data) (JavaScript)
Ustawia roku `Date` przy użyciu czasu lokalnego.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
dateObj.setFullYear(numYear[, numMonth[, numDate]])   
```  
  
## <a name="parameters"></a>Parametry  
 `dateObj`  
 Wymagany. Wszelkie `Date` obiektu.  
  
 `numYear`  
 Wymagany. Wartość liczbowa w roku.  
  
 `numMonth`  
 Opcjonalny. Liczony od zera wartość liczbowa w miesiącu (0, 11 stycznia do grudnia). Należy określić, czy `numDate` jest określona.  
  
 `numDate`  
 Opcjonalny. Liczbowa wartość równa dzień miesiąca.  
  
## <a name="remarks"></a>Uwagi  
 Wszystkie **ustawić** metody biorąc Argumenty opcjonalne używać wartość zwracana z odpowiadającego **uzyskać** metody, jeśli nie zostanie określony opcjonalny argument. Na przykład jeśli `numMonth` argument jest opcjonalny, ale nie został określony, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] używa wartość zwracana z **getMonth** metody.  
  
 Ponadto jeśli wartość argumentu jest większa niż jego zakres kalendarza lub ma wartość ujemną, Data przedstawia do przodu i do tyłu, zależnie od potrzeb.  
  
 Aby ustawić rok, używając uniwersalnego czasu koordynowanego (UTC), użyj `setUTCFullYear` metody.  
  
 Zakres lat obsługiwane w obiekcie data to około 285,616 lat przed i po rokiem 1970.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `setFullYear` metody:  
  
```JavaScript  
var date1 = new Date("1/1/2001");  
date1.setFullYear(2007);  
  
var date2 = new Date("1/1/2001");  
date2.setFullYear(2008, 10, 3);   
  
document.write (date1.toLocaleString());  
document.write ("<br />");  
document.write (date2.toLocaleString());  
  
// Output:  
// Monday, January 01, 2007 12:00:00 AM  
// Monday, November 03, 2008 12:00:00 AM  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Dotyczy**: [obiekt Date](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [getFullYear — metoda (Data)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [getUTCFullYear — metoda (Data)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [setUTCFullYear — metoda (Data)](../../javascript/reference/setutcfullyear-method-date-javascript.md)