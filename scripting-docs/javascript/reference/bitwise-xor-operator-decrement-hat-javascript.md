---
title: Bitowy Operator XOR (^) (JavaScript) | Dokumentacja firmy Microsoft
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
- ^
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- bitwise operators, XOR operator
- XOR operator
ms.assetid: 44ef0d18-abb5-4d83-9e77-6394635b3f48
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2ebe8ff9805793bf306688622b0b29007b1562e2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="bitwise-xor-operator--javascript"></a>Bitowy operator XOR (^) (JavaScript)
Wykonuje logiczną lub wykluczające dwóch wyrażeń.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
result = expression1 ^ expression2  
```  
  
## <a name="parameters"></a>Parametry  
 *wynik*  
 Dowolnej zmiennej.  
  
 *wyrażenie1*  
 Dowolne wyrażenie.  
  
 *wyrażenie2*  
 Dowolne wyrażenie.  
  
## <a name="remarks"></a>Uwagi  
 **^**  Operator analizuje binarna reprezentacja wartości dwóch wyrażeń i wykonuje operację OR wyłączne bitowe na nich. Wynik operacji działa w następujący sposób:  
  
```JavaScript  
0101   (expression1)  
1100   (expression2)  
----  
1001   (result)  
```  
  
 Kiedy jeden i tylko jedno z wyrażeń ma wartość 1 cyfrę, wynik zawiera wartość 1 w tym cyfr. W przeciwnym razie wynik ma wartość 0 w tym cyfr.  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Operator przypisania iloczynu bitowego XOR (^ =)](../../javascript/reference/bitwise-xor-assignment-operator-decrement-hat-equal-javascript.md)   
 [Kolejność wykonywania działań](../../javascript/operator-subtractprecedence-javascript.md)   
 [Podsumowanie dla operatorów (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)