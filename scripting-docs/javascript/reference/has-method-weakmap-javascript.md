---
title: has — metoda (WeakMap) (JavaScript) | Dokumentacja firmy Microsoft
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
ms.assetid: 12bedca1-bde7-413a-a4e2-06c03559044f
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e9a1706a1b96b5273ec280c4cef2be47a3bc6e17
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24790516"
---
# <a name="has-method-weakmap-javascript"></a>has — Metoda (WeakMap) (JavaScript)
Zwraca `true` Jeśli `WeakMap` obiekt zawiera określony element.  
  
## <a name="syntax"></a>Składnia  
  
```JavaScript  
weakmapObj.has(key)  
```  
  
#### <a name="parameters"></a>Parametry  
 `weakmapObj`  
 Wymagany. A `WeakMap` obiektu.  
  
 `key`  
 Wymagany. Klucz elementu do testowania.  
  
## <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość  
 `true`Jeśli `WeakMap` zawiera określony klucz.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak dodać członka do `WeakMap` , a następnie użyj `has` do sprawdzenia, czy jest obecny.  
  
```JavaScript  
var dog = {  
    breed: "yorkie"  
}  
  
var wm = new WeakMap();  
wm.set(dog, "fido");  
  
document.write(wm.has(dog));  
  
// Output:  
// true  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]