---
title: getUTCFullYear — metoda (Data) (JavaScript) | Dokumentacja firmy Microsoft
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
- getUTCFullYear
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- getUTCFullYear method
- Date object
- UTCFullYear method
- dates, UTC
- UTC dates, returning
- Full Year method
- UTC dates, getting
ms.assetid: f11e5363-ef8a-48dd-9d56-4ee7290c7c48
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c8268631a96eed1f61ef4ba908b78680c8522096
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24790564"
---
# <a name="getutcfullyear-method-date-javascript"></a>getUTCFullYear — Metoda (Data) (JavaScript)
Pobiera rok, używając uniwersalnego czasu koordynowanego (UTC).  
  
## <a name="syntax"></a>Składnia  
  
```  
  
dateObj.getUTCFullYear()   
```  
  
#### <a name="parameters"></a>Parametry  
 Wymagane `dateObj` odwołanie jest `Date` obiektu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca rok w postaci czterech cyfr. Lat określona w postaci dwóch cyfr w `Date` konstruktora lub `setFullYear` są rozpatrywane w dwudziestego wieku, dlatego podane "5/14/12" `getUTCFullYear` zwraca "1912".  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać roku przy użyciu czasu lokalnego, należy użyć `getFullYear` metody.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `getUTCFullYear` metody.  
  
```JavaScript  
var date = new Date("1/9/36");  
document.write(date.getUTCFullYear());  
  
// Output: 1936  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Dotyczy**: [obiekt Date](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [getFullYear — metoda (Data)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [setFullYear — metoda (Data)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [setUTCFullYear — metoda (Data)](../../javascript/reference/setutcfullyear-method-date-javascript.md)