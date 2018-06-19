---
title: Math.ACOS — funkcja (JavaScript) | Dokumentacja firmy Microsoft
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
- acos
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- acos method
- arcosine method
ms.assetid: 828cb3c3-bdf7-4bb7-97ae-3617ce4b2d62
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 773499287e215fbc161f289954811d3ef62bcba6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791011"
---
# <a name="mathacos-function-javascript"></a>Math.acos — Funkcja (JavaScript)
Zwraca arcus cosinus (lub cosinus) dla danej liczby.  
  
## <a name="syntax"></a>Składnia  
  
```  
Math.acos(number)  
```  
  
#### <a name="parameters"></a>Parametry  
 Wymagane `number` argument jest wyrażenia liczbowego.  
  
## <a name="return-value"></a>Wartość zwracana  
 Arcus cosinus z `number` argument w radianach.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia sposób użycia `acos` funkcji.  
  
```JavaScript  
var v1 = Math.acos(-1.0);  
var v2 = Math.cos(-1.0);  
  
document.write(v1);  
document.write("<br/>");  
document.write(v2);  
  
// Output:  
// 3.141592653589793  
// 0.5403023058681398  
  
```  
  
## <a name="remarks"></a>Uwagi  
 **Dotyczy**: [Math — obiekt](../../javascript/reference/math-object-javascript.md)  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Math.ASIN — funkcja](../../javascript/reference/math-asin-function-javascript.md)   
 [Math.ATAN — funkcja](../../javascript/reference/math-atan-function-javascript.md)   
 [Math.cos — funkcja](../../javascript/reference/math-cos-function-javascript.md)   
 [Math.sin — funkcja](../../javascript/reference/math-sin-function-javascript.md)   
 [Math.tan — funkcja](../../javascript/reference/math-tan-function-javascript.md)   
 [Math — obiekt](../../javascript/reference/math-object-javascript.md)