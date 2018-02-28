---
title: "parseInt — funkcja (JavaScript) | Dokumentacja firmy Microsoft"
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
- parseInt
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- parseInt method
ms.assetid: e86471af-2a0e-4359-83af-f1ac81e51421
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 54ee77470d32410ae46a628d54fc3bda97fecc51
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="parseint-function-javascript"></a>parseInt — Funkcja (JavaScript)
Konwertuje ciąg na liczbę całkowitą.  
  
## <a name="syntax"></a>Składnia  
  
```  
parseInt(numString, [radix])   
```  
  
## <a name="parameters"></a>Parametry  
 `numString`  
 Wymagany. Ciąg do przekonwertowania na liczbę.  
  
 `radix`  
 Opcjonalny. Wartość z zakresu od 2 do 36 określający base numeru w `numString`. Jeśli ten argument nie zostanie podany, ciągi z prefiksem '0 x' są traktowane jako szesnastkowe. Wszystkie inne ciągi są traktowane jako dziesiętne.  
  
## <a name="remarks"></a>Uwagi  
 `parseInt` Funkcja zwraca wartość całkowitą równą wartości zawartych w `numString`. Jeśli nie ma prefiksu z `numString` może pomyślnie przeanalizowano całkowitą, `NaN` (nie liczba) jest zwracany.  
  
```JavaScript  
parseInt("abc");     // Returns NaN.  
parseInt("12abc");   // Returns 12.  
```  
  
 Można sprawdzić `NaN` przy użyciu `isNaN` funkcji.  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Dotyczy**: [obiekt globalny](../../javascript/reference/global-object-javascript.md)  
  
> [!NOTE]
>  Począwszy od [!INCLUDE[jsv9textspecific](../../javascript/reference/includes/jsv9textspecific-md.md)], `parseInt` funkcja nie traktuje ciąg, który zawiera prefiks "0", jako ósemkowe. Jeśli nie używasz `parseInt` działać, jednak ciągów z prefiksem "0" nadal mogą być interpretowane jako octals. Zobacz [typy danych](../../javascript/data-types-javascript.md) informacji o ósemkową liczby całkowite.  
  
## <a name="see-also"></a>Zobacz też  
 [isNaN — funkcja](../../javascript/reference/isnan-function-javascript.md)   
 [parsefloat — funkcja](../../javascript/reference/parsefloat-function-javascript.md)   
 [String — obiekt](../../javascript/reference/string-object-javascript.md)   
 [valueOf — metoda (obiekt)](../../javascript/reference/valueof-method-object-javascript.md)