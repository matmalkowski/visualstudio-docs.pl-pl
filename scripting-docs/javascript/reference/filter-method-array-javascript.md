---
title: Filter — metoda (tablica) (JavaScript) | Dokumentacja firmy Microsoft
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
- arrays [JavaScript], filter method
- filter method [JavaScript]
ms.assetid: 1d260370-9e6e-43fc-870f-2d35850db7ee
caps.latest.revision: 32
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 33a08fdba38de558dabc749a634fb9b69c52c98a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24790843"
---
# <a name="filter-method-array-javascript"></a>filter — Metoda (Tablica) (JavaScript)
Zwraca elementy tablicy, które spełniają warunek określony w funkcji wywołania zwrotnego.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
array1.filter(callbackfn[, thisArg])  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Definicja|  
|---------------|----------------|  
|`array1`|Wymagany. Obiekt tablicy.|  
|`callbackfn`|Wymagany. Funkcja, która akceptuje maksymalnie trzy argumenty. `filter` Wywołania metody `callbackfn` funkcji jeden raz dla każdego elementu w tablicy.|  
|`thisArg`|Opcjonalny. Obiekt, do którego `this` — słowo kluczowe może odwoływać się w `callbackfn` funkcji. Jeśli `thisArg` zostanie pominięty, `undefined` jest używany jako `this` wartość.|  
  
## <a name="return-value"></a>Wartość zwracana  
 Nowej tablicy, która zawiera wszystkie wartości, dla których zwraca funkcja wywołania zwrotnego `true`. Jeśli funkcja wywołania zwrotnego `false` dla wszystkich elementów `array1`, długość nowej tablicy wynosi 0.  
  
## <a name="exceptions"></a>Wyjątki  
 Jeśli `callbackfn` argument nie jest obiektem funkcji `TypeError` wyjątku.  
  
## <a name="remarks"></a>Uwagi  
 `filter` Wywołania metody `callbackfn` funkcji jeden raz dla każdego elementu w tablicy, rosnąco indeksu. Funkcja wywołania zwrotnego nie jest wywoływana dla brakujących elementów tablicy.  
  
 Oprócz obiektów tablicy `filter` metody mogą być używane przez dowolny obiekt `length` właściwości oraz że ma wartość liczbowa indeksowane nazw właściwości.  
  
## <a name="callback-function-syntax"></a>Składnia funkcji wywołania zwrotnego  
 Składnia funkcji wywołania zwrotnego jest następująca:  
  
 `function callbackfn(value, index, array1)`  
  
 Funkcję wywołania zwrotnego można zadeklarować przy użyciu maksymalnie trzech parametrów.  
  
 Poniższa lista zawiera parametry funkcji wywołania zwrotnego.  
  
|Argument wywołania zwrotnego|Definicja|  
|-----------------------|----------------|  
|`value`|Wartość elementu tablicy.|  
|`index`|Indeks liczbowy elementu tablicy.|  
|`array1`|Obiekt tablicy zawierający element.|  
  
## <a name="modifying-the-array-object"></a>Modyfikowanie obiektu tablicy  
 `filter` Metoda bezpośrednio nie modyfikować oryginalnego tablicy, ale funkcja wywołania zwrotnego może go zmodyfikować. W poniższej tabeli przedstawiono wyniki modyfikowania obiektu tablicy po `filter` uruchamia metody.  
  
|Warunek po `filter` uruchamia — metoda|Element przekazany do funkcji wywołania zwrotnego?|  
|------------------------------------------------|------------------------------------------|  
|Element zostanie dodany poza pierwotną długością tablicy.|Nie.|  
|Element zostanie dodany do tablicy miejscu brakującego elementu.|Tak, jeśli w ten indeks nie został jeszcze przekazany do funkcji wywołania zwrotnego.|  
|Element został zmieniony.|Tak, jeśli ten element nie został jeszcze przekazany do funkcji wywołania zwrotnego.|  
|Element został usunięty z tablicy.|Nie, chyba że ten element został już przekazany do funkcji wywołania zwrotnego.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `filter` metody.  
  
```JavaScript  
// Define a callback function.  
function CheckIfPrime(value, index, ar) {  
    high = Math.floor(Math.sqrt(value)) + 1;  
  
    for (var div = 2; div <= high; div++) {  
        if (value % div == 0) {  
            return false;  
        }  
    }   
    return true;  
}  
  
// Create the original array.  
var numbers = [31, 33, 35, 37, 39, 41, 43, 45, 47, 49, 51, 53];  
  
// Get the prime numbers that are in the original array.   
var primes = numbers.filter(CheckIfPrime);  
  
document.write(primes);  
// Output: 31,37,41,43,47,53  
```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie `callbackfn` argument zawiera kod funkcji wywołania zwrotnego.  
  
```JavaScript  
// Create the original array.  
var arr = [5, "element", 10, "the", true];  
  
// Create an array that contains the string  
// values that are in the original array.  
var result = arr.filter(  
    function (value) {  
        return (typeof value === 'string');  
    }  
);  
  
document.write(result);  
// Output: element, the  
```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono nazwy właściwości rozpoczynających się od litery "css" w `window` DOM obiektu.  
  
```JavaScript  
var filteredNames = Object.getOwnPropertyNames(window).filter(IsC);  
  
    for (i in filteredNames)  
        document.write(filteredNames[i] + "<br/>");  
  
// Check whether the string starts with "css".  
function IsC(value) {  
    var firstChar = value.substr(0, 3);  
    if (firstChar.toLowerCase() == "css")  
        return true;  
    else  
        return false;  
    }  
  
// Output:  
// CSSRule  
// CSSFontFaceRule  
// CSSImportRule  
// CSSMediaRule  
// CSSNamespaceRule  
// CSSPageRule  
// CSSRuleList  
// CSSStyleDeclaration  
// CSSStyleRule  
// CSSStyleSheet  
  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `thisArg` argumentu, który określa obiekt, do którego `this` — słowo kluczowe może się odwoływać.  
  
```JavaScript  
var checkNumericRange = function(value) {  
    if (typeof value !== 'number')  
        return false;  
    else   
        return value >= this.minimum && value <= this.maximum;  
}  
  
var numbers = [6, 12, "15", 16, "the", -12];  
  
// The obj argument enables use of the this value  
// within the callback function.  
var obj = { minimum: 10, maximum: 20 }  
  
var result = numbers.filter(checkNumericRange, obj);  
  
document.write(result);  
// Output: 12,16  
  
```  
  
## <a name="example"></a>Przykład  
 `filter` Metoda może być stosowana do ciągu zamiast tablicy. W przykładzie poniżej pokazano, jak to zrobić.  
  
```JavaScript  
// Define a callback function that returns true  
// if the current array element follows a space  
// or is the first character.  
function CheckValue(value, index, ar) {  
    if (index == 0)  
        return true;  
    else  
        return ar[index - 1] === " ";  
}  
  
// Create a string.  
var sentence = "The quick brown fox jumps over the lazy dog.";   
  
// Create an array that contains all characters that follow a space.  
var subset = [].filter.call(sentence, CheckValue);   
  
// You can use this alternative syntax.  
//var subset = Array.prototype.filter.call(sentence, CheckValue);  
  
document.write(subset);  
// Output: T,q,b,f,j,o,t,l,d  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Array — obiekt](../../javascript/reference/array-object-javascript.md)   
 [Używanie tablic](../../javascript/advanced/using-arrays-javascript.md)   
 [map — metoda (tablica)](../../javascript/reference/map-method-array-javascript.md)   
 [forEach — metoda (tablica)](../../javascript/reference/foreach-method-array-javascript.md)