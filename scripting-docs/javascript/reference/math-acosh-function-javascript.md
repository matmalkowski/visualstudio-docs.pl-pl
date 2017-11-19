---
title: "Math.ACOSH — funkcja (JavaScript) | Dokumentacja firmy Microsoft"
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
ms.assetid: 881dd2a0-36a5-403b-a3dc-523d8e1e1317
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1fd75140dfcf3d9ac703c2aeadf68bea4da9e0dc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="mathacosh-function-javascript"></a>Math.acosh — funkcja (JavaScript)
Zwraca arcus cosinus hiperboliczny (odwrotny cosinus hiperboliczny) dla danej liczby.  
  
## <a name="syntax"></a>Składnia  
  
```  
Math.acosh(number)  
```  
  
#### <a name="parameters"></a>Parametry  
 Wymagane `number` argument jest wyrażenia liczbowego.  
  
## <a name="return-value"></a>Wartość zwracana  
 Odwrotny cosinus hiperboliczny dla `number` argument w radianach.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia sposób użycia `acosh` funkcji.  
  
```JavaScript  
var v1 = Math.acosh(3);  
vary v2 = Math.acosh(-1);  
  
document.write(v1);  
document.write("</br>");  
document.write(v2);  
  
// Output:  
// 1.762747174039086  
// NaN  
  
```  
  
## <a name="remarks"></a>Uwagi  
 **Dotyczy**: [Math — obiekt](../../javascript/reference/math-object-javascript.md)  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Math.ACOS — funkcja](../../javascript/reference/math-acos-function-javascript.md)   
 [Math.ASIN — funkcja](../../javascript/reference/math-asin-function-javascript.md)   
 [Math.ATAN — funkcja](../../javascript/reference/math-atan-function-javascript.md)   
 [Math.cos — funkcja](../../javascript/reference/math-cos-function-javascript.md)   
 [Math.sin — funkcja](../../javascript/reference/math-sin-function-javascript.md)   
 [Math.tan — funkcja](../../javascript/reference/math-tan-function-javascript.md)   
 [Math — obiekt](../../javascript/reference/math-object-javascript.md)