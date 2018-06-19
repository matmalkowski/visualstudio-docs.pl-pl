---
title: Metoda slice (tablica) (JavaScript) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- slice
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- zero-based index
- Array object
- slice method
ms.assetid: 3c122219-14de-4126-b091-809659c026d6
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a61cd331abef9d1a0d979f547f6d6f12222c1eee
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791662"
---
# <a name="slice-method-array-javascript"></a>slice — Metoda (Tablica) (JavaScript)
Zwraca część tablicy.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
arrayObj.slice(start, [end])   
```  
  
## <a name="parameters"></a>Parametry  
 `arrayObj`  
 Wymagany. `Array` Obiektu.  
  
 `start`  
 Wymagany. Na początku określoną część `arrayObj`.  
  
 `end`  
 Opcjonalny. Koniec określoną część `arrayObj`.  
  
## <a name="remarks"></a>Uwagi  
 `slice` Metoda zwraca `Array` obiekt zawierający określoną część `arrayObj`.  
  
 `slice` Metoda kopiuje do, z wyjątkiem, wskazane przez element `end`. Jeśli `start` jest ujemna, będzie traktowane jako `length`  +  `start`, gdzie `length` jest długości tablicy. Jeśli `end` jest ujemna, będzie traktowane jako `length`  +  `end` gdzie `length` jest długości tablicy. Jeśli `end` pominięcia wyodrębniania będzie nadal występować na końcu `arrayObj`. Jeśli `end` występuje przed `start`, elementy nie są kopiowane do nowej tablicy.  
  
## <a name="example"></a>Przykład  
 W poniższych przykładach pokazano, jak używać `slice` metody. W pierwszym przykładzie wszystkie z wyjątkiem ostatniego elementu `myArray` jest kopiowana do `newArray`. W drugim przykładzie, tylko ostatnie dwa elementy `myArray` są kopiowane do `newArray`.  
  
```JavaScript  
var origArray = [3, 5, 7, 9];  
var newArray = origArray. slice(0, -1);  
document.write(origArray);  
document.write("<br/>");  
newArray = origArray. slice(-2);  
document.write(newArray);  
  
// Output:  
// 3,5,7,9  
// 7,9  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Metoda slice (ciąg)](../../javascript/reference/slice-method-string-javascript.md)   
 [String — obiekt](../../javascript/reference/string-object-javascript.md)