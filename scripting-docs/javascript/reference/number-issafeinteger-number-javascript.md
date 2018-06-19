---
title: Number.isSafeInteger (numer) (JavaScript) | Dokumentacja firmy Microsoft
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
ms.assetid: c7ef6ce8-fe71-4e53-be44-4dd440aef21d
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eebc2147bc5043341be7e883548af825922036f9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791014"
---
# <a name="numberissafeinteger-number-javascript"></a>Number.isSafeInteger (Number) (JavaScript)
Zwraca wartość logiczną, wskazującą, czy liczba może być bezpiecznie reprezentowany w języku JavaScript.  
  
## <a name="syntax"></a>Składnia  
  
```  
Number.isSafeInteger(numValue)   
```  
  
## <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli liczba jest między `Number.MIN_SAFE_INTEGER` i `Number.MAX_SAFE_INTEGER`, wraz z wartościami granicznymi; w przeciwnym razie `false`.  
  
## <a name="remarks"></a>Uwagi  
 Bezpieczne całkowitą w języku JavaScript jest taki, który jest liczbą podwójne opisie IEEE-754, zanim wszystkie zaokrąglania zostały zastosowane.  
  
## <a name="example"></a>Przykład  
  
```JavaScript  
// Returns true  
Number.isSafeInteger(-100)  
Number.isSafeInteger(9007199254740991)  
  
// Returns false  
Number.isSafeInteger(Number.NaN)  
Number.isSafeInteger(Infinity)  
Number.isSafeInteger("100")  
Number.isSafeInteger(9007199254740992);  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **Dotyczy**: [numer obiektu](../../javascript/reference/number-object-javascript.md)