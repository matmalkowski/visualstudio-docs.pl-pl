---
title: Metoda lastIndexOf (tablica) (JavaScript) | Dokumentacja firmy Microsoft
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
- arrays [JavaScript], lastIndexOf method
- lastIndexOf method [JavaScript]
ms.assetid: 04f5145d-007e-498f-b06f-11ab384c2968
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 12d2a0fca7a7cd82543a83ea19aca49d3cbb93b6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="lastindexof-method-array-javascript"></a>lastIndexOf — Metoda (Array) (JavaScript)
Zwraca indeks ostatniego wystąpienia określonej wartości w tablicy.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
array1.lastIndexOf(searchElement[, fromIndex])  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Definicja|  
|---------------|----------------|  
|`array1`|Wymagany. Obiekt array do wyszukiwania.|  
|`searchElement`|Wymagany. Wartość do zlokalizowania w `array1`.|  
|`fromIndex`|Opcjonalny. Indeks tablicy, w którym należy rozpocząć wyszukiwanie. Jeśli `fromIndex` jest pominięty, wyszukiwanie rozpoczyna się od ostatniego indeks w tablicy.|  
  
## <a name="return-value"></a>Wartość zwracana  
 Indeks ostatniego wystąpienia `searchElement` w tablicy lub wartość-1, jeśli `searchElement` nie znaleziono.  
  
## <a name="remarks"></a>Uwagi  
 `lastIndexOf` Metoda szuka tablicy dla określonej wartości. Metoda zwraca indeks pierwszego wystąpienia lub wartość -1, jeśli określona wartość nie zostanie znaleziony.  
  
 Wyszukiwanie występuje malejąco według indeksu (najpierw ostatniego członka). Aby wyszukać w kolejności rosnącej, należy użyć [indexOf — metoda (tablica)](../../javascript/reference/indexof-method-array-javascript.md).  
  
 Elementy tablicy są porównywane z `searchElement` przez strict równości, podobnie jak porównanie dokonane przez wartość `===` operatora. Aby uzyskać więcej informacji, zobacz [operatory porównania](../../javascript/reference/comparison-operators-javascript.md).  
  
 Opcjonalny `fromIndex` argument określa indeks tablicy, w którym należy rozpocząć wyszukiwanie. Jeśli `fromIndex` jest większa niż lub równa długości tablicy, przeszukiwany jest całą tablicę. Jeśli `fromIndex` jest ujemna, wyszukiwanie rozpoczyna się od długości tablicy plus `fromIndex`. Jeśli obliczona indeks jest mniejszy niż 0, zwracana jest wartość -1.  
  
## <a name="example"></a>Przykład  
 Poniższe przykłady przedstawiają użycie `lastIndexOf` metody.  
  
```JavaScript  
// Create an array.  
var ar = ["ab", "cd", "ef", "ab", "cd"];  
  
// Determine the first location, in descending order, of "cd".  
document.write(ar.lastIndexOf("cd") + "<br/>");  
  
// Output: 4  
  
// Find "cd" in descending order, starting at index 2.  
document.write(ar.lastIndexOf("cd", 2) + "<br/>");  
  
// Output: 1  
  
// Search for "gh" (which is not found).  
document.write(ar.lastIndexOf("gh")+ "<br/>");  
  
// Output: -1  
  
// Find "ab" with a fromIndex argument of -3.  
// The search in descending order starts at index 3,  
// which is the array length minus 2.  
document.write(ar.lastIndexOf("ab", -3) + "<br/>");  
// Output: 0  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [indexOf — metoda (tablica)](../../javascript/reference/indexof-method-array-javascript.md)   
 [Array — obiekt](../../javascript/reference/array-object-javascript.md)   
 [Używanie tablic](../../javascript/advanced/using-arrays-javascript.md)