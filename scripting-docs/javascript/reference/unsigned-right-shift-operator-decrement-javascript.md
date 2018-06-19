---
title: Operator przesunięcia w prawo bez znaku (&gt;&gt;&gt;) (JavaScript) | Dokumentacja firmy Microsoft
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
- '>>>'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- unsigned right shift operator (>>>)
- '>>> operator'
ms.assetid: df48bdfc-8741-46ab-b681-449da57ac95c
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: efb873bedc0a64089c7ec892d6378b4869c0ca21
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24792016"
---
# <a name="unsigned-right-shift-operator-gtgtgt-javascript"></a>Operator przesunięcia w prawo bez znaku (&gt;&gt;&gt;) (JavaScript)
Prawo wykonuje przesunięcie bitów wyrażenia bez zachowania logowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
result = expression1 >>> expression2  
```  
  
## <a name="parameters"></a>Parametry  
 *wynik*  
 Dowolnej zmiennej.  
  
 *wyrażenie1*  
 Dowolne wyrażenie.  
  
 *wyrażenie2*  
 Dowolne wyrażenie.  
  
## <a name="remarks"></a>Uwagi  
 **>>>**  Operator wykonuje przesunięcie bitów z *wyrażenie1* prawej przez liczbę bitów określone w *wyrażenie2*. Wartości zerowe są wypełnione z lewej strony. Przesunąć poza z prawej strony cyfry zostaną odrzucone. Na przykład:  
  
```JavaScript  
var temp  
temp = -14 >>> 2  
```  
  
 Zmienna *temp* ma wartość początkową -14 (11111111 11111111 11111111 11110010 w dwóch w binarnym dopełnienia). Gdy nadejdzie przesuniętych odpowiednich bitów dwa, wartość równa 1073741820 (00111111 11111111 11111111 11111100 binarnie).  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Operator przypisania przesunięcia w prawo bez znaku (>>> =)](../../javascript/reference/unsigned-right-shift-assignment-operator-decrement-equal-javascript.md)   
 [Bitowy Operator przesunięcia w lewo (<\<)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [Operator przesunięcia bitowego w prawo (>>)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [Kolejność wykonywania działań](../../javascript/operator-subtractprecedence-javascript.md)   
 [Podsumowanie dla operatorów (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)