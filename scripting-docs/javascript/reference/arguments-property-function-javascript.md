---
title: arguments — właściwość (funkcja) (JavaScript) | Dokumentacja firmy Microsoft
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
- arguments
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- arguments, arguments property
- Arguments property
ms.assetid: efc7a1ee-0880-4f05-b0f2-808f31a4af1d
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5b0b18fb8164639119e5db5e7a5d76b4280f9c9d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24788866"
---
# <a name="arguments-property-function-javascript"></a>arguments — Właściwość (Funkcja) (JavaScript)
Pobiera argumenty dla aktualnie wykonywanych `Function` obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
function.arguments  
```  
  
## <a name="remarks"></a>Uwagi  
 `function` Argument jest nazwą funkcji aktualnie wykonywane i można pominąć.  
  
 Ta właściwość umożliwia funkcja obsługi zmienną liczbę argumentów. **Długość** właściwość `arguments` obiektu zawiera liczba argumentów przekazanych do funkcji. Oddzielne argumenty, które są zawarte w `arguments` obiektu można uzyskać w taki sam sposób jak elementy tablicy są dostępne.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `arguments` właściwości:  
  
```JavaScript  
function ArgTest(arg1, arg2){  
   var s = "";  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++){  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
   return(s);  
}  
document.write(ArgTest(1, 2, "hello"));  
  
//Output: function ArgTest(arg1, arg2){  
   var s = "";  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++){  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
   return(s);  
}  
document.write(ArgTest(1, 2, "hello"));  
  
// Output: The individual arguments are: 1 2 hello  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [arguments — obiekt](../../javascript/reference/arguments-object-javascript.md)   
 [Function — instrukcja](../../javascript/reference/function-statement-javascript.md)