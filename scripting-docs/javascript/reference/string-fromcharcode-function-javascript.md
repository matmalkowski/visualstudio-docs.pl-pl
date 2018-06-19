---
title: String.fromCharCode — funkcja (JavaScript) | Dokumentacja firmy Microsoft
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
- fromCharCode
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- fromCharCodeAt method
- characters, from Unicode
ms.assetid: f64120c1-23a7-48ca-8d1c-db3e8856cab4
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dbcd9062d7da0b73647c1d9eb6cc207af23c3532
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791461"
---
# <a name="stringfromcharcode-function-javascript"></a>String.fromCharCode — Funkcja (JavaScript)
Zwraca ciąg utworzony z wielu wartości znaków Unicode.  
  
## <a name="syntax"></a>Składnia  
  
```  
String.fromCharCode([code1[, code2[, ...[, codeN]]]])   
```  
  
## <a name="parameters"></a>Parametry  
 `String`  
 Wymagany. `String` Obiektu.  
  
 `code1`, . . . , `codeN`  
 Opcjonalny. Seria wartości znakowych Unicode do przekonwertowania na ciąg. Jeśli nie jest dostarczony bez argumentów, wynik jest ciągiem pustym.  
  
## <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji na `String` obiektu, a nie na wystąpienie ciągu.  
  
 Poniższy przykład przedstawia użycie tej metody:  
  
```JavaScript  
var test = String.fromCharCode(112, 108, 97, 105, 110);  
document.write(test);  
  
// Output: plain  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [charCodeAt — metoda (ciąg)](../../javascript/reference/charcodeat-method-string-javascript.md)