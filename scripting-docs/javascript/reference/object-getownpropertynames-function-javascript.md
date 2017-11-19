---
title: "Object.getOwnPropertyNames — funkcja (JavaScript) | Dokumentacja firmy Microsoft"
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
helpviewer_keywords:
- getOwnPropertyNames method [JavaScript]
- Object.getOwnPropertyNames method [JavaScript]
ms.assetid: 59f4b6b1-02be-44b3-a06c-a5ca8f70c3d8
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 76ca0036b9dedf7b4cee7b543469939e35dfe8d1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="objectgetownpropertynames-function-javascript"></a>Object.getOwnPropertyNames — Funkcja (JavaScript)
Zwraca nazwy własnej właściwości obiektu. Własnych właściwości obiektu są tymi, które są zdefiniowane bezpośrednio z tym obiektem, a nie są dziedziczone z obiektu prototypu. Właściwości obiektu obejmują zarówno pola (obiekty) i funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```JavaScript  
Object.getOwnPropertyNames(object)  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Definicja|  
|---------------|----------------|  
|`object`|Wymagany. Obiekt, który zawiera właściwości do własnej.|  
  
## <a name="return-value"></a>Wartość zwracana  
 Tablica zawierająca nazwy własnej właściwości obiektu.  
  
## <a name="exceptions"></a>Wyjątki  
 Jeśli wartość podana dla `object` argument nie jest nazwa obiektu `TypeError` wyjątku.  
  
## <a name="remarks"></a>Uwagi  
 `getOwnPropertyNames` Metoda zwraca nazwy wyliczalny i wyliczalny właściwości i metod. Aby przywrócić tylko nazwy wyliczenia właściwości i metod, można użyć [Object.keys — funkcja](../../javascript/reference/object-keys-function-javascript.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy obiekt, który ma trzy właściwości i metody. Następnie używa `getOwnPropertyNames` metodę, aby uzyskać własnych właściwości (w tym metoda) obiektu.  
  
```JavaScript  
function Pasta(grain, width, shape) {  
    // Define properties.  
    this.grain = grain;  
    this.width = width;  
    this.shape = shape;  
    this.toString = function () {  
        return (this.grain + ", " + this.width + ", " + this.shape);  
    }  
}  
  
// Create an object.  
var spaghetti = new Pasta("wheat", 0.2, "circle");  
  
// Get the own property names.  
var arr = Object.getOwnPropertyNames(spaghetti);  
document.write (arr);  
  
// Output:  
//   grain,width,shape,toString  
```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono nazwy właściwości rozpoczynające się od litery "w **postaci spaghetti** obiektu skonstruowany przy **makaronu** konstruktora.  
  
```JavaScript  
function Pasta(grain, size, shape) {  
    this.grain = grain;   
    this.size = size;   
    this.shape = shape;   
}  
  
var spaghetti = new Pasta("wheat", 2, "circle");  
  
var names = Object.getOwnPropertyNames(spaghetti).filter(CheckKey);  
document.write(names);   
  
// Check whether the first character of a string is 's'.   
function CheckKey(value) {  
    var firstChar = value.substr(0, 1);   
    if (firstChar.toLowerCase() == 's')  
        return true;   
    else  
         return false;   
}  
// Output:  
// size,shape  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Object.keys — funkcja](../../javascript/reference/object-keys-function-javascript.md)