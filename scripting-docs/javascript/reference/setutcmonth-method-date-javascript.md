---
title: setUTCMonth — metoda (Data) (JavaScript) | Dokumentacja firmy Microsoft
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
- setUTCMonth
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dates, UTC
- setUTCMonth method
- Month method
- UTC dates, setting
ms.assetid: cdac5f64-c4fd-44cc-ba3a-9a8dd3dd3fad
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 02cb69026b66e3f307a8709ab3f5b23d9518643a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791797"
---
# <a name="setutcmonth-method-date-javascript"></a>setUTCMonth — Metoda (Data) (JavaScript)
Ustawia wartość miesiąca w `Date` przy użyciu uniwersalnego czasu koordynowanego (UTC).  
  
## <a name="syntax"></a>Składnia  
  
```  
  
dateObj.setUTCMonth(numMonth[, dateVal])   
```  
  
## <a name="parameters"></a>Parametry  
 `dateObj`  
 Wymagany. Wszelkie `Date` obiektu.  
  
 `numMonth`  
 Wymagany. Liczbowa wartość równą miesiąca. Wartość w styczniu wynosi 0, a inne wartości miesiąca wykonaj po kolei.  
  
 `dateVal`  
 Opcjonalny. Wartość liczbowa reprezentującą dzień miesiąca. Jeśli nie zostanie podany, wartość po wywołaniu `getUTCDate` metoda jest używana.  
  
## <a name="remarks"></a>Uwagi  
 Aby ustawić wartość miesiąca przy użyciu czasu lokalnego, należy użyć `setMonth` metody.  
  
 Jeśli wartość `numMonth` jest większa niż 11 (styczeń jest miesiąc 0), lub wartość ujemną, jest przechowywane roku jest zwiększone lub zmniejszone odpowiednio. Na przykład, jeśli data przechowywanych jest "5 stycznia 1996 00:00:00.00" i **setUTCMonth(14)** jest nazywane, data została zmieniona na "5 marca 1997 00:00:00.00."  
  
 **SetUTCFullYear** metody można użyć do ustawienia rok, miesiąc i dzień miesiąca.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `setUTCMonth` metody.  
  
```JavaScript  
function SetUTCMonthDemo(newmonth){  
   var d, s;                       // Declare variables.  
   d = new Date();                 // Create Date object.  
   d.setUTCMonth(newmonth);        // Set UTC month.  
   s = "Current setting is ";  
   s += d.toUTCString();   
   return(s);                      // Return new setting.  
}  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Dotyczy**: [obiekt Date](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [getMonth — metoda (Data)](../../javascript/reference/getmonth-method-date-javascript.md)   
 [getUTCMonth — metoda (Data)](../../javascript/reference/getutcmonth-method-date-javascript.md)   
 [setMonth — metoda (Data)](../../javascript/reference/setmonth-method-date-javascript.md)