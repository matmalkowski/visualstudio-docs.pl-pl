---
title: "forEach — metoda (tablica) (JavaScript) | Dokumentacja firmy Microsoft"
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
- forEach method [JavaScript]
- arrays [JavaScript], forEach method
- callback function, forEach method [JavaScript]
ms.assetid: bd188034-a62b-4cbd-99c8-46d70dd6823d
caps.latest.revision: "28"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ec35c49e272ba50e26d3e4e7d892aa719a090d73
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="foreach-method-array-javascript"></a>forEach — Metoda (Array) (JavaScript)
Wykonuje określoną czynność dla każdego elementu w tablicy.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
array1.forEach(callbackfn[, thisArg])  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Definicja|  
|---------------|----------------|  
|`array1`|Wymagany. Obiekt tablicy.|  
|`callbackfn`|Wymagany. Funkcja, która akceptuje maksymalnie trzy argumenty. `forEach`wywołania `callbackfn` funkcji jeden raz dla każdego elementu w tablicy.|  
|`thisArg`|Opcjonalny. Obiekt, do którego `this` — słowo kluczowe może odwoływać się w `callbackfn` funkcji. Jeśli `thisArg` zostanie pominięty, `undefined` jest używany jako `this` wartość.|  
  
## <a name="exceptions"></a>Wyjątki  
 Jeśli `callbackfn` argument nie jest obiektem funkcji `TypeError` wyjątku.  
  
## <a name="remarks"></a>Uwagi  
 `forEach` Wywołania metody `callbackfn` funkcji jeden raz dla każdego elementu w tablicy, rosnąco indeksu. Funkcja wywołania zwrotnego nie jest wywoływana dla brakujących elementów tablicy.  
  
 Oprócz obiektów tablicy `forEach` metody mogą być używane przez dowolny obiekt `length` właściwości oraz że ma wartość liczbowa indeksowane nazw właściwości.  
  
## <a name="callback-function-syntax"></a>Składnia funkcji wywołania zwrotnego  
 Składnia funkcji wywołania zwrotnego jest następująca:  
  
 `function callbackfn(value, index, array1)`  
  
 Funkcję wywołania zwrotnego można zadeklarować przy użyciu maksymalnie trzech parametrów.  
  
 Parametry funkcji wywołania zwrotnego są następujące.  
  
|Argument wywołania zwrotnego|Definicja|  
|-----------------------|----------------|  
|`value`|Wartość elementu tablicy.|  
|`index`|Indeks liczbowy elementu tablicy.|  
|`array1`|Obiekt tablicy zawierający element.|  
  
## <a name="modifying-the-array-object"></a>Modyfikowanie obiektu tablicy  
 `forEach` Metoda bezpośrednio nie modyfikować oryginalnego tablicy, ale funkcja wywołania zwrotnego może go zmodyfikować. W poniższej tabeli przedstawiono wyniki modyfikowania obiektu tablicy po `forEach` uruchamia metody.  
  
|Warunek po `forEach` uruchamia — metoda|Element przekazany do funkcji wywołania zwrotnego?|  
|---------------------------------------------|------------------------------------------|  
|Element zostanie dodany poza pierwotną długością tablicy.|Nie.|  
|Element zostanie dodany do tablicy miejscu brakującego elementu.|Tak, jeśli w ten indeks nie został jeszcze przekazany do funkcji wywołania zwrotnego.|  
|Element został zmieniony.|Tak, jeśli ten element nie został jeszcze przekazany do funkcji wywołania zwrotnego.|  
|Element został usunięty z tablicy.|Nie, chyba że ten element został już przekazany do funkcji wywołania zwrotnego.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `forEach` metody.  
  
```JavaScript  
// Define the callback function.  
function ShowResults(value, index, ar) {  
    document.write("value: " + value);  
    document.write(" index: " + index);  
    document.write("<br />");  
}  
  
// Create an array.  
var letters = ['ab', 'cd', 'ef'];  
  
// Call the ShowResults callback function for each  
// array element.  
letters.forEach(ShowResults);  
  
// Output:  
//  value: ab index: 0   
//  value: cd index: 1   
//  value: ef index: 2   
```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie `callbackfn` argument zawiera kod funkcji wywołania zwrotnego.  
  
```JavaScript  
// Create an array.  
var numbers = [10, 11, 12];  
  
// Call the addNumber callback function for each array element.  
var sum = 0;  
numbers.forEach(  
    function addNumber(value) { sum += value; }  
);  
  
document.write(sum);  
// Output: 33  
  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `thisArg` argumentu, który określa obiekt, który może być określony `this` — słowo kluczowe.  
  
```JavaScript  
// Define the object that contains the callback function.  
var obj = {  
    showResults: function(value, index) {  
        // Call calcSquare by using the this value.  
        var squared = this.calcSquare(value);  
  
        document.write("value: " + value);  
        document.write(" index: " + index);  
        document.write(" squared: " + squared);  
        document.write("<br />");  
    },  
    calcSquare: function(x) { return x * x }  
};  
  
// Define an array.  
var numbers = [5, 6];  
  
// Call the showResults callback function for each array element.  
// The obj is the this value within the   
// callback function.  
numbers.forEach(obj.showResults, obj);  
  
// Embed the callback function in the forEach statement.  
// The obj argument is the this value within the obj object.  
// The output is the same as for the previous statement.  
numbers.forEach(function(value, index) { this.showResults(value, index) }, obj);  
  
// Output:  
//  value: 5 index: 0 squared: 25  
//  value: 6 index: 1 squared: 36  
//  value: 5 index: 0 squared: 25  
//  value: 6 index: 1 squared: 36  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Filter — metoda (tablica)](../../javascript/reference/filter-method-array-javascript.md)   
 [map — metoda (tablica)](../../javascript/reference/map-method-array-javascript.md)   
 [Some — metoda (tablica)](../../javascript/reference/some-method-array-javascript.md)   
 [Array — obiekt](../../javascript/reference/array-object-javascript.md)   
 [Używanie tablic](../../javascript/advanced/using-arrays-javascript.md)   
 [Hilo JavaScript przykładowej aplikacji (w Sklepie Windows)](http://hilojs.codeplex.com/SourceControl/latest)