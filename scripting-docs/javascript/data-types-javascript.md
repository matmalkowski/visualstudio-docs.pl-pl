---
title: Typy danych (JavaScript) | Dokumentacja firmy Microsoft
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
helpviewer_keywords: Boolean data type, supported data types
ms.assetid: c7a6bd3a-4b1c-4dbe-8505-106dbf483b41
caps.latest.revision: "35"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aa3a0e4cdbb25019758f89958afdf06c11f01a34
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="data-types-javascript"></a>Typy danych (JavaScript)
W [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], istnieją trzy podstawowe typy danych, dwa złożone typy danych i dwa specjalne typy danych.  
  
## <a name="primary-data-types"></a>Podstawowe typy danych  
 Typy danych podstawowych (pierwotne):  
  
-   String  
  
-   Wartość liczbowa  
  
-   Boolean  
  
## <a name="composite-data-types"></a>Złożone typy danych  
 Typy danych złożone (odwołanie):  
  
-   Obiekt  
  
-   Tablica  
  
## <a name="special-data-types"></a>Specjalne typy danych  
 Typy danych specjalne są:  
  
-   Null  
  
-   Niezdefiniowana  
  
## <a name="string-data-type"></a>Typ danych ciągu  
 Wartość ciągu jest łańcuch zero lub więcej znaków Unicode (liter, cyfr i znaków interpunkcyjnych). String — typ danych umożliwia reprezentują tekst w [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]. Literały ciągu w skryptach obejmują są ujęte w cudzysłów pojedynczym lub podwójnym. Podwójny cudzysłów mogą być zawarte w ciągach ujęta w znaki apostrofu i pojedynczy cudzysłów mogą być zawarte w ciągach ujęta w znaki podwójnego cudzysłowu. Poniżej przedstawiono przykłady ciągów znaków:  
  
```JavaScript  
"Happy am I; from care I'm free!"  
'"Avast, ye lubbers!" roared the technician.'   
"45"  
'c'  
```  
  
 Zwróć uwagę, że [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] nie ma typu oznaczającego pojedynczy znak. Do reprezentowania jednego znaku w [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], Utwórz ciąg składający się z tylko jednego znaku. Ciąg zawierający zero znaków ("") to ciąg pusty (zerowej długości).  
  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]udostępnia sekwencji unikowych, które można uwzględnić w ciągach znaków, których nie można wpisać bezpośrednio utworzyć. Na przykład `\t` określa znak tabulacji. Aby uzyskać więcej informacji, zobacz [znaki specjalne](../javascript/advanced/special-characters-javascript.md).  
  
## <a name="number-data-type"></a>Typ danych numerycznych  
 W [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], odróżnia liczb całkowitych i zmiennoprzecinkowych wartości; [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] liczba może być albo (wewnętrznie [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] reprezentuje wszystkie liczby jako wartości zmiennoprzecinkowych).  
  
