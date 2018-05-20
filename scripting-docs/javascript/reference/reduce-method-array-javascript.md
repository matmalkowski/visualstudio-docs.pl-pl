---
title: Reduce — metoda (tablica) (JavaScript) | Dokumentacja firmy Microsoft
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
- callback function, reduce method [JavaScript]
- arrays [JavaScript], reduce method
- reduce method [JavaScript]
ms.assetid: 48d069e0-e083-494f-86d5-d459d2377dc5
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d99f92d90885f26b19392b476ee64ae17bd40aed
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="reduce-method-array-javascript"></a>reduce — Metoda (Tablica) (JavaScript)
Wywołuje funkcję wywołania zwrotnego określony dla wszystkich elementów w tablicy. Zwracana wartość funkcji wywołania zwrotnego jest wynikiem zakumulowanym i jest dostarczana jako argument w następnym wywołaniu funkcji wywołania zwrotnego.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
array1.reduce(callbackfn[, initialValue])  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Definicja|  
|---------------|----------------|  
|`array1`|Wymagana. Obiekt tablicy.|  
|`callbackfn`|Wymagana. Funkcja akceptuje maksymalnie cztery argumenty. `reduce` Wywołania metody `callbackfn` funkcji jeden raz dla każdego elementu w tablicy.|  
|`initialValue`|Opcjonalna. Jeśli `initialValue` jest określony, jest używany jako wartości początkowej, aby rozpocząć gromadzenie. W pierwszym wywołaniu `callbackfn` funkcja zapewnia tej wartości jako argument zamiast wartości tablicy.|  
  
## <a name="return-value"></a>Wartość zwracana  
 Skumulowany wynik z ostatnim wywołaniem funkcji wywołania zwrotnego.  
  
## <a name="exceptions"></a>Wyjątki  
 A `TypeError` wyjątek jest zgłaszany, gdy spełniony jest jeden z następujących warunków:  
  
-   `callbackfn` Argument nie jest obiektem funkcji.  
  
-   Tablica nie zawiera żadnych elementów i `initialValue` jest niedostępny.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `initialValue` podano, `reduce` wywołania metody `callbackfn` funkcji jeden raz dla każdego elementu w tablicy, rosnąco indeksu. Jeśli `initialValue` nie zostanie podany, `reduce` wywołania metody `callbackfn` funkcję dla każdego elementu, począwszy od drugiego elementu.  
  
 Wartość zwracana funkcji wywołania zwrotnego jest dostępna jako `accumulator` argument przy następnym wywołaniu funkcji wywołania zwrotnego. Wartość zwracana ostatnim wywołaniem funkcji wywołania zwrotnego jest zwracana wartość `reduce` metody.  
  
 Funkcja wywołania zwrotnego nie jest wywoływana dla brakujących elementów tablicy.  
  
> [!NOTE]
>  [ReduceRight — metoda (tablica)](../../javascript/reference/reduceright-method-array-javascript.md) przetwarza elementy malejąco według indeksu.  
  
## <a name="callback-function-syntax"></a>Składnia funkcji wywołania zwrotnego  
 Składnia funkcji wywołania zwrotnego jest następująca:  
  
 `function callbackfn(accumulator, currentValue, currentIndex, array1)`  
  
 Funkcja wywołania zwrotnego można zadeklarować przy użyciu maksymalnie cztery parametry.  
  
 Poniższa lista zawiera parametry funkcji wywołania zwrotnego.  
  
|Argument wywołania zwrotnego|Definicja|  
|-----------------------|----------------|  
|`accumulator`|Wartość z poprzedniego wywołania funkcji wywołania zwrotnego. Jeśli `initialValue` został dostarczony do `reduce` metody `accumulator` jest `initialValue` funkcja jest wywoływana po raz pierwszy.|  
|`currentValue`|Wartość bieżącego elementu tablicy.|  
|`currentIndex`|Liczbowa indeks bieżącego elementu tablicy.|  
|`array1`|Obiekt tablicy zawierający element.|  
  
## <a name="first-call-to-the-callback-function"></a>Pierwsze wywołanie funkcji wywołania zwrotnego  
 Podczas pierwszego wywołania funkcji wywołania zwrotnego wartości podane jako argumenty są zależne od tego, czy `reduce` metoda ma `initialValue` argumentu.  
  
 Jeśli `initialValue` jest przekazane do metody Zmniejsz:  
  
-   `accumulator` Argument jest `initialValue`.  
  
