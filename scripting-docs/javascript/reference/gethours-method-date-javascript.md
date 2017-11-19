---
title: "getHours — metoda (Data) (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: getHours
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Date object
- GetHours method
- Hours method
ms.assetid: c3936496-a213-4d15-b308-d53926ed310c
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 87170f96ee6ae6b4a825436717a94749cc336ee0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="gethours-method-date-javascript"></a>getHours — Metoda (Data) (JavaScript)
Pobiera daty, godziny, przy użyciu czasu lokalnego.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
dateObj.getHours()   
```  
  
#### <a name="parameters"></a>Parametry  
 Wymagane `dateObj` odwołanie jest `Date` obiektu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Liczba całkowita między 0 a 23, wskazującą liczbę godzin od północy. Zero jest zwracany, gdy czas przed 1:00:00: 00. Jeśli `Date` obiekt został utworzony bez określania czasu, domyślnie godzinę wynosi 0.  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać wartość godziny przy użyciu uniwersalnego czasu koordynowanego (UTC), należy użyć `getUTCHours` metody.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `getHours` metody.  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getHours());  
document.write("<br/>");  
  
date.setTime(50000000);  
document.write(date.getHours());  
  
// Output:  
// 0   
// 5  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Dotyczy**: [obiekt Date](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [getUTCHours — metoda (Data)](../../javascript/reference/getutchours-method-date-javascript.md)   
 [setHours — metoda (Data)](../../javascript/reference/sethours-method-date-javascript.md)   
 [setUTCHours — metoda (Data)](../../javascript/reference/setutchours-method-date-javascript.md)