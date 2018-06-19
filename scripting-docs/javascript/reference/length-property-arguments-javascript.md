---
title: length — właściwość (argumenty) (JavaScript) | Dokumentacja firmy Microsoft
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
- length Property
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- length property (arguments)
- Length property
ms.assetid: 3cf36823-15bc-489b-a951-24c4923d9dba
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cede75a91244442f5f28ec9f71b7128814bed5d2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24790882"
---
# <a name="length-property-arguments-javascript"></a>length — Właściwość (argumenty) (JavaScript)
Zwraca wartość rzeczywista liczba argumentów przekazanych do funkcji przez obiekt wywołujący.  
  
## <a name="syntax"></a>Składnia  
  
```  
[function.]arguments.length  
```  
  
## <a name="remarks"></a>Uwagi  
 Opcjonalny *funkcja* argument jest nazwą aktualnie wykonywanych `Function` obiektu.  
  
 **Długość** właściwość **argumenty** obiekt został zainicjowany przez aparat skryptów do rzeczywista liczba argumentów przekazanych do `Function` obiektu po rozpoczęciu wykonywania w tej funkcji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie **długość** właściwość **argumenty** obiektu. Aby w pełni zrozumieć w przykładzie, należy przekazać argumenty więcej funkcji niż 2 argumenty, oczekiwano:  
  
```JavaScript  
function ArgTest(a, b){  
   var s = "";  
  
   s += "Expected Arguments: " + ArgTest.length;  
   s += "<br />";  
   s += "Passed Arguments: " + arguments.length;  
  
   document.write (s);  
}  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Dotyczy**: [obiekt arguments](../../javascript/reference/arguments-object-javascript.md)&#124; [Funkcji obiektu](../../javascript/reference/function-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [arguments — właściwość (funkcja)](../../javascript/reference/arguments-property-function-javascript.md)   
 [length — właściwość (tablica)](../../javascript/reference/length-property-array-javascript.md)   
 [length — właściwość (ciąg)](../../javascript/reference/length-property-string-javascript.md)