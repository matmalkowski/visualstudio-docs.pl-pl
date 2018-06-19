---
title: push — metoda (tablica) (JavaScript) | Dokumentacja firmy Microsoft
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
- push
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Push method
ms.assetid: fa6e5799-dabe-4b3d-bd1f-0afc68c77134
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ddb49f310eaff51fe9e9ba584281fdf07bc2e818
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791344"
---
# <a name="push-method-array-javascript"></a>push — Metoda (Tablica) (JavaScript)
Dołącza nowe elementy do tablicy i zwraca nową długość tablicy.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
arrayObj.push([item1 [item2 [. . . [itemN ]]]])  
```  
  
## <a name="parameters"></a>Parametry  
 `arrayObj`  
 Wymagany. `Array` Obiektu.  
  
 `item, item2,. . ., itemN`  
 Opcjonalny. Nowe elementy `Array`.  
  
## <a name="remarks"></a>Uwagi  
 `push` i `pop` metody umożliwiają symulować ostatnich, najpierw się stosu.  
  
 `push` Metody dołącza elementów w kolejności ich występowania. Jeśli jeden z argumentów jest tablicą, jest dodawana jako pojedynczy element. Użyj `concat` metody do dołączenia elementy z co najmniej dwa tablic.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `push` metody.  
  
```JavaScript  
var number;  
var my_array = new Array();  
  
my_array.push (5, 6, 7);  
my_array.push (8, 9);  
  
number = my_array.pop();  
while (number != undefined)  
   {  
   document.write (number + " ");  
   number = my_array.pop();  
   }  
  
// Output:  
// 9 8 7 6 5  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Metoda concat (tablica)](../../javascript/reference/concat-method-array-javascript.md)   
 [POP — metoda (tablica)](../../javascript/reference/pop-method-array-javascript.md)