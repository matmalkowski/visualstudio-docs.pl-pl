---
title: "Następnie — metoda (Promise) | Dokumentacja firmy Microsoft"
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
ms.assetid: c7f3259d-78f7-4ca7-8bdf-99fbd3f41e8d
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eeb97fae19ca9923280b5099e3e4d8c839fa2815
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="then-method-promise"></a>then (Promise) — metoda 
Umożliwia określenie zadań do wykonania na realizację obietnicę.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
promise.then(onCompleted, onRejected);  
```  
  
#### <a name="parameters"></a>Parametry  
 `promise`  
 Wymagany. Promise — obiekt.  
  
 `onCompleted`  
 Wymagany. Funkcja wypełniania programu obsługi do uruchomienia po pomyślnym zakończeniu promise.  
  
 `onRejected`  
 Opcjonalny. Funkcja obsługi błędu uruchamiany, gdy Obietnica został odrzucony.  
  
## <a name="remarks"></a>Uwagi  
 Obietnicę albo należy wykonać z wartością lub musi zostać odrzucone z powodu. `then` Metody obiektu Promise jest uruchamiany, gdy promise jest ukończona lub odrzucone, cokolwiek nastąpi najpierw. Jeśli Obietnica zakończyło się powodzeniem, realizacja funkcji obsługi `then` uruchamia metody. Odrzucony Obietnica funkcji obsługi błędu `then` — metoda (lub `catch` metody) uruchamia.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób wywołania funkcji (`timeout`) zwracająca obietnicę. Program obsługi realizacji `then` metoda jest uruchamiana po 5000ms upłynie limit czasu.  
  
```JavaScript  
function timeout(duration) {  
    return new Promise(function(resolve, reject) {  
        setTimeout(resolve, duration);  
    });  
}  
  
// Note: This code uses arrow function syntax  
var m = timeout(5000).then(() => {  
    console.log("done!");  
})  
  
// Output (after 5 seconds):  
// done!  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Promise — obiekt](../../javascript/reference/promise-object-javascript.md)