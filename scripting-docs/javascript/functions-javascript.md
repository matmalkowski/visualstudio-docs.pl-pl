---
title: Funkcje (JavaScript) | Dokumentacja firmy Microsoft
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
helpviewer_keywords: intrinsic JavaScript functions
ms.assetid: e2a72b5a-3edd-43d8-95e8-91721b38c1c1
caps.latest.revision: "24"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fd5626af6417b5f0010545874bd15c86b30a303a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="functions-javascript"></a>Funkcje (JavaScript)
[!INCLUDE[javascript](../javascript/includes/javascript-md.md)]funkcje wykonywania akcji; można także wrócić wartości. Czasami są wyniki obliczeń lub porównania. Funkcje są również nazywane "metody globalne".  
  
 Funkcje połączyć kilka operacji pod jedną nazwą. Dzięki temu można uprościć kod. Można zapisać zestaw instrukcji, nadaj jej nazwę, a następnie wykonaj całego zestawu przez wywołanie jego i przekazanie do niego wszystkie informacje niezbędne.  
  
 Informacje są przekazywane do funkcji umieszczając je w nawiasach po nazwie funkcji. Rodzajów informacji, które są przekazywane do funkcji są nazywane argumentów lub parametrów. Niektóre funkcje nie przyjmuje żadnych argumentów w ogóle, podczas gdy inne wykorzystują co najmniej jeden argument. W niektórych funkcjach liczba argumentów zależy od tego, jak używasz funkcji.  
  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]obsługuje dwa rodzaje funkcji: te, które są wbudowane w języku, a także utworzyć samodzielnie.  
  
## <a name="built-in-functions"></a>Funkcje wbudowane  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] Języka zawiera kilka wbudowanych funkcji. Niektóre pozwalają obsłużyć wyrażeń i znaków specjalnych, podczas gdy inne Konwertowanie ciągów na wartości liczbowe.  
  
 Zobacz [JavaScript — metody](../javascript/reference/javascript-methods.md) informacji o tych funkcji wbudowanych.  
  
## <a name="creating-your-own-functions"></a>Tworzenie własnych funkcji  
 Można tworzyć własne funkcje i używać ich w razie potrzeby. Definicja funkcji składa się z instrukcji function i blok [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] instrukcje.  
  
 **CheckTriplet** funkcja w poniższym przykładzie ma długości boków trójkąta jako jego argumenty. Oblicza od nich trójkąt czy trójkąt przez sprawdzenie, czy trzech cyfr stanowią Trzykolumnowa Pitagorasa (kwadratowe długości przeciwprostokątnej trójkąt jest taki sam, jak Suma kwadratów długości obu stron) . Funkcja checkTriplet wywołuje jeden z dwóch innych funkcji, aby rzeczywista testu.  
  
 Zwróć uwagę na bardzo niewielka liczba ("epsilon") jako zmienną testowania w wersji zmiennoprzecinkowe testu. Ze względu na wątpliwości i błędów zaokrąglania obliczeń zmiennoprzecinkowych nie jest praktyczne nawiązać bezpośrednie testu czy trzech cyfr stanowi Trzykolumnowa Pitagorasa, jeśli nie wiadomo, że wszystkie trzy wartości być liczbami całkowitymi. Ponieważ bezpośrednie testu jest dokładniejsze, kod w tym przykładzie określa, czy jest odpowiedni i, jeśli jest, używa go.  
  
```JavaScript  
var epsilon = 0.00000000001; // Some very small number to test against.  
  
// The test function for integers.  
function integerCheck(a, b, c)   
{  
   // The test itself.  
   if ( (a*a) == ((b*b) + (c*c)) )     
      return true;  
  
   return false;  
} // End of the integer checking function.  
  
// The test function for floating-point numbers.  
function floatCheck(a, b, c)     
{  
   // Make the test number.  
   var delta = ((a*a) - ((b*b) + (c*c)))  
  
   // The test requires the absolute value  
   delta = Math.abs(delta);  
  
   // If the difference is less than epsilon, then it's pretty close.  
   if (delta < epsilon)     
      return true;  
  
   return false;  
} // End of the floating-poing check function.  
  
// The triplet checker.   
function checkTriplet(a, b, c)  
{   
   // Create a temporary variable for swapping values  
   var d = 0;   
  
   // First, move the longest side to position "a".  
  
   // Swap a and b if necessary  
   if (b > a)  
   {  
      d = a;  
      a = b;  
      b = d;  
   }  
  
   // Swap a and c if necessary  
   if (c > a)  
   {  
      d = a;  
      a = c;  
      c = d;  
   }  
  
   // Test all 3 values. Are they integers?  
   if (((a % 1) == 0) && ((b % 1) == 0) && ((c % 1) == 0))  
   {   
      // If so, use the precise check.  
      return integerCheck(a, b, c);   
   }  
   else  
   {  
      // If not, get as close as is reasonably possible.  
      return floatCheck(a, b, c);   
   }  
} // End of the triplet check function.  
  
// The next three statements assign sample values for testing purposes.  
var sideA = 5;  
var sideB = 5;  
var sideC = Math.sqrt(50.001);  
  
// Call the function. After the call, 'result' contains the result.  
var result = checkTriplet(sideA, sideB, sideC);  
```  
  
<a name="Arrow"></a>   
## <a name="arrow-functions"></a>Funkcje Strzałka  
 Składnia funkcji strzałkę, `=>`, zapewnia skróconą formą określenie funkcji anonimowej. Oto składnia funkcji strzałki.  
  
