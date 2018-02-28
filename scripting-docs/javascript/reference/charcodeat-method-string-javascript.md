---
title: "charCodeAt — metoda (ciąg) (JavaScript) | Dokumentacja firmy Microsoft"
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
- charCodeAt
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- charCodeAt method
ms.assetid: 5b0290a7-ee4d-4738-a909-c02ef64a2f1a
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8e7b8e62dfd29aa42d9816d0c5e27cc90440751a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="charcodeat-method-string-javascript"></a>charCodeAt — Metoda (ciąg) (JavaScript)
Zwraca wartość Unicode znaku w określonej lokalizacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
strObj. charCodeAt(index)  
```  
  
## <a name="parameters"></a>Parametry  
 `strObj`  
 Wymagany. Wszelkie `String` obiektu lub literałem ciągu.  
  
 `index`  
 Wymagany. Liczony od zera indeks żądany znak. Jeśli w określonym indeksie nie ma żadnych znak `NaN` jest zwracany.  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `charCodeAt` metody.  
  
```JavaScript  
var str = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";   
document.write(str.charCodeAt(str.length - 1));  
  
// Output: 90   
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcja String.fromCharCode](../../javascript/reference/string-fromcharcode-function-javascript.md)