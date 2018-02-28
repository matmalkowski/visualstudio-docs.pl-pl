---
title: "Const — instrukcja (JavaScript) | Dokumentacja firmy Microsoft"
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
- const_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- declaring variables, const statement
- const statement
ms.assetid: 3ad0840f-437f-4163-9571-86ecc5ddb987
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 68130cec4f1b1fe89d2fe3e673b28963d79aebde
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="const-statement-javascript"></a>const — Instrukcja (JavaScript)
Deklaruje zmienną o zakresie bloku z wartością stałą.  
  
## <a name="syntax"></a>Składnia  
  
```  
const constant1 = value1  
```  
  
#### <a name="parameters"></a>Parametry  
 `constant1`  
 Nazwa zmiennej został zadeklarowany.  
  
 `value1`  
 Wartość początkowa przypisaną do zmiennej.  
  
## <a name="remarks"></a>Uwagi  
 Użyj `const` instrukcji w celu zadeklarowania zmiennej z wartością stałą, której zakres jest ograniczony do bloku, w którym jest zadeklarowany. Nie można zmienić wartość zmiennej.  
  
 Zmienna zadeklarowana przy użyciu `const` musi zostać zainicjowany, gdy jest on zadeklarowany jako.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `const` instrukcji.  
  
```JavaScript  
var c = 10;  
{  
    const c = 2;  
   // At this point, c = 2.  
}  
// At this point, c = 10.  
  
// Additional ways to declare a variable using const.  
const name = "Thomas Jefferson";  
const answer = 42, numpages = 10;  
const myarray = new Array();  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Let — instrukcja](../../javascript/reference/let-statement-javascript.md)   
 [New — Operator](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Array — obiekt](../../javascript/reference/array-object-javascript.md)   
 [Zmienne](../../javascript/variables-javascript.md)