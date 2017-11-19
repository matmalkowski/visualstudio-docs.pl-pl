---
title: "Class — instrukcja (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: bf45ebad-4678-4062-88df-55d32b603c69
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e828ae86c3f8f585179e3b097d98b3449c3f3b45
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="class-statement-javascript"></a>class — instrukcja (JavaScript)
Deklaruje nową klasę.  
  
## <a name="syntax"></a>Składnia  
  
```  
class classname () [extends object] {    [constructor([arg1 [,... [,argN]]]) {        statements    }]    [[static] method([arg1 [,... [,argN]]]) {        statements    }]}  
```  
  
#### <a name="parameters"></a>Parametry  
 `classname`  
 Wymagany. Nazwa klasy.  
  
 `object`  
 Opcjonalny. Obiekt lub klasa, z której nowa klasa dziedziczy właściwości i metody.  
  
 `constructor`  
 Opcjonalny. Funkcja konstruktora, który inicjuje nowe wystąpienie klasy.  
  
 `arg1...argN`  
 Opcjonalny. Opcjonalne, rozdzielana przecinkami lista argumentów rozumie funkcji.  
  
 `statements`  
 Opcjonalny. Co najmniej jeden [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] instrukcje.  
  
 `static`  
 Opcjonalny. Określa metody statycznej.  
  
 `method`  
 Opcjonalny. Co najmniej jeden [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] wystąpienia lub metod statycznych, które mogą być wywoływane na wystąpienie klasy.  
  
## <a name="remarks"></a>Uwagi  
 Klasa służy do tworzenia nowych obiektów przy użyciu na podstawie prototypu dziedziczenia, konstruktorów, metod wystąpienia i metod statycznych. Można użyć `super` obiektu w konstruktora klasy lub metoda klasy wywołanie tej samej konstruktora lub metody w klasie nadrzędnej lub obiektu. Można też użyć `extends` instrukcji po nazwie klasy określa klasę lub obiekt, z której nowa klasa dziedziczy metody.  
  
## <a name="example"></a>Przykład  
  
```JavaScript  
class Spelunking extends EXPERIENCE.Outdoor {  
  constructor(name, location) {  
    super(name, location);  
  
    this.minSkill = Spelunking.defaultSkill();  
    //...  
  }  
  update(minSkill) {  
    //...  
    super.update(minSkill);  
  }  
  static defaultSkill() {  
    return new EXPERIENCE.Level3();  
  }  
}  
```  
  
## <a name="example"></a>Przykład  
 Można również utworzyć nazwy właściwości obliczanej dla klas. Poniższy przykład kodu tworzy nazwę właściwości obliczanej przy użyciu `set` składni.  
  
```JavaScript  
var propName = "prop_42";  
  
class Spelunking {  
    set [propName](v) {  
        this.value = v;  
    }  
};  
  
var s = new Spelunking();  
console.log(s.value);  
s.prop_42 = 42;  
console.log(s.value);  
  
// Output:  
// undefined  
// 42  
  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu tworzy nazwę właściwości dla klasy dynamicznie za pomocą `get` składni.  
  
```JavaScript  
var propName = "prop_42";  
  
class Spelunking {  
    get [propName]() {  
        return 777;  
    }  
}  
  
var s = new Spelunking();  
console.log(s.prop_42);  
  
// Output:  
// 777  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv12exp](../../javascript/reference/includes/jsv12exp-md.md)]