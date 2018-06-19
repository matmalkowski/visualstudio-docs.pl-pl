---
title: EVERY — metoda (tablica) (JavaScript) | Dokumentacja firmy Microsoft
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
- every method
- arrays [JavaScript], every method
ms.assetid: dc4ee2f8-fb9e-4c9f-af5a-fe836e40ddd1
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4a05263ae45df61c47a3580d474863c8d4ff3dd1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24790729"
---
# <a name="every-method-array-javascript"></a>every — Metoda (Tablica) (JavaScript)
Określa, czy wszystkie elementy członkowskie tablicy spełniają określony test.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
array1.every(callbackfn[, thisArg])  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Definicja|  
|---------------|----------------|  
|`array1`|Wymagany. Obiekt tablicy.|  
|`callbackfn`|Wymagany. Funkcja, która akceptuje maksymalnie trzy argumenty. `every` Wywołania metody `callbackfn` funkcja dla każdego elementu w `array1` do momentu `callbackfn` zwraca `false`, lub do końca tablicy.|  
|`thisArg`|Opcjonalny. Obiekt, do którego `this` — słowo kluczowe może odwoływać się w `callbackfn` funkcji. Jeśli `thisArg` zostanie pominięty, `undefined` jest używany jako `this` wartość.|  
  
## <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli `callbackfn` funkcja zwraca `true` dla wszystkich elementów; w tablicy w przeciwnym razie `false`. Jeśli nie ma żadnych elementów tablicy `every` metoda zwraca `true`.  
  
## <a name="exceptions"></a>Wyjątki  
 Jeśli `callbackfn` argument nie jest obiektem funkcji `TypeError` wyjątku.  
  
## <a name="remarks"></a>Uwagi  
 `every` Wywołania metody `callbackfn` funkcji jeden raz dla każdego elementu tablicy, rosnąco indeksu, dopóki `callbackfn` funkcja zwraca `false`. Jeśli element, który powoduje, że `callbackfn` do zwrócenia `false` zostanie znaleziony, `every` metoda natychmiast zwraca `false`. W przeciwnym razie `every` metoda zwraca `true`.  
  
 Funkcja wywołania zwrotnego nie jest wywoływana dla brakujących elementów tablicy.  
  
 Oprócz obiektów tablicy `every` metody mogą być używane przez dowolny obiekt `length` właściwości oraz że ma wartość liczbowa indeksowane nazw właściwości.  
  
> [!NOTE]
>  Można użyć [some — metoda (tablica)](../../javascript/reference/some-method-array-javascript.md) do sprawdzenia, czy funkcja wywołania zwrotnego zwraca `true` dla każdego elementu tablicy.  
  
## <a name="callback-function-syntax"></a>Składnia funkcji wywołania zwrotnego  
 Składnia funkcji wywołania zwrotnego jest następująca:  
  
 `function callbackfn(value, index, array1)`  
  
 Można zadeklarować funkcji wywołania zwrotnego z maksymalnie trzech parametrów.  
  
 Poniższa lista zawiera parametry funkcji wywołania zwrotnego.  
  
|Parametr wywołania zwrotnego|Definicja|  
|------------------------|----------------|  
|`value`|Wartość elementu tablicy.|  
|`index`|Indeks liczbowy elementu tablicy.|  
|`array1`|Obiekt tablicy zawierający element.|  
  
## <a name="modifying-the-array-object"></a>Modyfikowanie obiektu tablicy  
 Obiekt tablicy można modyfikować przy użyciu funkcji wywołania zwrotnego.  
  
 W poniższej tabeli przedstawiono wyniki modyfikowania obiektu tablicy po `every` uruchamia metody.  
  
|Warunek po `every` uruchamia — metoda|Element przekazany do funkcji wywołania zwrotnego?|  
|-----------------------------------------------|------------------------------------------|  
|Element zostanie dodany poza pierwotną długością tablicy.|Nie.|  
|Element zostanie dodany do tablicy miejscu brakującego elementu.|Tak, jeśli w ten indeks nie został jeszcze przekazany do funkcji wywołania zwrotnego.|  
|Element został zmieniony.|Tak, jeśli ten element nie został jeszcze przekazany do funkcji wywołania zwrotnego.|  
|Element został usunięty z tablicy.|Nie, chyba że ten element został już przekazany do funkcji wywołania zwrotnego.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `every` metody.  
  
```JavaScript  
// Define the callback function.  
function CheckIfEven(value, index, ar) {  
    document.write(value + " ");  
  
    if (value % 2 == 0)  
        return true;  
    else  
        return false;  
}  
  
// Create an array.  
var numbers = [2, 4, 5, 6, 8];  
  
// Check whether the callback function returns true for all of the  
// array values.  
if (numbers.every(CheckIfEven))  
    document.write("All are even.");  
else  
    document.write("Some are not even.");  
  
// Output:  
// 2 4 5 Some are not even.  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `thisArg` argumentu, który określa obiekt, do którego `this` — słowo kluczowe może się odwoływać.  
  
```JavaScript  
// Create a function that returns true if the value is  
// numeric and within range.  
var checkNumericRange = function(value) {  
    if (typeof value !== 'number')  
        return false;  
    else   
        return value >= this.minimum && value <= this.maximum;  
}  
  
// Create an array of numbers.  
var numbers = [10, 15, 19];  
  
// Check whether the callback function returns true for  
// all of the array values.  
// The obj argument enables use of the this value  
// within the callback function.  
  
var obj = { minimum: 10, maximum: 20 }  
  
if (numbers.every(checkNumericRange, obj))  
    document.write ("All are within range.");  
else  
    document.write ("Some are not within range.");  
  
// Output:  
//   All are within range.  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Some — metoda (tablica)](../../javascript/reference/some-method-array-javascript.md)   
 [Filter — metoda (tablica)](../../javascript/reference/filter-method-array-javascript.md)   
 [Array — obiekt](../../javascript/reference/array-object-javascript.md)   
 [Używanie tablic](../../javascript/advanced/using-arrays-javascript.md)