---
title: "Obiekty wewnętrzne (JavaScript) | Dokumentacja firmy Microsoft"
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
helpviewer_keywords:
- built-in objects [JavaScript]
- intrinsic objects [JavaScript]
ms.assetid: 6520c634-a7d1-4a05-8c1b-2e79f449d2e4
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 242b572c2818f9968e6d5fc51e1272e3004c0f05
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="intrinsic-objects-javascript"></a>Obiekty wewnętrzne (JavaScript)
[!INCLUDE[javascript](../javascript/includes/javascript-md.md)]udostępnia obiekty wewnętrzne (lub "wbudowanych"). Są one `Array`, `Boolean`, `Date`, `Error`, `Function`, **Global**, **JSON**, **matematyczne**,  **Numer**, `Object`, `RegExp`, i `String` obiektów. Obiekty wewnętrzne skojarzony metod, funkcji, właściwości i stałe, które opisano szczegółowo w [materiały referencyjne dotyczące języka](../javascript/reference/javascript-reference.md).  
  
## <a name="array-object"></a>Obiekt Array  
 Dolny tablicy można traktować jako właściwości obiektu i odwołuje się ich indeksu liczbowego. Należy pamiętać, że właściwości o nazwie dodane do tablicy nie może być indeksowane według numerów; są one niezależne od elementów tablicy.  
  
 Aby utworzyć nową macierz, użyj **nowe** operatora i **Array()** [Konstruktor](../javascript/reference/constructor-property-object-javascript.md), jak w poniższym przykładzie.  
  
```JavaScript  
var theMonths = new Array(12);  
theMonths[0] = "Jan";  
theMonths[1] = "Feb";  
theMonths[2] = "Mar";  
theMonths[3] = "Apr";  
theMonths[4] = "May";  
theMonths[5] = "Jun";  
theMonths[6] = "Jul";  
theMonths[7] = "Aug";  
theMonths[8] = "Sep";  
theMonths[9] = "Oct";  
theMonths[10] = "Nov";  
theMonths[11] = "Dec";  
```  
  
 Podczas tworzenia tablicy przy użyciu `Array` — słowo kluczowe, [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] obejmuje **długość** właściwość, która rejestruje liczbę wpisów. Jeśli nie określisz numeru, długość wynosi 0, a tablica nie zawiera żadnych wpisów. Jeśli określisz liczbę długość wynosi ten numer. Jeśli określono więcej niż jeden parametr, parametry są używane jako wpisy w tablicy. Ponadto liczba parametrów jest przypisany do właściwości length, jak w poniższym przykładzie, który jest odpowiednikiem poprzedniego przykładu.  
  
```JavaScript  
var theMonths = new Array("Jan", "Feb", "Mar", "Apr", "May", "Jun",   
"Jul", "Aug", "Sep", "Oct", "Nov", "Dec");  
```  
  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]automatycznie zmienia wartość **długość** po dodaniu elementów do tablicy, które zostały utworzone z `Array` — słowo kluczowe. Indeksy w tablicy [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] zawsze rozpoczynają się od 0, 1 nie, dzięki czemu właściwości length jest zawsze dłuższą o jeden niż największa indeks w tablicy.  
  
## <a name="string-object"></a>Obiekt String  
 W [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], tak jakby były to obiekty można traktować ciągów (i cyfry). [Ciągu obiektu](../javascript/reference/string-object-javascript.md) ma niektórych metod wbudowanych, korzystających z Twojej ciągów. Jednym z nich jest [substring — metoda](../javascript/reference/substring-method-string-javascript.md), która zwraca część ciągu. Trwa dwóch liczb jako jego argumenty.  
  
```JavaScript  
var aString = "0123456789";  
  
// This code sets aChunk to "456".  
var aChunk = aString.substring(4, 7);  
  
// This code sets anotherChunk to "456", using  
// the lower value index as the starting index.  
var anotherChunk = aString.substring(7, 4);  
  
// This code sets the firstLetter variable to "J"  
// by using the array in the preceding array creation example.  
firstLetter = theMonths[5].substring(0,1);  
```  
  
 Inna właściwość o `String` obiekt jest **długość** właściwości. Ta właściwość zawiera liczbę znaków w ciągu (0 dla pustego ciągu). Ta liczbową wartość i mogą być używane bezpośrednio w obliczeniach.  
  
```JavaScript  
var howLong = "Hello World".length  // Sets the howLong variable to 11.  
```  
  
