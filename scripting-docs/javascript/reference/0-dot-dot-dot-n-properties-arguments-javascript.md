---
title: "0... n właściwości (argumenty) (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- 0...n
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- 0...n properties
ms.assetid: 52857c4b-3d56-4500-93ff-4db4729c2578
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f46c7dafef1cdc27d27f619936349637af172740
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="0n-properties-arguments-javascript"></a>0...n — Właściwości (argumenty) (JavaScript)
Zwraca wartość rzeczywistą oddzielne argumenty z **argumenty** obiektu zwróconego przez **argumenty** właściwość wykonywania funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
[function.]arguments[[0|1|2|...|n]]  
```  
  
## <a name="parameters"></a>Parametry  
 *Funkcja*  
 Opcjonalny. Nazwa aktualnie wykonywanych `Function` obiektu.  
  
 0, 1, 2, *, n*  
 Wymagany. Nieujemną całkowitą z zakresu od 0 do  *n*  gdzie 0 oznacza pierwszy argument i  *n*  reprezentuje ostatni argument. Wartość argumentu końcowego  *n*  jest **arguments.length 1**.  
  
## <a name="remarks"></a>Uwagi  
 Wartości zwracane przez 0. . . n właściwości są rzeczywiste wartości przekazanych do wykonywania funkcji. Podczas rzeczywiście tablicy argumentów, oddzielne argumenty wchodzące w skład **argumenty** obiektu są dostępne w taki sam sposób, że są dostępne elementy tablicy.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie **0...**  ***n***właściwości **argumenty** obiektu. Aby w pełni zrozumieć w przykładzie, należy przekazać co najmniej jeden z argumentów funkcji:  
  
```JavaScript  
function ArgTest(){  
   var s = "";  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++){  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
   return(s);  
}  
document.write(ArgTest(1, 2, "hello", new Date()));  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Dotyczy**: [obiekt arguments](../../javascript/reference/arguments-object-javascript.md)&#124; [Funkcji obiektu](../../javascript/reference/function-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [length — właściwość (argumenty)](../../javascript/reference/length-property-arguments-javascript.md)   
 [Właściwość length (funkcja)](../../javascript/reference/length-property-function-javascript.md)