---
title: splice — metoda (tablica) (JavaScript) | Dokumentacja firmy Microsoft
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
- splice
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- splice method
ms.assetid: 85fdfb13-e3d9-4c89-b524-3ccee7001c93
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0d56a22244f76f5ce7221c276629907811733d51
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791377"
---
# <a name="splice-method-array-javascript"></a>splice — Metoda (Tablica) (JavaScript)
Usuwa z tablicy elementy i jeśli to konieczne, wstawia w ich miejsce nowe elementy, zwracając elementy usunięte.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
arrayObj.splice(start, deleteCount, [item1[, item2[, . . . [,itemN]]]])  
```  
  
## <a name="parameters"></a>Parametry  
 `arrayObj`  
 Wymagany. `Array` Obiektu.  
  
 `start`  
 Wymagany. Liczony od zera lokalizacja w tablicy, w którym należy rozpocząć usuwanie elementów.  
  
 `deleteCount`  
 Wymagany. Liczba elementów do usunięcia.  
  
 `item1, item2,. . ., itemN`  
 Opcjonalny. Elementy można wstawić do tablicy zamiast usuniętych elementów.  
  
## <a name="remarks"></a>Uwagi  
 `splice` Metoda modyfikuje `arrayObj` przez usunięcie określoną liczbę elementów od pozycji `start` i wstawianie nowych elementów. Usunięte elementy zostaną zwrócone jako nowy `Array` obiektu.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia sposób użycia `splice` metody.  
  
```JavaScript  
var arr = new Array("4", "11", "2", "10", "3", "1");  
arr.splice(2, 2, "21", "31");  
document.write(arr);  
  
// Output: 4,11,21,31,3,1  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Metoda slice (tablica)](../../javascript/reference/slice-method-array-javascript.md)