---
title: Funkcja — instrukcja (JavaScript) | Dokumentacja firmy Microsoft
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
- function_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- new operator
- declaring functions, syntax
- function statement
- declaring functions
ms.assetid: cc9cfd43-1305-41c8-ad67-545d20f4fafe
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e5fac3647e9374a9c909a420b73b86354cac69b6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24790570"
---
# <a name="function-statement-javascript"></a>function — Instrukcja (JavaScript)
Deklaruje nową funkcję.  
  
## <a name="syntax"></a>Składnia  
  
```  
function functionname ([arg1 [, arg2 [,...[, argN]]]]) {  
    statements  
}   
```  
  
## <a name="parameters"></a>Parametry  
 `functionname`  
 Wymagany. Nazwa funkcji.  
  
 `arg1...argN`  
 Opcjonalny. Opcjonalne, rozdzielana przecinkami lista argumentów rozumie funkcji.  
  
 `statements`  
 Opcjonalny. Co najmniej jeden[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] instrukcje.  
  
## <a name="remarks"></a>Uwagi  
 Użyj `function` instrukcji do zadeklarowania funkcji do późniejszego użycia. Kod, który jest zawarty w `statements` nie jest wykonywana do czasu wywołania funkcji z innych miejscach w skrypcie.  
  
 [Zwracać](../../javascript/reference/return-statement-javascript.md) instrukcji służy do zwracania wartości z funkcji. Nie trzeba używać `return` instrukcję; zostanie program zwracane, gdy zostanie osiągnięty koniec funkcji. Jeśli nie `return` instrukcja jest wykonywana w funkcji, lub jeśli `return` wyrażenie nie ma instrukcji, funkcja zwraca wartość `undefined`.  
  
> [!NOTE]
>  Podczas wywoływania funkcji, należy uwzględnić nawiasy i wymagane argumenty. Wywołanie funkcji bez nawiasów zwraca odwołanie do funkcji, nie wyniki funkcji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `function` instrukcji.  
  
```JavaScript  
function myfunction (arg1, arg2) {  
    var r = arg1 * arg2;  
    return(r);  
}  
```  
  
## <a name="example"></a>Przykład  
 Funkcja można przypisać do zmiennej. Jest to zilustrowane w poniższym przykładzie.  
  
```JavaScript  
function AddFive(x) {  
    return x + 5;  
}  
  
function AddTen(x) {  
    return x + 10;  
}  
  
var condition = false;  
  
var MyFunc;  
if (condition) {  
    MyFunc = AddFive;  
}  
else {  
    MyFunc = AddTen;  
}  
  
var result = MyFunc(123);  
// Output: 133  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [New — Operator](../../javascript/reference/new-operator-decrementjavascript.md)