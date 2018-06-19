---
title: BIND — metoda (funkcja) (JavaScript) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- parameters [JavaScript], bind method
- arguments [JavaScript], bind method
- bind method [JavaScript]
- this keyword [JavaScript], bind method
ms.assetid: 28946f47-b758-48cf-b508-610a0f2f6e19
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dd7fc752df9bd41f8625ac2cb484486dfd19558d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24789235"
---
# <a name="bind-method-function-javascript"></a>bind — Metoda (Funkcja) (JavaScript)
Dla danej funkcji tworzy funkcję powiązaną, która ma tę samą treść, co funkcja pierwotna. W powiązanej funkcji `this` obiekt jest rozpoznawana jako przekazano obiekt. Funkcja powiązania ma określone parametry początkowe.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
function.bind(thisArg[,arg1[,arg2[,argN]]])  
```  
  
#### <a name="parameters"></a>Parametry  
 `function`  
 Wymagany. Obiekt funkcyjny.  
  
 `thisArg`  
 Wymagany. Obiekt, do którego `this` — słowo kluczowe może odwoływać się wewnątrz nowych funkcji.  
  
 `arg1`[,`arg2`[,`argN`]]]  
 Opcjonalny. Lista argumentów do przekazania do nowej funkcji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Nową funkcję, która jest taka sama jak `function` funkcji, z wyjątkiem `thisArg` obiektu i argumenty początkowej.  
  
## <a name="exceptions"></a>Wyjątki  
 Jeśli określony `function` nie jest to funkcja `TypeError` wyjątku.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia sposób użycia `bind` metody.  
  
```JavaScript  
// Define the original function.  
var checkNumericRange = function (value) {  
    if (typeof value !== 'number')  
        return false;  
    else  
        return value >= this.minimum && value <= this.maximum;  
}  
  
// The range object will become the this value in the callback function.  
var range = { minimum: 10, maximum: 20 };  
  
// Bind the checkNumericRange function.  
var boundCheckNumericRange = checkNumericRange.bind(range);  
  
// Use the new function to check whether 12 is in the numeric range.  
var result = boundCheckNumericRange (12);  
document.write(result);  
  
// Output: true  
```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie `thisArg` obiektu jest inny niż obiekt, który zawiera oryginalnej metody.  
  
```JavaScript  
// Create an object that contains the original function.  
var originalObject = {  
    minimum: 50,  
    maximum: 100,  
    checkNumericRange: function (value) {  
        if (typeof value !== 'number')  
            return false;  
        else  
            return value >= this.minimum && value <= this.maximum;  
    }  
}  
  
// Check whether 10 is in the numeric range.  
var result = originalObject.checkNumericRange(10);  
document.write(result + " ");  
// Output: false  
  
// The range object supplies the range for the bound function.  
var range = { minimum: 10, maximum: 20 };  
  
// Create a new version of the checkNumericRange function that uses range.  
var boundObjectWithRange = originalObject.checkNumericRange.bind(range);  
  
// Check whether 10 is in the numeric range.  
var result = boundObjectWithRange(10);  
document.write(result);  
// Output: true  
```  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia sposób użycia `arg1[,arg2[,argN]]]` argumentów. Powiązanej funkcji używa parametrów określonych w `bind` metody jako parametry pierwszego i drugiego. Wszelkie parametry określone, gdy wywoływana jest funkcja powiązana, są używane jako trzeci, czwarty (i tak dalej) parametr.  
  
```JavaScript  
// Define the original function with four parameters.  
var displayArgs = function (val1, val2, val3, val4) {  
    document.write(val1 + " " + val2 + " " + val3 + " " + val4);  
}  
  
var emptyObject = {};  
  
// Create a new function that uses the 12 and "a" parameters  
// as the first and second parameters.  
var displayArgs2 = displayArgs.bind(emptyObject, 12, "a");  
  
// Call the new function. The "b" and "c" parameters are used  
// as the third and fourth parameters.  
displayArgs2("b", "c");  
// Output: 12 a b c   
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Function — obiekt](../../javascript/reference/function-object-javascript.md)   
 [Filter — metoda (tablica)](../../javascript/reference/filter-method-array-javascript.md)   
 [Używanie metody bind](../../javascript/advanced/using-the-bind-method-javascript.md)   
 [Hilo JavaScript przykładowej aplikacji (w Sklepie Windows)](http://hilojs.codeplex.com/SourceControl/latest)