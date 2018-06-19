---
title: Operator przypisania przesunięcia w prawo bez znaku (&gt;&gt;&gt;=) (JavaScript) | Dokumentacja firmy Microsoft
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
- '>>>='
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- '>>>= operator'
- unsigned right shift assignment operator (>>>=)
- assignment operators, JavaScript
ms.assetid: f67c3737-7d39-41ae-9c11-8b16d38f6179
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1272cbb58645df605743c6790642cd0e295442aa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791938"
---
# <a name="unsigned-right-shift-assignment-operator-gtgtgt-javascript"></a>Operator przypisania przesunięcia w prawo bez znaku (&gt;&gt;&gt;=) (JavaScript)
Prawo przewiduje wartość zmiennej przez liczbę bitów określony w wartości wyrażenia bez znaku, zachowania i przypisuje wynik do zmiennej.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
result >>>= expression  
```  
  
## <a name="parameters"></a>Parametry  
 *wynik*  
 Dowolnej zmiennej.  
  
 *wyrażenie*  
 Dowolne wyrażenie.  
  
## <a name="remarks"></a>Uwagi  
 Przy użyciu >>> = — operator jest dokładnie taka sama jak wykonanie następujących czynności:  
  
```JavaScript  
result = result >>> expression  
```  
  
 **>>>=**  Operator wykonuje przesunięcie bitów z *wynik* prawej przez liczbę bitów określone w *wyrażenia*. Wartości zerowe są wypełnione z lewej strony. Przesunąć poza z prawej strony cyfry zostaną odrzucone. Na przykład:  
  
```JavaScript  
var temp  
temp = -14  
temp >>>= 2  
```  
  
 Zmienna *temp* ma wartość początkową -14 (11111111 11111111 11111111 11110010 w dwóch w binarnym dopełnienia). Przy przesunięciu odpowiednich bitów dwa, wartość równa 1073741820 (00111111 11111111 11111111 11111100 binarnie).  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Operator przesunięcia w prawo bez znaku (>>>)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [Bitowy Operator przesunięcia w lewo (<\<)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [Operator przesunięcia bitowego w prawo (>>)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [Kolejność wykonywania działań](../../javascript/operator-subtractprecedence-javascript.md)   
 [Podsumowanie dla operatorów (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)