---
title: Return — instrukcja (JavaScript) | Dokumentacja firmy Microsoft
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
- return_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- terminating execution
- return statement
- function statement
- return statement, syntax
- return statement, exiting functions in script
ms.assetid: a9130d90-11fb-43f5-a819-7e5435f74c05
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2c28f17bed2dfff021ea1aea268bb7a2eb3f3e58
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791308"
---
# <a name="return-statement-javascript"></a>return — Instrukcja (JavaScript)
Zamyka z bieżącej funkcji i zwraca wartość z tej funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
return[(][expression][)];   
```  
  
## <a name="remarks"></a>Uwagi  
 Opcjonalny *wyrażenie* argument jest wartością zwracaną z funkcji. Pominięcie funkcja nie zwraca wartości.  
  
 Możesz użyć `return` instrukcji, aby zatrzymać wykonanie funkcji i zwraca wartość *wyrażenia*. Jeśli *wyrażenie* zostanie pominięty, lub nie `return` wykonaniu instrukcji z wewnątrz funkcji, wyrażenie, które wywołały bieżącą funkcję przypisano niezdefiniowana wartość.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `return` instrukcji.  
  
```JavaScript  
function myfunction(arg1, arg2){  
   var r;  
   r = arg1 * arg2;  
   return(r);  
}  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `return` instrukcji, aby zwrócić funkcji.  
  
```JavaScript  
function doWork() {  
    return function calculate(y) { return y + 1; };  
}  
  
var func = doWork();  
var x = func(5);  
document.write(x);  
  
// Output: 6  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Function — instrukcja](../../javascript/reference/function-statement-javascript.md)