---
title: Operator przypisania przesunięcia w prawo (&gt;&gt;=) (JavaScript) | Dokumentacja firmy Microsoft
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
- '>>='
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- '>>= operator [JavaScript]'
- right shift operators [JavaScript]
- assignment operators, JavaScript
ms.assetid: 8c1f7f90-e3ac-42ee-94f2-5ccc47d7aef6
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cb93d146ad00bd19c09fb4cfca3af776a11f245d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791641"
---
# <a name="right-shift-assignment-operator-gtgt-javascript"></a>Operator przypisania przesunięcia w prawo (&gt;&gt;=) (JavaScript)
Prawo przewiduje wartość zmiennej przez liczbę bitów określony w wartości wyrażenia, Obsługa logowania i przypisuje wynik do zmiennej.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
result >>= expression  
```  
  
## <a name="parameters"></a>Parametry  
 *wynik*  
 Dowolnej zmiennej.  
  
 *wyrażenie*  
 Dowolne wyrażenie.  
  
## <a name="remarks"></a>Uwagi  
 Przy użyciu  **>>=**  operator jest dokładnie taka sama, jak określenie:  
  
```JavaScript  
result = result >> expression  
```  
  
 **>>=**  Operator wykonuje przesunięcie bitów z *wynik* prawej przez liczbę bitów określone w *wyrażenia*. Znak bit z *wynik* jest używany do wypełniania cyfr z lewej strony. Przesunąć poza z prawej strony cyfry zostaną odrzucone. Na przykład po oceny następujący kod *temp* o wartości -4: 14 (11110010 binarnie) przesunięte odpowiednich bitów dwa equals -4 (11111100 binarnie).  
  
```JavaScript  
var temp  
temp = -14  
temp >>= 2  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Bitowy Operator przesunięcia w lewo (<\<)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [Operator przesunięcia bitowego w prawo (>>)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [Operator przesunięcia w prawo bez znaku (>>>)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [Kolejność wykonywania działań](../../javascript/operator-subtractprecedence-javascript.md)   
 [Podsumowanie dla operatorów (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)