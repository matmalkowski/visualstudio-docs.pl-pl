---
title: Bitowy Operator AND (&amp;) (JavaScript) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '&'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- assignment operators, bitwise [JavaScript]
- '& operator, about & operator'
- AND operator
- '& operator'
- bitwise operators, AND operator
- '& operator, bitwise operators'
ms.assetid: a8c17a55-2599-4518-98d7-671699f4d5f3
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fa8b3eec0cbd7c172d08b16120fb54f3be3c6a48
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="bitwise-and-operator-amp-javascript"></a>Bitowy Operator AND (&amp;) (JavaScript)
Wykonuje operacji i dwóch wyrażeń 32-bitowych.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
result = expression1 & expression2  
```  
  
## <a name="parameters"></a>Parametry  
 `result`  
 Wynik operacji.  
  
 `expression1`  
 Dowolne wyrażenie.  
  
 `expression2`  
 Dowolne wyrażenie.  
  
## <a name="remarks"></a>Uwagi  
 `&` Jest operacji i na każdym bity dwóch wyrażeń 32-bitowych. Jeśli oba bity są 1, wynikiem jest 1. W przeciwnym razie wynikiem jest 0.  
  
|Bit1|Bit2|Wartość wykonywana|  
|----------|----------|-----------------|  
|0|0|0|  
|1|1|1|  
|1|0|0|  
|0|1|0|  
  
 W poniższych przykładach pokazano, jak używać `&` operatora.  
  
```JavaScript  
// 9 is 00000000000000000000000000001001  
var expr1 = 9;  
  
// 5 is 00000000000000000000000000000101  
var expr2 = 5;  
  
// 1 is 00000000000000000000000000000001  
var result = expr1 & expr2;  
  
document.write(result);  
// Output: 1  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Operator przypisania iloczynu bitowego AND (& =)](../../javascript/reference/bitwise-and-assignment-operator-decrement-equal-javascript.md)   
 [Kolejność wykonywania działań](../../javascript/operator-subtractprecedence-javascript.md)   
 [Podsumowanie dla operatorów (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)