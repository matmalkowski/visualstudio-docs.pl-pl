---
title: reduceRight — metoda (tablica) (JavaScript) | Dokumentacja firmy Microsoft
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
- arrays [JavaScript], reduceRight method
- reduceRight method [JavaScript]
ms.assetid: 85963761-da11-407c-8bce-278c930e61bd
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0d7fd2794157eadacefa7404f9333c51aed9425c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24792103"
---
# <a name="reduceright-method-array-javascript"></a>reduceRight — Metoda (Array) (JavaScript)
Wywołuje funkcję wywołania zwrotnego określony dla wszystkich elementów w tablicy, w kolejności malejącej. Zwracana wartość funkcji wywołania zwrotnego jest wynikiem zakumulowanym i jest dostarczana jako argument w następnym wywołaniu funkcji wywołania zwrotnego.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
array1.reduceRight(callbackfn[, initialValue])  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Definicja|  
|---------------|----------------|  
|`array1`|Wymagany. Obiekt tablicy.|  
|`callbackfn`|Wymagany. Funkcja akceptuje maksymalnie cztery argumenty. `reduceRight` Wywołania metody `callbackfn` funkcji jeden raz dla każdego elementu w tablicy.|  
|`initialValue`|Opcjonalny. Jeśli `initialValue` jest określony, jest używany jako wartości początkowej, aby rozpocząć gromadzenie. W pierwszym wywołaniu `callbackfn` funkcja zapewnia tej wartości jako argument zamiast wartości tablicy.|  
  
## <a name="return-value"></a>Wartość zwracana  
 Obiekt zawierający wynik skumulowany z ostatnim wywołaniem funkcji wywołania zwrotnego.  
  
## <a name="exceptions"></a>Wyjątki  
 A `TypeError` wyjątek jest zgłaszany, gdy spełniony jest jeden z następujących warunków:  
  
-   `callbackfn` Argument nie jest obiektem funkcji.  
  
-   Tablica nie zawiera żadnych elementów i `initialValue` jest niedostępny.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `initialValue` podano, `reduceRight` wywołania metody `callbackfn` funkcji jeden raz dla każdego elementu w tablicy, malejąco według indeksu. Jeśli nie `initialValue` podano, `reduceRight` wywołania metody `callbackfn` funkcję dla każdego elementu, poczynając od drugiego do ostatniego elementu, malejąco według indeksu.  
  
 Wartość zwracana funkcji wywołania zwrotnego jest dostępna jako `previousValue` argument przy następnym wywołaniu funkcji wywołania zwrotnego. Wartość zwracana ostatnim wywołaniem funkcji wywołania zwrotnego jest zwracana wartość `reduceRight` metody.  
  
 Funkcja wywołania zwrotnego nie jest wywoływana dla brakujących elementów tablicy.  
  
 Aby accumulate wynik rosnąco indeksu, należy użyć [reduce — metoda (tablica)](../../javascript/reference/reduce-method-array-javascript.md).  
  
## <a name="callback-function-syntax"></a>Składnia funkcji wywołania zwrotnego  
 Składnia funkcji wywołania zwrotnego jest następująca:  
  
 `function callbackfn(previousValue, currentValue, currentIndex, array1)`  
  
 Funkcja wywołania zwrotnego można zadeklarować przy użyciu maksymalnie cztery parametry.  
  
 Poniższa lista zawiera parametry funkcji wywołania zwrotnego.  
  
|Argument wywołania zwrotnego|Definicja|  
|-----------------------|----------------|  
|`previousValue`|Wartość z poprzedniego wywołania funkcji wywołania zwrotnego. Jeśli `initialValue` został dostarczony do `reduceRight` metody `previousValue` jest `initialValue` funkcja jest wywoływana po raz pierwszy.|  
|`currentValue`|Wartość bieżącego elementu tablicy.|  
|`currentIndex`|Liczbowa indeks bieżącego elementu tablicy.|  
|`array1`|Obiekt tablicy zawierający element.|  
  
## <a name="first-call-to-the-callback-function"></a>Pierwsze wywołanie funkcji wywołania zwrotnego  
 Podczas pierwszego wywołania funkcji wywołania zwrotnego wartości podane jako argumenty są zależne od tego, czy `reduceRight` metoda ma `initialValue` argumentu.  
  
 Jeśli `initialValue` został dostarczony do `reduceRight` metody:  
  
-   `previousValue` Argument jest `initialValue`.  
  
-   `currentValue` Argument ma wartość ostatniego elementu w tablicy.  
  
 Jeśli `initialValue` nie podano:  
  
-   `previousValue` Argument ma wartość ostatniego elementu w tablicy.  
  
