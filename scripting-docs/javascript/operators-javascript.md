---
title: Operatory (JavaScript) | Dokumentacja firmy Microsoft
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
- JavaScript, operators
ms.assetid: b8602b69-aba9-46e8-86e1-cb533ad41410
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a3068a609da2468c59066ccd38f6de87cef1ed17
ms.sourcegitcommit: 873c0e1a31def013bcca1b0caa0eb0249de89bec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2018
ms.locfileid: "29753274"
---
# <a name="operators-javascript"></a>Operatory (JavaScript)
[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] ma pełny zakres operatorów, łącznie z arytmetyczne logiczne, operator przypisania, jak również niektórych różne operatory. Wyjaśnienia dotyczące i przykłady zobacz Tematy w szczególnych operatorów.  
  
## <a name="computational-operators"></a>Operatory obliczeniowe  
  
|Opis|Symbol|  
|-----------------|------------|  
|[Jednoargumentowy negacji](../javascript/reference/subtraction-operator-decrement-javascript.md)|-|  
|[Przyrost](../javascript/reference/increment-and-decrement-operators-javascript.md)|++|  
|[Dekrementacji](../javascript/reference/increment-and-decrement-operators-javascript.md)|--|  
|[Mnożenia](../javascript/reference/multiplication-operator-decrement-javascript.md)|*|  
|[dzielenie](../javascript/reference/division-operator-decrement-javascript.md)|/|  
|[Pozostałe arytmetyczne](../javascript/reference/modulus-operator-decrementjavascript.md)|%|  
|[Dodanie](../javascript/reference/addition-operator-decrement-javascript.md)|+|  
|[Odejmowanie](../javascript/reference/subtraction-operator-decrement-javascript.md)|-|  
  
## <a name="logical-operators"></a>Operatory logiczne  
  
|Opis|Symbol|  
|-----------------|------------|  
|[NEGACJA](../javascript/reference/logical-not-operator-decrement-exclpt-javascript.md)|!|  
|[Mniej niż](../javascript/reference/comparison-operators-javascript.md)|\<|  
|[Większa niż](../javascript/reference/comparison-operators-javascript.md)|>|  
|[Mniejsze niż lub równe](../javascript/reference/comparison-operators-javascript.md)|\<=|  
|[Większe lub równe](../javascript/reference/comparison-operators-javascript.md)|>=|  
|[Equality](../javascript/reference/comparison-operators-javascript.md)|==|  
|[Nierówności](../javascript/reference/comparison-operators-javascript.md)|!=|  
|[Logiczny AND](../javascript/reference/logical-and-operator-decrement-javascript.md)|&&|  
|[Logiczne lub](../javascript/reference/logical-or-operator-decrement-javascript.md)|&#124;&#124;|  
|[Warunkowy (trójargumentowy)](../javascript/reference/conditional-ternary-operator-decrement-javascript.md)|?:|  
|[Przecinkami](../javascript/reference/comma-operator-decrement-javascript.md)|,|  
|[Ścisła równość](../javascript/reference/comparison-operators-javascript.md)|===|  
|[Ścisła nierówność](../javascript/reference/comparison-operators-javascript.md)|!==|  
  
## <a name="bitwise-operators"></a>Operatory bitowe  
  
|Opis|Symbol|  
|-----------------|------------|  
|[Bitowe NOT](../javascript/reference/bitwise-not-operator-decrement-tilde-javascript.md)|~|  
|[Operator przesunięcia w lewo](../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)|<\<|  
|[Przesunięcia bitowego w prawo](../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)|>>|  
|[Przesunięcia w prawo bez znaku](../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)|>>>|  
|[Iloczynu bitowego AND](../javascript/reference/bitwise-and-operator-decrement-javascript.md)|&|  
|[Iloczynu bitowego XOR](../javascript/reference/bitwise-xor-operator-decrement-hat-javascript.md)|^|  
|[Bitowe lub](../javascript/reference/bitwise-or-operator-decrement-javascript.md)|&#124;|  
  
## <a name="assignment-operators"></a>Operatory przypisania  
  
|Opis|Symbol|  
|-----------------|------------|  
|[Przypisanie](../javascript/reference/assignment-operator-decrement-equal-javascript.md)|=|  
|[Przydział złożony](../javascript/reference/compound-assignment-operators-javascript.md)|*OP*= (takich jak += i & =)|  
  
## <a name="miscellaneous-operators"></a>Różne operatory  
  
|Opis|Symbol|  
|-----------------|------------|  
|[delete](../javascript/reference/delete-operator-decrementjavascript.md)|Usuń|  
|[typeof](../javascript/reference/typeof-operator-decrementjavascript.md)|typeof|  
|[void](../javascript/reference/void-operator-decrementjavascript.md)|void|  
|[instanceof](../javascript/reference/instanceof-operator-decrementjavascript.md)|instanceof|  
|[new](../javascript/reference/new-operator-decrementjavascript.md)|new|  
|[in](../javascript/reference/in-operator-decrementjavascript.md)|in|  
  
## <a name="equality-and-strict-equality"></a>Równości i ścisła równość  
 Różnica między == (równości) i === (Ścisła równość) jest operatora równości zostanie wymuszone wartości różnych typów przed sprawdzeniem pod kątem równości. Na przykład porównanie ciągu "1" o numerze 1 zostanie porównany jako true. Operator równości ograniczeniami z drugiej strony, będzie nie przekształcić wartości do różnych typów, a więc ciąg "1" nie zostanie porównany jako równe numer 1.  
  
 Pierwotne ciągów, liczb i wartości logiczne są porównywane przez wartość. Jeśli użytkownicy mają taką samą wartość, są równe. Obiekty (w tym `Array`, `Function`, `String`, **numer**, `Boolean`, **błąd**, `Date` i `RegExp` obiektów) porównania przez odwołanie. Nawet jeśli dwie zmienne typu ma taką samą wartość, są one takie same tylko wtedy, gdy odnoszą się do tego samego obiektu.  
  
 Na przykład:  
  
```JavaScript  
// Two strings with the same value.  
var string1 = "Hello";  
var string2 = "Hello";  
  
// Two String objects with the same value.  
var StringObject1 = new String(string1);  
var StringObject2 = new String(string2);  
  
if (string1 == string2)  
    document.write("string1 is equal to string2 <br/>");  
  
if (StringObject1 != StringObject2)  
    document.write("StringObject1 is not equal to StringObject2 <br/>");  
  
// To compare the values of String objects, use the toString() or valueOf() methods.  
if (StringObject1.valueOf() == StringObject2.valueOf())  
    document.write("The value of StringObject1 is equal to the value of StringObject2");  
  
//Output:  
// string1 is equal to string2   
// StringObject1 is not equal to StringObject2   
// The value of StringObject1 is equal to the value of StringObject2  
  
```