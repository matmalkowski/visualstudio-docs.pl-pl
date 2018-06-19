---
title: TypeOf — Operator (JavaScript) | Dokumentacja firmy Microsoft
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
- typeof_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- typeof operator
ms.assetid: ee8a1036-119f-486f-b034-b07bdba87f0c
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a9ff8c7942c773d138dd599956c41d1e583e6288
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
ms.locfileid: "29899633"
---
# <a name="typeof-operator-javascript"></a>typeof — Operator (JavaScript)
Zwraca ciąg określający typ danych wyrażenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
typeof[(]expression[)] ;  
```  
  
## <a name="remarks"></a>Uwagi  
 *Wyrażenie* argument jest dowolne wyrażenie dla typu potrzebuje informacji.  
  
 `typeof` Operator zwraca informacje o typie jako ciąg. Istnieje siedem możliwe wartości, które `typeof` zwraca: "number", "string," "boolean", "obiektu" "działanie," "undefined" i "Nieznany".  
  
 Nawiasy są opcjonalne w `typeof` składni.  

 Obiekt może zwrócić w XMLHTTPRequest nieznanego typu. Obiektu modelu COM o nie analogowy w języku JavaScript może również zwrócić nieznanego typu.
  
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