---
title: "IF... else — instrukcja (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- else_JavaScriptKeyword
- if_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- if statement, if...else
- loop structures, if...else statements
ms.assetid: dfbe86e8-9c1e-4ef5-bb9c-7d1db7ce2506
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fad12b970f69a15040acb59195f957a2a6eec3e0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="ifelse-statement-javascript"></a>if...else — Instrukcja (JavaScript)
Warunkowo wykonuje grupy poleceń w zależności od wartości wyrażenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
if (condition1) {  
    statement1  
}  
[else if (condition2) {  
    statement2  
}]  
[else {  
    statement3]   
}]  
```  
  
## <a name="parameters"></a>Parametry  
 `condition1`  
 Wymagany. Wyrażenie logiczne. Jeśli `condition1` jest `null` lub `undefined`, `condition1` jest traktowany jako `false`.  
  
 `statement1`  
 Opcjonalny. Wykonywanie instrukcji do wykonania, jeśli `condition1` jest **true**. Może być złożonej instrukcji.  
  
 `condition2`  
 Warunek, który ma zostać obliczone.  
  
 `statement2`  
 Opcjonalny. Wykonywanie instrukcji do wykonania, jeśli `condition2` jest `true`. Może być złożonej instrukcji.  
  
 `statement3`  
 Jeśli oba `condition1` i `condition2` są `false`, ta instrukcja jest wykonywana.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia sposób użycia `if`, `if else`, i `else`.  
  
 Dobrą praktyką jest ujmij `statement1` i `statement2` w nawiasach klamrowych ({}) dla uzyskania przejrzystości Aby uniknąć przypadkowej błędów.  
  
```JavaScript  
var z = 3;  
if (x == 5) {  
    z = 10;  
}  
else if (x == 10) {  
    z = 15;  
}  
else {  
    z = 20;  
}  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Operator warunkowy (trójargumentowy) (?:)](../../javascript/reference/conditional-ternary-operator-decrement-javascript.md)