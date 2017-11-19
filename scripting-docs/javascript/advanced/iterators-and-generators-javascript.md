---
title: Iteratory i generatory (JavaScript) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 68ef5b2f-0349-492b-b557-73ff2a2f90cf
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 85c27969609a38b87b15c727e9c8aef89ee77032
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iterators-and-generators-javascript"></a>Iteratory i generatory (JavaScript)
Iteratora jest obiekt, który służy do przechodzenia obiektu kontenera, takie jak listy. W języku JavaScript, nie jest unikatowe, wbudowanego obiektu obiektu iteratora, ale jest obiekt, który implementuje `next` metody dostępu do następnego elementu w obiekcie kontenera.  
  
 W [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)], możesz utworzyć własne niestandardowe Iteratory. Jednak jest zwykle znacznie łatwiejsze do użycia generatory, co znacznie upraszcza tworzenie Iteratory. Generatory są typu fabryki dla Iteratory funkcji. Aby utworzyć niestandardowe iteratora, przy użyciu funkcji generator, zobacz [generatory](#Generators).  
  
> [!CAUTION]
>  Generatory są obsługiwane w [!INCLUDE[jsv12textExp](../../javascript/includes/jsv12textexp-md.md)].  
  
## <a name="iterators"></a>Iteratory  
 Implementacja iteratora JavaScript obejmuje dwie lub trzy obiekty, które są zgodne z określonych interfejsów:  
  
-   Interfejs iterable  
  
-   Iterator — interfejs  
  
-   Interfejs IteratorResult  
  
 Za pomocą tych interfejsów, można utworzyć niestandardowy Iteratory. Dzięki temu można przechodzić między nimi przy użyciu obiektu iterable `for…of` instrukcji.  
  
### <a name="iterable-interface"></a>Interfejs iterable  
 Iterable interfejs jest wymagany dla obiekt iterable (obiekt, dla którego można uzyskać iteratora). Na przykład `C` w `for (let e of C)` musi implementować interfejs Iterable.  
  
 Obiekt iterable podać metodę Symbol.iterator, która zwraca iteratora.  
  
```JavaScript  
obj[Symbol.iterator] = function() { return iterObj; }  
```  
  
 Ta właściwość musi mieć funkcję, która akceptuje żadnych argumentów i zwraca obiekt (`iterObject`) zgodne ze `Iterator` interfejsu.  
  
 Wiele wbudowanych typów, w tym tablic, są teraz iterable. `for…of` Pętli zużywa iterable obiektu. (Niemniej jednak nie wszystkie iterables wbudowanych są Iteratory. For example, tablicy obiektów nie jest iteratora sam, ale jest iterable, jest również iterable ArrayIterator.)  
  
### <a name="iterator-interface"></a>Iterator — interfejs  
 Obiekt zwrócony przez metodę Symbol.iterator musi implementować `next` metody. `next` Metoda ma następującą składnię.  
  
```JavaScript  
iterObj.next() = function() { return iterResultObj; };  
```  
  
 `next` Metoda to funkcja, która nie zwraca wartości. Funkcja zwraca obiekt (`iterResultObj`) zgodne ze `IteratorResult` interfejsu. Jeśli poprzednie wywołanie `next` zwróciła metodę iteratora `IteratorResult` którego `done` właściwość ma wartość true, a następnie zakończeniem iteracji i `next` — metoda nie zostanie ponownie wywołany.  
  
 Iteratory mogą również obejmować `return` metody, aby upewnić się, że iteratora zostanie usunięty, prawidłowo skrypt zakończy pracę z nim.  
  
### <a name="iteratorresult-interface"></a>Interfejs IteratorResult  
 Interfejs IteratorResult jest wymagany interfejs dla wyniku `next` metoda iteratora. Obiekt zwrócony przez `next` podać `done` i `value` właściwości.  
  
```JavaScript  
var iterResultObj = { done: true|false, value: value }  
```  
  
 `done` Właściwość zwraca stan iteratora `next` wywołania metody, wartość PRAWDA lub FAŁSZ. Jeśli osiągnięto koniec iteratora, `done` zwraca wartość true. Jeżeli nie osiągnięto koniec, `done` zwraca wartość FAŁSZ i wartość jest dostępna. Jeśli `done` właściwości (albo jego własnej lub to właściwość dziedziczona) nie istnieje, wynik `done` jest traktowany jako wartość false.  
  
 Jeśli `done` ma wartość false, `value` właściwość zwraca bieżącą wartość elementu iteracji. Jeśli `done` ma wartość true, jest zwracana wartość iteratora, jeśli podano wartość zwracaną. Jeśli iterator nie ma wartości zwracanej `value` jest niezdefiniowana. W takim przypadku `value` właściwości nie mogą występować z zgodnych obiektu, jeśli nie dziedziczy właściwości jawną wartość.  
  
<a name="Generators"></a>   
## <a name="generators"></a>Generatory kodu  
 Do łatwego tworzenia i używania niestandardowych Iteratory, Utwórz funkcję generator przy użyciu składni funkcji * wraz z co najmniej jeden `yield` wyrażenia. Generator funkcja iteratora (generator), co umożliwia treści generatora funkcja do wykonania. Funkcja wykonuje do następnego `yield` lub `return` instrukcji.  
  
 Wywołanie `next` metody iteracyjne, aby zwrócić wartość następnego z funkcji generatora.  
  
 W poniższym przykładzie przedstawiono generator zwracającą iterator dla obiekt ciągu.  
  
```JavaScript  
function* stringIter() {  
    var str = "bobsyouruncle";  
    var idx = 0;  
    while(idx < str.length)  
        yield str[idx++];  
}  
  
var si = stringIter();  
  
console.log(si.next().value);  
console.log(si.next().value);  
console.log(si.next().value);  
  
// Output:  
// b  
// o  
// b  
  
```  
  
 W generatorze, wyrażenie argumentu yield kończy wywołanie `next` i zwraca `IteratorResult` obiektu o dwie właściwości `done` (`done=false`) i `value` (`value=operand`). `operand`jest opcjonalna i jeśli brak następnie jego wartość jest niezdefiniowana.  
  
 W generatorze `return` instrukcji kończy generatora zwracając `IteratorResult` z `done=true` wraz z wynik opcjonalny argument dla właściwości value.  
  
 Można również użyć `yield*` wyrażenie zamiast `yield` delegować do innego generatora lub do innego obiektu iterable, takich jak tablica lub ciąg.  
  
 Jeśli Dołącz następujący kod do poprzedniego przykładu `yield*` deleguje do `stringIter` generatora.  
  
```JavaScript  
function* strIter() {  
    yield "jo";  
    yield* stringIter();  
}  
  
var si2 = strIter();  
  
console.log(si2.next().value);  
console.log(si2.next().value);  
console.log(si2.next().value);  
console.log(si2.next().value);  
  
// Output:  
// jo  
// b  
// o  
// b  
```  
  
 Można również utworzyć generatory bardziej zaawansowanych, przekazując argument `next` i przy użyciu argumentu do modyfikowania stanu generatora. `next`staje się wartość wyniku wcześniej wykonanego `yield` wyrażenia. W poniższym przykładzie, gdy przekazać wartości od 100 do `next` metody, Zresetuj wartość indeksu wewnętrzny generatora.  
  
```  
function* strIter() {  
    var str = "jobob";  
    var idx = 0;  
    while(idx , str.length) {  
        var modify = yield str[idx++];  
        if(modify == 100) {  
            idx = 0;  
        }  
    }
}
  
var si3 = strIter();  
  
console.log(si3.next().value);  
console.log(si3.next().value);  
console.log(si3.next().value);  
console.log(si3.next(100).value);  
  
// Output:  
// j  
// o  
// b  
// j  
  
```  
  
 Inne zaawansowane generatory może wywołać generator `throw` metody. Element zgłaszany błąd pojawia się do pobrania zgłoszony w momencie, gdy generatora jest wstrzymana (podjęcia kolejnej `yield` instrukcji).