-   `currentValue` Argument ma wartość sekundy do ostatniego elementu w tablicy.  
  
## <a name="modifying-the-array-object"></a>Modyfikowanie obiektu tablicy  
 Obiekt tablicy można modyfikować przy użyciu funkcji wywołania zwrotnego.  
  
 W poniższej tabeli przedstawiono wyniki modyfikowania obiektu tablicy po `reduceRight` uruchamia metody.  
  
|Warunek po `reduceRight` uruchamia — metoda|Element przekazany do funkcji wywołania zwrotnego?|  
|-----------------------------------------------------|------------------------------------------|  
|Element zostanie dodany poza pierwotną długością tablicy.|Nie.|  
|Element zostanie dodany do tablicy miejscu brakującego elementu.|Tak, jeśli w ten indeks nie został jeszcze przekazany do funkcji wywołania zwrotnego.|  
|Element został zmieniony.|Tak, jeśli ten element nie został jeszcze przekazany do funkcji wywołania zwrotnego.|  
|Element został usunięty z tablicy.|Nie, chyba że ten element został już przekazany do funkcji wywołania zwrotnego.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład łączy tablicy wartości na ciąg, oddzielając wartości z "::". Ponieważ nie jest podany żadnej wartości początkowej do `reduceRight` metoda, pierwsze wywołanie funkcji wywołania zwrotnego ma 456 jako `previousValue` argumentu a 123 jako `currentValue` argumentu.  
  
```JavaScript  
// Define the callback function.  
function appendCurrent (previousValue, currentValue) {  
    return previousValue + "::" + currentValue;  
    }  
  
// Create an array.  
var elements = ["abc", "def", 123, 456];  
  
// Call the reduceRight method, which calls the callback function  
// for each array element, in descending index order.  
var result = elements.reduceRight(appendCurrent);  
  
document.write(result);  
  
// Output:  
//  456::123::def::abc  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład umożliwia znalezienie sumę kwadratów elementów tablicy. `reduceRight` Wywoływana jest metoda o początkowej wartości 0.  
  
```JavaScript  
// Define the callback function.  
function Process(previousValue, currentValue, index, array) {  
    // Add the previous value to the current value squared.  
    var nextValue = previousValue + (currentValue * currentValue);  
  
    // If this is not the last call by the reduceRight method,  
    // the return value is previousValue on the next call.  
    // If this is the last call by the reduceRight method, the  
    // return value is the return value of the reduceRight method.  
    return nextValue;  
}  
  
// Create an array.  
var numbers = [3, 4, 5];  
  
// Call the reduceRight method with an initial value of 0.  
var sumOfSquares = numbers.reduceRight(Process, 0);  
  
document.write("sum of squares=" + sumOfSquares);  
  
// Output:  
//  sum of squares=50  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pobiera tych elementów w tablicy, której wartości należą do zakresu od 1 do 10. Początkowa wartość podana dla `reduceRight` metoda jest pusta tablica.  
  
```JavaScript  
function Process2(previousArray, currentValue) {  
    // If currentValue is between 1 and 10,   
    // append currentValue to the array.  
    var nextArray;  
    if (currentValue >= 1 && currentValue <= 10)  
        nextArray = previousArray.concat(currentValue);  
    else  
        nextArray = previousArray;  
  
    // If this is not the last call by the reduceRight method,  
    // the returned array is previousArray on the next call.  
    // If this is the last call by the reduceRight method, the  
    // returned array is the return value of the reduceRight method.  
    return nextArray;  
}  
  
// Create an array.  
var numbers = [20, 1, -5, 6, 50, 3];  
  
// Call the reduceRight method, starting with an empty array.  
var emptyArray = new Array();  
var resultArray = numbers.reduceRight(Process2, emptyArray);  
  
document.write("result array=" + resultArray);  
  
// Output:  
//  result array=3,6,1  
```  
  
## <a name="example"></a>Przykład  
 `reduceRight` Metoda może być stosowana do ciągu. Poniższy przykład pokazuje, jak do używania tej metody, aby odwrócić znaków w ciągu.  
  
```JavaScript  
// Define the callback function.  
function AppendToArray(previousValue, currentValue) {  
    return previousValue + currentValue;  
}  
  
var word = "retupmoc";  
  
// Create a string that reverses the characters of another string.  
// The commented-out statement shows an alternative syntax.  
var result = [].reduceRight.call(word, AppendToArray, "the ");  
// var result = Array.prototype.reduceRight.call(word, AppendToArray, "the ");  
  
document.write(result);  
  
// Output:  
// the computer  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Reduce — metoda (tablica)](../../javascript/reference/reduce-method-array-javascript.md)