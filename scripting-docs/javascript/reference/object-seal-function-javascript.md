---
title: Object.Seal — funkcja (JavaScript) | Dokumentacja firmy Microsoft
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
- Object.seal function
- seal function
ms.assetid: e72c804a-4dab-4ec9-b9df-9c9c908aa12d
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2dca9066be9a557b97a52ae749cecfb218504509
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791857"
---
# <a name="objectseal-function-javascript"></a>Object.seal — Funkcja (JavaScript)
Modyfikację atrybuty istniejącej właściwości i uniemożliwia dodanie nowych właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```JavaScript  
Object.seal(object)  
```  
  
#### <a name="parameters"></a>Parametry  
 `object`  
 Wymagany. Obiekt, w którym można zablokować atrybuty.  
  
## <a name="return-value"></a>Wartość zwracana  
 Obiekt, który jest przekazywany do funkcji.  
  
## <a name="exceptions"></a>Wyjątki  
 Jeśli `object` argument nie jest obiektem, `TypeError` wyjątku.  
  
## <a name="remarks"></a>Uwagi  
 `Object.seal` Funkcja wykonuje obie z następujących czynności:  
  
-   Sprawia, że obiekt nie rozszerzalne, dzięki czemu nowe właściwości nie można dodać do niego.  
  
-   Ustawia `configurable` atrybutu `false` dla wszystkich właściwości obiektu.  
  
 Gdy `configurable` atrybutu `false`, nie można zmienić właściwości atrybutów i nie można usunąć właściwości. Gdy `configurable` jest `false` i `writable` jest `true`, `value` i `writable` można zmienić atrybutów.  
  
 `Object.seal` Nie zmienia funkcja `writable` atrybutu.  
  
 Aby uzyskać więcej informacji na temat sposobu ustawiania właściwości atrybutów, zobacz [Object.defineproperty — funkcja](../../javascript/reference/object-defineproperty-function-javascript.md). Aby uzyskać atrybuty właściwości, można użyć [Object.getownpropertydescriptor — funkcja](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).  
  
## <a name="related-functions"></a>Funkcje pokrewne  
 Następujące funkcje pokrewne uniemożliwiają zmiany atrybutów obiektu.  
  
|Funkcja|Obiekt staje się z systemem innym niż rozszerzonego|`configurable`ustawiono `false` dla każdej właściwości|`writable`ustawiono `false` dla każdej właściwości|  
|--------------|------------------------------------|--------------------------------------------------------|----------------------------------------------------|  
|[Object.preventextensions —](../../javascript/reference/object-preventextensions-function-javascript.md)|Tak|Nie|Nie|  
|`Object.seal`|Tak|Tak|Nie|  
|[Object.FREEZE —](../../javascript/reference/object-freeze-function-javascript.md)|Tak|Tak|Tak|  
  
 Następujące funkcje zwracają `true` jeśli spełnione są wszystkie warunki oznaczone w poniższej tabeli.  
  
|Funkcja|Obiekt jest rozszerzalny?|`configurable`jest `false` dla wszystkich właściwości?|`writable`jest `false` dla wszystkich właściwości danych?|  
|--------------|---------------------------|---------------------------------------------------|----------------------------------------------------|  
|[Object.isextensible —](../../javascript/reference/object-isextensible-function-javascript.md)|Tak|Nie|Nie|  
|[Object.issealed —](../../javascript/reference/object-issealed-function-javascript.md)|Nie|Tak|Nie|  
|[Object.isfrozen —](../../javascript/reference/object-isfrozen-function-javascript.md)|Nie|Tak|Tak|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `Object.seal` funkcji.  
  
```JavaScript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
// Seal the object.  
Object.seal(obj);  
document.write(Object.isSealed(obj));  
document.write("<br/>");  
  
// Try to add a new property, and then verify that it is not added.   
obj.newProp = 50;  
document.write(obj.newProp);  
document.write("<br/>");  
  
// Try to delete a property, and then verify that it is still present.   
delete obj.length;  
document.write(obj.length);  
  
// Output:  
// true  
// undefined  
// 10  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Object.preventextensions — funkcja](../../javascript/reference/object-preventextensions-function-javascript.md)   
 [Object.FREEZE — funkcja](../../javascript/reference/object-freeze-function-javascript.md)   
 [Object.isextensible — funkcja](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Object.issealed — funkcja](../../javascript/reference/object-issealed-function-javascript.md)   
 [Object.isfrozen — funkcja](../../javascript/reference/object-isfrozen-function-javascript.md)