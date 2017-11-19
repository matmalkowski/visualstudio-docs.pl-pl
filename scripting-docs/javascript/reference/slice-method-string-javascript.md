---
title: "Metoda slice (ciąg) (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: slice
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- strings [Visual Studio], returning characters
- slice method
ms.assetid: 80cd77a6-3718-492e-8e96-f909d8721d91
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1baa0a05a2d6aa8c06cc962761c8e557632d034c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="slice-method-string-javascript"></a>slice — Metoda (Ciąg) (JavaScript)
Zwraca część ciągu.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
stringObj.slice(start, [end])   
```  
  
## <a name="parameters"></a>Parametry  
 `stringObj`  
 Wymagany. A `String` obiektu lub literałem ciągu.  
  
 `start`  
 Wymagany. Indeks na początku określoną część `stringObj`.  
  
 `end`  
 Opcjonalny. Indeksu do końca określoną część `stringObj`. Podciąg do zawiera znaki, ale bez tego znaku wskazywanym przez `end`. Jeśli ta wartość nie jest określona, podciąg będzie nadal występować na końcu `stringObj`.  
  
## <a name="remarks"></a>Uwagi  
 `slice` Metoda zwraca `String` obiekt zawierający określoną część `stringObj`.  
  
 `slice` Metoda kopiuje do, ale bez znaku wskazywanym przez `end`.  
  
 Jeśli `start` jest ujemna, będzie traktowane jako *długość*  +  `start` gdzie *długość* jest długość ciągu. Jeśli `end` jest ujemna, będzie traktowane jako *długość* + `end`. Jeśli `end` jest pominięty, kopiowanie trwa do końca `stringObj`. Jeśli `end` występuje przed `start`, żadne znaki nie są kopiowane do nowych parametrów.  
  
## <a name="example"></a>Przykład  
 W pierwszym przykładzie `slice` metoda zwraca cały ciąg. W drugim przykładzie `slice` metoda zwraca cały ciąg, z wyjątkiem ostatniego znaku.  
  
```JavaScript  
var str1 = "all good boys do fine";  
  
var slice1 = str1.slice(0);  
var slice2 = str1.slice(0,-1);  
var slice3 = str1.slice(4);  
var slice4 = str1.slice(4, 8);  
  
document.write(slice1 + "<br/>");  
document.write(slice2 + "<br/>");  
document.write(slice3 + "<br/>");  
document.write(slice4);  
  
// Output:  
// all good boys do fine  
// all good boys do fin  
// good boys do fine  
// good  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Dotyczy**: [ciągu obiektu](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Metoda slice (tablica)](../../javascript/reference/slice-method-array-javascript.md)