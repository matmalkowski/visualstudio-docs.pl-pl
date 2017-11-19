---
title: Tryb z ograniczeniami (JavaScript) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT1038
- VS.WebClient.Help.SCRIPT1050
- VS.WebClient.Help.SCRIPT1042
- VS.WebClient.Help.SCRIPT1041
- VS.WebClient.Help.SCRIPT1046
- VS.WebClient.Help.SCRIPT1045
- VS.WebClient.Help.SCRIPT1037
- VS.WebClient.Help.SCRIPT1039
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- strict mode
- use strict
ms.assetid: 0f27022a-f41c-4504-965c-5a2701f342cd
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 77ee7d54dd265026b2bf4c9af52a71cccf9a7675
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="strict-mode-javascript"></a>Tryb z ograniczeniami (JavaScript)
Tryb z ograniczeniami jest sposób wprowadzenie lepsze sprawdzanie błędów w kodzie. Użycie tryb z ograniczeniami, użytkownik nie może, na przykład używać zmiennych niejawnie zadeklarowanej przypisać wartości do właściwości tylko do odczytu lub dodawanie właściwości do obiektu, który nie jest rozszerzony. Ograniczenia są wymienione w [ograniczenia dotyczące kodu w trybie z ograniczeniami](../../javascript/advanced/strict-mode-javascript.md#rest) później w tym temacie. Aby uzyskać dodatkowe informacje w trybie z ograniczeniami, zobacz [specyfikacji języka ECMAScript, 5. Wersja](http://www.ecma-international.org/publications/standards/Ecma-262.htm).  
  
> [!WARNING]
>  Tryb z ograniczeniami nie jest obsługiwany w wersjach programu Internet Explorer starszych niż Internet Explorer 10.  
  
## <a name="declaring-strict-mode"></a>Deklarowanie tryb z ograniczeniami  
 Tryb z ograniczeniami mogą zadeklarować przez dodanie `"use strict";` na początku pliku, program lub funkcji. Tego rodzaju deklaracji nosi nazwę *dyrektywy prologu*. Zakres deklaracji tryb z ograniczeniami zależy od jego kontekstu. Jeśli jest on zadeklarowany w kontekście globalnym (poza zakresem funkcji), wszystkie kodu w programie jest w trybie z ograniczeniami. Jeśli jest on zadeklarowany w funkcji, cały kod w funkcji jest w trybie z ograniczeniami. Na przykład w poniższym przykładzie cały kod jest w trybie z ograniczeniami i deklaracja zmiennej poza funkcją powoduje błąd składni "Zmiennej niezdefiniowana w trybie z ograniczeniami."  
  
```JavaScript  
"use strict";  
function testFunction(){  
    var testvar = 4;  
    return testvar;  
}  
  
// This causes a syntax error.  
testvar = 5;  
  
```  
  
 W poniższym przykładzie kodu wewnątrz `testFunction` jest w trybie z ograniczeniami. Deklaracja zmiennej poza funkcją nie powoduje błąd składniowy, ale nie deklaracji wewnątrz funkcji.  
  
```JavaScript  
function testFunction(){  
    "use strict";  
    // This causes a syntax error.  
    testvar = 4;  
    return testvar;  
}  
testvar = 5;  
  
```  
  
<a name="rest"></a>   
## <a name="restrictions-on-code-in-strict-mode"></a>Ograniczenia dotyczące kodu w trybie z ograniczeniami  
 W poniższej tabeli wymieniono najważniejsze ograniczenia, które stosuje się w trybie z ograniczeniami.  
  
|||||  
|-|-|-|-|  
|**Element języka**|**Ograniczenie**|**Błąd**|**Przykład**|  
|Zmienna|Bez deklarowania go za pomocą zmiennej.|SCRIPT5042: Zmienna niezdefiniowana w trybie z ograniczeniami|`testvar = 4;`|  
|Właściwości tylko do odczytu|Zapisywanie właściwości tylko do odczytu.|SCRIPT5045: Przypisanie do właściwości tylko do odczytu jest niedozwolone w trybie z ograniczeniami|`var testObj = Object.defineProperties({}, {     prop1: {         value: 10,         writable: false // by default     },     prop2: {         get: function () {         }     } }); testObj.prop1 = 20;  testObj.prop2 = 30;`|  
|Inne niż extensible właściwości|Dodawanie właściwości do obiektu, którego `extensible` atrybut ma ustawioną `false`.|SCRIPT5046: Nie można utworzyć właściwości dla obiektu extensible|`var testObj = new Object();  Object.preventExtensions(testObj);  testObj.name = "Bob";`|  
|`delete`|Usuwanie zmiennej, funkcji lub argumentu.<br /><br /> Usuwanie właściwości którego `configurable` atrybut ma ustawioną `false`.|SCRIPT1045: Wywołanie usunięcia na \<wyrażenia > jest niedozwolone w trybie z ograniczeniami|`var testvar = 15; function testFunc() {}; delete testvar; delete testFunc;  Object.defineProperty(testObj, "testvar", {     value: 10,     configurable: false     }); delete testObj.testvar;`|  
|Duplikowanie właściwości|Definiowanie właściwości więcej niż raz w literału obiektu.|SCRIPT1046: Wiele definicji właściwości jest niedozwolone w trybie z ograniczeniami|`var testObj = {     prop1: 10,     prop2: 15,     prop1: 20 };`|  
|Duplikowanie nazwę parametru|Użycie nazwy parametru więcej niż raz w funkcji.|SCRIPT1038: Nazwy parametrów formalnych zduplikowane są niedozwolone w trybie z ograniczeniami|`function testFunc(param1, param1) {     return 1; };`|  
|Przyszłe zastrzeżonych słów kluczowych|Przy użyciu przyszłych zastrzeżonego słowa kluczowego jako nazwy zmiennej lub funkcji.|SCRIPT1050: Użycie zarezerwowanych na przyszłość słów jako identyfikator jest nieprawidłowy. Nazwa identyfikatora jest zarezerwowana w trybie z ograniczeniami.|-                      `implements`<br /><br /> -                      `interface`<br /><br /> -                      `package`<br /><br /> -                      `private`<br /><br /> -                      `protected`<br /><br /> -                      `public`<br /><br /> -                      `static`<br /><br /> -                      `yield`|  
|Octals|Przypisywanie wartość ósemkową do literał liczbowy lub próba użycia ucieczki na wartość ósemkową.|SCRIPT1039: Ósemkowe literały numeryczne i znaki ucieczki nie są dozwolone w trybie z ograniczeniami|`var testoctal = 010; var testescape = \010;`|  
|`this`|Wartość `this` nie jest konwertowany na obiekt globalny, gdy jest `null` lub `undefined`.||`function testFunc() {     return this; } var testvar = testFunc();`<br /><br /> W trybie — ścisłe, wartość `testvar` jest obiekt globalny, ale w trybie z ograniczeniami jest wartość `undefined`.|  
|`eval`jako identyfikator|Ciąg "eval" nie można użyć jako identyfikatora (nazwa typu zmienną lub funkcję, nazwa parametru i tak dalej).||`var eval = 10;`|  
|Funkcja zadeklarowana wewnątrz instrukcji lub bloku|Nie można zadeklarować funkcji wewnątrz instrukcji lub bloku.|SCRIPT1047: W trybie z ograniczeniami deklaracje funkcji nie mogą być zagnieżdżone wewnątrz instrukcji lub bloku. Mogą występować jedynie na najwyższym poziomie lub bezpośrednio wewnątrz ciała funkcji.|`var arr = [1, 2, 3, 4, 5]; var index = null; for (index in arr) {     function myFunc() {}; }`|  
|Zmienna zadeklarowana wewnątrz `eval` — funkcja|Jeśli zmienna jest zadeklarowana wewnątrz `eval` funkcji, nie można użyć poza tą funkcją.|SCRIPT1041: Nieprawidłowe użycie "eval" w trybie z ograniczeniami|`eval("var testvar = 10"); testvar = 15;`<br /><br /> Ocena pośrednie jest możliwa, ale nadal nie można użyć Zmienna zadeklarowana poza `eval` funkcji.<br /><br /> `var indirectEval = eval; indirectEval("var testvar = 10;"); document.write(testVar);`<br /><br /> Ten kod powoduje błąd SCRIPT5009: "testVar" jest niezdefiniowany.|  
|`Arguments`jako identyfikator|Ciągu "argumentów" nie można użyć jako identyfikatora (nazwa typu zmienną lub funkcję, nazwa parametru i tak dalej).|SCRIPT1042: Nieprawidłowe użycie "arguments" w trybie z ograniczeniami|`var arguments = 10;`|  
|`arguments`wewnątrz funkcji|Nie można zmienić wartości członków lokalnej `arguments` obiektu.||`function testArgs(oneArg) {     arguments[0] = 20; }`<br /><br /> W trybie z ograniczeniami nie można zmienić wartości `oneArg` parametru, zmieniając wartość `arguments[0]`, dzięki czemu zarówno wartość `oneArg` i `arguments[0]` wynosi 20. W trybie z ograniczeniami, zmiana wartości `arguments[0]` nie ma wpływu na wartość `oneArg`, ponieważ `arguments` obiekt jest tylko lokalna kopia.|  
|`arguments.callee`|Nie jest dozwolone.||`function (testInt) {     if (testInt-- == 0)         return;     arguments.callee(testInt--); }`|  
|`with`|Nie jest dozwolone.|SCRIPT1037: instrukcje "with" nie są dozwolone w trybie z ograniczeniami|`with (Math){     x = cos(3);     y = tan(7); }`|