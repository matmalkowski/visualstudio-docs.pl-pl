---
title: prototype — właściwość (tablica) | Dokumentacja firmy Microsoft
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
ms.assetid: 5fedf632-8316-4e5d-ab20-10e41aa4d9f8
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4fd5102fe2f49218de76c498a11256a6ef24ff0f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791212"
---
# <a name="prototype-property-array"></a>prototype — Właściwość (Tablica)
Zwraca odwołanie do prototypu dla klasy tablicy.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
array.prototype  
```  
  
## <a name="remarks"></a>Uwagi  
 `array` Argument jest nazwą tablicy.  
  
 Użyj `prototype` właściwości, aby zapewnić podstawowy zestaw funkcji do klasy obiektów. Nowe wystąpienia obiektu "dziedziczy" zachowanie prototypu przypisane do tego obiektu.  
  
 Na przykład, aby dodać metodę `Array` obiekt, który zwraca wartość największego elementu tablicy, zadeklarować funkcję, dodaj go do `Array.prototype`, a następnie użyć go.  
  
```JavaScript  
function array_max( ){  
    var i, max = this[0];  
    for (i = 1; i < this.length; i++)  
    {  
    if (max < this[i])  
    max = this[i];  
    }  
    return max;  
}  
Array.prototype.max = array_max;  
var myArray = new Array(7, 1, 3, 11, 25, 9  
);  
document.write(myArray.max());  
  
// Output: 25  
```  
  
 Wszystkie wewnętrzne [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] obiekty mają `prototype` właściwość, która jest tylko do odczytu. Właściwości i metody, które mogą być dodawane do prototyp, ale obiekt nie może być przypisany inny prototypu. Jednak obiekty zdefiniowane przez użytkownika można przypisać nowe prototypu.  
  
 Listy metod i właściwości dla każdego obiektu wewnętrznego w niniejszej dokumentacji języka wskazać te, które są częścią prototypu obiektu, a które nie są.  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]