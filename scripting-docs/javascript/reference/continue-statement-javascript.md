---
title: "Continue — instrukcja (JavaScript) | Dokumentacja firmy Microsoft"
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
- continue_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- do...while statement
- continue statement
- loop structures, continue statement
ms.assetid: f8a30d9f-e2de-4e1f-8668-4e4cf95f7df9
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 391f919c4d06a6c529bfee34e21ca7238b3c63b7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="continue-statement-javascript"></a>continue — Instrukcja (JavaScript)
Zatrzymuje bieżącej iteracji pętli i uruchamia nową iterację.  
  
## <a name="syntax"></a>Składnia  
  
```  
continue [label];  
```  
  
## <a name="remarks"></a>Uwagi  
 Opcjonalny `label` argument określa instrukcji, do którego `continue` ma zastosowanie.  
  
 Można użyć `continue` instrukcji tylko wewnątrz `while`, `do...while`, **dla**, lub `for...in` pętli. Wykonywanie `continue` instrukcji spowoduje zatrzymanie bieżącej iteracji pętli i kontynuuje przepływem programu z początkiem pętli. Ma to następujące skutki na różne typy sprzężeń:  
  
-   `while`i `do...while` pętle testowanie ich stanu i jeśli PRAWDA, wykonaj pętlę ponownie.  
  
-   `for`pętle wykonanie ich wyrażenie przyrostowe, a jeśli wyrażenie testu ma wartość true, wykonaj pętlę ponownie.  
  
-   `for...in`pętle, przejdź do następnego pola określonej zmiennej i ponownie wykonaj pętlę.  
  
## <a name="examples"></a>Przykłady  
 W tym przykładzie pętlę iteruje od 1 do 9. Instrukcje między `continue` i na końcu `for` treści zostały pominięte z powodu użycia `continue` instrukcji wraz z wyrażenia `(i < 5)`.  
  
```JavaScript  
for (var i = 1; i < 10; i++) {  
    if (i < 5) {  
        continue;  
    }  
    document.write (i);  
    document.write (" ");  
}  
  
// Output: 5 6 7 8 9  
```  
  
 W poniższym kodzie `continue` odwołuje się do `for` pętli, które jest poprzedzony `Inner:` etykiety. Gdy `j` to 24, `continue` instrukcja powoduje, że `for` przejdź do następnej iteracji pętli. Numery 21 do 23 i 25 do 30 wydruku w każdym wierszu.  
  
```JavaScript  
Outer:  
for (var i = 1; i <= 10; i++) {  
    document.write ("<br />");  
    document.write ("i: " + i);  
    document.write (" j: ");  
  
Inner:  
    for (var j = 21; j <= 30; j++) {  
        if (j == 24) {  
             continue Inner;  
        }  
        document.write (j + " ");  
    }  
}  
  
//Output:  
//i: 1 j: 21 22 23 25 26 27 28 29 30   
//i: 2 j: 21 22 23 25 26 27 28 29 30   
//i: 3 j: 21 22 23 25 26 27 28 29 30   
//i: 4 j: 21 22 23 25 26 27 28 29 30   
//i: 5 j: 21 22 23 25 26 27 28 29 30   
//i: 6 j: 21 22 23 25 26 27 28 29 30   
//i: 7 j: 21 22 23 25 26 27 28 29 30   
//i: 8 j: 21 22 23 25 26 27 28 29 30   
//i: 9 j: 21 22 23 25 26 27 28 29 30   
//i: 10 j: 21 22 23 25 26 27 28 29 30  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcja BREAK](../../javascript/reference/break-statement-javascript.md)   
 [do... while — instrukcja](../../javascript/reference/do-dot-dot-dot-while-statement-javascript.md)   
 [for — instrukcja](../../javascript/reference/for-statement-javascript.md)   
 [for... w instrukcji](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [Labeled — instrukcja](../../javascript/reference/labeled-statement-javascript.md)   
 [while — instrukcja](../../javascript/reference/while-statement-javascript.md)