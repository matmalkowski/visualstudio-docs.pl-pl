---
title: "do... while — instrukcja (JavaScript) | Dokumentacja firmy Microsoft"
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
- do_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- do...while statement
- terminating loops
- loop structures, do and do-while
ms.assetid: 8b7782ba-fbad-48cd-9639-193566da6ae5
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 895d98a3de3a6691ce60bf0456bb838403619f88
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="dowhile-statement-javascript"></a>do...while — Instrukcja (JavaScript)
Wykonuje bloku instrukcji raz, a następnie powtarza wykonywania pętli, dopóki wyrażenie warunku daje w wyniku `false`.  
  
## <a name="syntax"></a>Składnia  
  
```  
do {  
    statement  
}  
while (expression) ;   
```  
  
## <a name="parameters"></a>Parametry  
 `statement`  
 Wymagany. Wykonywanie instrukcji do wykonania, jeśli `expression` jest `true`. Może być złożonej instrukcji.  
  
 `expression`  
 Wymagany. Wyrażenie, które można rzutować na typ Boolean `true` lub `false`. Jeśli `expression` jest `true`, pętli jest wykonywane ponownie. Jeśli `expression` jest `false`, pętla zostanie zakończony.  
  
## <a name="remarks"></a>Uwagi  
 W odróżnieniu od `while` instrukcji `do...while` pętla jest wykonywana raz przed Obliczanie wyrażenia warunkowego.  
  
 Na każdej linii w `do...while` bloku, można użyć `break` można użyć instrukcji spowodują jego zakończenie pętli, albo przepływu program `continue` instrukcji, aby przejść bezpośrednio do `while` wyrażenia.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie instrukcje w `do...while` pętli kontynuować jego wykonywanie tak długo, jak zmienna `i` jest mniejsza niż 10.  
  
```JavaScript  
var i = 0;  
do {  
    document.write(i + " ");  
    i++;  
} while (i < 10);  
  
// Output: 0 1 2 3 4 5 6 7 8 9   
```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie instrukcje wewnątrz pętli są wykonywane raz, nawet jeśli warunek nie jest spełniony.  
  
```JavaScript  
var i = 10;  
do {  
    document.write(i + " ");  
    i++;  
} while (i < 10);  
  
// Output: 10  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcja BREAK](../../javascript/reference/break-statement-javascript.md)   
 [Continue — instrukcja](../../javascript/reference/continue-statement-javascript.md)   
 [for — instrukcja](../../javascript/reference/for-statement-javascript.md)   
 [for... w instrukcji](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [while — instrukcja](../../javascript/reference/while-statement-javascript.md)   
 [Labeled — instrukcja](../../javascript/reference/labeled-statement-javascript.md)