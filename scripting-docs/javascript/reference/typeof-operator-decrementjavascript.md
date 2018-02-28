---
title: "TypeOf — Operator (JavaScript) | Dokumentacja firmy Microsoft"
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
- typeof_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- typeof operator
ms.assetid: ee8a1036-119f-486f-b034-b07bdba87f0c
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c79c69e6c447b14e61fa67ccb8600d5d83bebd2b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="typeof-operator-javascript"></a>typeof — Operator (JavaScript)
Zwraca ciąg określający typ danych wyrażenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
typeof[(]expression[)] ;  
```  
  
## <a name="remarks"></a>Uwagi  
 *Wyrażenie* argument jest dowolne wyrażenie dla typu potrzebuje informacji.  
  
 `typeof` Operator zwraca informacje o typie jako ciąg. Brak sześciu możliwe wartości, które `typeof` zwraca: "number", "string," "boolean", "," "funkcji", a "undefined".  
  
 Nawiasy są opcjonalne w `typeof` składni.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład testy z typem danych zmiennych.  
  
```JavaScript  
var index = 5;  
var result = (typeof index === 'number');  
// Output: true  
  
var description = "abc";  
var result = (typeof description === 'string');  
// Output: true  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład testów dla typu danych `undefined` zmiennych zadeklarowanych i niezadeklarowany.  
  
```JavaScript  
var declared;  
var result = (declared === undefined);  
// Output: true  
  
var result = (typeof declared === 'undefined');  
// Output: true  
  
var result = (typeof notDeclared === 'undefined')  
// Output: true  
  
var obj = {};  
var result = (typeof obj.propNotDeclared === 'undefined');  
// Output: true  
  
// An undeclared variable cannot be used in a comparison without  
// the typeof operator, so the next line generates an error.  
//  var result = (notDeclared === undefined);  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Array.IsArray — funkcja](../../javascript/reference/array-isarray-function-javascript.md)   
 [Object.getprototypeof — funkcja](../../javascript/reference/object-getprototypeof-function-javascript.md)   
 [Stała undefined](../../javascript/reference/undefined-constant-javascript.md)   
 [Operatory porównania](../../javascript/reference/comparison-operators-javascript.md)   
 [Typy danych](../../javascript/data-types-javascript.md)   
 [Kolejność wykonywania działań](../../javascript/operator-subtractprecedence-javascript.md)   
 [Podsumowanie dla operatorów (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)