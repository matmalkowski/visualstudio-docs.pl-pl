---
title: prototype — właściwość (błąd) | Dokumentacja firmy Microsoft
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
ms.assetid: 6c268a51-1a3d-4397-abf8-e54ca4e598fe
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b7d0413d3541691a38672e7c0720b58245725b76
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791353"
---
# <a name="prototype-property-error"></a>prototype — Właściwość (Błąd)
Zwraca odwołanie do prototypu dla błędu.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
error.prototype  
```  
  
## <a name="remarks"></a>Uwagi  
 `error` Argument jest nazwą wystąpił błąd.  
  
 Użyj `prototype` właściwości, aby zapewnić podstawowy zestaw funkcji wystąpił błąd. Nowe wystąpienia obiektu "dziedziczy" zachowanie prototypu przypisane do tego obiektu.  
  
 Na przykład, aby dodać metodę `Error` obiekt, który zwraca wartość największego elementu tablicy, zadeklarować funkcję, dodaj go do `Error.prototype`, a następnie użyć go.  
  
```JavaScript  
function getSeverity(){  
    if (this.number > 1000)  
        return "high";  
    else  
        return "low";  
}  
Error.prototype.getSev = getSeverity;  
var myError = new Error();  
myError.number = 5000;  
  
document.write(myError.getSev());   
  
// Output: high  
  
```  
  
 Wszystkie wewnętrzne [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] obiekty mają `prototype` właściwość, która jest tylko do odczytu. Właściwości i metody, które mogą być dodawane do prototyp, ale obiekt nie może być przypisany inny prototypu. Jednak obiekty zdefiniowane przez użytkownika można przypisać nowe prototypu.  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]