---
title: Sterowanie przepływem programu (JavaScript) | Dokumentacja firmy Microsoft
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
- Boolean values, program flow
- continue statement
- break statement
- control flow, about control flow
ms.assetid: 4ef58c82-e5d6-4b09-9458-cf0aa3b39bf5
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 20c256d26c6991067d7c25c0c835eda6e5e5aac6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24789304"
---
# <a name="controlling-program-flow-javascript"></a>Sterowanie przepływem programu (JavaScript)
Zwykle instrukcje w [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] skryptu są wykonywane jeden po drugim, w kolejności, w którym są zapisywane. Jest nazywana wykonywania sekwencyjnego, a jest to domyślny kierunek przepływu danych programu.  
  
 Alternatywą do wykonywania sekwencyjnego przesyła przepływem programu do innej części skryptu. Oznacza to, ale nie wykonuje następnej instrukcji w sekwencji, innego instrukcja jest wykonywana zamiast tego.  
  
 Aby skrypt przydatne, to przeniesienie kontrolki musi zostać wykonane w sposób logiczny. Przekazanie sterowania program opiera się na decyzję, której wynikiem jest instrukcją prawdy (zwraca wartość Boolean **true** lub **false**). Należy utworzyć wyrażenie, a następnie sprawdź, czy jej wynikiem jest wartość true. Istnieją dwa główne rodzaje struktury programu, które w tym celu.  
  
 Pierwsza to struktura zaznaczenia. Umożliwia ona Określ alternatywny przebieg przepływu program tworzenia połączenia w programie (na przykład rozwidlenie w drodze). Cztery struktury wyboru są dostępne w [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  
  
-   Struktura pojedynczego wyboru (**Jeśli**),  
  
-   Struktura zaznaczenia o podwójnej precyzji (**if/else**),  
  
-   operator trójargumentowy wbudowany`?:`  
  
-   Struktura wielokrotnego wyboru (`switch`).  
  
 Drugi typ Struktura kontroli programu to struktura powtarzania. Umożliwia ona określić akcję jest powtarzany, gdy spełnienia określonego warunku jest PRAWDA. Gdy zostaną spełnione warunki instrukcji sterowania (zazwyczaj po niektórych określonej liczby iteracji), kontrola przechodzi do następnej instrukcji poza struktury powtarzania. Są dostępne w czterech struktury powtarzania [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  
  
-   wyrażenie jest testowany w górnej części pętli (`while`),  
  
-   wyrażenie jest testowany w dolnej części pętli (**czy / podczas**),  
  
-   działać na każdej z właściwości obiektu (**/w**).  
  
-   Licznik kontrolowane powtarzanie (**dla**).  
  
 Można tworzyć skrypty dość złożone wyboru zagnieżdżenia i stosu i struktury sterujące powtarzania.  
  
 Trzeci formę przepływu danych strukturalnych programu są udostępniane przez obsługi wyjątków, które nie są objęte w tym dokumencie.  
  
## <a name="using-conditional-statements"></a>Warunkowe instrukcje Using  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]obsługuje **Jeśli** i [if... else](../javascript/reference/if-dot-dot-dot-else-statement-javascript.md) warunkowe instrukcje. W **Jeśli** instrukcje testowany warunek i jeśli test odpowiedniego spełnia warunek [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] wykonywany jest kod. W `if...else` instrukcji, inny kod jest wykonywana, jeśli warunek nie powiedzie się uruchomienie testu. Najprostsza forma **Jeśli** instrukcji można zapisywać na jeden wiersz, ale multiline **Jeśli** i `if...else` instrukcje są znacznie bardziej powszechne.  
  
 W poniższych przykładach pokazano za pomocą składni **Jeśli** i `if...else` instrukcje. W pierwszym przykładzie najprostszym typu Boolean testu. Jeżeli (i tylko wtedy, gdy) elementu w nawiasach daje w wyniku (lub może zostać przekształcone na) **true**, instrukcji lub bloku instrukcji po **Jeśli** jest wykonywana.  
  
```JavaScript  
function GetReaction(newShip, color, texture, dayOfWeek)  
{  
   // The test succeeds if the newShip Boolean value is true.  
   if (newShip)  
   {  
      return "Champagne Bottle";  
   }  
  
   // The test succeeds if both conditions are true.  
   if (color == "deep yellow" && texture == "large and small wrinkles")  
   {  
      return "Is it a crenshaw melon?";  
   }  
  
   // The test succeeds if either condition is true.  
   if ((dayOfWeek == "Saturday") || (dayOfWeek == "Sunday"))  
   {  
      return "I'm off to the beach!";  
   }  
   else  
   {  
      return "I'm going to work.";  
   }  
}  
  
var reaction = GetReaction(false, "deep yellow", "smooth", "Sunday");  
document.write(reaction);  
  
// Output: I'm off to the beach!  
```  
  
## <a name="conditional-operator"></a>Operator warunkowy  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]obsługuje również niejawne warunkowego formularza. Używa znak zapytania po warunek do sprawdzenia (zamiast wyraz **Jeśli** przed warunek). Określa również dwie alternatywne: jeden do użycia, jeśli jest spełniony warunek, a drugi Jeśli nie jest. Te możliwości muszą być rozdzielone dwukropkiem.  
  
```JavaScript  
var AMorPM = (theHour >= 12) ? "PM" : "AM";  
```  
  
 Jeśli masz kilka warunków, które ma zostać przetestowana ze sobą i wiesz, co jest bardziej prawdopodobne zakończone powodzeniem lub niepowodzeniem od innych, można użyć funkcji o nazwie "ocena zwarcia" szybkość wykonywania skryptu. Gdy [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] ocenia wyrażenie logiczne tylko ocenia wymagane do uzyskania wyniku dowolną liczbę wyrażeń podrzędnych.  
  
 Na przykład, jeśli masz takich jak wyrażenia typu AND ((x == 123) & & (y == 6)), [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] najpierw sprawdza, czy x 123. Jeśli nie, całe wyrażenie nie może być ma wartość true, nawet jeśli y jest równa 6. W związku z tym testem y nigdy nie nawiązuje, i [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] zwraca wartość **false**.  
  
 Podobnie jeśli tylko jeden z kilku warunków musi mieć **true** (przy użyciu &#124; &#124; operator), testowanie zatrzymuje jak dowolnego jednego warunku przekazuje testu. Jest to skuteczne, jeśli warunki, które ma zostać przetestowana wymagają wykonywania wywołań funkcji lub innych złożonych wyrażeń. Z tym pamiętać podczas pisania lub wyrażeń, umieść warunki, które najprawdopodobniej będą **true** pierwszy. Podczas pisania i wyrażeń, umieść warunki, które najprawdopodobniej będą **false** pierwszy.  
  
 Zaletą projektowania skryptu w ten sposób jest to, że **runsecond()** nie zostanie wykonany w poniższym przykładzie, jeśli **runfirst()** zwraca wartość 0.  
  
```JavaScript  
if ((runfirst() == 0) || (runsecond() == 0)) {  
    // some code  
}  
```  
  
## <a name="using-loops"></a>Przy użyciu pętli  
 Istnieje kilka sposobów, można wykonać instrukcji lub bloku instrukcji wielokrotnie. Ogólnie rzecz biorąc, jest nazywany powtarzających się wykonanie *zapętlenia* lub *iteracji*. Iteracja jest po prostu pojedynczego wykonania pętli. Zazwyczaj jest kontrolowana przez test zmiennej, w którym jest przeprowadzana wartości, które jest zmieniana pętli. [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]cztery typy sprzężeń: [dla](../javascript/reference/for-statement-javascript.md) pętle, [for... w](../javascript/reference/for-dot-dot-dot-in-statement-javascript.md) pętle, [podczas](../javascript/reference/while-statement-javascript.md) pętle, [do... while](../javascript/reference/do-dot-dot-dot-while-statement-javascript.md) pętli.  
  
## <a name="using-for-loops"></a>Przy użyciu dla pętli  
 **Dla** instrukcji Określa zmienną licznika, warunku i akcji, która aktualizuje licznika. Przed każdej iteracji pętli jest testowany warunek. Jeśli test zakończy się pomyślnie, wykonywany jest kod wewnątrz pętli. Jeśli test zakończy się niepowodzeniem, kodu wewnątrz pętli nie jest wykonywana, a program nadal w pierwszym wierszu kodu bezpośrednio po pętli. Po wykonaniu pętli zmiennej licznik jest aktualizowany, przed rozpoczęciem następnej iteracji.  
  
 Jeśli nigdy nie jest spełniony warunek dla pętli, pętli nigdy nie została wykonana. Jeśli zawsze jest spełniony warunek testu, powoduje nieskończoną pętlę. Podczas pierwszej może być pożądane w niektórych przypadkach, rzadko jest, dlatego należy zachować ostrożność podczas zapisywania Twojego warunkach pętli.  
  
```JavaScript  
// The update expression ("icount++" in the following examples)  
// is executed at the end of the loop, after the block of  
// statements that forms the body of the loop is executed, and  
// before the condition is tested.  
  
// Set a limit of 10 on the loop.  
var howFar = 10;  
  
// Create an array called sum with 10 members, 0 through 9.  
var sum = new Array(howFar);  
sum[0] = 0;  
  
// Iterate from 0 through 9.  
var theSum = 0;  
for(var icount = 0; icount < howFar; icount++)  
{  
   theSum += icount;  
   sum[icount] = theSum;  
}  
  
// This code is not executed at all, because icount is not greater than howFar.  
var newSum = 0;  
for(var icount = 0; icount > howFar; icount++)  
{  
   newSum += icount;  
}  
  
// This is an infinite loop.  
var sum = 0;  
for(var icount = 0; icount >= 0; icount++)  
{  
   sum += icount;  
}  
```  
  
## <a name="using-forin-loops"></a>Przy użyciu for... w pętli  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]zapewnia specjalny rodzaj pętli krokowe wykonywanie wszystkich zdefiniowanych przez użytkownika właściwości [obiektu](../javascript/objects-and-arrays-javascript.md), lub wszystkie elementy tablicy. Licznik pętli `for...in` pętla jest ciąg znaków, a nie numeru. Zawiera nazwę bieżącej właściwości lub indeks bieżącego elementu tablicy.  
  
```JavaScript  
// Create an object with some properties  
var myObject = new Object();  
myObject.name = "James";  
myObject.age = "22";  
myObject.phone = "555 1234";  
  
// Enumerate (loop through)_all the properties in the object  
for (var prop in myObject)  
{  
    // This displays "The property 'name' is James", etc.  
    document.write("The property '" + prop + "' is " + myObject[prop]);  
    // New line.  
    document.write("<br />");    
}  
```  
  
 Mimo że `for...in` pętle wyglądać podobnie do języka VBScript `For Each...Next` pętle, nie działają w taki sam sposób. [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] **For... in w** przechodzi przez właściwości [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] obiektów. Skrypt VBScript **For Each... Następny** pętli przechodzi przez elementów w kolekcji. Do kolekcji w pętli [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], należy użyć [Enumerator — obiekt](../javascript/reference/enumerator-object-javascript.md) obiektu lub, jeśli jest obecny, `forEach` metody obiektu kolekcji. Mimo że niektóre obiekty, takie jak te w programie Internet Explorer obsługuje zarówno VBScript **For Each... Następny** pętli i [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] **for... w** pętli, większość obiektów nie.  
  
## <a name="using-while-loops"></a>Przy pętle  
 A `while` pętli jest podobny do **dla** pętli. Różnica polega na tym, `while` pętli nie ma wyrażenia zmiennej lub aktualizacji wbudowanych licznika. Jeśli chcesz kontrolować powtarzających się wykonanie instrukcji lub blok instrukcji, ale wymagają bardziej złożone do reguły niż po prostu "Uruchom ten kod n razy", użyj `while` pętli. W poniższym przykładzie użyto modelu obiektów programu Internet Explorer i `while` pętli, aby zadać je użytkownikowi proste pytanie.  
  
```JavaScript  
var x = 0;  
while ((x != 5) && (x != null))  
{  
    x = window.prompt("What is my favorite number?", x);  
}  
  
if (x == null)  
    window.alert("You gave up!");  
else  
    window.alert("Correct answer!");  
```  
  
> [!NOTE]
>  Ponieważ `while` pętle bez jawnego licznika wbudowane zmienne, są bardziej narażony na nieskończonej pętli od innych typów pętli. Ponadto, ponieważ nie jest zawsze ułatwia odnajdywanie, gdzie lub czas aktualizowania warunek pętli, to proste do zapisania `while` pętli w którego warunku nigdy nie zostanie zaktualizowany. Z tego powodu należy zachować ostrożność podczas projektowania `while` pętli.  
  
 Jak wspomniano powyżej, jest również **do... while** pętli w [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] jest podobny do while pętli, z tą różnicą, że jest gwarantowana zawsze wykonać co najmniej raz, ponieważ warunek został przetestowany pod koniec pętli, a nie na początku . Na przykład powyżej pętli można ponownie zapisany jako:  
  
```JavaScript  
var x = 0;  
do  
{  
    x = window.prompt("What is my favorite number?", x);  
} while ((x != 5) && (x != null));  
  
if (x == null)  
    window.alert("You gave up!");  
else  
    window.alert("Correct answer!");  
```  
  
## <a name="using-break-and-continue-statements"></a>Przy użyciu przerywanie i kontynuować — instrukcje  
 W [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], [podziału](../javascript/reference/break-statement-javascript.md) używana jest instrukcja można zatrzymać wykonywania pętli, jeśli niektóre warunki są spełnione. (Należy pamiętać, że **podziału** jest również używać do kończenia `switch` bloku). [Kontynuować](../javascript/reference/continue-statement-javascript.md) instrukcji można używać, aby od razu przejść do następnej iteracji, pomijanie reszty blok kodu podczas aktualizowania licznika zmiennej, jeśli wykonanie pętli się **dla** lub `for...in` pętli.  
  
 Poniższy przykład tworzy w poprzednim przykładzie, aby użyć **podziału** i **kontynuować** instrukcje, aby kontrolować pętli.  
  
```JavaScript  
var x = 0;  
do  
{  
    x = window.prompt("What is my favorite number?", x);  
  
    // Did the user cancel? If so, break out of the loop  
    if (x == null)  
        break;  
  
    // Did they enter a number?  
    // If so, no need to ask them to enter a number.  
    if (Number(x) == x)  
        continue;  
  
    // Ask user to only enter in numbers  
    window.alert("Please only enter in numbers!");  
  
} while (x != 5)  
  
if (x != 5)  
    window.alert("You gave up!");  
else  
    window.alert("Correct answer!");  
```