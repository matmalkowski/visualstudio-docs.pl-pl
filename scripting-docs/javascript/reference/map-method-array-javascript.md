---
title: "map — metoda (tablica) (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- map method [JavaScript]
- arrays [JavaScript], map method
ms.assetid: 500dc4f8-d73d-4a28-a5b8-c9bd5674ea36
caps.latest.revision: "20"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 609d9c88000a7a30fe8edc03b52df032f7d19ba9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="map-method-array-javascript"></a>map — Metoda (Tablica) (JavaScript)
Wywołuje zdefiniowaną funkcję wywołania zwrotnego dla każdego elementu tablicy i zwraca tablicę zawierającą wyniki.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
array1.map(callbackfn[, thisArg])  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Definicja|  
|---------------|----------------|  
|`array1`|Wymagany. Obiekt tablicy.|  
|`callbackfn`|Wymagany. Funkcja, która akceptuje maksymalnie trzy argumenty. `map` Wywołania metody `callbackfn` funkcji jeden raz dla każdego elementu w tablicy.|  
|`thisArg`|Opcjonalny. Obiekt, do którego `this` — słowo kluczowe może odwoływać się w `callbackfn` funkcji. Jeśli `thisArg` zostanie pominięty, `undefined` jest używany jako `this` wartość.|  
  
## <a name="return-value"></a>Wartość zwracana  
 Nowa tablica, w której każdy element jest wartością zwracaną przez funkcję wywołania zwrotnego dla skojarzonego oryginalnego elementu tablicy.  
  
## <a name="exceptions"></a>Wyjątki  
 Jeśli `callbackfn` argument nie jest obiektem funkcji `TypeError` wyjątku.  
  
## <a name="remarks"></a>Uwagi  
 `map` Wywołania metody `callbackfn` funkcji jeden raz dla każdego elementu w tablicy, rosnąco indeksu. Funkcja wywołania zwrotnego nie jest wywoływana dla brakujących elementów tablicy.  
  
 Oprócz obiektów tablicy `map` metody mogą być używane przez dowolny obiekt `length` właściwości oraz że ma wartość liczbowa indeksowane nazw właściwości.  
  
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
 Obiekt tablicy można modyfikować przy użyciu funkcji wywołania zwrotnego.  
  
 W poniższej tabeli przedstawiono wyniki modyfikowania obiektu tablicy po `map` uruchamia metody.  
  
|Warunek po `map` uruchamia — metoda|Element przekazany do funkcji wywołania zwrotnego?|  
|---------------------------------------------|------------------------------------------|  
|Element zostanie dodany poza pierwotną długością tablicy.|Nie.|  
|Element zostanie dodany do tablicy miejscu brakującego elementu.|Tak, jeśli w ten indeks nie został jeszcze przekazany do funkcji wywołania zwrotnego.|  
|Element został zmieniony.|Tak, jeśli ten element nie został jeszcze przekazany do funkcji wywołania zwrotnego.|  
|Element został usunięty z tablicy.|Nie, chyba że ten element został już przekazany do funkcji wywołania zwrotnego.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `map` metody.  
  
```JavaScript  
// Define the callback function.  
function AreaOfCircle(radius) {  
    var area = Math.PI * (radius * radius);  
    return area.toFixed(0);  
}  
  
// Create an array.  
var radii = [10, 20, 30];  
  
// Get the areas from the radii.  
var areas = radii.map(AreaOfCircle);  
  
document.write(areas);  
  
// Output:  
// 314,1257,2827  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `thisArg` argumentu, który określa obiekt, do którego `this` — słowo kluczowe może się odwoływać.  
  
```JavaScript  
// Define an object that contains a divisor property and  
// a remainder function.  
var obj = {  
    divisor: 10,  
    remainder: function (value) {  
        return value % this.divisor;  
    }  
}  
  
// Create an array.  
var numbers = [6, 12, 25, 30];  
  
// Get the remainders.  
// The obj argument specifies the this value in the callback function.  
var result = numbers.map(obj.remainder, obj);  
document.write(result);  
  
// Output:  
// 6,2,5,0  
```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie wbudowaną[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] metoda jest używana jako funkcja wywołania zwrotnego.  
  
```JavaScript  
// Apply Math.sqrt(value) to each element in an array.  
var numbers = [9, 16];  
var result = numbers.map(Math.sqrt);  
  
document.write(result);  
// Output: 3,4  
```  
  
## <a name="example"></a>Przykład  
 `map` Metoda może być stosowana do ciągu. Ilustruje to poniższy przykład.  
  
```JavaScript  
// Define the callback function.  
function threeChars(value, index, str) {  
    // Create a string that contains the previous, current,  
    // and next character.  
    return str.substring(index - 1, index + 2);  
}  
  
// Create a string.  
var word = "Thursday";  
  
// Apply the map method to the string.  
// Each array element in the result contains a string that  
// has the previous, current, and next character.  
// The commented out statement shows an alternative syntax.  
var result = [].map.call(word, threeChars);  
// var result = Array.prototype.map.call(word, threeChars);  
  
document.write(result);  
  
// Output:  
// Th,Thu,hur,urs,rsd,sda,day,ay  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [JavaScript — metody](../../javascript/reference/javascript-methods.md)   
 [Array — obiekt](../../javascript/reference/array-object-javascript.md)   
 [Używanie tablic](../../javascript/advanced/using-arrays-javascript.md)   
 [Filter — metoda (tablica)](../../javascript/reference/filter-method-array-javascript.md)   
 [forEach — metoda (tablica)](../../javascript/reference/foreach-method-array-javascript.md)   
 [Hilo JavaScript przykładowej aplikacji (w Sklepie Windows)](http://hilojs.codeplex.com/SourceControl/latest)