---
title: "isNaN — funkcja (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: isNaN
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: isNaN method
ms.assetid: 5af4eb29-72f6-484f-93bd-04ae1261f849
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7b7e6d3687e795ea5d5e38308a8af0d73ba7f5ff
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="isnan-function-javascript"></a>isNaN — Funkcja (JavaScript)
Zwraca wartość logiczną wskazującą, czy wartość jest wartością zarezerwowanej wartości `NaN` (nie liczba).  
  
## <a name="syntax"></a>Składnia  
  
```  
isNaN(numValue)   
```  
  
## <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli można przekonwertować daną wartość `Number` jest typu `NaN`, w przeciwnym razie `false`.  
  
## <a name="remarks"></a>Uwagi  
 Wymagane `numValue` jest to wartość do sprawdzenia przed `NaN`.  
  
 Ta metoda używane zwykle do testowania wartości zwracanych z `parseInt` i `parseFloat` metody.  
  
 Alternatywnie zmienna, która zawiera `NaN` lub innej wartości może porównać do samej siebie. Jeśli porównuje jako nierównej, jest `NaN`. Jest to spowodowane `NaN` jest to jedyna wartość, która nie jest równy sobie samemu.  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Dotyczy**: [obiekt globalny](../../javascript/reference/global-object-javascript.md)  
  
## <a name="example"></a>Przykład  
  
```JavaScript  
// Returns false.  
isNaN(100);  
  
// Returns false.  
isNaN("100");  
  
// Returns true.  
isNaN("ABC");  
  
// Returns true.  
isNaN("10C");  
  
// Returns true.  
isNaN("abc123");  
  
// Returns true.  
isNaN(Math.sqrt(-1));           
```  
  
## <a name="see-also"></a>Zobacz też  
 [isfinite — funkcja](../../javascript/reference/isfinite-function-javascript.md)   
 [NaN — stała](../../javascript/reference/nan-constant-javascript.md)   
 [parsefloat — funkcja](../../javascript/reference/parsefloat-function-javascript.md)   
 [parseInt — funkcja](../../javascript/reference/parseint-function-javascript.md)