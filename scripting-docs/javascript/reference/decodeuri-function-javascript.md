---
title: decodeURI — funkcja (JavaScript) | Dokumentacja firmy Microsoft
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
- decodeURI
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- decodeURI method
ms.assetid: af6c81dc-10f4-4243-a7ce-d18ae3ea0fb8
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 97291142083ae88c7dc84d9cd08af5c3c39ff9e8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24790381"
---
# <a name="decodeuri-function-javascript"></a>decodeURI — Funkcja (JavaScript)
Pobiera wersję niekodowany z zakodowany identyfikator URI (Uniform Resource).  
  
## <a name="syntax"></a>Składnia  
  
```  
decodeURI(URIstring)  
```  
  
## <a name="remarks"></a>Uwagi  
 Wymagane `URIstring` argument ma wartość reprezentującą zakodowany identyfikator URI.  
  
 Użyj `decodeURI` funkcja zamiast przestarzałych `unescape` funkcji.  
  
 `decodeURI` Funkcja zwraca wartość typu ciąg.  
  
 Jeśli `URIString` nie jest prawidłowy, URIError występuje.  
  
 **Dotyczy**: [obiekt globalny](../../javascript/reference/global-object-javascript.md)  
  
## <a name="example"></a>Przykład  
 Poniższy kod najpierw koduje składnika identyfikatora URI i następnie dekoduje go.  
  
```JavaScript  
var uriEncode = encodeURIComponent ("www.Not a URL.com");  
var uriDecode = decodeURIComponent(uriEncode);  
  
document.write (uriEncode);  
document.write ("<br/>");  
document.write (uriDecode);  
  
// Output:  
// www.Not%20a%20URL.com  
// www.Not a URL.com  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [decodeuricomponent — funkcja](../../javascript/reference/decodeuricomponent-function-javascript.md)   
 [encodeURI — funkcja](../../javascript/reference/encodeuri-function-javascript.md)   
 [Obiekt Global](../../javascript/reference/global-object-javascript.md)