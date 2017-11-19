---
title: "delete — metoda (WeakSet) (JavaScript) | Dokumentacja firmy Microsoft"
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
ms.assetid: 19e93366-7d42-4abf-b7b9-fcf943fa17a3
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 46eeac8ddd0072712c1867bc2a419a4e3255ffd6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="delete-method-weakset-javascript"></a>delete (WeakSet) — metoda (JavaScript)
Usuwa określony element z `WeakSet`.  
  
## <a name="syntax"></a>Składnia  
  
```JavaScript  
weaksetObj.delete(obj)  
```  
  
#### <a name="parameters"></a>Parametry  
 `weaksetObj`  
 Wymagany. A `WeakSet` obiektu.  
  
 `obj`  
 Wymagany. Element do usunięcia.  
  
## <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość  
 `true`Jeśli element został usunięty.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób dodawania i usuwania elementów `WeakSet`.  
  
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