---
title: Object.defineproperty — funkcja (JavaScript) | Dokumentacja firmy Microsoft
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
- defineProperty function [JavaScript]
- Object.defineProperty function [JavaScript]
ms.assetid: c5d05346-940a-40c2-b12a-e8b25abc8d46
caps.latest.revision: 74
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 89291f5c836f74a5dd71099328ce389a12f6fd24
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24792172"
---
# <a name="objectdefineproperty-function-javascript"></a>Object.defineProperty — Funkcja (JavaScript)
Dodaje właściwość do obiektu lub zmienia atrybuty istniejącej właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```  
Object.defineProperty(object, propertyname, descriptor)  
```  
  
## <a name="parameters"></a>Parametry  
 `object`  
 Wymagany. Obiekt, w którym można dodać lub zmodyfikować właściwości. Może to być natywny [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] obiektu (to znaczy zdefiniowane przez użytkownika obiektu lub wbudowane) lub DOM.  
  
 `propertyname`  
 Wymagany. Ciąg zawierający nazwę właściwości.  
  
 `descriptor`  
 Wymagany. Deskryptor właściwości. Można go do właściwości danych lub właściwości metody dostępu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zmodyfikowanego obiektu.  
  
## <a name="remarks"></a>Uwagi  
 Można użyć `Object.defineProperty` funkcja wykonać następujące czynności:  
  
-   Dodaj nową właściwość do obiektu. Dzieje się tak, gdy obiekt nie jest określona nazwa właściwości.  
  
-   Atrybuty istniejącej właściwości można modyfikować. Dzieje się tak, jeśli obiekt jest już określona nazwa właściwości.  
  
 Definicja właściwości jest świadczona w obiekt deskryptora zawiera opis atrybutów właściwości danych lub właściwości metody dostępu. Obiekt deskryptora jest parametrem `Object.defineProperty` funkcji.  
  
 Aby dodać wiele właściwości do obiektu lub zmodyfikować wielu istniejących właściwości, można użyć [Object.defineproperties — funkcja](../../javascript/reference/object-defineproperties-function-javascript.md).  
  
## <a name="exceptions"></a>Wyjątki  
 A `TypeError` jest zgłaszany wyjątek, jeśli spełniony jest jeden z następujących warunków:  
  
-   `object` Argument nie jest obiektem.  
  
-   Obiekt nie jest [extensible](../../javascript/reference/object-isextensible-function-javascript.md) i określona nazwa właściwości nie istnieje.  
  
-   `descriptor` Ma `value` lub `writable` atrybutu i ma `get` lub `set` atrybutu.  
  
-   `descriptor` Ma `get` lub `set` atrybut oznacza to nie funkcja lub niezdefiniowana.  
  
-   Określona nazwa właściwości już istnieje, ma istniejącej właściwości `configurable` atrybutu `false`i `descriptor` zawiera jeden lub więcej atrybutów, które są inne niż w istniejącej właściwości. Jednakże, gdy istniejącej właściwości ma `configurable` atrybutu `false` i `writable` atrybutu `true`, jest dozwolone w przypadku `value` lub `writable` atrybut różnić się.  
  
## <a name="adding-a-data-property"></a>Dodawanie właściwości danych  
 W poniższym przykładzie `Object.defineProperty` funkcja dodaje właściwość danych do obiektów zdefiniowanych przez użytkownika. Aby zamiast tego dodać właściwości do istniejącego obiektu modelu DOM, usuń znaczniki komentarza `var = window.document` wiersza.  
  
```JavaScript  
var newLine = "<br />";  
  
// Create a user-defined object.  
var obj = {};  
  
// Add a data property to the object.  
Object.defineProperty(obj, "newDataProperty", {  
    value: 101,  
    writable: true,  
    enumerable: true,  
    configurable: true  
});  
  
// Set the property value.  
obj.newDataProperty = 102;  
document.write("Property value: " + obj.newDataProperty + newLine);  
  
// Output:  
// Property value: 102  
```  
  
 Aby wyświetlić listę właściwości obiektu, Dodaj następujący kod do tego przykładu.  
  
```JavaScript  
var names = Object.getOwnPropertyNames(obj);  
for (var i = 0; i < names.length; i++) {  
    var prop = names[i];  
  
    document.write(prop + ': ' + obj[prop]);  
    document.write(newLine);  
}  
  
// Output:  
//  newDataProperty: 102  
```  
  
## <a name="modifying-a-data-property"></a>Modyfikowanie właściwości danych  
 Aby zmodyfikować właściwości atrybutu dla obiektu, Dodaj następujący kod do `addDataProperty` funkcja przedstawiona wcześniej. `descriptor` Parametr zawiera tylko `writable` atrybutu. Inne atrybuty właściwości dane pozostaną bez zmian.  
  
