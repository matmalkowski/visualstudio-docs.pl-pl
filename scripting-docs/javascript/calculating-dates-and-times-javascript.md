---
title: Obliczanie dat i godzin (JavaScript) | Dokumentacja firmy Microsoft
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
- date and time arithmetic [JavaScript]
- JavaScript, date and time
- date comparison [JavaScript]
- date and time calculations [JavaScript]
ms.assetid: ea976f78-d934-479b-9056-880390d8bddd
caps.latest.revision: "34"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 18b4ff307c8f2c48a37ed9ca50e7c5f1ff693ece
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="calculating-dates-and-times-javascript"></a>Obliczanie dat i godzin (JavaScript)
Można użyć [obiekt Date](../javascript/reference/date-object-javascript.md) do wykonywania typowych zadań kalendarza i zegara, takie jak porównywanie dat i obliczanie czas, który upłynął.  
  
## <a name="setting-a-date-to-the-current-date"></a>Wyznaczenie daty do daty bieżącej  
 Podczas tworzenia wystąpienia [obiekt Date](../javascript/reference/date-object-javascript.md) bez określenia daty, zwraca wartość odpowiadającą bieżącej daty i czasu, w tym rok, miesiąc, dzień, godzinę, minutę, sekundę i milisekund. Można odczytywać lub modyfikować tego dnia i godziny.  
  
 Poniższy przykład przedstawia sposób tworzenia wystąpienia typu date bez korzystania z żadnych parametrów i wyświetl ją w formacie *mm-dd rr*.  
  
```JavaScript  
var dt = new Date();  
  
// Display the month, day, and year. getMonth() returns a 0-based number.  
var month = dt.getMonth()+1;  
var day = dt.getDate();  
var year = dt.getFullYear();  
document.write(month + '-' + day + '-' + year);  
  
// Output: current month, day, year  
```  
  
## <a name="setting-a-specific-date"></a>Ustawienie określonej daty  
 Można ustawić określonej daty, przekazując ciąg daty do konstruktora.  
  
```JavaScript  
var dt = new Date('8/24/2009');  
document.write(dt);  
  
// Output: Mon Aug 24 00:00:00 PDT 2009  
  
```  
  
> [!IMPORTANT]
>  Strefa czasowa wyświetlane w ciągu daty odpowiada ustawiony na maszynie lokalnej strefy czasowej.  
>   
>  [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]jest elastyczny o formacie ciąg, który jest używany jako parametr. Na przykład możesz wpisać "8 – 24-2009", "24 sierpnia 2009", lub "24 sie 2009".  
  
 Można również określić godzinę. Poniższy przykład przedstawia sposób określ datę i godzinę w formacie ISO. "Z" wskazuje czas UTC.  
  
```JavaScript  
var dt = new Date('2010-06-09T15:20:00Z');  
document.write(dt);  
document.write("<br />");  
document.write(dt.toISOString());  
  
// Output:  
// Wed Jun 09 2010 08:20:00 GMT-0700 (Pacific Daylight Time)  
// 2010-06-09T15:20:00.000Z  
```  
  
 Aby uzyskać więcej informacji na formaty daty, takie jak ISO, zobacz [ciągów daty i godziny](../javascript/date-and-time-strings-javascript.md).  
  
 Poniższy przykład przedstawia inny sposób, aby określić godzinę.  
  
```JavaScript  
var dtA = new Date('8/24/2009 14:52:10');  
  
// The parameters are year, month, day, hours, minutes, seconds.  
var dtB = new Date(2009, 7, 24, 14, 52, 10);  
document.write(dtA);  
document.write("<br/>");  
document.write(dtB);  
  
// Output:  
// Mon Aug 24 14:52:10 PDT 2009  
// Mon Aug 24 14:52:10 PDT 2009  
  
```  
  
## <a name="adding-and-subtracting-days-months-and-years"></a>Dodawanie i odejmowanie dni, miesięcy i lat  
 Można użyć metody getX i setX `Date` obiektu można ustawić określonej daty i godziny.  
  
 W poniższym przykładzie pokazano, jak można ustawić daty do poprzedniego dnia. Należy pamiętać, że w razie potrzeby wartości miesiąca i roku również są zmieniane.  
  
