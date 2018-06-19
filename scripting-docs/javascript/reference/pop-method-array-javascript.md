---
title: POP — metoda (tablica) (JavaScript) | Dokumentacja firmy Microsoft
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
- pop
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Pop method
ms.assetid: 4fae7f98-29f1-4041-ba43-601f2e5145ec
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f7635ddcc1b3d336f5e3de66e62714bd93a06158
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791293"
---
# <a name="pop-method-array-javascript"></a>pop — Metoda (Tablica) (JavaScript)
Usuwa z tablicy ostatni element i zwraca go.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
arrayObj.pop( )  
```  
  
## <a name="remarks"></a>Uwagi  
 [Wypychania](../../javascript/reference/push-method-array-javascript.md) i `pop` metody umożliwiają symulować stosu, w którym korzysta z zasady ostatnich, najpierw LIFO do przechowywania danych.  
  
 Wymagane `arrayObj` odwołanie jest `Array` obiektu.  
  
 Jeśli tablica jest pusta, `undefined` jest zwracany.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `pop` metody.  
  
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
  
// Output: 9 8 7 6 5  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [push — metoda (tablica)](../../javascript/reference/push-method-array-javascript.md)