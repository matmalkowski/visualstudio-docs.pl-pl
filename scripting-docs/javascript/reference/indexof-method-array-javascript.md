---
title: "indexOf — metoda (tablica) (JavaScript) | Dokumentacja firmy Microsoft"
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
- arrays [JavaScript], indexOf method
- indexOf method [JavaScript]
ms.assetid: 5bee31ae-aaf1-4466-8cfd-ed287e3cdf17
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 63685219faf42991da6b798493c58b356ab97279
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="indexof-method-array-javascript"></a>indexOf — Metoda (Array) (JavaScript)
Zwraca indeks pierwszego wystąpienia wartości w tablicy.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
array1.indexOf(searchElement[, fromIndex])  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Definicja|  
|---------------|----------------|  
|`array1`|Wymagany. Obiekt tablicy.|  
|`searchElement`|Wymagany. Wartość do zlokalizowania w `array1`.|  
|`fromIndex`|Opcjonalny. Indeks tablicy, w którym należy rozpocząć wyszukiwanie. Jeśli `fromIndex` jest pominięty, wyszukiwanie rozpoczyna się pod indeksem 0.|  
  
## <a name="return-value"></a>Wartość zwracana  
 Indeks pierwszego wystąpienia `searchElement` w tablicy lub wartość-1, jeśli `searchElement` nie znaleziono.  
  
## <a name="remarks"></a>Uwagi  
 `indexOf` Metoda szuka tablicy dla określonej wartości. Metoda zwraca indeks pierwszego wystąpienia lub wartość -1, jeśli określona wartość nie zostanie znaleziony.  
  
 Wyszukiwanie występuje rosnąco indeksu.  
  
 Elementy tablicy są porównywane z `searchElement` przez strict równości, podobnie jak wartość `===` operatora. Aby uzyskać więcej informacji, zobacz [operatory porównania](../../javascript/reference/comparison-operators-javascript.md).  
  
 Opcjonalny `fromIndex` argument określa indeks tablicy, w którym należy rozpocząć wyszukiwanie. Jeśli `fromIndex` jest większa niż lub równa długości tablicy, jest zwracana wartość -1. Jeśli `fromIndex` jest ujemna, wyszukiwanie rozpoczyna się od długości tablicy plus `fromIndex`.  
  
## <a name="example"></a>Przykład  
 Poniższe przykłady przedstawiają użycie `indexOf` metody.  
  
```JavaScript  
// Create an array. (The elements start at index 0.)  
var ar = ["ab", "cd", "ef", "ab", "cd"];  
  
// Determine the first location of "cd".  
document.write(ar.indexOf("cd") + "<br/>");  
  
// Output: 1  
  
// Find "cd" starting at index 2.  
document.write(ar.indexOf("cd", 2) + "<br/>");  
  
// Output: 4  
  
// Find "gh" (which is not found).  
document.write (ar.indexOf("gh")+ "<br/>");  
  
// Output: -1  
  
// Find "ab" with a fromIndex argument of -2.  
// The search starts at index 3, which is the array length plus -2.  
document.write (ar.indexOf("ab", -2) + "<br/>");  
// Output: 3  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [JavaScript — metody](../../javascript/reference/javascript-methods.md)   
 [Array — obiekt](../../javascript/reference/array-object-javascript.md)   
 [Używanie tablic](../../javascript/advanced/using-arrays-javascript.md)