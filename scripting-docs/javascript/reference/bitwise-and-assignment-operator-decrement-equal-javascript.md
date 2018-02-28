---
title: Operator przypisania iloczynu bitowego AND (&amp;=) (JavaScript) | Dokumentacja firmy Microsoft
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
- '&='
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- '&= operator'
- assignment operators, bitwise [JavaScript]
- AND operator
- bitwise operators, AND operator
ms.assetid: e7e2eabb-4fc1-4fdc-9dd8-1e6d715371fa
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dfd2a77e66296cafc6c8403570f0536e1333e081
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="bitwise-and-assignment-operator-amp-javascript"></a>Operator przypisania iloczynu bitowego AND (&amp;=) (JavaScript)
Ustawia wynik operacji i na wartość zmiennej i wartości wyrażenia. Zmienna i wyrażenie, które są traktowane jako 32-bitowych liczb całkowitych.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
result &= expression  
```  
  
## <a name="parameters"></a>Parametry  
 `result`  
 Dowolnej zmiennej.  
  
 `expression`  
 Dowolne wyrażenie.  
  
## <a name="remarks"></a>Uwagi  
 Używanie tego operatora jest taki sam jak określenie:  
  
```JavaScript  
result = result & expression  
```  
  
 [Bitowy Operator AND (&)](../../javascript/reference/bitwise-and-operator-decrement-javascript.md) analizuje binarna reprezentacja wartości `result` i `expression` oraz operacji i na nich operacje. Dane wyjściowe ta operacja zachowuje się jak to:  
  
```JavaScript  
// 9 is 00000000000000000000000000001001  
var expr1 = 9;  
  
// 5 is 00000000000000000000000000000101  
var expr2 = 5;  
  
// 1 is 00000000000000000000000000000001  
expr1 &= expr2;  
  
document.write(expr1);  
```  
  
 Kiedykolwiek wyrażenia mają wartość 1 w cyfrę, wynik ma wartość 1 w tym cyfrę. W przeciwnym razie wynik ma wartość 0 w tym cyfr.  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Bitowy Operator AND (&)](../../javascript/reference/bitwise-and-operator-decrement-javascript.md)   
 [Kolejność wykonywania działań](../../javascript/operator-subtractprecedence-javascript.md)   
 [Podsumowanie dla operatorów (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)