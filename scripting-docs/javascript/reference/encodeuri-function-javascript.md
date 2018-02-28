---
title: "encodeURI — funkcja (JavaScript) | Dokumentacja firmy Microsoft"
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
- encodeURI
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- encodeURI method
ms.assetid: 17bab5a2-bcd4-46c2-8b52-b2b5a0ed98a3
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8cf9bbdf34c0481c889d1176bc32ab0246a333a4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="encodeuri-function-javascript"></a>encodeURI — Funkcja (JavaScript)
Koduje ciąg tekstowy jako prawidłowy zasób identyfikator URI (Uniform)  
  
## <a name="syntax"></a>Składnia  
  
```  
  
encodeURI(  
URIString  
)  
  
```  
  
## <a name="remarks"></a>Uwagi  
 Wymagane `URIString` argument ma wartość reprezentującą zakodowany identyfikator URI.  
  
 `encodeURI` Funkcja zwraca zakodowany identyfikator URI. W przypadku przekazania wyników do `decodeURI`, zwracany jest oryginalny ciąg. `encodeURI` Funkcja nie przeprowadza kodowania następujących znaków: ":", "/", ";" i "?". Użyj `encodeURIComponent` do kodowania tych znaków.  
  
## <a name="example"></a>Przykład  
 Poniższy kod najpierw koduje i następnie dekoduje identyfikatora URI.  
  
```JavaScript  
var uriEncode = encodeURI ("http://www.Not a URL.com");  
var uriDecode = decodeURIComponent(uriEncode);  
  
document.write(uriEncode);  
document.write("<br/>");  
document.write(uriDecode);  
  
// Output:  
// http://www.Not%20a%20URL.com  
// http://www.Not a URL.com  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [decodeURI — funkcja](../../javascript/reference/decodeuri-function-javascript.md)   
 [decodeuricomponent — funkcja](../../javascript/reference/decodeuricomponent-function-javascript.md)