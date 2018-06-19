---
title: decodeuricomponent — funkcja (JavaScript) | Dokumentacja firmy Microsoft
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
- decodeURIComponent
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- decodeURIComponent method
ms.assetid: 486ccee2-afd7-4863-97ce-4adb50cf39c0
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ef7bdcd374a328bad632381d19e9823853d37f01
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24790366"
---
# <a name="decodeuricomponent-function-javascript"></a>decodeURIComponent — Funkcja (JavaScript)
Pobiera wersję niekodowany zakodowanego składnika z zasobów identyfikator URI (Uniform).  
  
## <a name="syntax"></a>Składnia  
  
```  
decodeURIComponent(encodedURIString)  
```  
  
## <a name="remarks"></a>Uwagi  
 Wymagane `encodedURIString` argument ma wartość reprezentującą zakodowanego składnika identyfikatora URI.  
  
 URIComponent jest częścią pełny identyfikator URI.  
  
 Jeśli `encodedURIString` nie jest prawidłowy, URIError występuje.  
  
## <a name="example"></a>Przykład  
 Poniższy kod najpierw koduje i następnie dekoduje identyfikatora URI.  
  
```JavaScript  
var uriEncode = encodeURI ("http://www.Not a URL.com");  
var uriDecode = decodeURIComponent(uriEncode);  
  
document.write (uriEncode);  
document.write("<br/>");  
document.write (uriDecode);  
  
// Output:  
// http://www.Not%20a%20URL.com  
// http://www.Not a URL.com  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [decodeURI — funkcja](../../javascript/reference/decodeuri-function-javascript.md)   
 [encodeURI — funkcja](../../javascript/reference/encodeuri-function-javascript.md)