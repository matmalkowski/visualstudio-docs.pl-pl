---
title: "BREAK — instrukcja (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: break_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- do...while statement
- break statement
ms.assetid: 5be0f2a8-5fe7-4a6c-89af-ca20a925ce87
caps.latest.revision: "23"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5f085a4e51309bf9a060e9ffa352c6ae85924237
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="break-statement-javascript"></a>break — Instrukcja (JavaScript)
Kończy pętlę bieżącego lub, jeśli w połączeniu z `label`, kończy skojarzona instrukcja.  
  
## <a name="syntax"></a>Składnia  
  
```  
break [label];  
```  
  
## <a name="remarks"></a>Uwagi  
 Opcjonalny `label` argument określa etykiety są krytyczne z instrukcji.  
  
 Zazwyczaj używają `break` instrukcji w `switch` instrukcje i `while`, `for`, `for...in`, lub `do...while` pętli. Najczęściej używać `label` argument `switch` instrukcji, ale może być używana w żadnej instrukcji, zarówno proste i złożone.  
  
 Wykonywanie `break` instrukcji kończy działanie z bieżącej pętli lub instrukcji i rozpocznie się wykonywanie skryptu z instrukcją bezpośrednio po.  
  
## <a name="examples"></a>Przykłady  
 W tym przykładzie licznik ustawiono liczba z zakresu od 1 do 99; jednak `break` instrukcji pętli kończy się po 14 liczby.  
  
```JavaScript  
for (var i = 1; i < 100; i++) {  
    if (i == 15) {  
        break;  
    }  
    document.write (i);  
    document.write (" ");  
}  
  
// Output: 1234567891011121314  
```  
  
 W poniższym kodzie `break` odwołuje się do `for` pętli, które jest poprzedzony `Inner:` instrukcji. Gdy `j` wynosi 24 `break` instrukcja powoduje przepływem programu zakończyć pracę tego pętli. Numery 21 do 23 wydruku w każdym wierszu.  
  
```JavaScript  
Outer:  
for (var i = 1; i <= 10; i++) {  
    document.write ("<br />");  
    document.write ("i: " + i);  
    document.write (" j: ");  
Inner:  
    for (var j = 21; j <= 30; j++) {  
        if (j == 24) {  
            break Inner;  
        }  
        document.write (j + " ");  
    }  
}  
  
// Output:   
// i: 1 j: 21 22 23   
// i: 2 j: 21 22 23   
// i: 3 j: 21 22 23   
// i: 4 j: 21 22 23   
// i: 5 j: 21 22 23   
// i: 6 j: 21 22 23   
// i: 7 j: 21 22 23   
// i: 8 j: 21 22 23   
// i: 9 j: 21 22 23   
// i: 10 j: 21 22 23  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Continue — instrukcja](../../javascript/reference/continue-statement-javascript.md)   
 [do... while — instrukcja](../../javascript/reference/do-dot-dot-dot-while-statement-javascript.md)   
 [for — instrukcja](../../javascript/reference/for-statement-javascript.md)   
 [for... w instrukcji](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [Labeled — instrukcja](../../javascript/reference/labeled-statement-javascript.md)   
 [while — instrukcja](../../javascript/reference/while-statement-javascript.md)