-   `currentValue` Argument ma wartość pierwszego elementu w tablicy.  
  
 Jeśli `initialValue` nie podano:  
  
-   `accumulator` Argument ma wartość pierwszego elementu w tablicy.  
  
-   `currentValue` Argument ma wartość drugiego elementu w tablicy.  
  
## <a name="modifying-the-array-object"></a>Modyfikowanie obiektu tablicy  
 Obiekt tablicy można modyfikować przy użyciu funkcji wywołania zwrotnego.  
  
 W poniższej tabeli przedstawiono wyniki modyfikowania obiektu tablicy po `reduce` uruchamia metody.  
  
|Warunek po `reduce` uruchamia — metoda|Element przekazany do funkcji wywołania zwrotnego?|  
|------------------------------------------------|------------------------------------------|  
|Element zostanie dodany poza pierwotną długością tablicy.|Nie.|  
|Element zostanie dodany do tablicy miejscu brakującego elementu.|Tak, jeśli w ten indeks nie został jeszcze przekazany do funkcji wywołania zwrotnego.|  
|Element został zmieniony.|Tak, jeśli ten element nie został jeszcze przekazany do funkcji wywołania zwrotnego.|  
|Element został usunięty z tablicy.|Nie, chyba że ten element został już przekazany do funkcji wywołania zwrotnego.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład łączy tablicy wartości na ciąg, oddzielając wartości z "::". Ponieważ nie jest podany żadnej wartości początkowej do `reduce` metoda, pierwsze wywołanie funkcji wywołania zwrotnego ma "abc" jako `accumulator` argument i "def" jako `currentValue` argumentu.  
  
```JavaScript  
// Define the callback function.  
function appendCurrent (accumulator, currentValue) {  
    return accumulator + "::" + currentValue;  
    }  
  
// Create an array.  
var elements = ["abc", "def", 123, 456];  
  
// Call the reduce method, which calls the callback function  
// for each array element.  
var result = elements.reduce(appendCurrent);  
  
document.write(result);  
  
// Output:  
//  abc::def::123::456  
  
```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie dodano wartości tablicy po ich zaokrąglony. `reduce` Wywoływana jest metoda o początkowej wartości 0.  
  
```JavaScript  
// Define the callback function.  
function addRounded (accumulator, currentValue) {  
    return accumulator + Math.round(currentValue);  
    }  
  
// Create an array.  
var numbers = [10.9, 15.4, 0.5];  
  
// Call the reduce method, starting with an initial value of 0.  
var result = numbers.reduce(addRounded, 0);  
  
document.write (result);  
// Output: 27  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład dodaje wartości w tablicy. `currentIndex` i `array1` są używane parametry w funkcji wywołania zwrotnego.  
  
```JavaScript  
function addDigitValue(accumulator, currentDigit, currentIndex, array) {  
    var exponent = (array.length - 1) - currentIndex;  
    var digitValue = currentDigit * Math.pow(10, exponent);  
    return accumulator + digitValue;  
    }  
  
var digits = [4, 1, 2, 5];  
  
// Determine an integer that is computed from values in the array.  
var result = digits.reduce(addDigitValue, 0);  
  
document.write (result);  
// Output: 4125  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pobiera tablicę, która zawiera tylko wartości, które należą do zakresu od 1 do 10 w innej tablicy. Początkowa wartość podana dla `reduce` metoda jest pusta tablica.  
  
```JavaScript  
function Process(accumulatedArray, currentValue) {  
    // If currentValue is between 1 and 10,   
    // append currentValue to the array.  
    var nextArray;  
    if (currentValue >= 1 && currentValue <= 10)  
        nextArray = accumulatedArray.concat(currentValue);  
    else  
        nextArray = accumulatedArray;  
  
    // If this is not the last call by the reduce method,  
    // the returned array is accumulatedArray on the next call.  
    // If this is the last call by the reduce method, the  
    // returned array is the return value of the reduce method.  
    return nextArray;  
}  
  
// Create an array.  
var numbers = [20, 1, -5, 6, 50, 3];  
  
// Call the reduce method, starting with an initial empty array.  
var emptyArray = new Array();  
var resultArray = numbers.reduce(Process, emptyArray);  
  
document.write("result array=" + resultArray);  
  
// Output:  
// result array=1,6,3  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [reduceRight, metoda (Array)](../../javascript/reference/reduceright-method-array-javascript.md)
