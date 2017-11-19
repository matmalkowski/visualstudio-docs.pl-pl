---
title: Operator przypisania iloczynu bitowego XOR (^ =) (JavaScript) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: ^=
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- ^= operator, about ^= operator
- assignment operators, bitwise [JavaScript]
- bitwise operators, XOR operator
- XOR operator
- ^= operator
ms.assetid: a6ded216-27b6-4fc4-a51b-7d10cc6f820c
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 511ff5b3346bb2b04bf4c24cb3e0b715b2ccf4c5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="bitwise-xor-assignment-operator--javascript"></a>Operator przypisania iloczynu bitowego XOR (^=) (JavaScript)
Wykonuje logiczną lub wykluczające w zmiennej i wyrażenia i przypisuje wynik do zmiennej.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
result ^= expression  
```  
  
## <a name="parameters"></a>Parametry  
 *wynik*  
 Dowolnej zmiennej.  
  
 *wyrażenie*  
 Dowolne wyrażenie.  
  
## <a name="remarks"></a>Uwagi  
 Przy użyciu  **^=**  operator jest dokładnie taka sama, jak określenie:  
  
```JavaScript  
result = result ^ expression  
```  
  
 **^=**  Operator analizuje binarna reprezentacja wartości dwóch wyrażeń i wykonuje operację OR wyłączne bitowe na nich. Wynik operacji działa w następujący sposób:  
  
```JavaScript  
0101    (result)  
1100    (expression)  
----  
1001    (result)  
```  
  
 Kiedy jeden i tylko jedno z wyrażeń ma wartość 1 cyfrę, wynik zawiera wartość 1 w tym cyfr. W przeciwnym razie wynik ma wartość 0 w tym cyfr.  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Bitowy Operator XOR (^)](../../javascript/reference/bitwise-xor-operator-decrement-hat-javascript.md)   
 [Kolejność wykonywania działań](../../javascript/operator-subtractprecedence-javascript.md)   
 [Podsumowanie dla operatorów (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)