---
title: "Proxy — obiekt (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 2b89abee-04fa-47e6-9676-980016cff5f8
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4ee75310f1d976e0a0896b1be34a80c594cdd054
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
---
# <a name="proxy-object-javascript"></a>Proxy — obiekt (JavaScript)
Włącza niestandardowe zachowanie dla obiekt.  
  
## <a name="syntax"></a>Składnia  
  
```  
proxyObj = new Proxy(target, handler)  
```  
  
#### <a name="parameters"></a>Parametry  
 `target`  
 Wymagany. Obiekt lub funkcję, która ma zostać Zwirtualizowana przez serwer proxy.  
  
 `handler`  
 Wymagany. Obiekt z metody (pułapki), które implementuje zachowania niestandardowego.  
  
## <a name="remarks"></a>Uwagi  
 A `Proxy` obiekt jest używany do przechwycenia niskiego poziomu operacji wewnętrznych na inny obiekt. Obiekty serwera proxy może służyć do przechwycenia, obiekt wirtualizacji rejestrowania/profilowania i innych celów.  
  
 Jeśli nie został zdefiniowany pułapki dla określonej operacji obsługi dla serwera proxy, operacja jest przekazywane do obiektu docelowego.  
  
 Obiekt obsługi definiuje następujące metody (pułapki) służące do implementacji niestandardowych zachowanie. Przykłady w tym miejscu nie są wyczerpujące. Aby obsługiwać warunkowego domyślne zachowanie w metodzie obsługi, należy użyć metod [odzwierciedlają obiektu](../../javascript/reference/reflect-object-javascript.md).  
  
|Składnia programu obsługi — metoda (pułapki)|Przykłady użycia|  
|------------------------------------|-----------------------|  
|`apply: function(target, thisArg, args)`|Pułapki wywołanie funkcji.|  
|`construct: function(target, args)`|Pułapki dla konstruktora.|  
|`defineProperty: function(target, propertyName, descriptor)`|Dla komunikatu trap [Object.defineproperty — funkcja](../../javascript/reference/object-defineproperty-function-javascript.md).|  
|`deleteProperty: function(target, propertyName)`|Dla komunikatu trap `delete` instrukcji.|  
|`enumerate: function(target)`|Dla komunikatu trap [for... w](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md) instrukcji, [Object.getownpropertysymbols —](../../javascript/reference/object-getownpropertysymbols-function-javascript.md), [Object.keys —](../../javascript/reference/object-keys-function-javascript.md) funkcji i [JSON.stringify](../../javascript/reference/json-stringify-function-javascript.md).|  
|`get: function(target, propertyName, receiver)`|Dla każdego komunikatu trap [metody pobierającej](../../javascript/creating-objects-javascript.md) właściwości.|  
|`getOwnPropertyDescriptor: function(target, propertyName)`|Dla komunikatu trap [Object.getownpropertydescriptor — funkcja](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).|  
|`getPrototypeOf: function(target)`|Dla komunikatu trap [Object.getprototypeof — funkcja](../../javascript/reference/object-getprototypeof-function-javascript.md).|  
|`has: function(target, propertyName)`|Dla komunikatu trap `in` operatora, [hasOwnProperty — metoda (obiekt)](../../javascript/reference/hasownproperty-method-object-javascript.md)i innych metod.|  
|`isExtensible: function(target)`|Dla komunikatu trap [Object.isextensible — funkcja](../../javascript/reference/object-isextensible-function-javascript.md).|  
|`ownKeys: function(target)`|Dla komunikatu trap [Object.getownpropertynames — funkcja](../../javascript/reference/object-getownpropertynames-function-javascript.md).|  
|`preventExtensions: function(target)`|Dla komunikatu trap [Object.preventextensions — funkcja](../../javascript/reference/object-preventextensions-function-javascript.md).|  
|`set: function(target, propertyName, value, receiver)`|Dla każdego komunikatu trap [metody ustawiającej](../../javascript/creating-objects-javascript.md) właściwości.|  
|`setPrototypeOf: function(target, prototype)`|Dla komunikatu trap [Object.setPrototypeOf](../../javascript/reference/object-setprototypeof-function-javascript.md).|  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono sposób tworzenia serwera proxy dla obiekt literału przy użyciu `get` pułapki.  
  
```JavaScript  
var target = {};  
var handler = {  
  get: function (target, property, receiver) {  
    // This example includes a template string.  
    return `Hello, ${property}!`;  
  }  
};  
  
var p = new Proxy(target, handler);  
console.log(p.world);  
  
// Output:  
// Hello, world!  
  
```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono sposób tworzenia serwera proxy dla funkcji przy użyciu `apply` pułapki.  
  
```JavaScript  
var target = function () { return 'I am the target'; };  
var handler = {  
  // This example includes a rest parameter.  
  apply: function (receiver, ...args) {  
    return 'I am the proxy';  
  }  
};  
  
var p = new Proxy(target, handler);  
console.log(target()):  
console.log(p()):  
  
// Output:  
// I am the target  
// I am the proxy  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]
