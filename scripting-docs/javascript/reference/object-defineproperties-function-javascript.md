---
title: "Object.defineproperties — funkcja (JavaScript) | Dokumentacja firmy Microsoft"
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
helpviewer_keywords:
- Object.defineProperties function [JavaScript]
ms.assetid: 2dae6658-a1c9-495f-bf06-bb3e964e6762
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 65f4f5817a105283a26c971bd98869d000ca0bc2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="objectdefineproperties-function-javascript"></a>Object.defineProperties — Funkcja (JavaScript)
Dodaje jedną lub więcej właściwości do obiektu i/lub modyfikuje atrybuty istniejącej właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
object.defineProperties(object, descriptors)  
```  
  
## <a name="parameters"></a>Parametry  
 `object`  
 Wymagany. Obiekt, w którym można dodać lub zmodyfikować właściwości. Może to być natywny [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] obiekt lub obiekt modelu DOM.  
  
 `descriptors`  
 Wymagany. A [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] obiekt, który zawiera co najmniej jeden obiekt deskryptora. Każdy obiekt deskryptora opisuje właściwości danych lub właściwości metody dostępu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Obiekt, który został przekazany do funkcji.  
  
## <a name="remarks"></a>Uwagi  
 `descriptors` Argument jest obiekt, który zawiera co najmniej jeden obiekt deskryptora.  
  
 A *właściwości danych* jest właściwością, które można przechowywać i pobierać wartość. Deskryptor właściwości danych zawiera `value` atrybutu `writable` atrybutu lub jednocześnie. Aby uzyskać więcej informacji, zobacz [danych właściwości i metody dostępu właściwości](../../javascript/advanced/data-properties-and-accessor-properties.md).  
  
 *Akcesor właściwości* wywołuje funkcję dostarczane przez użytkownika za każdym razem, gdy wartość właściwości jest ustawiona lub pobrać. Deskryptor właściwości metody dostępu zawiera `set` atrybutu `get` atrybutu lub jednocześnie.  
  
 Jeśli obiekt ma już właściwość, która ma określoną nazwę, atrybuty są modyfikowane. Aby uzyskać więcej informacji, zobacz [Object.defineproperty — funkcja](../../javascript/reference/object-defineproperty-function-javascript.md).  
  
 Aby utworzyć obiekt i dodać właściwości do nowego obiektu, można użyć [Object.Create — funkcja](../../javascript/reference/object-create-function-javascript.md).  
  
## <a name="adding-properties"></a>Dodawanie właściwości  
 W poniższym przykładzie `Object.defineProperties` funkcja dodaje właściwości danych i dostępu do obiektów zdefiniowanych przez użytkownika.  
  
 W przykładzie użyto literału obiektu można utworzyć `descriptors` obiekt z `newDataProperty` i `newAccessorProperty` obiektów deskryptora.  
  
```JavaScript  
var newLine = "<br />";  
  
var obj = {};  
Object.defineProperties(obj, {  
    newDataProperty: {  
        value: 101,  
        writable: true,  
        enumerable: true,  
        configurable: true  
    },  
    newAccessorProperty: {  
        set: function (x) {  
            document.write("in property set accessor" + newLine);  
            this.newaccpropvalue = x;  
        },  
        get: function () {  
            document.write("in property get accessor" + newLine);  
            return this.newaccpropvalue;  
        },  
        enumerable: true,  
        configurable: true  
    }});  
  
// Set the accessor property value.  
obj.newAccessorProperty = 10;  
document.write ("newAccessorProperty value: " + obj.newAccessorProperty + newLine);  
  
// Output:  
// in property set accessor  
// in property get accessor  
// newAccessorProperty value: 10  
  
```  
  
 Podobnie jak poprzedniego przykładu w poniższym przykładzie dodano właściwości dynamicznie zamiast z literału obiektu.  
  
```JavaScript  
  
var newLine = "<br />";  
  
// Create the descriptors object.  
var descriptors = new Object();  
  
// Add a data property descriptor to the descriptors object.  
descriptors.newDataProperty = new Object();  
descriptors.newDataProperty.value = 101;  
descriptors.newDataProperty.writable = true;  
descriptors.newDataProperty.enumerable = true;  
descriptors.newDataProperty.configurable = true;  
  
// Add an accessor property descriptor to the descriptors object.  
descriptors.newAccessorProperty = new Object();  
descriptors.newAccessorProperty.set = function (x) {  
    document.write("in property set accessor" + newLine);  
    this.newaccpropvalue = x;  
};  
descriptors.newAccessorProperty.get = function () {  
    document.write("in property get accessor" + newLine);  
    return this.newaccpropvalue;  
};  
descriptors.newAccessorProperty.enumerable = true;  
descriptors.newAccessorProperty.configurable = true;  
  
// Call the Object.defineProperties function.  
var obj = new Object();  
Object.defineProperties(obj, descriptors);  
  
// Set the accessor property value.  
obj.newAccessorProperty = 10;  
document.write ("newAccessorProperty value: " + obj.newAccessorProperty + newLine);  
  
// Output:  
// in property set accessor  
// in property get accessor  
// newAccessorProperty value: 10  
  
```  
  
## <a name="modifying-properties"></a>Modyfikowanie właściwości  
 Aby zmodyfikować właściwości atrybutów dla obiektu, Dodaj następujący kod. `Object.defineProperties` Modyfikuje funkcja `writable` atrybutu `newDataProperty`i modyfikuje `enumerable` atrybutu `newAccessorProperty`. Dodaje `anotherDataProperty` do obiektu, ponieważ nazwa tej właściwości nie istnieje.  
  
```  
Object.defineProperties(obj, {  
    newDataProperty: { writable: false },  
    newAccessorProperty: { enumerable: false },  
    anotherDataProperty: { value: "abc" }  
});  
```  
  
## <a name="requirements"></a>Wymagania  
 Obsługiwane standardy programu Internet Explorer 9, Standardy programu Internet Explorer 10 i [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] aplikacji. Obsługiwane w programu Internet Explorer 8 dla obiektów modelu DOM, w przeciwnym razie nie obsługiwane.  
  
## <a name="see-also"></a>Zobacz też  
 [Object.getownpropertydescriptor — funkcja](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)   
 [Object.getownpropertynames — funkcja](../../javascript/reference/object-getownpropertynames-function-javascript.md)   
 [Object.defineproperty — funkcja](../../javascript/reference/object-defineproperty-function-javascript.md)   
 [Object.Create — funkcja](../../javascript/reference/object-create-function-javascript.md)   
 [Object — obiekt](../../javascript/reference/object-object-javascript.md)