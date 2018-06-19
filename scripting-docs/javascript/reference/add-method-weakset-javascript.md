---
title: Dodaj metodę (WeakSet) (JavaScript) | Dokumentacja firmy Microsoft
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
ms.assetid: d35d0287-6b33-4720-b9d7-8954c428ce4e
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3ab486beaba4a26c73930b5ceaee927f73aa077a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24788665"
---
# <a name="add-method-weakset-javascript"></a>add (WeakSet) — metoda (JavaScript)
Dodaje nowy element `WeakSet`.  
  
## <a name="syntax"></a>Składnia  
  
```JavaScript  
weaksetObj.add(obj)  
```  
  
#### <a name="parameters"></a>Parametry  
 `weaksetObj`  
 Wymagany. A `WeakSet` obiektu.  
  
 `obj`  
 Wymagany. Nowy element `WeakSet`.  
  
## <a name="remarks"></a>Uwagi  
 Nowy element musi być obiektem, a nie dowolną wartość, a musi być unikatowa. Jeśli użytkownik dodany element nie jest unikatowa `WeakSet`, nie zostanie dodany nowy element do kolekcji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób dodawania członków do zestawu i sprawdź, czy zostały one dodane.  
  
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