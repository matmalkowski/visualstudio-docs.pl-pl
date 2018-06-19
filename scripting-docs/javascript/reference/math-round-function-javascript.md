---
title: Math.round — funkcja (JavaScript) | Dokumentacja firmy Microsoft
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
- round
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Round method
- Math object
ms.assetid: 51008df3-5d0c-4951-84cb-4f41000db0be
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9543d529e3d0e4e45cff29f1286edbfad8dc0e27
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791266"
---
# <a name="mathround-function-javascript"></a>Math.round — Funkcja (JavaScript)
Zwraca wartość wyrażenia liczbowego dostarczony zaokrąglona do najbliższej liczby całkowitej.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
Math.round(  
number  
)   
```  
  
## <a name="remarks"></a>Uwagi  
 Wymagane `number` argument ma wartość, która ma zostać zaokrąglona do najbliższej liczby całkowitej.  
  
 Dla liczby dodatnie Jeśli część `number` 0,5 lub większą, zwracana wartość jest równa najmniejszą liczbę całkowitą większą niż `number`. Jeśli dziesiętny jest mniejsza niż 0,5, wartość zwracana jest największa liczba całkowita mniejsza lub równa `number`.  
  
 Dla wartości ujemne, jeśli dziesiętny jest dokładnie -0,5, wartość zwracana jest najmniejsza liczba całkowita, która jest większa niż liczba.  
  
 Na przykład `Math.round(8.5)` zwraca 9, ale `Math.round(-8.5)` zwraca -8.  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Dotyczy**: [Math — obiekt](../../javascript/reference/math-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Math.Random — funkcja](../../javascript/reference/math-random-function-javascript.md)