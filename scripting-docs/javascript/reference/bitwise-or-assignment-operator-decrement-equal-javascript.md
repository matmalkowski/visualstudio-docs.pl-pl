---
title: Bitowy Operator przypisania OR (| =) (JavaScript) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '|='
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- assignment operators, bitwise [JavaScript]
- '|= operator'
- bitwise operators, OR operator
- OR operator
ms.assetid: 9b424ff6-4442-4621-b3b6-83e7fd1e5cd5
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8ce9cadcf07906c9eba6749706620ae6293c2682
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="bitwise-or-assignment-operator--javascript"></a>Operator przypisania sumy bitowej OR (|=) (JavaScript)
Wykonuje logiczną lub na wartość zmiennej i wartość wyrażenia i przypisuje wynik do zmiennej.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
result |= expression  
```  
  
## <a name="parameters"></a>Parametry  
 *wynik*  
 Dowolnej zmiennej.  
  
 *wyrażenie*  
 Dowolne wyrażenie.  
  
## <a name="remarks"></a>Uwagi  
 Używanie tego operatora dokładnie jest taki sam jak określenie:  
  
```JavaScript  
result = result | expression  
```  
  
 **&#124; =** operator analizuje binarna reprezentacja wartości *wynik* i *wyrażenie* i operacji lub na nich. Wynik operacji zachowuje się jak to:  
  
```JavaScript  
0101    (result)  
1100    (expression)  
----  
1101    (output)  
```  
  
 Każdy razem z wyrażeń ma wartość 1 w cyfrę, wynik ma wartość 1 w tym cyfr. W przeciwnym razie wynik ma wartość 0 w tym cyfr.  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Bitowe lub operatora (&#124;)](../../javascript/reference/bitwise-or-operator-decrement-javascript.md)   
 [Kolejność wykonywania działań](../../javascript/operator-subtractprecedence-javascript.md)   
 [Podsumowanie dla operatorów (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)