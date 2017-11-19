---
title: "indexOf — metoda (ciąg) (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: indexOf
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- indexOf method, string
- string, indexOf method
ms.assetid: a17372fa-669b-471b-9240-46927a265152
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ecd96acb21f9d7711f9ee00dbf1c1bb70705c0d8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="indexof-method-string-javascript"></a>indexOf — Metoda (ciąg) (JavaScript)
Zwraca pozycję pierwszego wystąpienia podciągu.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
strObj. indexOf(subString[, startIndex])  
```  
  
## <a name="parameters"></a>Parametry  
 `strObj`  
 Wymagany. A `String` obiektu lub literałem ciągu.  
  
 `subString`  
 Wymagany. Podciąg, który należy wyszukać w ciągu  
  
 `startIndex`  
 Opcjonalny. Indeks, w którym należy rozpocząć wyszukiwanie `String` obiektu. W przypadku pominięcia, wyszukiwanie rozpoczyna się na początku ciągu znaków.  
  
## <a name="remarks"></a>Uwagi  
 **IndexOf** metoda zwróci wartość początku podciągu w `String` obiektu. Jeśli nie zostanie znaleziony podciąg, zwracana jest wartość -1.  
  
 Jeśli `startindex` jest ujemna, `startindex` jest traktowany jako zero. Jeśli jest większy niż najwyższy indeks, jest traktowany jako najwyższy indeks.  
  
 Wyszukiwanie jest wykonywane od lewej do prawej. W przeciwnym razie ta metoda jest taki sam jak **lastIndexOf**.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie **indexOf** metody.  
  
```JavaScript  
var str = "original equipment manufacturer";  
  
var s = "equip is at position " + str.indexOf("equip");  
s += "<br />";  
s += "abc is at position " + str.indexOf("abc");  
  
document.write(s);  
  
// Output:  
// equip is at position 9  
// abc is at position -1  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Dotyczy**: [ciągu obiektu](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [lastIndexOf — metoda (ciąg)](../../javascript/reference/lastindexof-method-string-javascript.md)   
 [Przewijanie, przesuwać i powiększać przykładowej aplikacji](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)