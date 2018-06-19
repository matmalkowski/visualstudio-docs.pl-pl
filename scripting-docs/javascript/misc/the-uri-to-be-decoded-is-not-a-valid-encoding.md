---
title: Identyfikator URI, który ma być zdekodowany jest nie prawidłowym kodowaniem | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5025
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 029e0790-ffd1-496d-8700-3b3dbac1b6fd
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2d37ca55dfd701aaeba2af729511a5ae6a4fa5f4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24788842"
---
# <a name="the-uri-to-be-decoded-is-not-a-valid-encoding"></a>Identyfikator URI, który ma być zdekodowany, nie jest poprawnie zakodowany
Próbowano dekodowania nieprawidłowo sformułowanego identyfikatora URI (Uniform Resource Identifier). Identyfikatory URI mają specjalne składnię; musi być zakodowany znaki inne niż alfanumeryczne, przed ich użyciem w identyfikatorze URI. Można użyć `encodeURI` i `encodeURIComponent` metody służące do utworzenia identyfikatora URI z zwykłym [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] ciągu.  
  
 Pełny identyfikator URI składa się z sekwencji składników i separatorów. Ogólny kształt jest:  
  
```JavaScript  
<Scheme>:<first>/<second>;<third>?<fourth>  
```  
  
 Nazwy w nawiasach ostrych reprezentują składników i ":", "/", ";" i "?" są zastrzeżone znaki używane jako separatorów.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Upewnij się, że próby dekodowania tylko prawidłowymi identyfikatorami URI. Nie można zdekodować normalne [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] ciągów, jak mogą zawierać nieprawidłowych znaków.  
  
## <a name="see-also"></a>Zobacz też  
 [decodeURI — funkcja](../../javascript/reference/decodeuri-function-javascript.md)   
 [decodeuricomponent — funkcja](../../javascript/reference/decodeuricomponent-function-javascript.md)