---
title: "Number — stałe (JavaScript) | Dokumentacja firmy Microsoft"
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
- POSITIVE_INFINITY constant [JavaScript]
- MAX_VALUE constant [JavaScript]
- MIN_VALUE constant [JavaScript]
- number constants [JavaScript]
- Number.NEGATIVE_INFINITY constant [JavaScript]
- Number.POSITIVE_INFINITY constant [JavaScript]
- NEGATIVE_INFINITY constant [JavaScript]
- NaN constant [JavaScript]
- Number.MIN_VALUE constant [JavaScript]
- constants [JavaScript], number
- Number.NaN constant [JavaScript]
- Number.MAX_VALUE constant [JavaScript]
ms.assetid: e0701b41-99ae-4916-9ec0-f79bb15386fb
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f846ef7cbd9609f7913d6305e48cb4942476ca21
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="number-constants-javascript"></a>Number — Stałe (JavaScript)
Następujące number — stałe są właściwościami `Number` obiektu.  
  
## <a name="number-object-constants"></a>Number — stałe obiektu  
 Nie trzeba tworzyć `Number` obiekt, aby dostęp do tych stałych.  
  
|Stała|Wartość zwracana|  
|--------------|--------------------|  
|`Number.EPSILON`|Najmniejsza liczba, która ma być reprezentowane w [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]. Równa około 2.2204460492503130808472633361816E-16.|  
|`Number.MAX_SAFE_INTEGER`|Największa liczba, która może być bezpiecznie reprezentowany w języku JavaScript. Taki sam jak 9007199254740991.|  
|`Number.MAX_VALUE`|Największa liczba, która ma być reprezentowane w [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]. Równa około 1.79E + 308.|  
|`Number.MIN_SAFE_INTEGER`|Najmniejsza liczba może być bezpiecznie reprezentowany w języku JavaScript. Taki sam jak-9007199254740991.|  
|`Number.MIN_VALUE`|Najbliższej liczby na zero, który ma być reprezentowane w [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]. Równa około 5.00E-324.|  
|`Number.NaN`|Wartość, która nie jest liczbą.<br /><br /> W porównywanie równości `NaN` nie ma żadnej wartości, wraz z tym elementem. Aby sprawdzić, czy wartość jest odpowiednikiem `NaN`, użyj [isNaN — funkcja](../../javascript/reference/isnan-function-javascript.md).|  
|`Number.NEGATIVE_INFINITY`|Wartość, która jest mniejsza niż największa liczba ujemna, który może być reprezentowany w [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].<br /><br /> [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]Wyświetla `NEGATIVE_INFINITY` wartości jako `-infinity`.|  
|`Number.POSITIVE_INFINITY`|Wartość większą niż największa liczba, która ma być reprezentowane w [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].<br /><br /> [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]Wyświetla `POSITIVE_INFINITY` wartości jako `infinity`.|  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
 Aby uzyskać `Number.EPSILON`, `Number.MAX_SAFE_INTEGER`, i `Number.MIN_SAFE_INTEGER`:  
  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **Dotyczy**: [numer obiektu](../../javascript/reference/number-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Stałe matematyczne](../../javascript/reference/math-constants-javascript.md)   
 [JavaScript — stałe](../../javascript/reference/javascript-constants.md)   
 [Stała infinity](../../javascript/reference/infinity-constant-javascript.md)   
 [NaN — stała](../../javascript/reference/nan-constant-javascript.md)   
 [isNaN — funkcja](../../javascript/reference/isnan-function-javascript.md)