---
title: Reflect — obiekt (JavaScript) | Dokumentacja firmy Microsoft
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
ms.assetid: 1df74f34-2eb4-42f1-a930-b943c86daa0e
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3574c54ee7ff69f56951cd7f4c9a93cac5275fc1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791788"
---
# <a name="reflect-object-javascript"></a>Reflect — obiekt (JavaScript)
Udostępnia metody do użycia podczas wykonywania operacji, które są przechwytywane.  
  
## <a name="syntax"></a>Składnia  
  
```  
Reflect.[method]  
```  
  
#### <a name="parameters"></a>Parametry  
 `method`  
 Wymagany. Nazwa metody `Reflect` obiektu.  
  
## <a name="remarks"></a>Uwagi  
 Nie można skonkretyzować obiektu odbicie z `new` operatora.  
  
 Odzwierciedlić metody są często używane z [proxy](../../javascript/reference/proxy-object-javascript.md) ponieważ umożliwiają one delegować do domyślne zachowanie bez stosowania domyślne zachowanie w kodzie.  
  
 Odzwierciedlają udostępnia metodę statyczną o takiej samej nazwie jak każdy pułapki serwera proxy. Opisy w tabeli nie są wyczerpujące.  
  
|Metoda|Opis|  
|------------|-----------------|  
|`Reflect.apply(target, thisArg, args)`|Podobnie jak [zastosować](../../javascript/reference/apply-method-function-javascript.md) metody obiektu funkcji.|  
|`Reflect.construct(target, args)`|Funkcja równoważnej `new` operatora.|  
|`Reflect.defineProperty(target, propertyName, descriptor)`|Podobnie jak [Object.defineproperty —](../../javascript/reference/object-defineproperty-function-javascript.md). Zwraca wartość logiczną wskazującą, czy wywołanie zakończyło się pomyślnie.|  
|`Reflect.deleteProperty(target, propertyName)`|Podobnie jak `delete` instrukcji. Zwraca wartość logiczną wskazującą, czy wywołanie zakończyło się pomyślnie.|  
|`Reflect.enumerate(target)`|Podobnie jak [for... w](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md) instrukcji, [Object.getownpropertysymbols —](../../javascript/reference/object-getownpropertysymbols-function-javascript.md), [Object.keys —](../../javascript/reference/object-keys-function-javascript.md) funkcji i [JSON.stringify](../../javascript/reference/json-stringify-function-javascript.md).|  
|`Reflect.get(target, propertyName, receiver)`|Odpowiednik w każdej funkcji [metody pobierającej](../../javascript/creating-objects-javascript.md) właściwości.|  
|`Reflect.getOwnPropertyDescriptor(target, propertyName)`|Podobnie jak [Object.getownpropertydescriptor —](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md). Zwraca wartość logiczną wskazującą, czy wywołanie zakończyło się pomyślnie.|  
|`Reflect.getPrototypeOf(target)`|Podobnie jak [Object.getprototypeof —](../../javascript/reference/object-getprototypeof-function-javascript.md).|  
|`Reflect.has(target, propertyName)`|Podobnie jak `in` operatora, [hasOwnProperty — metoda (obiekt)](../../javascript/reference/hasownproperty-method-object-javascript.md)i innych metod. Zwraca wartość logiczną wskazującą, czy wywołanie zakończyło się pomyślnie.|  
|`Reflect.isExtensible(target)`|Podobnie jak [Object.isextensible —](../../javascript/reference/object-isextensible-function-javascript.md).|  
|`Reflect.ownKeys(target)`|Podobnie jak [Object.getOwnPropertyNames](../../javascript/reference/object-getownpropertynames-function-javascript.md).|  
|`Reflect.preventExtensions(target)`|Podobnie jak [Object.preventextensions —](../../javascript/reference/object-preventextensions-function-javascript.md). Zwraca wartość logiczną wskazującą, czy wywołanie zakończyło się pomyślnie.|  
|`Reflect.set(target, propertyName, value, receiver)`|Podobnie jak przy użyciu dowolnego [metody ustawiającej](../../javascript/creating-objects-javascript.md) właściwości. Zwraca wartość logiczną wskazującą, czy wywołanie zakończyło się pomyślnie.|  
|`Reflect.setPrototypeOf(target, prototype)`|Podobnie jak [Object.setPrototypeOf](../../javascript/reference/object-setprototypeof-function-javascript.md). Zwraca wartość logiczną wskazującą, czy wywołanie zakończyło się pomyślnie.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje sposób użycia `Reflect.get` zapisu serwer proxy, że bloki Pobierz operacje dla właściwości, które zaczynają się od znaku podkreślenia.  
  
```JavaScript  
var p = new Proxy({}, {  
    get(k, t, r) {  
        // return undefined if key begins with underscore  
        if(k[0] === '_') return undefined;  
  
       // otherwise do default behavior  
       return Reflect.get(k, t, r);  
    }  
});  
  
p._foo = 1;  
console.log(p._foo);  
  
p.foo = 1;  
console.log(p.foo);  
  
// Output:  
// undefined  
// 1  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]