---
title: Zakres zmiennej (JavaScript) | Dokumentacja firmy Microsoft
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
- scope, JavaScript
- variable scope [JavaScript]
- variables, scope [JavaScript]
ms.assetid: a811a9a6-856f-46e9-8be3-f2d22a0c245f
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5afc99bf3d1006b68e1d6c4c8d5bbcfc90eb776f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24789115"
---
# <a name="variable-scope-javascript"></a>Zakres zmiennej (JavaScript)
[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]ma dwa zakresy: globalne i lokalne. Zmienna, która jest zadeklarowana poza definicją funkcji jest zmienną globalną i jego wartość jest dostępna i modyfikować w programie. Zmienna, która jest zadeklarowana w definicji funkcji jest lokalny. Jest tworzone i niszczone za każdym razem funkcja jest uruchomiona, i są niedostępne na dowolny kod poza funkcją. Język JavaScript nie obsługuje zakresie bloku (w którym zestaw nawiasów klamrowych `{. . .}` definiuje nowy zakres), z wyjątkiem w szczególnych przypadkach zmiennych o zakresie bloku.  
  
## <a name="scope-in-javascript"></a>Zakres w języku JavaScript  
 Zmienna lokalna może mieć takiej samej nazwie jako zmiennej globalnej, ale jest rozłączne; Zmiana wartości jednej zmiennej nie ma wpływu na drugi. Lokalna wersja ma znaczenie wewnątrz funkcji, w którym jest zadeklarowany.  
  
```JavaScript  
// Global definition of aCentaur.  
var aCentaur = "a horse with rider,";  
  
// A local aCentaur variable is declared in this function.  
function antiquities(){  
  
   var aCentaur = "A centaur is probably a mounted Scythian warrior";  
}  
  
antiquities();  
aCentaur += " as seen from a distance by a naive innocent.";  
  
document.write(aCentaur);  
  
// Output: "a horse with rider, as seen from a distance by a naive innocent."  
```  
  
 W języku JavaScript zmienne są oceniane tak, jakby zostały zgłoszone na początku zakresu, które istnieją w. Czasami powoduje to nieoczekiwanego zachowania, jak pokazano poniżej.  
  
```JavaScript  
var aNumber = 100;  
tweak();  
  
function tweak(){  
  
    // This prints "undefined", because aNumber is also defined locally below.  
    document.write(aNumber);  
  
    if (false)  
    {  
        var aNumber = 123;    
    }  
}  
```  
  
 Gdy [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] wykonuje funkcję, najpierw szuka wszystkie deklaracje zmiennych, na przykład `var someVariable;`. Tworzy zmienne o początkowej wartości `undefined`. Jeśli zmienna jest zadeklarowana z wartością, na przykład `var someVariable = "something";`, a następnie nadal początkowo ma wartość `undefined` i przyjmuje wartość zadeklarowane tylko wtedy, gdy jest wykonywana wiersza, który zawiera deklarację.  
  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]przetwarza wszystkie deklaracje zmiennych przed wykonaniem jakiegokolwiek kodu, czy deklaracja jest wewnątrz bloku warunkowego lub innych konstrukcji. Raz [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] ma znaleźć wszystkie zmienne, wykonuje kod w funkcji. Jeśli zmienna jest niejawnie zadeklarowanym wewnątrz funkcji - oznacza to, jeśli pojawi się po lewej stronie wyrażenia przypisania, ale nie została zadeklarowana z `var` — jest tworzony jako zmiennej globalnej.  
  
 W języku JavaScript wewnętrzny (zagnieżdżona) funkcja przechowuje odwołań do zmiennych lokalnych, które znajdują się w tym samym zakresie co funkcja, nawet po funkcja zwraca wartość. Ten zestaw odwołania jest nazywana zamknięciem. W poniższym przykładzie, drugie wywołanie funkcji wewnętrznych generuje ten sam komunikat ("Witaj zestawienia") jako pierwsze wywołanie, ponieważ parametr wejściowy funkcji zewnętrznej `name`, jest zmiennej lokalnej, która jest przechowywana w zamknięcia dla funkcji wewnętrznej.  
  
```JavaScript  
function send(name) {  
    // Local variable 'name' is stored in the closure  
    // for the inner function.  
    return function () {  
        sendHi(name);  
    }  
}  
  
function sendHi(msg) {  
    console.log('Hello ' + msg);  
}  
  
var func = send('Bill');  
func();  
// Output:  
// Hello Bill  
sendHi('Pete');  
// Output:  
// Hello Pete  
func();  
// Output:  
// Hello Bill  
```  
  
## <a name="block-scoped-variables"></a>Zmienne o zakresie bloku  
 Internet Explorer 11 wprowadzono obsługę [let](../../javascript/reference/let-statement-javascript.md) i [const](../../javascript/reference/const-statement-javascript.md), które są zmienne o zakresie bloku. Dla tych zmiennych nawiasy klamrowe `{. . .}` Zdefiniuj nowy zakres. Po ustawieniu określonej wartości jednego z tych zmiennych wartość dotyczy tylko zakres, w której jest ustawiony.  
  
 Poniższy przykład przedstawia użycie `let` i zakres bloku.  
  
> [!NOTE]
>  Poniższy kod jest obsługiwana w trybie standardów programu Internet Explorer 11 i nowszych.  
  
```JavaScript  
let x = 10;  
var y = 10;  
{  
    let x = 5;  
    var y = 5;  
    {  
        let x = 2;  
        var y = 2;  
        document.write("x: " + x + "<br/>");  
        document.write("y: " + y + "<br/>");  
        // Output:  
        // x: 2  
        // y: 2  
    }  
    document.write("x: " + x + "<br/>");  
    document.write("y: " + y + "<br/>");  
    // Output:  
    // x: 5  
    // y: 2  
}  
  
document.write("x: " + x + "<br/>");  
document.write("y: " + y + "<br/>");  
// Output:  
// x: 10  
// y: 2  
```