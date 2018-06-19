---
title: Object.isextensible — funkcja (JavaScript) | Dokumentacja firmy Microsoft
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
- Object.isExtensible function [JavaScript]
- isExtensible function [JavaScript]
ms.assetid: a7d10beb-0d01-4e2d-8263-59ff07ac4352
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f88a61917811a5c6b5583e6c30539efc682296df
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791842"
---
# <a name="objectisextensible-function-javascript"></a>Object.isExtensible — Funkcja (JavaScript)
Zwraca wartość wskazującą, czy można dodawać nowych właściwości do obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```JavaScript  
Object.isExtensible(object)  
```  
  
#### <a name="parameters"></a>Parametry  
 `object`  
 Wymagany. Obiekt do przetestowania.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli obiekt jest rozszerzalny, co oznacza, że nowe właściwości można dodawać do obiektu. w przeciwnym razie `false`.  
  
## <a name="exceptions"></a>Wyjątki  
 Jeśli `object` argument nie jest obiektem, `TypeError` wyjątku.  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać informacje o tym, jak można ustawić właściwości atrybutów, zobacz [Object.defineproperty — funkcja](../../javascript/reference/object-defineproperty-function-javascript.md). Aby uzyskać atrybuty właściwości, można użyć [Object.getownpropertydescriptor — funkcja](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).  
  
## <a name="related-functions"></a>Funkcje pokrewne  
 Następujące funkcje pokrewne uniemożliwiają zmiany atrybutów obiektu.  
  
|Funkcja|Obiekt staje się z systemem innym niż rozszerzonego|`configurable`ustawiono `false` dla każdej właściwości|`writable`ustawiono `false` dla każdej właściwości|  
|--------------|------------------------------------|--------------------------------------------------------|----------------------------------------------------|  
|[Object.preventextensions —](../../javascript/reference/object-preventextensions-function-javascript.md)|Tak|Nie|Nie|  
|[Object.Seal —](../../javascript/reference/object-seal-function-javascript.md)|Tak|Tak|Nie|  
|[Object.FREEZE —](../../javascript/reference/object-freeze-function-javascript.md)|Tak|Tak|Tak|  
  
 Następujące funkcje zwracają `true` jeśli spełnione są wszystkie warunki oznaczone w poniższej tabeli.  
  
|Funkcja|Obiekt jest rozszerzalny?|`configurable`jest `false` dla wszystkich właściwości?|`writable`jest `false` dla wszystkich właściwości danych?|  
|--------------|---------------------------|---------------------------------------------------|----------------------------------------------------|  
|`Object.isExtensible`|Tak|Nie|Nie|  
|[Object.issealed —](../../javascript/reference/object-issealed-function-javascript.md)|Nie|Tak|Nie|  
|[Object.isfrozen —](../../javascript/reference/object-isfrozen-function-javascript.md)|Nie|Tak|Tak|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `Object.isExtensible` funkcji.  
  
```JavaScript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
  
// Make the object non-extensible.  
Object.preventExtensions(obj);  
  
// Try to add a new property, and then verify that it is not added.  
obj.newProp = 50;  
document.write(obj.newProp);  
  
// Output:  
undefined  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Object.preventextensions — funkcja](../../javascript/reference/object-preventextensions-function-javascript.md)   
 [Object.Seal — funkcja](../../javascript/reference/object-seal-function-javascript.md)   
 [Object.FREEZE — funkcja](../../javascript/reference/object-freeze-function-javascript.md)   
 [Object.issealed — funkcja](../../javascript/reference/object-issealed-function-javascript.md)   
 [Object.isfrozen — funkcja](../../javascript/reference/object-isfrozen-function-javascript.md)