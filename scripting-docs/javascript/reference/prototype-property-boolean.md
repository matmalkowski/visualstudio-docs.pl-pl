---
title: "prototype — właściwość (wartość logiczna) | Dokumentacja firmy Microsoft"
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
ms.assetid: e4f07cb5-3462-488c-a418-76064ab10eae
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 52d2d241c4d550fe4491ea827fab9d586281242d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="prototype-property-boolean"></a>prototype — Właściwość (wartość logiczna)
Zwraca odwołanie do prototyp wartość logiczną.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
boolean.prototype  
```  
  
## <a name="remarks"></a>Uwagi  
 `boolean` Argument jest nazwą obiektu.  
  
 `prototype` Właściwość zapewnia podstawowy zestaw funkcji do klasy obiektów. Nowe wystąpienia obiektu "dziedziczy" zachowanie prototypu przypisane do tego obiektu. Właściwości i metody, które mogą być dodawane do prototyp, ale obiekty wbudowane nie może być przypisany inny prototypu.  
  
 Na przykład, aby dodać metodę `Boolean` obiekt, który zwraca wartość największego elementu tablicy, zadeklarować funkcję, dodaj go do `Boolean.prototype`, a następnie użyć go.  
  
```JavaScript  
function isFalse( ){  
    if (this.toString() == "false")  
         return true;  
    else  
        return false;  
}  
Boolean.prototype.isFalse = isFalse;  
var bool = new Boolean(1);  
document.write(bool.isFalse());  
  
// Output:  
// false  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]