## <a name="math-object"></a>Obiekt Math  
 **Matematyczne** obiektu zawiera szereg wstępnie zdefiniowanych stałe i funkcji. Stałe są określone liczbami. Jeden z tych numerów określonych jest wartość liczby pi (około 3,14159...). Jest to **Math.pi —** stałą, pokazano w poniższym przykładzie.  
  
```JavaScript  
var radius = 5;  
var circleArea = Math.PI * radius * radius;  
```  
  
 Jedną z wbudowanych funkcji **matematyczne** obiekt jest metoda potęgowania lub `Math.pow`, które podnosi liczbę do określonej potęgi. W poniższym przykładzie użyto zarówno pi i potęgowania można obliczyć wielkość sfery.  
  
```JavaScript  
var volume = (4/3)*(Math.PI*Math.pow(radius,3));  
```  
  
## <a name="date-object"></a>Obiekt Date  
 `Date` Obiekt może być używany do reprezentowania dowolnego daty i godziny, aby uzyskać bieżącą datą systemu i do obliczania różnic między datami. Ma kilka właściwości i metod, wszystkie wstępnie zdefiniowane. Ogólnie rzecz biorąc `Date` obiektu zapewnia dzień tygodnia; miesiąc, dzień i rok; i czasu w godzinach, minuty i sekundy. Informacje te są oparte na wyrażony w milisekundach czas od 1 stycznia 1970 GMT 00:00:00.000, który jest czas uniwersalny Greenwich (preferowany termin jest UTC lub "Universal Coordinated Time,", który odwołuje się do sygnały wystawiony przez World czas standardowy). [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]może obsłużyć, które są w zakresie tekstem P.N.E. 250 000 Aby 255,000 r.  
  
 Aby utworzyć nową `Date` obiektów, użyj **nowe** operatora, jak pokazano w poniższym przykładzie.  
  
```JavaScript  
var toDay = new Date();    
var thisYear = toDay.getFullYear();  
var thisMonth = theMonths[toDay.getMonth()];  
var thisDay = thisMonth  + " " + toDay.getDate() + ", " + thisYear;  
```  
  
## <a name="number-object"></a>Obiekt Number  
 Oprócz specjalne stałe numeryczne (`PI`, na przykład) dostępnych w **matematyczne** obiektu, są dostępne w kilku innych stałe [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] za pośrednictwem **numer** obiekt.  
  
|Stała|Opis|  
|--------------|-----------------|  
|Number.MAX_VALUE —|Największa możliwa liczba o 1.79E + 308; może być liczbą dodatnią lub ujemną. (Wartość różni się nieco od systemu do systemu.)|  
|Number.MIN_VALUE|Najmniejsza możliwa liczba, o 5.00E-324; może być liczbą dodatnią lub ujemną. (Wartość różni się nieco od systemu do systemu.)|  
|Number.NaN|Specjalna wartość liczbą "nieliczbową."|  
|Number.positive_infinity —|Wartość dodatnią większą niż największą liczbę dodatnią (Number.MAX_VALUE —) jest automatycznie konwertowany do tej wartości; reprezentowana jako nieskończoność.|  
|Number.negative_infinity —|Wartości ujemne więcej niż największa liczba ujemna (-Number.MAX_VALUE —) jest automatycznie konwertowany do tej wartości; reprezentowane jako — wartości infinity.|  
  
 **Number.NaN** jest stałą specjalne, który jest zdefiniowany jako "nieliczbową." Próba przeanalizować składni ciągu, który nie może być analizowana jako liczba zwraca **Number.NaN**. `NaN`porównuje nierówne dowolną liczbę i do samej siebie. Do testowania `NaN` powodować, nie porównać **Number.NaN**; użyj **isNaN()** zamiast tego działania.  
  
## <a name="json-object"></a>Obiekt JSON  
 JSON to format lekkie wymiany danych oparte na podzbiór literału obiektu notacji języka JavaScript.  
  
 Obiekt JSON oferuje dwie funkcje do przekonwertowania do i z formatu tekstu JSON. [JSON.stringify](../javascript/reference/json-stringify-function-javascript.md) funkcja serializuje obiekty i tablice w tekście JSON. [JSON.parse](../javascript/reference/json-parse-function-javascript.md) funkcja cofnąć serializuje tekst JSON w celu utworzenia obiektów w pamięci. Aby uzyskać więcej informacji, zobacz [wprowadzenie do języka JavaScript Object Notation (JSON) w JavaScript i .NET](http://go.microsoft.com/fwlink/?LinkId=124098).  
  
## <a name="see-also"></a>Zobacz też  
 [JavaScript — obiekty](../javascript/reference/javascript-objects.md)