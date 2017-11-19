---
title: "forEach — metoda (Set) (JavaScript) | Dokumentacja firmy Microsoft"
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
ms.assetid: 813bff6e-6098-4260-ab6e-b0d2da6be94d
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b89c56b54fd74c25c43a84f2f0fd68922aa9f637
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="foreach-method-set-javascript"></a>forEach — Metoda (Set) (JavaScript)
Wykonuje określoną akcję dla każdego elementu w zestawie.  
  
## <a name="syntax"></a>Składnia  
  
```JavaScript  
setObj.forEach(callbackfn[, thisArg])  
```  
  
#### <a name="parameters"></a>Parametry  
 `setObj`  
 Wymagany. A `Set` obiektu.  
  
 `callbackfn`  
 Wymagany. `callbackfn`akceptuje maksymalnie trzech argumentów. Funkcja który `forEach` wywołuje jeden raz dla każdego elementu w zestawie.  
  
 `thisArg`  
 Opcjonalny. Obiekt który `this` — słowo kluczowe może odwoływać się do w `callbackfn` funkcji. Jeśli `thisArg` zostanie pominięty, `undefined` jest używany jako `this` wartość.  
  
## <a name="exceptions"></a>Wyjątki  
 Jeśli `callbackfn` argument nie jest obiektem funkcji `TypeError` wyjątku.  
  
## <a name="remarks"></a>Uwagi  
 Składnia funkcji wywołania zwrotnego jest następująca:  
  
 `function callbackfn(value, key, setObj)`  
  
 Funkcja wywołania zwrotnego można zadeklarować przy użyciu maksymalnie trzech parametrów, jak pokazano w poniższej tabeli.  
  
|Argument wywołania zwrotnego|Definicja|  
|-----------------------|----------------|  
|`value`|Wartość zawartych w zestawie.|  
|`key`|Wartość zawartych w zestawie. Zestaw nie ma kluczy, dlatego ta wartość jest taka sama jak `value`.|  
|`setObj`|`Set` Obiekt, aby przechodzić między nimi.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `forEach`. `callbackfn` Argument zawiera kod dla funkcji wywołania zwrotnego.  
  
```JavaScript  
var s = new Set();  
  
s.add("scale");  
s.add(10);  
s.add("5");  
  
s.forEach(function(item, sameItem, s) {  
    document.write("Size of the set object is: " + s.size + "<br />");  
    document.write("Deleting item: " + item + "<br />");  
    s.delete(sameItem);  
});  
  
// Output:  
// Size of the set object is: 3  
// Deleting item: scale  
// Size of the set object is: 2  
// Deleting item: 10  
// Size of the set object is: 1  
// Deleting item: 5  
```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, że można również pobierać elementy członkowskie zestawu przekazując tylko jeden parametr do funkcji wywołania zwrotnego.  
  
```JavaScript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
s.add("founding father");  
  
s.forEach(function (item) {  
    document.write(item.toString() + ", ");  
});  
  
// Output:  
// Thomas Jefferson, 1776, founding father,  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]