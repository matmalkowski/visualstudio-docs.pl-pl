---
title: "substring — metoda (ciąg) (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: substring
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- substrings
- substring method
ms.assetid: 9cf9a005-cbe3-42fd-828b-57a39f54224c
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 15ebaadc7b24fa97f531a22f6deb1453ff52b3e7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="substring-method-string-javascript"></a>substring — Metoda (Ciąg) (JavaScript)
Zwraca podciąg w określonej lokalizacji w ramach `String` obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      strVariable. substring(start [, end])  
"String Literal".substring(start [, end])   
```  
  
## <a name="parameters"></a>Parametry  
 `start`  
 Wymagany. Liczony od zera indeks liczba całkowita wskazująca na początku podciąg.  
  
 `end`  
 Opcjonalny. Liczba całkowita liczony od zera indeks, co oznacza koniec podciąg. Podciąg do zawiera znaki, ale bez tego znaku wskazywanym przez `end`.  
  
 Jeśli `end` zostanie pominięty, znaki z `start` do końca oryginalnego ciągu są zwracane.  
  
## <a name="remarks"></a>Uwagi  
 `substring` Metoda zwraca ciąg zawierający podciąg `start` do, z wyłączeniem `end`.  
  
 **Podciąg** metoda używa niższe wartości `start` i `end` jako punkt początkowy podciągu. Na przykład strvar.substring (0, 3**)** i tego samego podciąg zwracać strvar.substring (3, 0).  
  
 Jeśli dowolny `start` lub `end` jest `NaN` lub ujemne, zostanie zastąpiony wartością zero.  
  
 Długość podciąg jest wartość bezwzględna różnicy między `start` i `end`. Na przykład długość podciąg zwracane w strvar.substring (0, 3) i strvar.substring (3, 0) jest trzy.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie **podciąg** metody.  
  
```JavaScript  
var s = "The quick brown fox jumps over the lazy dog.";  
var ss = s.substring(10, 15);  
document.write(ss);  
  
// Output:  
// brown  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [substr — metoda (ciąg)](../../javascript/reference/substr-method-string-javascript.md)