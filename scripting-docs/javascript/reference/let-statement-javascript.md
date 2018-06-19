---
title: Let — instrukcja (JavaScript) | Dokumentacja firmy Microsoft
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
- let_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- let statement
- declaring variables, let statement
ms.assetid: c7e4f8a9-8f54-47b6-aed2-956959c1ecfd
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c447a1bf0c430771ff146965a592f7e160e2055b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791176"
---
# <a name="let-statement-javascript"></a>let — Instrukcja (JavaScript)
Deklaruje zmienną o zakresie bloku.  
  
## <a name="syntax"></a>Składnia  
  
```  
let variable1 = value1  
```  
  
#### <a name="parameters"></a>Parametry  
 `variable1`  
 Nazwa zmiennej został zadeklarowany.  
  
 `value1`  
 Wartość początkowa przypisaną do zmiennej.  
  
## <a name="remarks"></a>Uwagi  
 Użyj `let` instrukcji, aby zadeklarować zmienną, której zakres jest ograniczony do bloku, w którym jest zadeklarowany. Można przypisać wartości do zmiennych przy deklarowaniu je lub później w skrypcie.  
  
 Zmienna zadeklarowana przy użyciu `let` nie może służyć przed spowoduje jego deklaracji lub wystąpił błąd.  
  
 Jeśli nie zainicjować zmiennej użytkownika w `let` instrukcji, zostaje automatycznie przypisany [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] wartość `undefined`.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `let` instrukcji.  
  
```JavaScript  
var  l = 10;  
{  
    let l = 2;  
   // At this point, l = 2.  
}  
// At this point, l = 10.  
  
// Additional ways to declare a variable using let.  
let index;  
let name = "Thomas Jefferson";  
let answer = 42, counter, numpages = 10;  
let myarray = new Array();  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Const — instrukcja](../../javascript/reference/const-statement-javascript.md)   
 [New — Operator](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Array — obiekt](../../javascript/reference/array-object-javascript.md)   
 [Zmienne](../../javascript/variables-javascript.md)