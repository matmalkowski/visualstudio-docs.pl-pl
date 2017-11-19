---
title: "Math.min — funkcja (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: min
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: min method
ms.assetid: a1d7dd85-27ef-45cd-aa2a-f8e80f0b2898
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bb496cff65db11cf6c99d6a6e687f39e20ea857c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="mathmin-function-javascript"></a>Math.min — Funkcja (JavaScript)
Zwraca mniejszy zestaw wyrażeń liczbowych.  
  
## <a name="syntax"></a>Składnia  
  
```  
Math.min([number1[, number2[... [,numberN]]]])  
```  
  
## <a name="remarks"></a>Uwagi  
 Opcjonalny `number1, number2, ..., numberN` argumenty są wyrażeń liczbowych ma zostać obliczone.  
  
 Jeśli podano w nim żadnych argumentów zwracana wartość jest równa [Number.positive_infinity —](../../javascript/reference/number-constants-javascript.md). Jeśli któryś argument `NaN`, wartość zwracana jest również `NaN`.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia sposób uzyskać mniejszy z dwóch wyrażeń.  
  
```JavaScript  
var x = Math.min(107 - 3, 48 * 90);  
document.write(x);  
  
// Output:  
// 104  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Math.max — funkcja](../../javascript/reference/math-max-function-javascript.md)