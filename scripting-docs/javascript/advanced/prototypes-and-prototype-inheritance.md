---
title: Prototypy i dziedziczenie | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- prototype [JavaScript]
- prototype inheritance [JavaScript]
ms.assetid: 1e1d0631-2a9f-4011-b9fe-fa338e1ef34c
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 200ca757e72b2eec8f09fd48a841cc8eb816c85d
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
---
# <a name="prototypes-and-prototype-inheritance"></a>Prototypy i dziedziczenie
W języku JavaScript `prototype` jest właściwością, funkcje i obiekty, które są tworzone za pomocą funkcji konstruktora. Prototyp funkcji jest obiektem. Znajduje podstawowe zastosowanie, gdy funkcja jest używana jako konstruktor.  
  
```JavaScript  
function Vehicle(wheels, engine) {  
    this.wheels = wheels;  
    this.engine = engine;  
}  
```  
  
 W przykładzie przedstawionym powyżej prototyp `Vehicle` funkcji jest prototyp każdy obiekt, który zostanie uruchomiony z `Vehicle` konstruktora.  
  
## <a name="using-prototypes-to-add-properties-and-methods"></a>Dodawanie właściwości i metod przy użyciu prototypów  
 Można użyć `prototype` właściwości, aby dodać właściwości i metod do obiektów, nawet te, które zostały już utworzone:  
  
```JavaScript  
var testVehicle = new Vehicle(2, false);  
Vehicle.prototype.color = "red";  
var testColor = testVehicle.color;  
```  
  
 Wartość `testColor` jest "red".  
  
 Możesz nawet dodać właściwości i metody do wstępnie zdefiniowanych obiektów. Na przykład można zdefiniować `Trim` metoda `String` prototypu obiektu i wszystkich ciągów w skrypcie odziedziczą metody.  
  
```JavaScript  
String.prototype.trim = function()  
{  
    // Replace leading and trailing spaces with the empty string  
    return this.replace(/(^\s*)|(\s*$)/g, "");  
}  
var s = "    leading and trailing spaces    ";  
// Displays "    leading and trailing spaces     (35)"  
window.alert(s + " (" + s.length + ")");  
// Remove the leading and trailing spaces  
s = s.trim();  
// Displays "leading and trailing spaces (27)"  
window.alert(s + " (" + s.length + ")");  
```  
  
### <a name="using-prototypes-to-derive-one-object-from-another-with-objectcreate"></a>Używanie prototypów do wyprowadzenia jednego obiektu z innego za pomocą Object.create  

Prototyp `Object` może być użyty do uzyskania jeden obiekt z innej. Na przykład można użyć [Object.create —](../../javascript/reference/object-create-function-javascript.md) funkcji do uzyskania nowego obiektu `Bicycle` przy użyciu prototypu z `Vehicle` zdefiniowanego wcześniej (oraz nowe właściwości należy).  
  
```JavaScript  
var bicycle = Object.create(Object.getPrototypeOf(Vehicle), {  
    "pedals" :{value: true}  
});  
  
```  
  
 `bicycle` Obiekt ma właściwości `wheels`, `engine`, `color`, i `pedals`, i jest prototyp `Vehicle.prototype`. Aparat JavaScript umożliwia znalezienie `pedals` właściwość `bicycle`, i pobiera ona łańcuch prototypu w celu znalezienia `wheels`, `engine`, i `color` właściwości `Vehicle`.  
  
### <a name="changing-an-objects-prototype"></a>Zmiana prototypu obiektu  
W programie Internet Explorer 11, można zastąpić wewnętrzny prototypu obiektu lub funkcja nowe prototypu przy użyciu [ __proto__ ](../../javascript/reference/proto-property-object-javascript.md) właściwości. Gdy używasz tej właściwości, dziedziczysz właściwości i metody nowego prototypu oraz inne właściwości i metody w łańcuchu jego prototypów.  

> [!WARNING]
> `__proto__` Właściwości jest funkcją starszej wersji. Użyj [Object.getprototypeof —](../reference/object-getprototypeof-function-javascript.md) zamiast tego.
  
Poniższy przykład przedstawia, jak zmienić prototyp obiektu. Ten przykład przedstawia, jak się zmieniają dziedziczone właściwości obiektu po zmianie jego prototypu.  
  
```JavaScript  
function Friend() {  
    this.demeanor = "happy";  
}  
  
function Foe() {  
    this.demeanor = "suspicious";  
}  
  
var friend = new Friend();  
var foe = new Foe();  
  
var player = new Object();  
player.__proto__ = foe;  
  
friend.ally = "Tom";  
  
if (console && console.log) {  
    console.log(player.demeanor === "happy" );      // Returns false  
    console.log(player.demeanor === "suspicious");  // Returns true  
    console.log(player.ally === "Tom");             // Returns false  
    // Turn the foe to a friend.  
    player.__proto__ = friend;  
    console.log(player.demeanor === "happy");       // Returns true  
    console.log(player.demeanor === "suspicious");  // Returns false  
    console.log(player.ally === "Tom");             // Returns true  
}  
```
