---
title: "Array — obiekt (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Array
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Array object
- constructor property
ms.assetid: 08e5f552-0797-4b48-8164-609582fc18c9
caps.latest.revision: "27"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a48d0ab5bac9d532e8fe8e356f4ea4df9e377b02
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="array-object-javascript"></a>Array — Obiekt (JavaScript)
Zapewnia obsługę tworzenia tablic zawierających dowolne typy danych.  
  
## <a name="syntax"></a>Składnia  
  
```
arrayObj = new Array()  
arrayObj = new Array([size])  
arrayObj = new Array([element0[, element1[, ...[, elementN]]]])  
```  
  
## <a name="parameters"></a>Parametry  
 `arrayObj`  
 Wymagany. Nazwa zmiennej, do której `Array` obiekt jest przypisany.  
  
 `size`  
 Opcjonalny. Rozmiar tablicy. Tablice są liczony od zera, utworzone elementy zostaną indeksów od zera do `size` -1.  
  
 `element0,...,elementN`  
 Opcjonalny. Elementy, które mają zostać umieszczone w tablicy. Spowoduje to utworzenie w tablicy o  *n*  + 1 elementów i `length` z  *n*  + 1. Używając tej składni, należy podać więcej niż jeden element.  
  
## <a name="remarks"></a>Uwagi  
 Po utworzeniu tablicy można uzyskać dostęp do poszczególnych elementów tablicy przy użyciu notacji [ ]. Należy pamiętać, że stałych w [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] jest liczony od zera.  
  
```JavaScript  
var my_array = new Array();  
for (i = 0; i < 10; i++) {  
    my_array[i] = i;  
}  
x = my_array[4];  
document.write(x);  
  
// Output: 4  
```  
  
 Można przekazać całkowitą bez znaku 32-bitowej do `Array` konstruktora, aby określić rozmiar tablicy. Jeśli wartość będzie ujemna lub nie będzie liczbą całkowitą, wystąpi błąd w czasie wykonywania. Jeśli uruchomisz poniższy kod, na konsoli powinien pojawić się ten błąd.  
  
```JavaScript  
var arr = new Array(10);  
document.write(arr.length);  
  
// Output: 10  
  
// Don't do this  
var arr = new Array(-1);  
arr = new Array(1.50);   
```  
  
 Jeśli pojedynczą wartość jest przekazywana do `Array` Konstruktor który nie jest liczbą, `length` właściwość jest ustawiona na 1, a wartość elementu tylko staje się pojedynczą, przekazany argument.  
  
```npl  
var arr = new Array("one");  
document.write(arr.length);  
document.write("<br/>");  
document.write(arr[0]);  
  
// Output:  
1  
one  
  
```  
  
 Tablice JavaScript są rzadkimi tablicami, co oznacza, że nie wszystkie elementy tablicy mogą zawierać dane. W języku JavaScript jedynie elementy, które faktycznie zawierają dane, istnieją w tablicy. Zmniejsza to ilość pamięci używanej przez tablicę.  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
 Niektóre elementy członkowskie wymienione na poniższej liście zostały wprowadzone w nowszych wersjach. Aby uzyskać więcej informacji, zobacz [informacje o wersji](../../javascript/reference/javascript-version-information.md) lub dokumentacji dla poszczególnych elementów.  
  
## <a name="properties"></a>Właściwości  
 W poniższej tabeli wymieniono właściwości `Array` obiektu.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|[constructor — właściwość](../../javascript/reference/constructor-property-array.md)|Określa funkcję, która tworzy tablicę.|  
|[length — właściwość (tablica)](../../javascript/reference/length-property-array-javascript.md)|Zwraca wartość całkowitą, która jest większa o jeden niż najwyższy indeks elementu zdefiniowanego w tablicy.|  
|[prototype — właściwość](../../javascript/reference/prototype-property-array.md)|Zwraca odwołanie do prototypu tablicy.|  
  
## <a name="functions"></a>Funkcje  
 W poniższej tabeli opisano funkcje `Array` obiektu.  
  
|Funkcja|Opis|  
|--------------|-----------------|  
|[Array.from — funkcja](../../javascript/reference/array-from-function-array-javascript.md)|Zwraca tablicę z tablicy lub iterable obiektu.|  
|[Array.IsArray — funkcja](../../javascript/reference/array-isarray-function-javascript.md)|Zwraca wartość logiczną, która wskazuje, czy obiekt jest tablicą.|  
|[Array.of — funkcja](../../javascript/reference/array-of-function-array-javascript.md)|Zwraca tablicę z przekazano argumentów.|  
  
<a name="js56jsobjarraymeth"></a>   
## <a name="methods"></a>Metody  
 W poniższej tabeli przedstawiono metody `Array` obiektu.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Metoda concat (tablica)](../../javascript/reference/concat-method-array-javascript.md)|Zwraca nową tablicę, stanowiącą kombinację dwóch tablic.|  