```JavaScript  
var myDate = new Date("1/1/1990");  
var dayOfMonth = myDate.getDate();  
myDate.setDate(dayOfMonth - 1);  
  
document.write(myDate);  
  
// Output: Sun Dec 31 00:00:00 PST 1989  
```  
  
 Poniższy przykład ustawia datę ostatniego dnia miesiąca przez odjęcie dzień od pierwszego dnia następnego miesiąca.  
  
> [!TIP]
>  Miesięcy roku są ponumerowane od 0 (styczeń) do 11 (grudzień). Dni tygodnia są ponumerowane od 0 (niedziela) do 6 (sobota).  
  
```JavaScript  
var myDate = new Date("1/1/1990")  
myDate.setMonth(myDate.getMonth() + 1);  
  
myDate.setDate (myDate.getDate() - 1);  
  
document.write(myDate);  
  
// Output: Wed Jan 31 00:00:00 PST 1990  
  
```  
  
## <a name="working-with-days-of-the-week"></a>Praca z dniami tygodnia  
 [GetDay — metoda](../javascript/reference/getday-method-date-javascript.md) pobiera dzień tygodnia jako liczbę z zakresu od 0 (niedziela) i 6 (sobota). (To nie jest taka sama jak [getDate — metoda](../javascript/reference/getdate-method-date-javascript.md), która pobiera dzień miesiąca jako liczbę z zakresu od 1 do 31).  
  
 Poniższy przykład przedstawia datę Mikołajki, czyli w Stanach Zjednoczonych czwarty czwartek w listopadzie. Skrypt umożliwia znalezienie 1 listopada bieżącego roku, a następnie znajduje pierwszy czwartek, a następnie dodanie trzy tygodnie.  
  
```JavaScript  
var myDate = new Date();  
myDate.setHours(0, 0, 0, 0);  
  
myDate.setYear(2013);  
  
// Determine November 1.  
myDate.setDate(1);  
myDate.setMonth(10);  
  
// Find Thursday.  
var thursday = 4;  
while(myDate.getDay() != thursday) {  
    myDate.setDate(myDate.getDate() + 1);  
}  
  
// Add 3 weeks.  
myDate.setDate(myDate.getDate() + 21);  
  
document.write(myDate);  
  
// Output: Thu Nov 28 00:00:00 <time zone> 2013  
  
```  
  
## <a name="calculating-elapsed-time"></a>Obliczanie czasu, który upłynął  
 [GetTime — metoda](../javascript/reference/gettime-method-date-javascript.md) zwraca liczbę milisekund, które upłynęły od północy 1 stycznia 1970. Wszystkie daty przed tą datą zwraca wartość ujemną.  
  
 Można użyć [getTime — metoda](../javascript/reference/gettime-method-date-javascript.md) ustawienie czasu rozpoczęcia i zakończenia obliczania czas, który upłynął. Może służyć do pomiaru małych jednostek, takich jak kilka sekund i dużych jednostek, takich jak dni.  
  
 W poniższym przykładzie oblicza czas w sekundach. [GetTime — metoda](../javascript/reference/gettime-method-date-javascript.md) pobiera wyrażony w milisekundach czas od zera daty.  
  
```JavaScript  
var startTime = new Date('1/1/1990');  
var startMsec = startTime.getMilliseconds();  
startTime.setTime(5000000);  
var elapsed = (startTime.getTime() - startMsec) / 1000;   
document.write(elapsed);  
  
// Output: 5000  
  
```  
  
 Aby pracować z jednostki łatwiejsze w obsłudze, można podzielić milisekund dostarczonych przez [getTime — metoda](../javascript/reference/gettime-method-date-javascript.md) przez odpowiedniej liczby. Na przykład aby włączyć milisekund na dni, podzieleniu przez 86,400,000 (1000 milisekund x sekund 60 x 60 minut x 24 godzin).  
  
 Poniższy przykład przedstawia czas, jaki upłynął od pierwszego dnia roku określony. Aby obliczyć Upłynęło czasu w dni, godziny, minuty i sekundy używa operacji dzielenia. Go bez uwzględnienia czasu letniego.  
  
