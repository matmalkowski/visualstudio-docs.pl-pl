---
title: unescape — funkcja (JavaScript) | Dokumentacja firmy Microsoft
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
- unescape
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Unescape method
ms.assetid: 4adf0270-88b5-4d54-8110-d879d6ae97c2
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 96601fc21f47c86aec8c3702a6861c3676aacacf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791941"
---
# <a name="unescape-function-javascript"></a>unescape — Funkcja (JavaScript)
Dekoduje `String` obiektów zakodowane za pomocą `escape` funkcji. Przestarzałe.  
  
## <a name="syntax"></a>Składnia  
  
```  
unescape(charString)   
```  
  
## <a name="remarks"></a>Uwagi  
 Wymagane `charString` argument jest `String` obiektu lub literału ma być zdekodowany.  
  
 `unescape` Funkcja zwraca wartość ciągu, który zawiera zawartość `charstring`. Wszystkie znaki zakodowane za pomocą %*xx* postaci szesnastkowej są zastępowane przez ich odpowiedniki zestawu znaków ASCII.  
  
 Znaki zakodowane w **%u** *xxxx* formatu (znaki Unicode) są zastępowane znaku Unicode o kodowanie szesnastkowe *xxxx*.  
  
> [!NOTE]
>  `unescape` Nie należy używać funkcji w celu zdekodowania identyfikatory URI (Uniform Resource). Użyj `decodeURI` i `decodeURIComponent` zamiast tego funkcje.  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Dotyczy**: [obiekt globalny](../../javascript/reference/global-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [decodeURI — funkcja](../../javascript/reference/decodeuri-function-javascript.md)   
 [decodeuricomponent — funkcja](../../javascript/reference/decodeuricomponent-function-javascript.md)   
 [Escape — funkcja](../../javascript/reference/escape-function-javascript.md)   
 [String — obiekt](../../javascript/reference/string-object-javascript.md)