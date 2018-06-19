---
title: parsefloat — funkcja (JavaScript) | Dokumentacja firmy Microsoft
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
- parseFloat
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- parseFloat method
ms.assetid: a7d87a69-1919-4623-be85-972e6376dd2d
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eb8f6d179abba887542e59d083141534732ed42a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791206"
---
# <a name="parsefloat-function-javascript"></a>parseFloat — Funkcja (JavaScript)
Konwertuje ciąg na liczba zmiennoprzecinkowa.  
  
## <a name="syntax"></a>Składnia  
  
```  
parseFloat(numString)   
```  
  
## <a name="remarks"></a>Uwagi  
 Wymagane `numString` argument jest ciąg znaków zawierający liczba zmiennoprzecinkowa.  
  
 `parseFloat` Funkcja zwraca wartość liczbową równą wartości zawartych w `numString`. Jeśli nie ma prefiksu z `numString` może pomyślnie przeanalizowano liczba zmiennoprzecinkowa `NaN` (nie liczba) jest zwracany.  
  
```JavaScript  
parseFloat("abc")      // Returns NaN.  
parseFloat("1.2abc")   // Returns 1.2.  
```  
  
 Można sprawdzić `NaN` przy użyciu `isNaN` funkcji.  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Dotyczy**: [obiekt globalny](../../javascript/reference/global-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [isNaN — funkcja](../../javascript/reference/isnan-function-javascript.md)   
 [parseInt — funkcja](../../javascript/reference/parseint-function-javascript.md)   
 [String — obiekt](../../javascript/reference/string-object-javascript.md)