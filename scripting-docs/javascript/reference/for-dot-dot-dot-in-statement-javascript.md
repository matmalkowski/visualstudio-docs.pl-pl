---
title: for... w — instrukcja (JavaScript) | Dokumentacja firmy Microsoft
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
- iteration statements, for...in statement
- loop structures, for...in statements
ms.assetid: 1b51a0ce-89f7-4a69-88ed-017b47dc398f
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a9c3ce78def6ab91256ff724a4acc87b7cf19ba2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24790528"
---
# <a name="forin-statement-javascript"></a>for...in — Instrukcja (JavaScript)
Wykonuje jedną lub więcej instrukcji dla każdej właściwości obiektu lub każdy element tablicy.  
  
## <a name="syntax"></a>Składnia  
  
```  
for (variable in [object | array]) {  
    statements   
}  
```  
  
## <a name="parameters"></a>Parametry  
 `variable`  
 Wymagany. Zmienna, która może być dowolną nazwą właściwości z `object` lub dowolnego indeks elementu `array`.  
  
 `object`, `array`  
 Opcjonalny. Obiekt lub tablicy służącym do wykonywania iteracji.  
  
 `statements`  
 Opcjonalny. Co najmniej jeden instrukcje do wykonania dla każdej właściwości `object` lub każdy element `array`. Może być złożonej instrukcji.  
  
## <a name="remarks"></a>Uwagi  
 Na początku każdej iteracji pętli, wartość `variable` jest nazwą właściwości dalej `object` lub indeks następnego elementu `array`. Następnie można użyć `variable` w żadnych instrukcji w pętli do odwołania z właściwością `object` lub element `array`.  
  
 Właściwości obiektu nie są przypisane w określony sposób. Nie można określić określoną właściwość według indeksu, tylko przez nazwę właściwości.  
  
 Iteracja przez tablicy jest wykonywane w kolejności elementów, oznacza to, 0, 1, 2.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `for...in` instrukcji z obiekt używany jako asocjacyjną.  
  
```JavaScript  
// Initialize object.  
a = {"a" : "Athens" , "b" : "Belgrade", "c" : "Cairo"}  
  
// Iterate over the properties.  
var s = ""  
for (var key in a) {  
    s += key + ": " + a[key];  
    s += "<br />";  
    }  
document.write (s);  
  
// Output:  
// a: Athens  
// b: Belgrade  
// c: Cairo  
```  
  
## <a name="example"></a>Przykład  
 W tym przykładzie przedstawiono użycie `for ... in` instrukcji iteracyjne jednak `Array` obiektu, który ma expando właściwości.  
  
```JavaScript  
// Initialize the array.  
var arr = new Array("zero","one","two");  
  
// Add a few expando properties to the array.  
arr["orange"] = "fruit";  
arr["carrot"] = "vegetable";  
  
// Iterate over the properties and elements.  
var s = "";  
for (var key in arr) {  
    s += key + ": " + arr[key];  
    s += "<br />";  
}  
  
document.write (s);  
  
// Output:  
//   0: zero  
//   1: one  
//   2: two  
//   orange: fruit  
//   carrot: vegetable  
```  
  
> [!NOTE]
>  Użyj `Enumerator` obiekt, aby przejść przez członków kolekcji.  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [for — instrukcja](../../javascript/reference/for-statement-javascript.md)   
 [while — instrukcja](../../javascript/reference/while-statement-javascript.md)