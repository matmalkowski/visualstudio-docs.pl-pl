---
title: Call — metoda (funkcja) (JavaScript) | Dokumentacja firmy Microsoft
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
- call
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- call method
ms.assetid: fa356dec-48e6-4f75-8bf3-c1814a76818f
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2ef871f85459ad875a747ae79c7c054b30a82e55
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24789118"
---
# <a name="call-method-function-javascript"></a>call — Metoda (Funkcja) (JavaScript)
Wywołuje metodę obiektu, zastępując innego obiektu dla bieżącego obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
call([thisObj[, arg1[, arg2[,  [, argN]]]]])  
```  
  
## <a name="parameters"></a>Parametry  
 `thisObj`  
 Opcjonalny. Obiekt, który ma być używany jako bieżący obiekt.  
  
 `arg1, arg2, , argN`  
 Opcjonalny. Lista argumentów, które mają być przekazane do metody.  
  
## <a name="remarks"></a>Uwagi  
 `call` Metoda jest używana do wywołania metody w imieniu innego obiektu. Umożliwia zmianę `this` obiektu funkcji z oryginalnego kontekstu nowy obiekt określony przez `thisObj`.  
  
 Jeśli `thisObj` nie zostanie podany, `global` obiekt jest używany jako `thisObj`.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia sposób użycia `call` metody.  
  
```JavaScript  
function callMe(arg1, arg2){  
    var s = "";  
  
    s += "this value: " + this;  
    s += "<br />";  
    for (i in callMe.arguments) {  
        s += "arguments: " + callMe.arguments[i];  
        s += "<br />";  
    }  
    return s;  
}  
  
document.write("Original function: <br/>");  
document.write(callMe(1, 2));  
document.write("<br/>");  
  
document.write("Function called with call: <br/>");  
document.write(callMe.call(3, 4, 5));  
  
// Output:   
// Original function:   
// this value: [object Window]  
// arguments: 1  
// arguments: 2  
  
// Function called with call:   
// this value: 3  
// arguments: 4  
// arguments: 5  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Function — obiekt](../../javascript/reference/function-object-javascript.md)   
 [Apply — metoda (funkcja)](../../javascript/reference/apply-method-function-javascript.md)