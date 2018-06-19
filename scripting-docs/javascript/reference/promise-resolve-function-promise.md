---
title: Funkcja Promise.Resolve (Promise) | Dokumentacja firmy Microsoft
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
ms.assetid: 0fb6bff9-54ab-41be-97d7-04f7e6fe9cff
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6d815c9c23da48c877f7f1d995df8991429375e1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791077"
---
# <a name="promiseresolve-function-promise"></a>Promise.resolve (Promise) — funkcja
Tworzy nowy promise rozwiązany z wyników równą jej argument.  
  
## <a name="syntax"></a>Składnia  
  
```  
Promise.resolve(x)  
```  
  
#### <a name="parameters"></a>Parametry  
 `x`  
 Wymagany. Wartość zwracana z promise ukończone.  
  
## <a name="remarks"></a>Uwagi  
 Realizacja funkcji programu obsługi `then` metody jest uruchamiany, gdy ukończone promise obiekt jest zwracany.  
  
## <a name="example"></a>Przykład  
  
```JavaScript  
var p = Promise.resolve('success');  
p.then(function(result) {  
    console.log(result);  
});  
  
// Output:  
// success  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Promise — obiekt](../../javascript/reference/promise-object-javascript.md)