### <a name="integer-values"></a>Wartości całkowite  
 Liczby całkowite mogą być dodatnie liczby całkowite, ujemnej liczby całkowite i 0. One być reprezentowane w podstawie 10 (dziesiętna), podstawowe 16 (szesnastkowo) i podstawowy 8 (ósemkowe). Większość numerów w [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] są zapisywane w dziesiętnych.  
  
 Określa szesnastkową liczby całkowite ("szesnastkowych") dodając wiodące "0 x" (zero a x &#124; X). Zawierają cyfr od 0 do 9 i litery od A do F (wielkie i małe litery) tylko. Litery od A do F są używane do reprezentowania jako pojedynczy cyfr, 10 do 15 w podstawie 10. 0xF jest odpowiednikiem 15 i 0x10 jest odpowiednikiem 16.  
  
 Określa się ósemkową liczby całkowite, dodając je z początku "0" (zero). Mogą zawierać cyfry od 0 do 7 tylko. Liczba, która wiodące "0", a następnie zawiera cyfry, "8" lub "9" jest interpretowany jako liczbę dziesiętną.  
  
 Zarówno szesnastkowym i ósemkową liczby może być liczbą ujemną, ale nie mogą jednak mieć dziesiętną części i nie można zapisać w notacji naukowej (wykładniczej).  
  
> [!NOTE]
>  Począwszy od [!INCLUDE[jsv9text](../javascript/includes/jsv9text-md.md)], [funkcja parseInt](../javascript/reference/parseint-function-javascript.md) nie traktuje ciąg, który zawiera prefiks "0", jako ósemkowe. Jeśli nie używasz `parseInt` działać, jednak ciągów z prefiksem "0", może nadal być interpretowane jako ósemkowe.  
  
### <a name="floating-point-values"></a>Wartości zmiennoprzecinkowe  
 Wartości zmiennoprzecinkowych można liczby całkowite z części dziesiętnych. Ponadto może być wyrażona w notacji wykładniczej. Oznacza to, że wielkie i małe "e" jest używana do reprezentowania "dziesięciu do potęgi równej". [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]reprezentuje liczb przy użyciu standardowego zmiennoprzecinkowe 8-bajtowej IEEE-754 dla reprezentacji liczbowej. Oznacza to, że można pisać liczby tak duże jak 1.79769x10<sup>308</sup>i jak 5 x 10<sup>-324</sup>. Numer zawierający punkt dziesiętny, na którym jest jeden "0" przed separatorem dziesiętnym jest interpretowany jako liczbę dziesiętną zmiennoprzecinkowych.  
  
 Zwróć uwagę, że liczba, która rozpoczyna się od "0 x" lub "00" i zawiera punkt dziesiętny, zostanie wygenerowany błąd. Poniżej przedstawiono kilka przykładów [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] cyfry.  
  
|Wartość liczbowa|Opis|Wartość dziesiętną|  
|------------|-----------------|------------------------|  
|.0001, 0,0001, 1e-4, 1.0e-4|Cztery równoważne liczb zmiennoprzecinkowych.|0.0001|  
|3.45e2|Liczba zmiennoprzecinkowa.|345|  
|45|Liczba całkowita.|45|  
|0378|Liczba całkowita. Chociaż wydaje liczbę ósemkową (zaczyna się od zera), 8 nie jest prawidłową ósemkowego, więc numer jest traktowane jako wartości dziesiętnej.|378|  
|0377|Ósemkową liczby całkowitej. Należy zauważyć, że chociaż wydaje się jeden mniejszej niż powyższa liczba, wartość rzeczywista jest zupełnie różne.|255|  
|0.0001|Zmiennoprzecinkowa numer. Mimo to rozpoczyna się od zera, nie jest liczbą ósemkową ponieważ ma ona separatorem dziesiętnym.|0.0001|  
|00.0001|Jest to błąd. Dwa zera wiodące oznaczyć numer jako ósemkowe, ale octals nie są dozwolone dziesiętną składnika.|N/d (błąd kompilatora)|  
|0Xff|Szesnastkową liczby całkowitej.|255|  
|0x37CF|Szesnastkową liczby całkowitej.|14287|  
|0x3e7|Szesnastkową liczby całkowitej. Należy zauważyć, że "e" nie jest traktowana jako potęgowania.|999|  
|0x3.45e2|Jest to błąd. Szesnastkowe nie może zawierać części dziesiętnych.|N/d (błąd kompilatora)|  
  
 Ponadto [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] zawiera liczby o wartości specjalnych. Są to:  
  
-   NaN (nieliczbową). To jest używany podczas operacji matematycznych odbywa się na nieodpowiednie dane, takie jak ciągów lub niezdefiniowaną wartość  
  
-   Nieskończoności dodatniej. Jest używana, gdy jest zbyt duży, aby reprezentować w liczbą dodatnią[!INCLUDE[javascript](../javascript/includes/javascript-md.md)]  
  
-   Nieskończoności ujemnej. Jest używana, gdy jest zbyt duży, aby reprezentować w liczbą ujemną.[!INCLUDE[javascript](../javascript/includes/javascript-md.md)]  
  
-   Dodatnie i ujemne 0. [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]rozróżnia między zero dodatnie i ujemne.  
  
## <a name="boolean-data-type"></a>Typ logiczny danych (boolowski)  
 Ciąg i liczba typy danych mogą mieć praktycznie nieograniczoną liczbę różne wartości, typu Boolean może zawierać tylko dwa. Są one literały `true` i `false`. Wartość logiczna ma truth-value: Określa, czy warunek jest spełniony.  
  
 Porównania wprowadzone w skryptach zawsze mają wynik Boolean. Należy rozważyć następujący wiersz [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] kodu.  
  
```JavaScript  
y = (x == 2000);  
```  
  
 Tutaj, wartość zmiennej `x` jest porównywany z numerem 2000. Jeśli tak jest, wynik porównania jest wartość logiczna **true**, który jest przypisany do zmiennej `y`. Jeśli `x` nie równa się 2000, a następnie wynik porównania jest wartość logiczna `false`.  
  
 Wartości logiczna są szczególnie przydatne w struktury sterujące. Poniższy kod łączy porównania, która tworzy wartość logiczną bezpośrednio z instrukcji, która korzysta z niego. Należy rozważyć [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] przykładowy kod.  
  
```JavaScript  
if (x == 2000) {  
    z = z + 1;  
}  
else {  
    x = x + 1;  
}  
```  
  
 `if/else` Instrukcji w [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] wykonuje jedno działanie, jeśli jest wartość logiczna `true` (`z = z + 1`) i akcji alternatywnego, jeśli jest wartość logiczna `false` (`x = x + 1`).  
  
 Można użyć dowolnego wyrażenia jako wyrażenie porównawczych. Wyrażeń na 0, null, niezdefiniowane lub pusty ciąg jest interpretowany jako `false`. Wyrażenie obliczane do innych wartość jest interpretowana jako `true`. Na przykład można użyć wyrażenia takie jak:  
  
```JavaScript  
// This may not do what you expect. See below!  
if (x = y + z)   
```  
  
 Należy pamiętać, że wiersz powyżej nie sprawdza, czy `x` jest równa `y + z`, ponieważ jest używany tylko jeden znak równości (operator przypisania). Zamiast tego przypisuje wartość w powyższym kodzie `y + z` do zmiennej `x`i sprawdza, czy wynik wyrażenia (wartość `x`) wynosi zero. Aby sprawdzić, czy `x` jest równa `y + z`, należy użyć następującego kodu.  
  
```JavaScript  
// This is different from the code above!  
if (x == y + z)   
```  
  
 Aby uzyskać więcej informacji dotyczących porównania, zobacz [sterowanie przepływem programu](../javascript/controlling-program-flow-javascript.md).  
  
## <a name="the-null-data-type"></a>Typ danych null  
 `null` — Typ danych jest tylko jedna wartość [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]: wartość null. `null` Nie można użyć słowa kluczowego jako nazwy funkcji lub zmienna.  
  
 Zmienna, która zawiera `null` nie zawiera nieprawidłowy numer, ciąg, wartość logiczna, tablicy ani obiektu. Można wymazać zawartość zmiennej (bez usuwania zmiennej) przez przypisanie `null` wartość.  
  
 Zwróć uwagę, że w [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], `null` nie jest taka sama jak 0 (ponieważ jest on C i C++). Należy również zauważyć, że `typeof` operatora w [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] raporty `null` wartości jako typu `Object`, nie jest typu `null`. Jest to zachowanie może być mylące dla zapewnienia zgodności.  
  
## <a name="the-undefined-data-type"></a>Niezdefiniowany typ danych  
 `undefined` Wartość jest zwracana, gdy właściwość obiektu, który nie istnieje, lub zmienna, która została zadeklarowana, ale nigdy nie ma miał przypisaną do niej wartość.  
  
 należy sprawdzić, jeśli istnieje zmienna, porównując go do `undefined`, mimo że można sprawdzić, czy jego typ jest `undefined` porównując typu zmienną do ciągu "undefined". Poniższy przykład przedstawia sposób sprawdzić zmiennej `x` został zadeklarowany:  
  
```JavaScript  
  
var x;  
  
// This method works.  
if (x == undefined) {  
    document.write("comparing x to undefined <br/>");  
}  
.  
// This method doesn't work - you must check for the string "undefined".  
if (typeof(x) == undefined) {  
    document.write("comparing the type of x to undefined <br/>");  
}  
// This method does work.   
if (typeof(x) == "undefined") {  
    document.write("comparing the type of x to the string 'undefined'");  
}  
  
// Output:   
// comparing x to undefined   
// comparing the type of x to the string 'undefined'  
  
```  
  
 Można także porównać niezdefiniowana wartość do `null`. Jest to porównanie `true` Jeśli właściwość `someObject.prop` jest `null` lub, jeśli właściwość `someObject.prop` nie istnieje.  
  
```JavaScript  
someObject.prop == null;  
```  
  
 Aby dowiedzieć się, czy istnieje właściwość obiektu, można użyć **w** operator:  
  
```JavaScript  
if ("prop" in someObject)  
    // someObject has the property 'prop'  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Obiekty i tablice](../javascript/objects-and-arrays-javascript.md)   
 [TypeOf — Operator](../javascript/reference/typeof-operator-decrementjavascript.md)