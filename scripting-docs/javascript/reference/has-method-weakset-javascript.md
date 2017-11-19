---
title: "has — metoda (WeakSet) (JavaScript) | Dokumentacja firmy Microsoft"
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
ms.assetid: e24f0876-26bd-4007-b12a-360bb6fa0951
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0dbc7e17e3fd73730386293c5e3f894455e41a93
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="has-method-weakset-javascript"></a>has (WeakSet) — metoda (JavaScript)
Zwraca `true` Jeśli `WeakSet` zawiera określony element.  
  
## <a name="syntax"></a>Składnia  
  
```JavaScript  
setObj.has(obj)  
```  
  
#### <a name="parameters"></a>Parametry  
 `setObj`  
 Wymagany. A `WeakSet` obiektu.  
  
 `obj`  
 Wymagany. Element do testu.  
  
## <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość  
 `true`Jeśli zestaw zawiera określony element.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób dodawania elementów członkowskich do `WeakSet` , a następnie sprawdź, czy zestaw zawiera określonego elementu członkowskiego.  
  
```JavaScript  
var ws = new WeakSet();  
  
var str = new String("Thomas Jefferson");  
var num = new Number(1776);  
  
ws.add(str);  
ws.add(num);  
  
console.log(ws.has(str));  
console.log(ws.has(num));  
  
ws.delete(str);  
console.log(ws.has(str));  
  
// Output:  
// true  
// true  
// false  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]