---
title: Operator przesunięcia bitowego w prawo (&gt;&gt;) (JavaScript) | Dokumentacja firmy Microsoft
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
- '>>'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- '>> operator'
- '>> operator, about >> operator'
- '>> operator, bitsets'
- bitwise operators, right shift operator
ms.assetid: 89dc57e0-0b0d-49a4-a8ed-56d8bb20f3e3
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 70db0c176b475886a26cfe4c06f7f2f0c9d4fc2a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24789193"
---
# <a name="bitwise-right-shift-operator-gtgt-javascript"></a>Operator przesunięcia bitowego w prawo (&gt;&gt;) (JavaScript)
Prawo wykonuje przesunięcie bitów wyrażenia, Obsługa logowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
result = expression1 >> expression2  
```  
  
## <a name="parameters"></a>Parametry  
 *wynik*  
 Dowolnej zmiennej.  
  
 *wyrażenie1*  
 Dowolne wyrażenie.  
  
 *wyrażenie2*  
 Dowolne wyrażenie.  
  
## <a name="remarks"></a>Uwagi  
 >> Operator wykonuje przesunięcie bitów z *wyrażenie1* prawej przez liczbę bitów określone w *wyrażenie2*. Znak bit z *wyrażenie1* jest używany do wypełniania cyfr z lewej strony. Przesunąć poza z prawej strony cyfry zostaną odrzucone. Na przykład po oceny następujący kod *temp* o wartości -4:-14 (11110010 w dwóch dopełnienia binary) przesunięte odpowiednich bitów dwa equals -4 (11111100 w dwóch dopełnienia binarny).  
  
```JavaScript  
var temp  
temp = -14 >> 2  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Bitowy Operator przesunięcia w lewo (<\<)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [Operator przypisania przesunięcia w prawo (>> =)](../../javascript/reference/right-shift-assignment-operator-decrement-equal-javascript.md)   
 [Operator przesunięcia w prawo bez znaku (>>>)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [Kolejność wykonywania działań](../../javascript/operator-subtractprecedence-javascript.md)   
 [Podsumowanie dla operatorów (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)