---
title: Object.Assign (Object) (JavaScript) funkcja | Dokumentacja firmy Microsoft
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
ms.assetid: 2dd6b312-dcd3-414e-8d53-088c6341c46d
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c156369299e58eac556d43a87476de2ce09173e1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791155"
---
# <a name="objectassign-function-object-javascript"></a>Object.assign (Object) — funkcja (JavaScript)
Kopiuje wartości z jednego lub większej liczby obiektów źródła do obiektu docelowego.  
  
## <a name="syntax"></a>Składnia  
  
```  
Object.assign(target, ...sources );  
```  
  
#### <a name="parameters"></a>Parametry  
 `target`  
 Wymagany. Obiekt, do której są kopiowane wyliczalny właściwości.  
  
 `...sources`  
 Wymagany. Co najmniej jeden obiekt, z których wyliczalny właściwości są kopiowane.  
  
## <a name="exceptions"></a>Wyjątki  
 Ta funkcja zwraca `TypeError` Jeśli błąd przypisania, która kończy operację kopiowania. A `TypeError` zostanie wygenerowany, jeśli właściwość docelowa nie jest zapisywalny.  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja zwraca obiekt docelowy. Tylko *wyliczalny własnych* właściwości są kopiowane z obiektu źródłowego do obiektu docelowego. Ta funkcja służy do scalenia lub sklonować obiektów.  
  
 `null`lub `undefined` źródeł, są traktowane jak pusty obiektów i brać udział nic do obiektu docelowego.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje sposób scalania obiektów przy użyciu `Object.assign`.  
  
```JavaScript  
var first = { name: "Bob" };  
var last = { lastName: "Smith" };  
  
var person = Object.assign(first, last);  
console.log(person);  
  
// Output:  
// { name: "Bob", lastName: "Smith" }   
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób klonowania obiekt przy użyciu `Object.assign`.  
  
```JavaScript  
var obj = { person: "Bob Smith"};  
var clone = Object.assign({}, obj);  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]