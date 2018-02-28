---
title: Funkcja obiekt (JavaScript) | Dokumentacja firmy Microsoft
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
- function
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Function object
ms.assetid: d3834767-203c-475e-848c-95c423ba15b6
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4392fd57967e6312c96af50bdff2415d0f2dcd4d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="function-object-javascript"></a>Function — Obiekt (JavaScript)
Tworzy nową funkcję.  
  
## <a name="syntax"></a>Składnia  
  
```  
function functionName([argname1  [, ...[, argnameN]]])  
{  
   body  
}  
```  
  
## <a name="syntax"></a>Składnia  
  
```  
  
functionName = new Function( [argname1,  [... argnameN,]] body );  
```  
  
## <a name="parameters"></a>Parametry  
 `functionName`  
 Wymagany. Nazwa funkcji nowo utworzony  
  
 `argname1...argnameN`  
 Opcjonalny. Lista argumentów, które akceptuje funkcji.  
  
 `body`  
 Opcjonalny. Ciąg, który zawiera blok [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] kod do wykonania po wywołaniu funkcji.  
  
## <a name="remarks"></a>Uwagi  
 Funkcja jest typu podstawowego w [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]. Składnia 1 tworzy wartość funkcja [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] konwertuje `Function` obiektu, gdy jest to konieczne. [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]Konwertuje `Function` obiekty utworzone przez Składnia 2 w wartości funkcji w momencie wywołania funkcji.  
  
 Składnia 1 jest standardowym sposobem tworzenia nowych funkcji w [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]. Składnia 2 jest alternatywny używany do tworzenia obiektów funkcji jawnie.  
  
 Na przykład aby zadeklarować funkcji, która dodaje dwa argumenty przekazane do niego, można wykonać w jednym z dwóch sposobów:  
  
## <a name="example-1"></a>Przykład 1  
  
```JavaScript  
function add(x, y)  
{  
   return(x + y);  
}  
```  
  
## <a name="example-2"></a>Przykład 2  
  
```  
var add = function(x, y) {  
     return(x+y);  
}  
```  
  
 W obu przypadkach można wywołać funkcji z wierszem kodu podobne do następujących:  
  
```JavaScript  
add(2, 3);  
```  
  
> [!NOTE]
>  Podczas wywoływania funkcji upewnij się, że należy zawsze zawierać nawiasy i wymagane argumenty. Wywołanie funkcji bez nawiasów powoduje, że ta funkcja ma zostać zwrócona, zamiast wartości funkcji.  
  
## <a name="properties"></a>Właściwości  
 [0... n właściwości](../../javascript/reference/0-dot-dot-dot-n-properties-arguments-javascript.md) &#124;[ arguments — właściwość](../../javascript/reference/arguments-property-function-javascript.md) &#124; [callee — właściwość](../../javascript/reference/callee-property-arguments-javascript.md) &#124; [caller — właściwość](../../javascript/reference/caller-property-function-javascript.md) &#124; [Konstruktora właściwości](../../javascript/reference/constructor-property-object-javascript.md) &#124; [length — właściwość (funkcja)](../../javascript/reference/length-property-function-javascript.md) &#124; [prototype — właściwość](../../javascript/reference/prototype-property-object-javascript.md)  
  
## <a name="methods"></a>Metody  
 [zastosowanie metody](../../javascript/reference/apply-method-function-javascript.md) &#124; [bind — metoda](../../javascript/reference/bind-method-function-javascript.md) &#124; [Wywołaj metodę](../../javascript/reference/call-method-function-javascript.md) &#124; [toString — metoda](../../javascript/reference/tostring-method-object-javascript.md) &#124; [valueOf — metoda](../../javascript/reference/valueof-method-object-javascript.md)  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Function — instrukcja](../../javascript/reference/function-statement-javascript.md)   
 [New — Operator](../../javascript/reference/new-operator-decrementjavascript.md)   
 [var — instrukcja](../../javascript/reference/var-statement-javascript.md)