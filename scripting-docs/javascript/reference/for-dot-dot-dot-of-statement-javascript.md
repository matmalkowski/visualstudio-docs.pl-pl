---
title: for... instrukcji (JavaScript) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 7872b0b2-5701-4d72-9b52-ed13991542cc
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2373d319347f927304c32cb47856405a1d69a6b2
ms.sourcegitcommit: b400528a83bea06d208d95c77282631ae4a93091
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2018
---
# <a name="forof-statement-javascript"></a>for...of — instrukcja (JavaScript)
Wykonuje jedną lub więcej instrukcji dla każdej wartości uzyskanych z obiektu iterable iteratora.  
  
## <a name="syntax"></a>Składnia  
  
```  
for (variable of object) {  
    statements   
}  
```  
  
## <a name="parameters"></a>Parametry  
 `variable`  
 Wymagana. Zmienna, która może być dowolną wartością właściwości `object`.  
  
 `object`  
 Wymagana. Obiekt iterable, takich jak `Array`, `Map`, `Set`, lub obiekt, który implementuje [interfejsy iteratora](../../javascript/advanced/iterators-and-generators-javascript.md).  
  
 `statements`  
 Opcjonalna. Co najmniej jeden instrukcje do wykonania dla każdej wartości `object`. Może być złożonej instrukcji.  
  
## <a name="remarks"></a>Uwagi  
 Na początku każdej iteracji pętli, wartość `variable` jest dalej wartość właściwości `object`.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `for...of` instrukcją w tablicy.  
  
```JavaScript  
let arr = [ "fred", "tom", "bob" ];  
  
for (let i of arr) {  
    console.log(i);  
}  
  
// Output:  
// fred  
// tom  
// bob  
  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `for...of` instrukcji na `Map` obiektu.  
  
```JavaScript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
  
for (var n of m) {  
  console.log(n);  
}  
  
// Output:  
// 1,black  
// 2,red  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [for... w instrukcji](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [for — instrukcja](../../javascript/reference/for-statement-javascript.md)   
 [while, instrukcja](../../javascript/reference/while-statement-javascript.md)