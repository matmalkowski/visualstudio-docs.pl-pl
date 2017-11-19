---
title: "setMonth — metoda (Data) (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: setMonth
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Month method
- setMonth method
ms.assetid: 4f5be295-d536-46c0-b3a4-ad06457efe82
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0f2672abebd327af8b0da58d46ebc183b8159711
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="setmonth-method-date-javascript"></a>setMonth — Metoda (Data) (JavaScript)
Ustawia wartość miesiąca w `Date` przy użyciu czasu lokalnego.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
dateObj. setMonth(numMonth[, dateVal])   
```  
  
## <a name="parameters"></a>Parametry  
 `dateObj`  
 Wymagany. Wszelkie `Date` obiektu.  
  
 `numMonth`  
 Wymagany. Liczbowa wartość równą miesiąca. Wartość w styczniu wynosi 0, a inne wartości miesiąca wykonaj po kolei.  
  
 `dateVal`  
 Opcjonalny. Wartość liczbowa reprezentującą dzień miesiąca. Jeśli ta wartość nie zostanie podany, wartość po wywołaniu `getDate` metoda jest używana.  
  
## <a name="remarks"></a>Uwagi  
 Aby ustawić wartość miesiąca przy użyciu uniwersalnego czasu koordynowanego (UTC), użyj `setUTCMonth` metody.  
  
 Jeśli wartość `numMonth` jest większa niż 11 (styczeń jest miesiąc 0) lub wartość ujemną, przechowywane roku jest odpowiednio zmienione. Na przykład, jeśli data przechowywanych jest "5 stycznia 1996" i **setMonth(14)** jest wywoływana, data została zmieniona na "5 marca 1997."  
  
 **SetFullYear** metody można użyć do ustawienia rok, miesiąc i dzień miesiąca.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `setMonth` metody.  
  
```JavaScript  
date = new Date('1/1/1990');  
date.setMonth(14);  
document.write(date);  
  
// Output: Fri Mar 1 00:00:00 PST 1991  
// Note that the time zone corresponds to the time zone on the local computer.  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Dotyczy**: [obiekt Date](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [getMonth — metoda (Data)](../../javascript/reference/getmonth-method-date-javascript.md)   
 [getUTCMonth — metoda (Data)](../../javascript/reference/getutcmonth-method-date-javascript.md)   
 [setUTCMonth — metoda (Data)](../../javascript/reference/setutcmonth-method-date-javascript.md)