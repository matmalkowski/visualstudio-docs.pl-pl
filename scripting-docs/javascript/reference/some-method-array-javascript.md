---
title: "Some — metoda (tablica) (JavaScript) | Dokumentacja firmy Microsoft"
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
- arrays [JavaScript], some method
- some method [JavaScript]
ms.assetid: 7b6822f9-c406-4f4e-bfec-a93459745992
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ba3f855c61daac511bcf7aca6b47f643dda93313
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="some-method-array-javascript"></a>some — Metoda (Tablica) (JavaScript)
Określa, czy funkcja wywołania zwrotnego określonego zwraca `true` dla każdego elementu tablicy.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
array1.some(callbackfn[, thisArg])  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Definicja|  
|---------------|----------------|  
|`array1`|Wymagany. Obiekt tablicy.|  
|`callbackfn`|Wymagany. Funkcja, która akceptuje maksymalnie trzy argumenty. `some` Wywołania metody `callbackfn` funkcja dla każdego elementu w `array1` do momentu `callbackfn` zwraca `true`, lub do końca tablicy.|  
|`thisArg`|Opcjonalny. Obiekt, do którego `this` — słowo kluczowe może odwoływać się w `callbackfn` funkcji. Jeśli `thisArg` zostanie pominięty, `undefined` jest używany jako `this` wartość.|  
  
## <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli `callbackfn` funkcja zwraca `true` dla każdego elementu tablicy; w przeciwnym razie `false`.  
  
## <a name="exceptions"></a>Wyjątki  
 Jeśli `callbackfn` argument nie jest obiektem funkcji `TypeError` wyjątku.  
  
## <a name="remarks"></a>Uwagi  
 `some` Wywołania metody `callbackfn` funkcję dla każdego elementu tablicy, rosnąco indeksu, dopóki `callbackfn` funkcja zwraca `true`. Jeśli element, który powoduje, że `callbackfn` do zwrócenia `true` zostanie znaleziony, `some` metoda natychmiast zwraca `true`. Jeśli wywołanie zwrotne nie zwraca `true` w dowolnym elemencie `some` metoda zwraca `false`.  
  
 Funkcja wywołania zwrotnego nie jest wywoływana dla brakujących elementów tablicy.  
  
 Oprócz obiektów tablicy `some` metody mogą być używane przez dowolny obiekt `length` właściwości oraz że ma wartość liczbowa indeksowane nazw właściwości.  
  
> [!NOTE]
>  Można użyć [every — metoda (tablica)](../../javascript/reference/every-method-array-javascript.md) do sprawdzenia, czy funkcja wywołania zwrotnego zwraca `true` dla wszystkich elementów tablicy.  
  
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
  
 W poniższej tabeli przedstawiono wyniki modyfikowania obiektu tablicy po `some` uruchamia metody.  
  
|Warunek po `some` uruchamia — metoda|Element przekazany do funkcji wywołania zwrotnego?|  
|----------------------------------------------|------------------------------------------|  
|Element zostanie dodany poza pierwotną długością tablicy.|Nie.|  
|Element zostanie dodany do tablicy miejscu brakującego elementu.|Tak, jeśli w ten indeks nie został jeszcze przekazany do funkcji wywołania zwrotnego.|  
|Element został zmieniony.|Tak, jeśli ten element nie został jeszcze przekazany do funkcji wywołania zwrotnego.|  
|Element został usunięty z tablicy.|Nie, chyba że ten element został już przekazany do funkcji wywołania zwrotnego.|  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `some` metodę, aby sprawdzić, czy wszystkie elementy w tablicy są parzyste.  
  
```JavaScript  
// The callback function.  
function CheckIfEven(value, index, ar) {  
    if (value % 2 == 0)  
        return true;  
}  
  
var numbers = [1, 15, 4, 10, 11, 22];  
  
var evens = numbers.some(CheckIfEven);  
document.write(evens);  
  
// Output:  
// true  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `thisArg` parametr, który określa obiekt, do którego `this` — słowo kluczowe może się odwoływać. Sprawdza, czy którakolwiek z liczb w tablicy są poza zakresem dostarczony przez obiekt przekazany  
  
```JavaScript  
// Create a function that returns true if the value is   
// outside the range.  
var isOutsideRange = function (value) {  
    return value < this.minimum || value > this.maximum;  
}  
  
// Create an array of numbers.  
var numbers = [6, 12, 16, 22, -12];  
  
// The range object is to be the 'this' object.  
var range = { minimum: 10, maximum: 20 };  
  
document.write(numbers.some(isOutsideRange, range));  
  
// Output: true  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [EVERY — metoda (tablica)](../../javascript/reference/every-method-array-javascript.md)   
 [Filter — metoda (tablica)](../../javascript/reference/filter-method-array-javascript.md)   
 [map — metoda (tablica)](../../javascript/reference/map-method-array-javascript.md)