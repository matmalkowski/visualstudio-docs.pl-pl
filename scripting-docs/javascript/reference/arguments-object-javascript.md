---
title: "arguments — obiekt (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: arguments
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- arguments, arguments object
- arguments object
ms.assetid: 5eb79ca9-bbb8-4a42-aaf5-16a93ecb425f
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2a5c526d19ad5469d9d099f51cc5a2e2d089814f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="arguments-object-javascript"></a>arguments — Obiekt (JavaScript)
Obiekt reprezentujący argumenty funkcji aktualnie wykonywane i funkcje, które ją.  
  
## <a name="syntax"></a>Składnia  
  
```  
[function.]arguments[n]  
```  
  
## <a name="parameters"></a>Parametry  
 *Funkcja*  
 Opcjonalny. Nazwa aktualnie wykonywanych `Function` obiektu.  
  
 *n*  
 Wymagany. Liczony od zera indeks wartości argumentu przekazany do `Function` obiektu.  
  
## <a name="remarks"></a>Uwagi  
 Nie można jawnie utworzyć **argumenty** obiektu. **Argumenty** obiektu tylko stają się dostępne po funkcji rozpoczyna się wykonanie. **Argumenty** obiektu funkcji nie jest tablicą, ale oddzielne argumenty są dostępne w taki sam sposób jak elementy tablicy są dostępne. Indeks  *n*  jest rzeczywiście odwołanie do jednej z **0**  ***n***  właściwości **argumenty** obiektu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie **argumenty** obiektu.  
  
```JavaScript  
function ArgTest(a, b)  
{  
   var s = "";  
  
   s += "Expected Arguments: " + ArgTest.length;  
   s += "<br />";  
   s += "Passed Arguments: " + arguments.length;  
   s += "<br />";  
  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++)  
   {  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
  
   document.write(s);  
}  
  
ArgTest(1, 2, "hello", new Date())  
  
// Output:  
// Expected Arguments: 2  
// Passed Arguments: 4  
// The individual arguments are: 1 2 hello Tues Jan 8 08:27:09 PST 20xx  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [0... n właściwości (argumenty)](../../javascript/reference/0-dot-dot-dot-n-properties-arguments-javascript.md)   
 [callee — właściwość (argumenty)](../../javascript/reference/callee-property-arguments-javascript.md)   
 [length — właściwość (argumenty)](../../javascript/reference/length-property-arguments-javascript.md)