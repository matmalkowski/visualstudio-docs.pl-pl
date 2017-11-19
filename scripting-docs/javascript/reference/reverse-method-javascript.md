---
title: "reverse — metoda (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: reverse
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- arrays [Visual Studio], reversing elements
- reverse method
- transposing elements
ms.assetid: 02ab051b-79b8-4646-b502-381671e78c12
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9a34385ccf89557688698b50384b3dfe359478df
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="reverse-method-javascript"></a>reverse — Metoda (JavaScript)
Odwraca elementów w `Array`.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
arrayObj.reverse()   
```  
  
## <a name="parameters"></a>Parametry  
 `arrayObj`  
 Wymagany. Wszelkie `Array` obiektu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Tablica odwróconej.  
  
## <a name="remarks"></a>Uwagi  
 Wymagane `arrayObj` odwołanie jest `Array` obiektu.  
  
 `reverse` Metody odwraca elementy `Array` obiektu w miejscu. Nie tworzy nową `Array` obiektu podczas wykonywania.  
  
 Jeśli tablica nie jest ciągły, `reverse` metoda tworzy elementów w tablicy, która wypełniania luk w tablicy. Każdy z tych utworzonych elementów ma wartość `undefined`.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `reverse` metody.  
  
```JavaScript  
var arr = new Array(0,1,2,3,4);   
var reverseArr = arr.reverse();  
document.write(reverseArr);  
  
// Output:  
// 4,3,2,1,0  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Metoda concat (tablica)](../../javascript/reference/concat-method-array-javascript.md)