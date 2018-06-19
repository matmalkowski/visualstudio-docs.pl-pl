---
title: Stałe matematyczne (JavaScript) | Dokumentacja firmy Microsoft
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
- LN2 constant [JavaScript]
- E constant [JavaScript]
- LOG10E constant [JavaScript]
- SQRT1_2 constant [JavaScript]
- LOG2E constant [JavaScript]
- Math.SQRT2 constant [JavaScript]
- PI constant [JavaScript]
- Math.LOG2E constant [JavaScript]
- constants [JavaScript], math
- Math.E constant [JavaScript]
- logarithm consants [JavaScript]
- Math.LOG10E constant [JavaScript]
- Math.SQRT1_2 constant [JavaScript]
- SQRT2 constant [JavaScript]
- square root constants [JavaScript]
- Math.PI constant [JavaScript]
- math constants [JavaScript]
- LN10 constant [JavaScript]
- Math.LN2 constant [JavaScript]
- Math.LN10 constant [JavaScript]
ms.assetid: 8a674046-cb99-4103-92be-83697fba6344
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9942abb69af416cd4cd7f092dc9f1478e0bc3a69
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791194"
---
# <a name="math-constants-javascript"></a>Stałe matematyczne (JavaScript)
Stałe matematyczne zwracać stałe wartości, które są właściwościami `Math` obiektu.  
  
## <a name="math-object-constants"></a>Matematyczne stałe obiektu  
 W poniższej tabeli wymieniono stałe wartości, które są właściwościami [Math — obiekt](../../javascript/reference/math-object-javascript.md).  
  
|Stała|Opis|Przybliżona wartość|  
|--------------|-----------------|-----------------------|  
|`Math.E`|Stałe matematyczne e. To jest liczba Eulera w, podstawę logarytmów naturalnych.|2.718|  
|`Math.LN2`|Logarytm naturalny z 2.|0.693|  
|`Math.LN10`|Logarytm naturalny 10.|2.302|  
|`Math.LOG2E`|E logarytmu base-2.|1.443|  
|`Math.LOG10E`|Base — logarytm o podstawie 10 e.|0.434|  
|`Math.PI`|Pi. Jest to stosunek obwodu do jego średnica okręgu.|3.14159|  
|`Math.SQRT1_2`|Pierwiastek kwadratowy liczby 0,5 lub, ekwiwalentnie jeden rozdzielonych pierwiastek kwadratowy liczby 2.|0.707|  
|`Math.SQRT2`|Pierwiastek kwadratowy liczby 2.|1.414|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób użycia `Math.PI` stałej.  
  
```JavaScript  
var radius = 3;  
var area = Math.PI * radius * radius;  
document.write(area);  
  
// Output: 28.274333882308138  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Dotyczy**: [Math — obiekt](../../javascript/reference/math-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Number — stałe](../../javascript/reference/number-constants-javascript.md)   
 [JavaScript — stałe](../../javascript/reference/javascript-constants.md)