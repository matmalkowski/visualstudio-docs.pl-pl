---
title: __proto__ właściwość (obiekt) (JavaScript) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- __proto__
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 97c3f84d-125e-4905-b921-b021264964ee
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f8659c7a4ece5e30378838f20341ec6712f77ca3
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
ms.locfileid: "29899578"
---
# <a name="proto-property-object-javascript"></a>__proto__ właściwość (obiekt) (JavaScript)
Zawiera odwołanie do wewnętrznego prototypu określonego obiektu.  

> [!WARNING]
> `__proto__` Właściwości jest funkcją starszej wersji. Użyj [Object.getprototypeof —](../reference/object-getprototypeof-function-javascript.md) zamiast tego.
  
## <a name="syntax"></a>Składnia  
  
```  
object.__proto__  
```  
  
#### <a name="parameters"></a>Parametry  
 `object`  
 Wymagany. Obiekt, w którym można ustawić prototypu.  
  
## <a name="remarks"></a>Uwagi  
 `__proto__` Właściwości można ustawić prototypu dla obiekt.  
  
 Obiekt lub funkcja dziedziczy wszystkie metody i właściwości nowe prototyp, oraz wszystkie metody i właściwości w łańcuchu prototypu prototypu nowe. Każdy obiekt może mieć tylko jeden prototyp (nie w tym dziedziczone prototypy w łańcuchu prototypu), dlatego podczas wywoływania `__proto__` właściwości, Zastąp poprzedniej prototypu.  
  
 Prototyp można ustawić tylko na obiekcie rozszerzonego. Aby uzyskać więcej informacji, zobacz [Object.preventextensions — funkcja](../../javascript/reference/object-preventextensions-function-javascript.md).  
  
> [!NOTE]
>  `__proto__` Nazwa właściwości rozpoczyna się i kończy dwa znaki podkreślenia.  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod przedstawia sposób ustawiania prototypu dla obiekt.  
  
```JavaScript  
function Rectangle() {  
}  
  
var rec = new Rectangle();  
  
if (console && console.log) {  
    console.log(rec.__proto__ === Rectangle.prototype);  // Returns true  
    rec.__proto__ = Object.prototype;  
    console.log(rec.__proto__ === Rectangle.prototype);  // Returns false  
}  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje, jak dodać właściwości do obiektu przez dodanie ich do prototypu.  
  
```JavaScript  
var proto = { y: 2 };  
  
var obj = { x: 10 };  
obj.__proto__ = proto;  
  
proto.y = 20;  
proto.z = 40;  
  
if (console && console.log) {  
    console.log(obj.x === 10);  // Returns true  
    console.log(obj.y === 20);  // Returns true  
    console.log(obj.z === 40);  // Returns true  
}  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod dodaje właściwości `String` obiektu przez ustawienie nowego prototypu.  
  
```JavaScript  
var stringProp = { desc: "description" };  
  
String.__proto__ = stringProp;  
var s1 = "333";  
var s2 = new String("333");  
  
if (console && console.log) {  
  
    console.log(String.desc === "description"); // Returns true  
    console.log(s1.desc === "description");     // Returns false  
    console.log(s2.desc === "description");     // Returns false  
  
    s1.__proto__ = String;  // Can't be set.  
    s2.__proto__ = String;  
  
    console.log(s1.desc === "description"); // Returns false  
    console.log(s2.desc === "description"); // Returns true  
}  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Prototypy i dziedziczenie oparte na prototypach](../../javascript/advanced/prototypes-and-prototype-inheritance.md)