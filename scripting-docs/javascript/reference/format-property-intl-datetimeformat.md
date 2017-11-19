---
title: "Format — właściwość (Intl.DateTimeFormat) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 487930fe-a948-446f-902d-06bb0d7685d5
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2e94fcd797a63944d0162dceadf773cf9b15f943
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="format-property-intldatetimeformat"></a>format — Właściwość (Intl.DateTimeFormat)
Zwraca funkcję, która formaty daty specyficzne dla ustawień regionalnych przy użyciu ustawień programu formatującego określonej daty/godziny.  
  
## <a name="syntax"></a>Składnia  
  
```  
dateTimeFormatObj.format  
```  
  
#### <a name="parameters"></a>Parametry  
 `dateTimeFormatObj`  
 Wymagany. Nazwa `DateTimeFormat` obiekt ma być używany jako elementu formatującego.  
  
## <a name="remarks"></a>Uwagi  
 Funkcja zwrócony przez `format` właściwość przyjmuje jeden argument `date`i zwraca ciąg reprezentujący zlokalizowane daty przy użyciu określonego w opcji `DateTimeFormat` obiektu. `date` Parametru zwracane funkcji musi być liczba, ciąg daty lub `Date` obiektu. Jeśli `date` nie zostanie podany, funkcja używa [Date.now](../../javascript/reference/date-now-function-javascript.md) jako domyślne wartości wejściowej.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `DateTimeFormat` obiekt do zlokalizowania daty "1 gru 2007" niemiecki i sformatować go ponownie.  
  
```JavaScript  
var dtFormat = new Intl.DateTimeFormat(["de"], {  
    year: "numeric",  
    month: "long",  
    day: "2-digit",  
    hour: "numeric"  
});  
  
if (console && console.log) {  
    console.log(dtFormat.format(new Date("Dec 1, 2007")));  
    // Returns 01. Dezember 2007 00:00  
}  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Intl.datetimeformat — obiekt](../../javascript/reference/intl-datetimeformat-object-javascript.md)