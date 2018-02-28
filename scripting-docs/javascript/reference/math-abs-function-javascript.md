---
title: "Math.Abs — funkcja (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- abs
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- absolute values, calculating
- absolute values
- numeric expressions
- abs method
ms.assetid: 9af4b5b8-de77-47bb-bb59-abdde371e4c3
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5719905a7de375f1b409378f0579e3d8b25209fc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="mathabs-function-javascript"></a>Math.abs — Funkcja (JavaScript)
Zwraca wartość bezwzględną liczby (wartość niezależnie od tego, czy jest liczbą dodatnią lub ujemną). Na przykład wartość bezwzględną liczby -5 jest taka sama jak wartość bezwzględną liczby 5.  
  
## <a name="syntax"></a>Składnia  
  
```  
Math.abs(number)  
```  
  
#### <a name="parameters"></a>Parametry  
 Wymagane `number` argument jest wyrażenia liczbowego, dla którego jest potrzebny wartość bezwzględna.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość bezwzględna `number` argumentu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `abs` funkcji.  
  
```JavaScript  
var s;  
var v1 = Math.abs(6);  
var v2 = Math.abs(-6);  
if (v1 == v2) {  
    document.write("Absolute values are the same.");  
}  
else {  
document.write("Absolute values are different.");  
}  
  
// Output: Absolute values are the same.  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Dotyczy**: [Math — obiekt](../../javascript/reference/math-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Math — obiekt](../../javascript/reference/math-object-javascript.md)