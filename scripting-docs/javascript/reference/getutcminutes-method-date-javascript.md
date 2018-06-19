---
title: getUTCMinutes — metoda (Data) (JavaScript) | Dokumentacja firmy Microsoft
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
- getUTCMinutes
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- minutes
- UTC times, returning
- getUTCMinutes method
ms.assetid: b6d92543-b285-4e46-8f47-bba36e53fabd
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fe691d3b52d18340eeeff81a91c049a262277c54
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24790552"
---
# <a name="getutcminutes-method-date-javascript"></a>getUTCMinutes — Metoda (Data) (JavaScript)
Pobiera notatki z `Date` przy użyciu uniwersalnego czasu koordynowanego (UTC).  
  
## <a name="syntax"></a>Składnia  
  
```  
  
dateObj.getUTCMinutes()   
```  
  
#### <a name="parameters"></a>Parametry  
 Wymagane `dateObj` odwołanie jest `Date` obiektu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca liczbę całkowitą od 0 do 59. Zero jest zwracany czas jest mniej niż minutę godziny. Jeśli `Date` obiekt został utworzony bez określania czasu, domyślnie UTC minuty wartość jest równa 0. Jednak w innych strefach czasowych może być różne.  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać liczbę minut przechowywane przy użyciu czasu lokalnego, należy użyć `getMinutes` metody.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `getUTCMinutes` metody.  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getUTCMinutes());  
document.write("<br/>");  
  
date.setMinutes(5);  
document.write(date.getUTCMinutes());  
  
// Output:   
// 0  
// 5  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Dotyczy**: [obiekt Date](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [getMinutes — metoda (Data)](../../javascript/reference/getminutes-method-date-javascript.md)   
 [setMinutes — metoda (Data)](../../javascript/reference/setminutes-method-date-javascript.md)   
 [setUTCMinutes — metoda (Data)](../../javascript/reference/setutcminutes-method-date-javascript.md)