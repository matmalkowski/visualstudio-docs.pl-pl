---
title: Math.hypot — funkcja (JavaScript) | Dokumentacja firmy Microsoft
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
ms.assetid: 31488f5a-2230-4114-911e-b6d854c7b0a0
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a66c0b082356b8dde3f51f739c130378d694f3b4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24790987"
---
# <a name="mathhypot-function-javascript"></a>Math.hypot — funkcja (JavaScript)
Zwraca pierwiastek kwadratowy liczby sumę kwadratów argumentów.  
  
## <a name="syntax"></a>Składnia  
  
```  
Math.hypot ( value1[, value2[, ...values] );  
```  
  
#### <a name="parameters"></a>Parametry  
 `value1`  
 Wymagany. Pierwsza liczba.  
  
 `value2`  
 Opcjonalny. Druga liczba.  
  
 `values`  
 Opcjonalny. Jeden lub więcej numerów.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli któryś argument jest wartością typu NaN, funkcja zwraca NaN. Jeśli są podane bez argumentów, funkcja zwraca wartość 0.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono przykład użycia `Math.hypot` funkcji.  
  
```JavaScript  
Math.hypot(3, 4);  
// Returns 5  
  
Math.hypot(3, "4");  
// Returns 5  
  
Math.hypot(3, "four");  
// Returns NaN   
  
Math.hypot(3, 4, 10);  
// Returns 11.180339887498949  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]