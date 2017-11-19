---
title: Number.isNaN (Number) (JavaScript) funkcja | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 2d9813d6-ec9c-433b-b060-8e3c3ff62ca4
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7c11abe2dd2fc70431800d31f4c44279a88cd75d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="numberisnan-function-number-javascript"></a>Number.isNaN (Number) — funkcja (JavaScript)
Zwraca wartość logiczną wskazującą, czy wartość jest wartością zarezerwowanej wartości `NaN` (nie liczba).  
  
## <a name="syntax"></a>Składnia  
  
```  
Number.isNaN(numValue)   
```  
  
#### <a name="parameters"></a>Parametry  
 `numValue`  
 Wymagany. Wartość do sprawdzenia przed `NaN`.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli można przekonwertować daną wartość `Number` jest typu `NaN`, w przeciwnym razie `false`.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda używane zwykle do testowania wartości zwracanych z `parseInt` i `parseFloat` metody.  
  
 `Number.isNaN`rozwiązuje problemy z globalnej `isNaN` funkcji. `Number.isNaN`tylko konwertuje jej argument na typ Number po należy go porównać z `NaN`. W związku z tym zwraca `true` tylko wtedy, gdy przekazany argument jest dokładnie taką samą wartość jak `NaN`. Globalny `isNaN` funkcja konwertuje jej argument typu Liczba przed porównania, co może prowadzić do zwracania wartości innych niż liczba `true`, podczas gdy mogą nie zwracać `true` dla `Number.isNaN`.  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **Dotyczy**: [numer obiektu](../../javascript/reference/number-object-javascript.md)  
  
## <a name="example"></a>Przykład  
  
```JavaScript  
// Returns true.  
Number.isNaN(NaN);  
Number.isNaN(Number.NaN);  
Number.isNaN(0 / 0);  
  
// Returns false.  
Number.isNaN(100);  
// Returns false.  
// Strings are converted to numbers and return false.  
Number.isNaN("100");  
Number.isNaN("ABC");  
Number.isNaN("10C");  
Number.isNaN("abc123");  
  
```