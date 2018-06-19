---
title: Object.FREEZE — funkcja (JavaScript) | Dokumentacja firmy Microsoft
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
- Object.freeze function
- freeze function
ms.assetid: 83ffe193-0a37-4e0c-9b66-44c422765fb3
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ec08b34c3c8b32245928e6e75f5df1fbdfe2d4a6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24792073"
---
# <a name="objectfreeze-function-javascript"></a>Object.freeze — Funkcja (JavaScript)
Modyfikację istniejące atrybuty właściwości i wartości i uniemożliwia dodanie nowych właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```JavaScript  
Object.freeze(object)  
```  
  
#### <a name="parameters"></a>Parametry  
 `object`  
 Wymagany. Obiekt, w którym można zablokować atrybuty.  
  
## <a name="return-value"></a>Wartość zwracana  
 Obiekt, który jest przekazywany do funkcji.  
  
## <a name="exceptions"></a>Wyjątki  
 Jeśli `object` argument nie jest obiektem, `TypeError` wyjątku.  
  
## <a name="remarks"></a>Uwagi  
 `Object.freeze` Funkcja wykonuje następujące czynności:  
  
-   Sprawia, że obiekt nie rozszerzalne, dzięki czemu nowe właściwości nie można dodać do niego.  
  
-   Ustawia `configurable` atrybutu `false` dla wszystkich właściwości obiektu. Gdy `configurable` jest `false`, nie można zmienić właściwości atrybutów i nie można usunąć właściwości.  
  
-   Ustawia `writable` atrybutu `false` dla wszystkich właściwości obiektu danych. Gdy `writable` ma wartość false, nie można zmienić wartości właściwości danych.  
  
 Aby uzyskać więcej informacji na temat sposobu ustawiania właściwości atrybutów, zobacz [Object.defineproperty — funkcja](../../javascript/reference/object-defineproperty-function-javascript.md). Aby uzyskać atrybuty właściwości, można użyć [Object.getownpropertydescriptor — funkcja](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).  
  
## <a name="related-functions"></a>Funkcje pokrewne  
 Następujące funkcje pokrewne uniemożliwiają zmiany atrybutów obiektu.  
  
|Funkcja|Obiekt staje się z systemem innym niż rozszerzonego|`configurable`ustawiono `false` dla każdej właściwości|`writable`ustawiono `false` dla każdej właściwości|  
|--------------|------------------------------------|--------------------------------------------------------|----------------------------------------------------|  
|[Object.preventextensions —](../../javascript/reference/object-preventextensions-function-javascript.md)|Tak|Nie|Nie|  
|[Object.Seal —](../../javascript/reference/object-seal-function-javascript.md)|Tak|Tak|Nie|  
|`Object.freeze`|Tak|Tak|Tak|  
  
 Następujące funkcje zwracają `true` jeśli spełnione są wszystkie warunki oznaczone w poniższej tabeli.  
  
|Funkcja|Obiekt jest rozszerzalny?|`configurable`jest `false` dla wszystkich właściwości?|`writable`jest `false` dla wszystkich właściwości danych?|  
|--------------|---------------------------|---------------------------------------------------|----------------------------------------------------|  
|[Object.isextensible —](../../javascript/reference/object-isextensible-function-javascript.md)|Tak|Nie|Nie|  
|[Object.issealed —](../../javascript/reference/object-issealed-function-javascript.md)|Nie|Tak|Tak|  
|[Object.isfrozen —](../../javascript/reference/object-isfrozen-function-javascript.md)|Nie|Tak|Tak|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `Object.freeze` funkcji.  
  
```JavaScript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
  
// Freeze the object.  
Object.freeze(obj);  
  
// Try to add a new property, and then verify that it is not added.   
    obj.newProp = 50;  
    document.write(obj.newProp);  
    document.write("<br/>");  
  
// Try to delete a property, and then verify that it is still present.   
delete obj.length;  
document.write(obj.length);  
document.write("<br/>");  
  
// Try to change a property value, and then verify that it is not changed.   
obj.pasta = "linguini";  
document.write(obj.pasta);  
  
// Output:  
// undefined  
// 10  
// spaghetti  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Object.preventextensions — funkcja](../../javascript/reference/object-preventextensions-function-javascript.md)   
 [Object.Seal — funkcja](../../javascript/reference/object-seal-function-javascript.md)   
 [Object.isextensible — funkcja](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Object.issealed — funkcja](../../javascript/reference/object-issealed-function-javascript.md)   
 [Object.isfrozen — funkcja](../../javascript/reference/object-isfrozen-function-javascript.md)