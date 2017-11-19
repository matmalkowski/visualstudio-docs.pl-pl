---
title: "sort — metoda (tablica) (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: sort
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: Sort method
ms.assetid: 9bd8b54a-c838-4806-85c8-62eebe6bc48c
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2d098b47591ca7bbb4e3e8da5e5c14f8c0e9b255
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="sort-method-array-javascript"></a>sort — Metoda (Tablica) (JavaScript)
Sortuje `Array`.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
arrayobj.sort(sortFunction)   
```  
  
## <a name="parameters"></a>Parametry  
 `arrayObj`  
 Wymagany. Wszelkie `Array` obiektu.  
  
 `sortFunction`  
 Opcjonalny. Nazwa funkcji umożliwia określenie kolejności elementów. Pominięcie elementy są sortowane w kolejności rosnącej kolejności znaków ASCII.  
  
## <a name="return-value"></a>Wartość zwracana  
 Tablica posortowane.  
  
## <a name="remarks"></a>Uwagi  
 `sort` Sortuje metody `Array` obiektu w miejscu; brak nowych `Array` obiekt jest tworzony podczas wykonywania.  
  
 Jeśli podasz funkcję `sortFunction` argumentu, aplikacja musi zwracać jedną z następujących wartości:  
  
-   Wartość ujemną, jeśli pierwszy argument przekazywany jest mniejsza niż drugi argument.  
  
-   Zero, jeśli dwa argumenty są równoważne.  
  
-   Dodatnia wartość, jeśli pierwszy argument jest większy niż drugi argument.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `sort` metody.  
  
```JavaScript  
var a = new Array(4, 11, 2, 10, 3, 1);  
  
var b = a.sort();  
document.write(b);  
document.write("<br/>");  
  
// This is ASCII character order.  
// Output: 1,10,11,2,3,4)  
  
// Sort the array elements with a function that compares array elements.  
b = a.sort(CompareForSort);  
document.write(b);  
document.write("<br/>");  
// Output: 1,2,3,4,10,11.  
  
// Sorts array elements in ascending order numerically.  
function CompareForSort(first, second)  
{  
    if (first == second)  
        return 0;  
    if (first < second)  
        return -1;  
    else  
        return 1;   
}  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]