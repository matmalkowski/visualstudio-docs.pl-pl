---
title: Tworzenie obiektów (JavaScript) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- constructors, including properties and methods
- function constructor
- creating objects, constructor functions
- constructor functions
- prototype objects
- creating objects
- custom objects, creating
- creating objects, about creating objects
- objects, creating [JavaScript]
- creating objects, prototypes
- custom objects
- initializing objects, using constructors
ms.assetid: 58d1baa5-4fe8-4a56-a926-5b11765df704
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0ba7962179cc2f0fcb972caee692edabee368c7d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24788872"
---
# <a name="creating-objects-javascript"></a>Tworzenie obiektów (JavaScript)
Istnieją różne sposoby tworzenia własnych obiektów w języku JavaScript. Można bezpośrednio utworzyć wystąpienia [dla obiektu](../javascript/reference/object-object-javascript.md) , a następnie dodać własne właściwości i metod. Lub notacji literału obiektu umożliwia definiowanie obiektu. Funkcja Konstruktor umożliwia również definiowanie obiektu. Aby uzyskać więcej informacji o korzystaniu z funkcji konstruktora, zobacz [za pomocą konstruktorów do definiowania typów](../javascript/advanced/using-constructors-to-define-types.md).  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia sposób tworzenia wystąpienia obiektu i dodać niektórych właściwości. W takim przypadku tylko `pasta` obiekt ma `grain`, `width`, i `shape` właściwości.  
  
```JavaScript  
const pasta = new Object();  
pasta.grain = "wheat";  
pasta.width = 0.5;  
pasta.shape = "round";  
pasta.getShape = function() {   
    return this.shape;   
};  
document.write(pasta.grain);  
document.write("<br/>");  
document.write(pasta.getShape());  
  
// Output:  
// wheat  
// round  
  
```  
  
## <a name="object-literals"></a>Literały obiektu  
 Umożliwia także notacji literału obiektu można utworzyć tylko jedno wystąpienie obiektu. Poniższy kod przedstawia sposób tworzenia wystąpienia obiektu przy użyciu notacji literału obiektu.  
  
```JavaScript  
const pasta = {  
    grain: "wheat",  
    width: 0.5,  
    shape: "round"  
};  
```  
  
 Można również użyć literału w Konstruktorze obiektu.  
  
> [!CAUTION]
>  Funkcje opisane poniżej są obsługiwane tylko w [!INCLUDE[jsv12text](../javascript/includes/jsv12text-md.md)].  
  
 W [!INCLUDE[jsv12text](../javascript/includes/jsv12text-md.md)], za pomocą składni skrótu do utworzenia literału obiektu.  
  
```JavaScript  
const key = 'a';  
const value = 5;  
  
// Older version  
const obj1 = {  
    key: key,  
    value: value  
};  
  
// Edge mode  
const obj2 = {key, value};  
  
console.log(obj2);  
  
// Output:  
// [object Object] {key: "a", value: 5}  
```  
  
 Poniższy przykład przedstawia użycie składni skrótu do definiowania metod w literałach obiektu.  
  
```JavaScript  
// Older versions  
const obj = {  
    method1: function() {},  
    method2: function() {}  
};  
  
// Edge mode  
const obj = {  
    method1() {},  
    method2() {}  
};  
```  
  
 Można również ustawić właściwość nazwy dynamicznie w literałach obiektu w [!INCLUDE[jsv12text](../javascript/includes/jsv12text-md.md)]. Poniższy przykład kodu tworzy nazwę właściwości obiektu dynamicznie przy użyciu składni zestawu.  
  
```JavaScript  
const propName = "prop_42";  
  
const obj = {  
    value: 0,  
    set [propName](v) {  
        this.value = v;  
    }  
}  
  
console.log(obj.value);  
// Runs the setter property.  
obj.prop_42 = 777;  
console.log(obj.value);  
  
// Output:  
// 0  
// 777  
  
```  
  
 Poniższy przykład kodu tworzy nazwę właściwości obiektu dynamicznie przy użyciu składni get.  
  
```JavaScript  
const propName = "prop_42";  
  
const obj = {  
    get [propName]() {  
        return 777;  
    }  
}  
  
console.log(obj.prop_42);  
  
// Output:  
// 777  
```  
  
 Poniższy przykład kodu tworzy właściwości obliczanej przy użyciu [Składnia funkcji strzałka](../javascript/functions-javascript.md) do dołączenia 42 nazwę właściwości.  
  
```JavaScript  
const obj = {  
    [ 'prop_' + (() => 42)() ]: 42  
};  
```
