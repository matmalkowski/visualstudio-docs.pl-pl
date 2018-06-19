---
title: encodeuricomponent — funkcja (JavaScript) | Dokumentacja firmy Microsoft
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
- encodeURIComponent
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- encodeURIComponent method
ms.assetid: 8202bce6-1342-40dc-a5ef-ac6d210a7d15
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 56680e9bcfe1de61d8a1eabd0ff8d2eced01d603
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24790438"
---
# <a name="encodeuricomponent-function-javascript"></a>encodeURIComponent — Funkcja (JavaScript)
Koduje ciąg tekstowy jako nieprawidłowy składnik z zasobów identyfikator URI (Uniform).  
  
## <a name="syntax"></a>Składnia  
  
```  
encodeURIComponent(encodedURIString)  
```  
  
## <a name="remarks"></a>Uwagi  
 Wymagane `encodedURIString` argument ma wartość reprezentującą zakodowanego składnika identyfikatora URI.  
  
 `encodeURIComponent` Funkcja zwraca zakodowany identyfikator URI. W przypadku przekazania wyników do `decodeURIComponent`, zwracany jest oryginalny ciąg. Ponieważ `encodeURIComponent` funkcja koduje znaki, należy zachować ostrożność, jeśli ciąg reprezentuje ścieżkę, takich jak **/folder1/folder2/default.html**. Znaki ukośnika będzie zapisywana i nie jest prawidłowy, jeśli wysyłane jako żądania do serwera sieci web. Użyj `encodeURI` działać, jeśli ciąg zawiera więcej niż jeden składnik identyfikatora URI.  
  
## <a name="example"></a>Przykład  
 Poniższy kod najpierw koduje składnika identyfikatora URI i następnie dekoduje go.  
  
```JavaScript  
var uriEncode = encodeURIComponent ("www.Not a URL.com");  
var uriDecode = decodeURIComponent(uriEncode);  
  
document.write(uriEncode);  
document.write("<br/>");  
document.write(uriDecode);  
  
// Output:  
// www.Not%20a%20URL.com  
// www.Not a URL.com  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [decodeURI — funkcja](../../javascript/reference/decodeuri-function-javascript.md)   
 [decodeuricomponent — funkcja](../../javascript/reference/decodeuricomponent-function-javascript.md)