```JavaScript  
([arg] [, arg]) => {  
    statements  
}  
```  
  
 Wartości z lewej strony strzałki, które mogą być ujęte w nawiasy, określ argument przekazany do funkcji. Pojedynczy argument do funkcji nie wymaga nawiasów. Nawiasy są wymagane, jeżeli nie przekazano argumentów w. Definicja funkcji strzałkę po prawej stronie może być albo wyrażenia, takich jak `v + 1`, lub blok instrukcji w nawiasach klamrowych ({}).  
  
> [!IMPORTANT]
>  Składnia funkcji strzałka jest obsługiwana tylko w programie [!INCLUDE[jsv12text](../javascript/includes/jsv12text-md.md)].  
  
 Nie można użyć `new` operatora z funkcji strzałkowej.  
  
 W poniższych przykładach kodu pokazano korzystanie z funkcji strzałkowej za pomocą wyrażeń jako definicje funkcji. W pierwszym przykładzie v jest przekazywany jako argument do wyrażenia. W drugim przykładzie v i i zostały przekazane jako argumenty do wyrażenia.  
  
```  
var evens = [2, 4, 6, 8];  
  
// Using standard syntax.  
var odds = evens.map(function(v) { return v + 1; });  
  
// Using arrow function syntax.  
// Add one to each value to produce output.  
var odds = evens.map(v => v + 1);  
  
// The following line of code adds the index value to the passed  
// in value to produce output.  
// Note: the second argument to the callback function in the map   
// method is the index value (i).  
var nums = evens.map((v, i) => v + i);  
  
console.log(odds);  
console.log(nums);  
  
// Output:  
// [object Array] [3, 5, 7, 9]  
// [object Array] [2, 5, 8, 11]  
```  
  
 W poniższym przykładzie pokazano sposób użycia funkcji strzałkowej z bloku instrukcji.  
  
```JavaScript  
var fives = new Array();  
  
// Statement block, re-using nums array from previous example.  
// Note: The first argument to the callback function in forEach  
// is the value of the array element (v).  
nums.forEach(v => {  
  if (v % 5 === 0)  
    fives.push(v);  
});  
  
console.log(fives);  
  
// Output:  
// [object Array] [5]  
```  
  
 W przeciwieństwie do standardowych funkcji strzałkę funkcji udostępniania takie same leksykalne `this` obiektu jako otaczające kod, który może służyć do eliminuje konieczność obejścia, takich jak `var self = this;`.  
  
 W poniższym przykładzie pokazano, że wartość `this` obiektu w funkcji strzałkowej jest taki sam jak otaczającego kodu (nadal odwołuje się do `bob` zmiennej.  
  
```JavaScript  
var bob = {  
  _name: "Bob",  
  _friends: ["Pete", "Joe", "Larry"],  
  printFriends() {  
    this._friends.forEach(f =>  
      console.log(this._name + " knows " + f));  
  }  
}  
  
// Output:  
// Bob knows Pete  
// Bob knows Joe  
// Bob knows Larry  
```  
  
 Funkcje strzałkę również udostępniać takie same leksykalne `arguments` obiektu jako otaczającego kodu (podobnie jak `this` obiektu).  
  
<a name="Default"></a>   
## <a name="default-parameters"></a>domyślne parametry  
 Przypisując wartości początkowej, można określić wartości domyślnej dla parametru w funkcji. Wartość domyślna może być wartością stałą lub wyrażenie.  
  
> [!IMPORTANT]
>  Domyślne parametry są obsługiwane tylko w [!INCLUDE[jsv12textExp](../javascript/includes/jsv12textexp-md.md)].  
  
 W poniższym przykładzie y wartość domyślna to 10, a wartość domyślna z wynosi 20. Funkcja użyje 10 jako wartość y, chyba że obiekt wywołujący przekazuje unikatowe wartości (lub undefined) jako drugi argument. Funkcja użyje jako wartość z 20, chyba że obiekt wywołujący przekazuje unikatowe wartości (lub undefined) jako trzeci argument.  
  
```JavaScript  
var val = 20;  
  
function f(x, y=10, z=val) {  
  return x + y + z;  
}  
  
console.log(f(3));  
console.log(f(3, 3));  
console.log(f(3, 3, 3));  
  
// Output:  
// 33  
// 26  
// 9  
```  
  
<a name="Rest"></a>   
## <a name="rest-parameters"></a>Parametrów REST  
 Parametry REST, określony przez operator () rozpowszechniania umożliwiają włączenie kolejnych argumentów w wywołaniu funkcji do tablicy.  
  
 Pozostałe parametry, eliminując konieczność stosowania `arguments` obiektu. Pozostałe parametry różnią się od `arguments` obiekt na kilka sposobów, takich jak:  
  
-   Parametr rest jest wystąpieniem bieżącej tablicy i w związku z tym obsługuje operacje wykonywane na tablicy.  
  
-   Parametr rest zawiera tylko kolejne argumenty, które nie są przekazywane jako oddzielne argumenty (nazwane) w (i odwrotnie, `arguments` obiekt zawiera wszystkie argumenty przekazane do funkcji).  
  
> [!IMPORTANT]
>  Pozostałe parametry i operator rozpiętości są obsługiwane tylko w [!INCLUDE[jsv12text](../javascript/includes/jsv12text-md.md)].  
  
 W poniższym przykładzie kodu "tekst hello" wartość true przekazany jako tablica wartości i przechowywane w parametrze y. Parametr rest musi być ostatnim parametrem funkcji.  
  
```JavaScript  
function f(x, ...y) {  
  // y is an array.  
  return x * y.length;  
}  
  
console.log(f(3, "hello", true));  
  
// Output:  
// 6  
  
```  
  
 Dodatkowe użycia operator rozpiętości, zobacz [rozkładu Operator](../javascript/reference/spread-operator-decrement-dot-dot-dot-javascript.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja języka JavaScript](../javascript/javascript-language-reference.md)