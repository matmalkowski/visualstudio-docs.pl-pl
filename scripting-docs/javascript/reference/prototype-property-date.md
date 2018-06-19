---
title: prototype — właściwość (Data) | Dokumentacja firmy Microsoft
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
ms.assetid: 44f9c637-7da7-4833-906d-358506f32ced
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8c0b337964d2a2fe17a4e9a7906d81069470e61b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791275"
---
# <a name="prototype-property-date"></a>prototype — Właściwość (Data)
Zwraca odwołanie do prototyp daty.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
date.prototype  
```  
  
## <a name="remarks"></a>Uwagi  
 `date` Argument jest nazwą obiektu.  
  
 Użyj `prototype` właściwości, aby zapewnić podstawowy zestaw funkcji do daty. Nowe wystąpienia obiektu "dziedziczy" zachowanie prototypu przypisane do tego obiektu.  
  
 Na przykład, aby dodać metodę `Date` obiekt, który zwraca wartość największego elementu tablicy, zadeklarować funkcję, dodaj go do `Date.prototype`, a następnie użyć go.  
  
```JavaScript  
function max( ){  
    var max = new Date();  
    max.setFullYear(2200, 01, 01);  
    return max;  
}  
Date.prototype.maxDate = max;  
var myDate = new Date();  
  
if (myDate < myDate.maxDate())  
    document.write("today isn't the max");  
else if (myDate == myDate.maxDate())  
    document.write("today is the max");   
  
// Output:  
// today isn't the max  
  
```  
  
 Wszystkie wewnętrzne [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] obiekty mają `prototype` właściwość, która jest tylko do odczytu. Właściwości i metody, które mogą być dodawane do prototyp, ale obiekt nie może być przypisany inny prototypu. Jednak obiekty zdefiniowane przez użytkownika można przypisać nowe prototypu.  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]