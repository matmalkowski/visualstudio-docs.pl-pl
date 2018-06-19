---
title: Object.isfrozen — funkcja (JavaScript) | Dokumentacja firmy Microsoft
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
- isFrozen function [JavaScript]
- Object.isFrozen function [JavaScript]
ms.assetid: 6cf1bbc6-56e8-429b-8e2c-0024fa614acc
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3e1ccd11d5b4ef3b5f24dbfc8e815f0e3e156347
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24792040"
---
# <a name="objectisfrozen-function-javascript"></a>Object.isFrozen — Funkcja (JavaScript)
Zwraca `true` Jeśli istniejące atrybuty właściwości i wartości nie można zmodyfikować obiektu i nie można dodać nowych właściwości do obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```JavaScript  
Object.isFrozen(object)  
```  
  
#### <a name="parameters"></a>Parametry  
 `object`  
 Wymagany. Obiekt do przetestowania.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli spełnione są wszystkie z następujących czynności:  
  
-   Obiekt jest nie rozszerzalny, co oznacza, że nie można dodać nowych właściwości do obiektu.  
  
-   `configurable` Atrybutu `false` dla wszystkich istniejących właściwości.  
  
-   `writable` Atrybutu `false` dla wszystkich właściwości istniejących danych.  
  
 Jeśli obiekt nie ma istniejących właściwości, funkcja zwraca `true` Jeśli obiekt jest z systemem innym niż rozszerzonego.  
  
## <a name="exceptions"></a>Wyjątki  
 Jeśli `object` argument nie jest obiektem, `TypeError` wyjątku.  
  
## <a name="remarks"></a>Uwagi  
 Gdy `configurable` atrybutu właściwości `false`, nie można zmienić właściwości atrybutów i nie można usunąć właściwości. Gdy `writable` jest `false`, nie można zmienić wartości właściwości danych. Gdy `configurable` jest `false` i `writable` jest `true`, `value` i `writable` można zmienić atrybutów.  
  
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
|[Object.isextensible —](../../javascript/reference/object-isextensible-function-javascript.md)|Tak|Nie|Nie|  
|[Object.issealed —](../../javascript/reference/object-issealed-function-javascript.md)|Nie|Tak|Nie|  
|`Object.isFrozen`|Nie|Tak|Tak|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `Object.isFrozen` funkcji.  
  
```JavaScript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
  
// Freeze the object, and verify that it is frozen.  
Object.freeze(obj);  
document.write(obj.isFrozen());  
  
// Try to add a new property, and then verify that it is not added.   
obj.newProp = 50;  
document.write (obj.newProp);  
document.write ("<br/>");  
  
// Try to delete a property, and then verify that it is still present.  
delete obj.length;  
document.write (obj.length);  
document.write ("<br/> ");  
  
// Try to change a property value, and then verify that it is not changed.  
obj.pasta = "linguini";  
document.write (obj.pasta);  
  
// Output:  
// true  
// undefined  
// 10  
// spaghetti  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Object.preventextensions — funkcja](../../javascript/reference/object-preventextensions-function-javascript.md)   
 [Object.Seal — funkcja](../../javascript/reference/object-seal-function-javascript.md)   
 [Object.FREEZE — funkcja](../../javascript/reference/object-freeze-function-javascript.md)   
 [Object.isextensible — funkcja](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Object.issealed — funkcja](../../javascript/reference/object-issealed-function-javascript.md)   
 [Object.defineproperty — funkcja](../../javascript/reference/object-defineproperty-function-javascript.md)   
 [Object.getownpropertydescriptor — funkcja](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)   
 [Object.getownpropertynames — funkcja](../../javascript/reference/object-getownpropertynames-function-javascript.md)