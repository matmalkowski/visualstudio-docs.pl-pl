---
title: getDay — metoda (Data) (JavaScript) | Dokumentacja firmy Microsoft
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
- getDay
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- GetDay method
- Date object
- dates, returning day of the week
ms.assetid: 27be7168-3dce-41c9-ae69-6280b7984c2e
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1749eca5aceee76947a0162f22700f32525fdec0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24790513"
---
# <a name="getday-method-date-javascript"></a>getDay — Metoda (Data) (JavaScript)
Pobiera dzień tygodnia, przy użyciu czasu lokalnego.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
dateObj. getDay()   
```  
  
#### <a name="parameters"></a>Parametry  
 Wymagane `dateObj` odwołanie jest `Date` obiektu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Całkowitą z przedziału od 0 do 6 reprezentującą dzień tygodnia (niedziela wynosi 0, sobota 6).  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać przy użyciu uniwersalnego czasu koordynowanego (UTC) dnia, należy użyć `getUTCDay` metody.  
  
 Poniższy przykład przedstawia użycie `getDay` metody.  
  
```JavaScript  
var date = new Date("Saturday, February 9, 2008");  
day = date.getDay();  
document.write(day);  
  
// Output: 6  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Dotyczy**: [obiekt Date](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [getUTCDay — metoda (Data)](../../javascript/reference/getutcday-method-date-javascript.md)