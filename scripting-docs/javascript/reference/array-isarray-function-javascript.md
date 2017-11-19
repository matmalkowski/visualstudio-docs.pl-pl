---
title: "Array.IsArray — funkcja (JavaScript) | Dokumentacja firmy Microsoft"
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
helpviewer_keywords:
- isArray function [JavaScript]
- Array.isArray function [JavaScript]
ms.assetid: 58f7d2e0-d310-4292-b9bc-37a73c585780
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c31bdfe022cd41648117fc80c8df257e48e592ae
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="arrayisarray-function-javascript"></a>Array.isArray — Funkcja (JavaScript)
Określa, czy obiekt jest tablicą.  
  
## <a name="syntax"></a>Składnia  
  
```  
Array.isArray(object)   
```  
  
#### <a name="parameters"></a>Parametry  
 `object`  
 Wymagany. Obiekt do przetestowania.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli `object` jest tablicą; w przeciwnym razie `false`. Jeśli `object` argument nie jest obiektem, `false` jest zwracany.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `Array.isArray` funkcji.  
  
```JavaScript  
var ar = [];  
var result = Array.isArray(ar);  
// Output: true  
  
var ar = new Array();  
var result = Array.isArray(ar);  
// Output: true  
  
var ar = [1, 2, 3];  
var result = Array.isArray(ar);  
// Output: true  
  
var result = Array.isArray("an array");  
document.write(result);  
// Output: false  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Array — obiekt](../../javascript/reference/array-object-javascript.md)   
 [Używanie tablic](../../javascript/advanced/using-arrays-javascript.md)   
 [TypeOf — Operator](../../javascript/reference/typeof-operator-decrementjavascript.md)