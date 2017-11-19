---
title: "callee — właściwość (argumenty) (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: callee
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: callee property
ms.assetid: ad9d4d21-73f0-44f6-8bec-502f3456cd23
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 33f1c2926d76c0a1f088c8f4222b6f24c004b73b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="callee-property-arguments-javascript"></a>callee — Właściwość (argumenty) (JavaScript)
Zwraca `Function` obiektu wykonywana, oznacza to, że tekst podstawowy określonego `Function` obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
[function.]arguments.callee  
```  
  
## <a name="remarks"></a>Uwagi  
 Opcjonalny *funkcja* argument jest nazwą aktualnie wykonywanych `Function` obiektu.  
  
 `callee` Właściwości jest elementem członkowskim **argumenty** obiekt, który staje się dostępna tylko podczas wykonywania funkcji skojarzone.  
  
 Początkowa wartość `callee` jest właściwość `Function` obiektów, które było wykonywane. Dzięki temu funkcje anonimowe za cyklicznego.  
  
## <a name="example"></a>Przykład  
  
```JavaScript  
function factorial(n){  
  if (n <= 0)  
     return 1;  
  else  
     return n * arguments.callee(n - 1)  
}  
document.write(factorial(4));  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Dotyczy**: [obiekt arguments](../../javascript/reference/arguments-object-javascript.md)&#124; [Funkcji obiektu](../../javascript/reference/function-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [caller — właściwość (funkcja)](../../javascript/reference/caller-property-function-javascript.md)