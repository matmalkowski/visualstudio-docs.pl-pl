---
title: "lastIndexOf — metoda (ciąg) (JavaScript) | Dokumentacja firmy Microsoft"
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
- lastIndexOf
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- lastIndexOf method, string
- string, lastIndexOf method
ms.assetid: 1ed36ccd-0f0b-4f16-be45-0567207670af
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0fa0f35e970435a4d0296493c20afdeaac128cae
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="lastindexof-method-string-javascript"></a>lastIndexOf — Metoda (ciąg) (JavaScript)
Zwraca ostatnie wystąpienie podciągu w ciągu.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
strObj.lastIndexOf(substring[, startindex])  
```  
  
## <a name="parameters"></a>Parametry  
 `strObj`  
 Wymagany. A `String` obiektu lub literałem ciągu.  
  
 `substring`  
 Wymagany. Podciąg do wyszukania.  
  
 `startindex`  
 Opcjonalny. Indeks, w którym należy rozpocząć wyszukiwanie. Pominięcie wyszukiwanie rozpoczyna się od końca ciągu.  
  
## <a name="remarks"></a>Uwagi  
 **LastIndexOf** metoda zwraca wartość wskazującą na początku substring w `String` obiektu. Jeśli nie zostanie znaleziony podciąg, zwracana jest wartość -1.  
  
 Jeśli `startindex` jest ujemna, `startindex` jest traktowany jako zero. Jeśli jest większy niż największy indeksu pozycji znaku, będzie traktowane jako największa możliwa indeksu.  
  
 Wyszukiwanie jest wykonywane, zaczynając od ostatniego znaku w ciągu. W przeciwnym razie ta metoda jest taki sam jak **indexOf**.  
  
 Poniższy przykład przedstawia użycie **lastIndexOf** metody.  
  
```JavaScript  
var str = "time, time";  
  
var s = "";  
s += "time is at position " + str.lastIndexOf("time");  
s += "<br />";  
s += "abc is at position " + str.lastIndexOf("abc");  
  
document.write(s);  
  
// Output:  
// time is at position 6  
// abc is at position -1  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Dotyczy**: [ciągu obiektu](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [indexOf — metoda (ciąg)](../../javascript/reference/indexof-method-string-javascript.md)