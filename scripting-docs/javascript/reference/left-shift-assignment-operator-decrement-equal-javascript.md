---
title: Operator przypisania przesunięcia w lewo (&lt;&lt;=) (JavaScript) | Dokumentacja firmy Microsoft
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
- <<=
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- <<= operator [JavaScript]
- left shift assignment operator (<<=) [JavaScript]
- left shift operators [JavaScript]
- assignment operators, JavaScript
ms.assetid: 9f30ff46-48cc-4931-b260-edef31ff0076
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bf00545947f6a84f99c519fcbed887b84c179fb5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24790774"
---
# <a name="left-shift-assignment-operator-ltlt-javascript"></a>Operator przypisania przesunięcia w lewo (&lt;&lt;=) (JavaScript)
Przesuwa określoną liczbę bitów w lewo i przypisuje wynik, który ma `result`. Bity pojazdowy operacji są wypełniane 0.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
result <<= expression  
```  
  
## <a name="parameters"></a>Parametry  
 `result`  
 Dowolnej zmiennej.  
  
 `expression`  
 Liczba bitów do przeniesienia.  
  
## <a name="remarks"></a>Uwagi  
 Przy użyciu `<<=` operator jest taki sam jak określenie`result = result << expression`  
  
 Poniższy przykład przedstawia użycie `<<=` operatora.  
  
```JavaScript  
// 14 is 00000000000000000000000000001110  
var temp = 14;  
temp <<= 2;   
document.write(temp);  
// 56 is 00000000000000000000000000111000  
Output: 56  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Bitowy Operator przesunięcia w lewo (<\<)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [Operator przesunięcia bitowego w prawo (>>)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [Operator przesunięcia w prawo bez znaku (>>>)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [Kolejność wykonywania działań](../../javascript/operator-subtractprecedence-javascript.md)   
 [Podsumowanie dla operatorów (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)