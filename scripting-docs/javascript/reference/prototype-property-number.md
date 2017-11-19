---
title: "prototype — właściwość (numer) | Dokumentacja firmy Microsoft"
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
ms.assetid: d5fb87af-fc3a-4469-8dde-d31daf654f94
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2dba8b8886b4fdbc48a662796863b1dfca019aec
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="prototype-property-number"></a>prototype — Właściwość (Numer)
Zwraca odwołanie do prototypu dla klasy liczby.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
number.prototype  
```  
  
## <a name="remarks"></a>Uwagi  
 `number` Argument jest nazwą dla danej liczby.  
  
 Użyj `prototype` właściwości, aby zapewnić podstawowy zestaw funkcji do klasy obiektów. Nowe wystąpienia obiektu "dziedziczy" zachowanie prototypu przypisane do tego obiektu.  
  
 Na przykład, aby dodać metodę `Number` obiekt, który zwraca cyfrach numeru (liczba całkowita), zadeklarować funkcję, dodaj go do `Number.prototype`, a następnie użyć go.  
  
```JavaScript  
function number_digits() {  
    var digits = 0;  
    var num = this;  
    while (num) >= 1) {  
        digits++;  
        num /= 10;  
    }  
    return digits;  
}  
  
Number.prototype.digits = number_digits;  
var myNumber = new Number(3456.789);  
document.write(myNumber.digits());  
// Output:  
// 4  
```  
  
 Wszystkie wewnętrzne [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] obiekty mają `prototype` właściwość, która jest tylko do odczytu. Właściwości i metody, które mogą być dodawane do prototyp, ale obiekt nie może być przypisany inny prototypu. Jednak obiekty zdefiniowane przez użytkownika można przypisać nowe prototypu.  
  
 Listy metod i właściwości dla każdego obiektu wewnętrznego w niniejszej dokumentacji języka wskazać te, które są częścią prototypu obiektu, a które nie są.  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]