|[wpisy — metoda](../../javascript/reference/entries-method-array-javascript.md)|Zwraca iteratora zawierający pary klucz wartość tablicy.|  
|[EVERY — metoda](../../javascript/reference/every-method-array-javascript.md)|Sprawdza, czy funkcja wywołania zwrotnego zdefiniowanego zwraca `true` dla wszystkich elementów w tablicy.|  
|[Fill — metoda](../../javascript/reference/fill-method-array-javascript.md)|Wypełnia tablicę o określonej wartości.|  
|[Filter — metoda](../../javascript/reference/filter-method-array-javascript.md)|Wywołuje funkcję wywołania zwrotnego zdefiniowanego w każdy element tablicy i zwraca tablicę wartości, dla których zwraca funkcja wywołania zwrotnego `true`.|  
|[findIndex — metoda](../../javascript/reference/findindex-method-array-javascript.md)|Zwraca wartość indeksu pierwszego elementu tablicy, czy spełnia testu kryteria określone w funkcji wywołania zwrotnego.|  
|[forEach — metoda](../../javascript/reference/foreach-method-array-javascript.md)|Wywołuje zdefiniowaną funkcję wywołania zwrotnego dla każdego elementu w tablicy.|  
|[hasOwnProperty — metoda](../../javascript/reference/hasownproperty-method-object-javascript.md)|Zwraca wartość logiczną, która wskazuje, czy obiekt ma właściwość o określonej nazwie.|  
|[indexOf — metoda (tablica)](../../javascript/reference/indexof-method-array-javascript.md)|Zwraca indeks pierwszego wystąpienia wartości w tablicy.|  
|[isPrototypeOf — metoda](../../javascript/reference/isprototypeof-method-object-javascript.md)|Zwraca wartość logiczną, która wskazuje, czy obiekt istnieje w łańcuchu prototypów innego obiektu.|  
|[JOIN — metoda](../../javascript/reference/join-method-array-javascript.md)|Zwraca `String` obiekt zawierający wszystkie elementy tablicy połączonych ze sobą.|  
|[keys — metoda](../../javascript/reference/keys-method-array-javascript.md)|Zwraca iteratora zawierającą wartości indeksu tablicy.|  
|[Metoda lastIndexOf (tablica)](../../javascript/reference/lastindexof-method-array-javascript.md)|Zwraca indeks ostatniego wystąpienia określonej wartości w tablicy.|  
|[map — metoda](../../javascript/reference/map-method-array-javascript.md)|Wywołuje zdefiniowaną funkcję wywołania zwrotnego dla każdego elementu tablicy i zwraca tablicę zawierającą wyniki.|  
|[POP — metoda](../../javascript/reference/pop-method-array-javascript.md)|Usuwa z tablicy ostatni element i zwraca go.|  
|[propertyIsEnumerable — metoda](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|Zwraca wartość logiczną, która wskazuje, czy określona właściwość jest częścią obiektu i czy jest wyliczalna.|  
|[push — metoda](../../javascript/reference/push-method-array-javascript.md)|Dołącza nowe elementy do tablicy i zwraca nową długość tablicy.|  
|[Reduce — metoda](../../javascript/reference/reduce-method-array-javascript.md)|Gromadzi pojedynczy wynik, wywołując zdefiniowaną funkcję wywołania zwrotnego dla wszystkich elementów w tablicy. Zwracana wartość funkcji wywołania zwrotnego jest wynikiem zakumulowanym i jest dostarczana jako argument w następnym wywołaniu funkcji wywołania zwrotnego.|  
|[reduceRight — metoda](../../javascript/reference/reduceright-method-array-javascript.md)|Gromadzi pojedynczy wynik, wywołując zdefiniowaną funkcję wywołania zwrotnego dla wszystkich elementów w tablicy, w kolejności malejącej. Zwracana wartość funkcji wywołania zwrotnego jest wynikiem zakumulowanym i jest dostarczana jako argument w następnym wywołaniu funkcji wywołania zwrotnego.|  
|[reverse — metoda](../../javascript/reference/reverse-method-javascript.md)|Zwraca `Array` cofnąć obiektu z elementami.|  
|[SHIFT — metoda](../../javascript/reference/shift-method-array-javascript.md)|Usuwa z tablicy pierwszy element i zwraca go.|  
|[Metoda slice (tablica)](../../javascript/reference/slice-method-array-javascript.md)|Zwraca część tablicy.|  
|[Some — metoda](../../javascript/reference/some-method-array-javascript.md)|Sprawdza, czy funkcja wywołania zwrotnego zdefiniowanego zwraca `true` dla każdego elementu tablicy.|  
|[sort — metoda](../../javascript/reference/sort-method-array-javascript.md)|Zwraca `Array` obiektu z elementami sortowane.|  
|[splice — metoda](../../javascript/reference/splice-method-array-javascript.md)|Usuwa z tablicy elementy i jeśli to konieczne, wstawia w ich miejsce nowe elementy, zwracając elementy usunięte.|  
|[toLocaleString — metoda](../../javascript/reference/tolocalestring-method-object-javascript.md)|Zwraca ciąg przy użyciu bieżących ustawień regionalnych.|  
|[toString — metoda](../../javascript/reference/tostring-method-array.md)|Zwraca ciąg reprezentujący tablicę.|  
|[unshift — metoda](../../javascript/reference/unshift-method-array-javascript.md)|Wstawia nowe elementy na początku tablicy.|  
|[valueOf — metoda](../../javascript/reference/valueof-method-array.md)|Pobiera odwołanie do tablicy.|  
|[wartości — metoda](../../javascript/reference/values-method-array-javascript.md)|Zwraca iterację, który zawiera wartości w tablicy.|  
  
## <a name="see-also"></a>Zobacz też  
 [Przewijanie, przesuwać i powiększać przykładowej aplikacji](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)