---
title: Object.preventextensions — funkcja (JavaScript) | Dokumentacja firmy Microsoft
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
- properties [JavaScript], preventing new
- preventing new properties [JavaScript]
- preventExtensions function [JavaScript]
- Object.preventExtensions function [JavaScript]
ms.assetid: e6b48197-2374-4437-a9fe-519dd45a2077
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 868f917cc2249a1634194e4b2dd097e0dcbd4c08
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791845"
---
# <a name="objectpreventextensions-function-javascript"></a>Object.preventExtensions — Funkcja (JavaScript)
Uniemożliwia dodanie nowych właściwości do obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```JavaScript  
Object.preventExtensions(object)  
```  
  
#### <a name="parameters"></a>Parametry  
 `object`  
 Wymagany. Obiekt z systemem innym niż rozszerzonego.  
  
## <a name="return-value"></a>Wartość zwracana  
 Obiekt, który jest przekazywany do funkcji.  
  
## <a name="exceptions"></a>Wyjątki  
 Jeśli `object` argument nie jest obiektem, `TypeError` wyjątku.  
  
## <a name="remarks"></a>Uwagi  
 `Object.preventExtensions` Funkcja sprawia, że obiekt nie rozszerzalny, tak, aby nowe nazwane właściwości nie można dodać do niego. Po utworzeniu obiektu nie jest rozszerzony, nie można dokonać rozszerzonego.  
  
 Aby uzyskać informacje o tym, jak można ustawić właściwości atrybutów, zobacz [Object.defineproperty — funkcja](../../javascript/reference/object-defineproperty-function-javascript.md).  
  
## <a name="related-functions"></a>Funkcje pokrewne  
 Następujące funkcje pokrewne uniemożliwiają zmiany atrybutów obiektu.  
  
|Funkcja|Obiekt staje się z systemem innym niż rozszerzonego|`configurable`ustawiono `false` dla każdej właściwości|`writable`ustawiono `false` dla każdej właściwości|  
|--------------|------------------------------------|--------------------------------------------------------|----------------------------------------------------|  
|`Object.preventExtensions`|Tak|Nie|Nie|  
|[Object.Seal —](../../javascript/reference/object-seal-function-javascript.md)|Tak|Tak|Nie|  
|[Object.FREEZE —](../../javascript/reference/object-freeze-function-javascript.md)|Tak|Tak|Tak|  
  
 Następujące funkcje zwracają `true` jeśli spełnione są wszystkie warunki oznaczone w poniższej tabeli.  
  
|Funkcja|Obiekt jest rozszerzalny?|`configurable`jest `false` dla wszystkich właściwości?|`writable`jest `false` dla wszystkich właściwości danych?|  
|--------------|---------------------------|---------------------------------------------------|----------------------------------------------------|  
|[Object.isextensible —](../../javascript/reference/object-isextensible-function-javascript.md)|Tak|Nie|Nie|  
|[Object.issealed —](../../javascript/reference/object-issealed-function-javascript.md)|Nie|Tak|Nie|  
|[Object.isfrozen —](../../javascript/reference/object-isfrozen-function-javascript.md)|Nie|Tak|Tak|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `Object.preventExtensions` funkcji.  
  
```JavaScript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
  
// Make the object non-extensible.  
Object.preventExtensions(obj);  
document.write(Object.isExtensible(obj));  
document.write("<br/>");  
  
// Try to add a new property, and then verify that it is not added.  
obj.newProp = 50;  
document.write(obj.newProp);  
  
// Output:  
// false  
// undefined  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Object.Seal — funkcja](../../javascript/reference/object-seal-function-javascript.md)   
 [Object.FREEZE — funkcja](../../javascript/reference/object-freeze-function-javascript.md)   
 [Object.isextensible — funkcja](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Object.issealed — funkcja](../../javascript/reference/object-issealed-function-javascript.md)   
 [Object.isfrozen — funkcja](../../javascript/reference/object-isfrozen-function-javascript.md)