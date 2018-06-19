---
title: Object.Create — funkcja (JavaScript) | Dokumentacja firmy Microsoft
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
helpviewer_keywords:
- create function [JavaScript]
- Object.create function [JavaScript]
ms.assetid: 0ad31f36-a9ee-444e-b0fe-c87843d03196
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f359908c5c836743e22390580f542df27d7b98e7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791653"
---
# <a name="objectcreate-function-javascript"></a>Object.create — Funkcja (JavaScript)
Tworzy obiekt mający określonego prototypu i opcjonalnie zawiera określonej właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```  
Object.create(prototype, descriptors)  
```  
  
#### <a name="parameters"></a>Parametry  
 `prototype`  
 Wymagany. Obiekt, który ma być używana jako prototyp. Może być `null`.  
  
 `descriptors`  
 Opcjonalny. A [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] obiekt, który zawiera co najmniej jeden deskryptorów właściwości.  
  
 A *właściwości danych* jest właściwością, który można pobrać i ustawić wartość. Deskryptor właściwości danych zawiera `value` atrybutu, oraz `writable`, `enumerable`, i `configurable` atrybutów. Jeśli ostatnie trzy atrybuty nie są określone, są domyślnie `false`. *Akcesor właściwości* wywołuje funkcję dostarczane przez użytkownika za każdym razem, pobrać lub ustawić wartości. Deskryptor właściwości metody dostępu zawiera `set` atrybutu `get` atrybutu lub jednocześnie. Aby uzyskać więcej informacji, zobacz [Object.defineproperty — funkcja](../../javascript/reference/object-defineproperty-function-javascript.md).  
  
## <a name="return-value"></a>Wartość zwracana  
 Nowy obiekt, który ma określony wewnętrzny prototypu i zawiera określone właściwości, jeśli istnieje.  
  
## <a name="exceptions"></a>Wyjątki  
 A `TypeError` jest zgłaszany wyjątek, jeśli jest spełniony jeden z następujących warunków:  
  
-   `prototype` Argument nie jest obiektem i nie jest `null`.  
  
-   Deskryptor w `descriptors` argument ma `value` lub `writable` atrybutu i ma `get` lub `set` atrybutu.  
  
-   Deskryptor w `descriptors` argument ma `get` lub `set` atrybut, który nie jest funkcją.  
  
## <a name="remarks"></a>Uwagi  
 Można użyć tej funkcji przy użyciu `null``prototype` parametr, aby zatrzymać łańcuch prototypów. Obiekt utworzony nie odniesie bez prototypu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy obiekt przy użyciu `null` prototypu i dodaje dwie właściwości wyliczenia.  
  
```JavaScript  
var newObj = Object.create(null, {  
            size: {  
                value: "large",  
                enumerable: true  
            },  
            shape: {  
                value: "round",  
                enumerable: true  
            }  
        });  
  
document.write(newObj.size + "<br/>");  
document.write(newObj.shape + "<br/>");  
document.write(Object.getPrototypeOf(newObj));  
  
// Output:  
// large  
// round  
// null  
  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy obiekt, który ma tego samego prototypu wewnętrzny jako obiekt obiektu. Widać, że ma tego samego prototypu jako obiekt, który został utworzony za pomocą literału obiektu. [Object.getprototypeof —](../../javascript/reference/object-getprototypeof-function-javascript.md) funkcja pobiera prototypu obiektu oryginalnego. Aby uzyskać deskryptora właściwości obiektu, można użyć [Object.getownpropertydescriptor — funkcja](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).  
  
```JavaScript  
var firstLine = { x: undefined, y: undefined };  
  
var secondLine = Object.create(Object.prototype, {  
        x: {  
                value: undefined,   
                writable: true,   
                configurable: true,   
                enumerable: true  
            },  
            y: {  
                value: undefined,   
                writable: true,   
                configurable: true,   
                enumerable: true  
            }  
});  
  
document.write("first line prototype = " + Object.getPrototypeOf(firstLine));  
document.write("<br/>");  
document.write("second line prototype = " + Object.getPrototypeOf(secondLine));  
  
// Output:  
// first line prototype = [object Object]  
// second line prototype = [object Object]  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy obiekt, który ma tego samego prototypu wewnętrzny jako obiektu kształtu.  
  
```JavaScript  
  
// Create the shape object.  
var Shape = { twoDimensional: true, color: undefined, hasLineSegments: undefined };  
  
var Square = Object.create(Object.getPrototypeOf(Shape));  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Object.getprototypeof — funkcja](../../javascript/reference/object-getprototypeof-function-javascript.md)   
 [isPrototypeOf — metoda (obiekt)](../../javascript/reference/isprototypeof-method-object-javascript.md)   
 [Tworzenie obiektów](../../javascript/creating-objects-javascript.md)