```JavaScript  
// Set the unit values in milliseconds.  
var msecPerMinute = 1000 * 60;  
var msecPerHour = msecPerMinute * 60;  
var msecPerDay = msecPerHour * 24;  
  
// Set a date and get the milliseconds  
var date = new Date('6/15/1990');  
var dateMsec = date.getTime();  
  
// Set the date to January 1, at midnight, of the specified year.  
date.setMonth(0);  
date.setDate(1);  
date.setHours(0, 0, 0, 0);  
  
// Get the difference in milliseconds.  
var interval = dateMsec - date.getTime();  
  
// Calculate how many days the interval contains. Subtract that  
// many days from the interval to determine the remainder.  
var days = Math.floor(interval / msecPerDay );  
interval = interval - (days * msecPerDay );  
  
// Calculate the hours, minutes, and seconds.  
var hours = Math.floor(interval / msecPerHour );  
interval = interval - (hours * msecPerHour );  
  
var minutes = Math.floor(interval / msecPerMinute );  
interval = interval - (minutes * msecPerMinute );  
  
var seconds = Math.floor(interval / 1000 );  
  
// Display the result.  
document.write(days + " days, " + hours + " hours, " + minutes + " minutes, " + seconds + " seconds.");  
  
//Output: 164 days, 23 hours, 0 minutes, 0 seconds.  
```  
  
### <a name="determining-the-users-age"></a>Określenia wieku użytkownika  
 W poniższym przykładzie przyjmuje urodzinach użytkownika i oblicza wieku użytkownika w latach. Odejmuje rok urodzenia z bieżącego roku, a następnie odejmuje 1, jeśli data urodzenia nie przeprowadzono jeszcze w bieżącym roku.  
  
```JavaScript  
var birthday = new Date("8/1/1985");  
var today = new Date();  
var years = today.getFullYear() - birthday.getFullYear();  
  
// Reset birthday to the current year.  
birthday.setFullYear(today.getFullYear());  
  
// If the user's birthday has not occurred yet this year, subtract 1.  
if (today < birthday)  
{  
    years--;  
}  
document.write("You are " + years + " years old.");  
  
// Output: You are <number of years> years old.  
  
```  
  
## <a name="comparing-dates"></a>Porównywanie dat  
 Jeśli do porównania dat w [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], należy mieć na uwadze który `==` operator zwraca `true` tylko wtedy, gdy dat po obu stronach operatora odwoływać się do tego samego obiektu. W związku z tym jeśli masz dwie oddzielne `Date` ustawić obiekty do tego samego dnia, `date1 == date2` zwraca `false`. Ponadto `Date` obiektu ustawione tylko data i czas nie został zainicjowany północy tej daty. Dlatego w przypadku możesz porównać `Date` bez określony czas `Date.now`, na przykład należy zwrócić uwagę który pierwszy `Date` jest przyjmowana północ i `Date.now` nie jest.  
  
 Poniższy przykład umożliwia sprawdzenie, czy bieżąca data jest taki sam, przed lub po określonej dacie. Aby ustawić bieżącą datę w `todayAtMidn`, skrypt tworzy `Date` obiektu dla bieżącego roku, miesiąca i dnia.  
  
```JavaScript  
// Get the current date at midnight.  
var now = new Date();   
var todayAtMidn = new Date(now.getFullYear(), now.getMonth(), now.getDate());  
  
// Set specificDate to a specified date at midnight.  
var specificDate = new Date("9/21/2009");  
  
// Compare the two dates by comparing the millisecond  
// representations.  
if (todayAtMidn.getTime() == specificDate.getTime())  
{  
    document.write("Same");  
}  
else  
{  
    document.write("Different");  
}  
  
//Output: Different  
```  
  
 Zmieniając w poprzednim przykładzie, możemy Sprawdź, czy podana wartość daty znajduje się w określonym zakresie.  
  
```JavaScript  
// Get the current date at midnight.  
var now = new Date();  
var todayAtMidn = new Date(now.getFullYear(), now.getMonth(), now.getDate());  
  
// Set start/end dates to a specified date (ISO format).  
var startDate = new Date("2009-06-09T15:20:00Z");  
var endDate = new Date("2011-06-09T15:20:00Z");  
  
// Compare the two dates by comparing the millisecond  
// representations.  
if (todayAtMidn.getTime() > startDate.getTime() &&   
    todayAtMidn.getTime() < endDate.getTime()) {  
    document.write("Specified date is within this range.");  
}  
else {  
    document.write("Specified date is not in this range.");  
}  
  
// Output: Specified date is not in this range.  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Date — obiekt](../javascript/reference/date-object-javascript.md)