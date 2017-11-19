---
title: Funkcja Promise.all (Promise) | Dokumentacja firmy Microsoft
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
ms.assetid: 02a7b90c-96f6-4484-9466-d261efa1b494
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 997a419a990b407ae018f7da39fd75673ea28b6d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="promiseall-function-promise"></a>Promise.all (Promise) — funkcja
Łączy dwa lub więcej ze zobowiązania i zwraca tylko po ukończeniu wszystkich ze zobowiązania określony lub został odrzucony.  
  
## <a name="syntax"></a>Składnia  
  
```  
Promise.all(func1, func2 [,funcN])  
```  
  
#### <a name="parameters"></a>Parametry  
 `func1`  
 Wymagany. Funkcja, która zwraca obietnicę.  
  
 `func2`  
 Wymagany. Funkcja, która zwraca obietnicę.  
  
 `funcN`  
 Opcjonalny. Jeden lub więcej funkcji, które Zwróć obietnicę.  
  
## <a name="remarks"></a>Uwagi  
 Wynik zwracany jest tablica wartości zwracanych przez ukończone ze zobowiązania. Jeśli jeden z połączonych ze zobowiązania został odrzucony, `Promise.all` natychmiast zwraca o przyczynie odrzucone promise (wszystkich innych zwraca wartości zostaną odrzucone).  
  
## <a name="example"></a>Przykład  
 W tym kodzie limitu czasu w pierwszym wywołaniu zwraca po 5000ms. Wywołania programu obsługi zakończenia `Promise.all`, która zwraca tylko wtedy, gdy oba wywołania do czasu zakończenia lub odrzucone.  
  
```JavaScript  
function timeout(duration) {  
    return new Promise(function(resolve, reject) {  
        setTimeout(resolve, duration);  
    });  
}  
  
var p = timeout(5000).then(() => {  
    return Promise.all([timeout(100), timeout(200)]);  
})  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Promise — obiekt](../../javascript/reference/promise-object-javascript.md)