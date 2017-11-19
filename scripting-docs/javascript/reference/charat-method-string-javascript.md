---
title: "charAt — metoda (ciąg) (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: charAt
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- String object, returning characters
- charAt method
- characters, returning part of
ms.assetid: 63173e15-17f6-47c5-8f94-98ef1eb04c1a
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 201d85fec4ba184f0842c7401d986650b9ee078c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="charat-method-string-javascript"></a>charAt — Metoda (ciąg) (JavaScript)
Zwraca znak pod określonym indeksem.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
strObj. charAt(index)  
```  
  
## <a name="parameters"></a>Parametry  
 `strObj`  
 Wymagany. Wszelkie `String` obiektu lub literałem ciągu.  
  
 `index`  
 Wymagany. Liczony od zera indeks żądany znak.  
  
## <a name="remarks"></a>Uwagi  
 `charAt` Metoda zwraca wartość znaku równa znaków w określonym `index`. Pierwszy znak w ciągu znajduje się pod indeksem 0, drugi ma indeks 1 i tak dalej. Wartości typu `index` które są poza zakresem zwracany ciąg pusty.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `charAt` metody:  
  
```JavaScript  
var str = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";  
document.write(str.charAt(str.length - 1));  
  
// Output: Z  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Dotyczy**: [ciągu obiektu](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [String — obiekt](../../javascript/reference/string-object-javascript.md)