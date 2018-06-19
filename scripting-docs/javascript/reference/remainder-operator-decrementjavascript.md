---
title: Remainder — Operator (JavaScript) | Dokumentacja firmy Microsoft
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
- '%'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- remainder operator, JavaScript
- '% operator [JavaScript]'
- Remainder function [JavaScript]
ms.assetid: 087d654f-623b-498d-95ff-596d26bf674d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ce74b8512b25cfe215d294873102b274623b42a2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791380"
---
# <a name="remainder-operator-javascript"></a>Operator reszty (JavaScript)
Dzieli wartość jednego wyrażenia przez inną wartość i zwraca resztę.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
result = number1 % number2  
```  
  
## <a name="arguments"></a>Argumenty  
 `result`  
 Dowolnej zmiennej.  
  
 `number1`  
 Dowolne wyrażenie liczbowe.  
  
 `number2`  
 Dowolne wyrażenie liczbowe.  
  
## <a name="remarks"></a>Uwagi  
 Operator reszty dzieli `number1` przez `number2`i zwraca tylko resztę jako `result`. Znak `result` jest taka sama jak znak `number1`. Wartość `result` między 0 a wartość bezwzględną liczby `number2`.  
  
 Poniższy kod przedstawia sposób użycia operator reszty.  
  
```  
var modResult = 19 % 6.7;  
document.write(modResult);  
  
// Output: 5.6  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Kolejność wykonywania działań](../../javascript/operator-subtractprecedence-javascript.md)   
 [Podsumowanie dla operatorów (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)
