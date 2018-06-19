---
title: codepointat — metoda (ciąg) (JavaScript) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 7979018f-1be3-4a13-9e8f-c84c7ed35288
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0dd5ef17db177dfb1d532bfb88d1d0d77cdb7304
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24788938"
---
# <a name="codepointat-method-string-javascript"></a>codePointAt (String) — metoda (JavaScript)
Zwraca punkt kodu znaku Unicode UTF-16.  
  
## <a name="syntax"></a>Składnia  
  
```  
stringObj.codePointAt(pos);  
```  
  
#### <a name="parameters"></a>Parametry  
 `stringObj`  
 Wymagany. Z obiektem ciągu.  
  
 `pos`  
 Wymagany. Pozycja znaku.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zwraca wartości punktu kodu, w tym punktów kodowych błyszczące (punkty kodu z więcej niż cztery wartości szesnastkowe), wszystkie znaki UTF-16.  
  
 Jeśli `pos` jest mniejsza niż zero (0) lub większy niż rozmiar ciągu jest wartością zwracaną `undefined`.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `codePointAt` metody.  
  
```JavaScript  
var cp1 = "𠮷".codePointAt(0);  
var cp2 = 'abc'.codePointAt(1);  
  
if(console && console.log) {  
    console.log(cp1);  
    console.log(cp2);}  
  
// Output:  
// 0x20BB7  
// 98   
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]