```JavaScript  
// Modify the writable attribute of the property.  
Object.defineProperty(obj, "newDataProperty", { writable: false });  
  
// List the property attributes by using a descriptor.  
// Get the descriptor with Object.getOwnPropertyDescriptor.  
var descriptor = Object.getOwnPropertyDescriptor(obj, "newDataProperty");  
for (var prop in descriptor) {  
    document.write(prop + ': ' + descriptor[prop]);  
    document.write(newLine);  
}  
  
// Output  
// writable: false  
// value: 102  
// configurable: true  
// enumerable: true  
```  
  
## <a name="adding-an-accessor-property"></a>Dodawanie właściwości akcesora  
 W poniższym przykładzie `Object.defineProperty` funkcja dodaje właściwość dostępu do obiektów zdefiniowanych przez użytkownika.  
  
```JavaScript  
var newLine = "<br />";  
  
// Create a user-defined object.  
var obj = {};  
  
// Add an accessor property to the object.  
Object.defineProperty(obj, "newAccessorProperty", {  
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
});  
  
// Set the property value.  
obj.newAccessorProperty = 30;  
document.write("Property value: " + obj.newAccessorProperty + newLine);  
  
// Output:  
// in property set accessor  
// in property get accessor  
// Property value: 30  
  
```  
  
 Aby wyświetlić listę właściwości obiektu, Dodaj następujący kod do tego przykładu.  
  
```JavaScript  
var names = Object.getOwnPropertyNames(obj);  
for (var i = 0; i < names.length; i++) {  
    var prop = names[i];  
  
    document.write(prop + ': ' + obj[prop]);  
    document.write(newLine);  
}  
// Output:  
// in property get accessor  
// newAccessorProperty: 30  
  
```  
  
## <a name="modifying-an-accessor-property"></a>Modyfikowanie właściwość akcesora  
 Aby zmodyfikować właściwości atrybutu dla obiektu, Dodaj następujący kod do kodu pokazano wcześniej. `descriptor` Parametr zawiera tylko `get` definicję metody dostępu. Inne atrybuty właściwości pozostają takie same.  
  
```JavaScript  
// Modify the get accessor.  
Object.defineProperty(obj, "newAccessorProperty", {  
    get: function () { return this.newaccpropvalue; }  
});  
  
// List the property attributes by using a descriptor.  
// Get the descriptor with Object.getOwnPropertyDescriptor.  
var descriptor = Object.getOwnPropertyDescriptor(obj, "newAccessorProperty");  
for (var prop in descriptor) {  
    document.write(prop + ': ' + descriptor[prop]);  
    document.write(newLine);  
}  
  
// Output:  
// get: function () { return this.newaccpropvalue; }  
// set: function (x) { document.write("in property set accessor" + newLine); this.newaccpropvalue = x; }  
// configurable: true  
// enumerable: true  
```  
  
## <a name="modifying-a-property-on-a-dom-element"></a>Modyfikowanie właściwości elementu modelu DOM  
 W poniższym przykładzie pokazano, jak dostosować za pomocą wbudowanych właściwości w modelu DOM `Object.getOwnPropertyDescriptor` funkcji, aby pobrać i zmodyfikować właściwości deskryptora właściwości. Na przykład należy przez element DIV o identyfikatorze "div".  
  
```JavaScript  
// Get the querySelector property descriptor.  
var descriptor = Object.getOwnPropertyDescriptor(Element.prototype, "querySelector");  
  
// Make the property read-only.  
descriptor.value = "query";  
descriptor.writable = false;  
// Apply the changes to the Element prototype.  
Object.defineProperty(Element.prototype, "querySelector", descriptor);  
  
// Get a DOM element from the HTML body.  
var elem = document.getElementById("div");  
  
// Attempt to change the value. This causes the revised value attribute to be called.  
elem.querySelector = "anotherQuery";  
document.write(elem.querySelector);  
  
// Output:  
// query  
  
```  
  
## <a name="requirements"></a>Wymagania  
 Tryb standardów programu Internet Explorer 9 i tryb standardów programu Internet Explorer 10, a także [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] aplikacje, obsługują wszystkie funkcje.  
  
 [!INCLUDE[jsv58textspecific](../../javascript/reference/includes/jsv58textspecific-md.md)]obsługuje obiekty modelu DOM, ale nie zdefiniowany przez użytkownika obiekty. `enumerable` i `configurable` można określić atrybuty, ale nie są one używane.  
  
## <a name="see-also"></a>Zobacz też  
 [Prototypy modelu obiektu dokumentu, część 2: Metoda dostępu (metody pobierającej/ustawiającej) pomocy technicznej](http://msdn.microsoft.com/library/dd229916\(v=VS.85\).aspx)   
 [Object.defineproperties — funkcja](../../javascript/reference/object-defineproperties-function-javascript.md)   
 [Object.Create — funkcja](../../javascript/reference/object-create-function-javascript.md)   
 [Object.getownpropertydescriptor — funkcja](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)   
 [Object.getownpropertynames — funkcja](../../javascript/reference/object-getownpropertynames-function-javascript.md)