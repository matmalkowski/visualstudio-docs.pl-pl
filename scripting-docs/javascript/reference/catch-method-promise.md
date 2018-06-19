---
title: CATCH — metoda (Promise) | Dokumentacja firmy Microsoft
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
ms.assetid: 55266f6a-db4d-4de8-857a-8bc7d35ed4b8
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 307e5b2a501b038542a602df4538523a3fc6eccd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24789070"
---
# <a name="catch-method-promise"></a>catch (Promise) — metoda
Umożliwia określenie zadań do wykonania na odrzucenie obietnicę.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
promise.catch(onRejected)  
```  
  
#### <a name="parameters"></a>Parametry  
 `promise`  
 Wymagany. Promise — obiekt.  
  
 `onRejected`  
 Wymagany. Funkcja obsługi błędu uruchamiany, gdy obietnicę został odrzucony.  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie kodu w pierwszym wywołaniu limitu czasu zwraca po 5000ms. W tym kodzie Obietnica zostanie odrzucone i uruchomieniu funkcji obsługi błędów.  
  
```JavaScript  
function timeout(duration) {  
    return new Promise(function(resolve, reject) {  
        setTimeout(reject, duration);  
    });  
}  
  
var p = timeout(5000).then(() => {  
    console.log("done!");  
}).catch(err => {  
    console.log("error!");  
})  
  
// Output (after five seconds):  
// error!  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]