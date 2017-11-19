---
title: "forEach — metoda (Map) (JavaScript) | Dokumentacja firmy Microsoft"
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
ms.assetid: 9cdf0adc-77c7-4407-8ba7-ada0fb09e507
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8d0ffa12b9a1995df14f4868872238cdc45b674a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="foreach-method-map-javascript"></a>forEach — Metoda (Map) (JavaScript)
Wykonuje określoną akcję dla każdego elementu na mapie.  
  
## <a name="syntax"></a>Składnia  
  
```JavaScript  
mapObj.forEach(callbackfn[, thisArg])  
```  
  
#### <a name="parameters"></a>Parametry  
 `mapObj`  
 Wymagany. A `Map` obiektu.  
  
 `callbackfn`  
 Wymagany. Funkcja który `forEach` wywołuje jeden raz dla każdego elementu na mapie. `callbackfn`akceptuje maksymalnie trzech argumentów. `forEach`wywołania `callbackfn` funkcji jeden raz dla każdego elementu na mapie.  
  
 `thisArg`  
 Opcjonalny. Obiekt który `this` — słowo kluczowe może odwoływać się do w `callbackfn` funkcji. Jeśli `thisArg` zostanie pominięty, `undefined` jest używany jako `this` wartość.  
  
## <a name="exceptions"></a>Wyjątki  
 Jeśli `callbackfn` argument nie jest obiektem funkcji `TypeError` wyjątku.  
  
## <a name="remarks"></a>Uwagi  
 Składnia funkcji wywołania zwrotnego jest następująca:  
  
 `function callbackfn(value, key, mapObj)`  
  
 Funkcja wywołania zwrotnego można zadeklarować przy użyciu maksymalnie trzech parametrów, jak pokazano w poniższej tabeli.  
  
|Argument wywołania zwrotnego|Definicja|  
|-----------------------|----------------|  
|`value`|Wartość zawarte w planie.|  
|`key`|Klucz zawarte w planie.|  
|`mapObj`|`Map` Obiekt, aby przechodzić między nimi.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak można pobrać elementów członkowskich `Map` przy użyciu `forEach`.  
  
```JavaScript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
m.set({x:1}, 3);  
  
m.forEach(function (item, key, mapObj) {  
    document.write(item.toString() + "<br />");  
});  
  
document.write("<br />");  
document.write(m.get(2));  
  
// Output:  
// black  
// red  
// 2  
// 3  
//  
// red  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]