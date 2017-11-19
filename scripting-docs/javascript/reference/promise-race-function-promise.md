---
title: Funkcja Promise.RACE (Promise) | Dokumentacja firmy Microsoft
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
ms.assetid: 9236eced-d313-4d03-8c3e-d89d762b3084
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fedd512f4565009c8429b43b0d9d93de943d13fb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="promiserace-function-promise"></a>Promise.race (Promise) — funkcja
Tworzy nowe obietnicę, które zostaną rozwiązania lub Odrzuć o tej samej wartości wynik jako pierwszy obietnicę w celu rozwiązania lub odrzucić między przekazano argumentów.  
  
## <a name="syntax"></a>Składnia  
  
```  
Promise.race(iterable)  
```  
  
#### <a name="parameters"></a>Parametry  
 `iterable`  
 Wymagany. Co najmniej jeden ze zobowiązania.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli jeden ze zobowiązania w `iterable` jest już w stanie rozwiązane lub odrzucone `Promise.race` zwraca promise rozwiązane lub odrzucone w taki sam sposób w taki sam, jak wartość używana do rozwiązania (lub nie) tego promise wartość wyniku. Jeśli wiele niesie obietnice zwiększenia w `iterable` już rozwiązane lub odrzucone, `Promise.race` zwraca obietnicę rozwiązane w taki sam sposób jak pierwszy Obietnica iterowane. Jeśli nie promise iterable rozwiązuje lub odrzuci Obietnica zwracane z `Promise.race` również nie rozpoznać lub Odrzuć.  
  
## <a name="example"></a>Przykład  
  
```JavaScript  
var p1 = new Promise(function(resolve, reject) {  
    setTimeout(resolve, 0, 'success');  
});  
var p2 = new Promise(function(resolve, reject) { });  
var p2 = new Promise(function(resolve, reject) { });  
  
var race = Promise.race( [p1, p2, p3] );  
race.then(function(result) {  
    console.log(result);  
});  
  
// Output:  
// success  
  
var race = Promise.race( [Promise.reject('failure'),  
    Promise.resolve('success')] );  
race.catch(function(result) {  
    console.log(result);  
});  
  
// Output:  
// failure  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Promise — obiekt](../../javascript/reference/promise-object-javascript.md)