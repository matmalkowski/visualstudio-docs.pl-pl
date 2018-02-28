---
title: Metoda concat (tablica) (JavaScript) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- concat
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- concat method (array)
- Concat method
ms.assetid: bc2b4a6a-209e-4d59-8c24-59db01d53b1e
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 19f3a216a36f9ad8c422036476e46b89b6ee488c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="concat-method-array-javascript"></a>concat — Metoda (Tablica) (JavaScript)
Łączy dwa lub więcej tablic.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
array1.concat([item1[, item2[, . . . [, itemN]]]])   
```  
  
## <a name="parameters"></a>Parametry  
 `array1`  
 Wymagany. `Array` Do połączonych są inne tablice obiektu.  
  
 `item1,. . ., itemN`  
 Opcjonalny. Dodatkowe elementy do dodania na koniec `array1`.  
  
## <a name="remarks"></a>Uwagi  
 `concat` Metoda zwraca `Array` obiektu zawierającego połączenie `array1` i inne elementy dostarczony.  
  
 Elementy do dodania (*item1 itemN*) do tablicy zostaną dodane, w kolejności, rozpoczynając od pierwszego elementu na liście. Jeśli jeden z elementów jest tablicą, jego zawartości są dodawane na końcu `array1`. Jeśli element jest inna niż tablica, jest ona dodana do końca tablicy jako elementu pojedynczą tablicę.  
  
 Źródło tablic są kopiowane elementy do tabeli wynikowej w następujący sposób:  
  
-   Jeśli obiekt jest kopiowana za pomocą dowolnego jest połączony do nowej tablicy tablic, odwołanie do obiektu w dalszym ciągu wskazywać tego samego obiektu. Zmiany w nowej tablicy lub tablica oryginalnego spowoduje zmianę do drugiego.  
  
-   Jeśli wartość liczbą lub ciągiem jest dodawana do nowej tablicy, jest kopiowany tylko wartości. Zmiana wartości w tablicy nie ma wpływu na wartość w innym.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `concat` metody, gdy jest używany z tablicy:  
  
```JavaScript  
var a, b, c, d;  
a = new Array(1,2,3);  
b = "dog";  
c = new Array(42, "cat");  
d = a.concat(b, c);  
document.write(d);  
  
//Output:   
1, 2, 3, "dog", 42, "cat"  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Metoda concat (ciąg)](../../javascript/reference/concat-method-string-javascript.md)   
 [JOIN — metoda (tablica)](../../javascript/reference/join-method-array-javascript.md)