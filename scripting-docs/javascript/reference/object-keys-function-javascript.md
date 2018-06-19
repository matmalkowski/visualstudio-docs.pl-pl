---
title: Object.keys — funkcja (JavaScript) | Dokumentacja firmy Microsoft
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
- Object.keys method [JavaScript]
- keys method [JavaScript]
ms.assetid: cf4a7daf-cf28-4467-bc6b-f7f106ec3876
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0e725c3ab7206b04d9a900cb614b57c37dfc4351
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791434"
---
# <a name="objectkeys-function-javascript"></a>Object.keys — Funkcja (JavaScript)
Zwraca nazwy wyliczenia właściwości i metod obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```JavaScript  
Object.keys(object)  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Definicja|  
|---------------|----------------|  
|`object`|Wymagany. Obiekt, który zawiera właściwości i metody. Może to być obiekt, który został utworzony lub istniejący obiekt modelu DOM (Document Object).|  
  
## <a name="return-value"></a>Wartość zwracana  
 Tablica zawiera nazwy wyliczenia właściwości i metody obiektu.  
  
## <a name="exceptions"></a>Wyjątki  
 Jeśli wartość podana dla `object` argument nie jest nazwa obiektu `TypeError` wyjątku.  
  
## <a name="remarks"></a>Uwagi  
 `keys` Metoda zwraca tylko nazwy wyliczenia właściwości i metod. Aby przywrócić nazwy wyliczalny i wyliczalny właściwości i metod, można użyć [Object.getownpropertynames — funkcja](../../javascript/reference/object-getownpropertynames-function-javascript.md).  
  
 Aby uzyskać informacje o `enumerable` atrybut z właściwością, zobacz [Object.defineproperty — funkcja](../../javascript/reference/object-defineproperty-function-javascript.md) i [Object.getownpropertydescriptor — funkcja](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy obiekt, który ma trzy właściwości i metody. Następnie używa `keys` metody można pobrać właściwości i metody obiektu.  
  
```JavaScript  
// Create a constructor function.  
function Pasta(grain, width, shape) {  
    this.grain = grain;  
    this.width = width;  
    this.shape = shape;  
  
    // Define a method.  
    this.toString = function () {  
        return (this.grain + ", " + this.width + ", " + this.shape);  
    }  
}  
  
// Create an object.  
var spaghetti = new Pasta("wheat", 0.2, "circle");  
  
// Put the enumerable properties and methods of the object in an array.  
var arr = Object.keys(spaghetti);  
document.write (arr);  
  
// Output:  
// grain,width,shape,toString  
```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono nazwy wszystkich właściwości wyliczenia, rozpoczynających się od litery "g" w obiekcie makaronu.  
  
```JavaScript  
// Create a constructor function.  
function Pasta(grain, width, shape) {  
    this.grain = grain;  
    this.width = width;  
    this.shape = shape;  
}  
  
var polenta = new Pasta("corn", 1, "mush");  
  
var keys = Object.keys(polenta).filter(CheckKey);  
document.write(keys);  
  
// Check whether the first character of a string is "g".  
function CheckKey(value) {  
    var firstChar = value.substr(0, 1);  
    if (firstChar.toLowerCase() == "g")  
        return true;  
    else  
        return false;  
}  
  
// Output:  
// grain  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Object.getownpropertynames — funkcja](../../javascript/reference/object-getownpropertynames-function-javascript.md)