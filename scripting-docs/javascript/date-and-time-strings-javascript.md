---
title: "Ciągi daty i godziny (JavaScript) | Dokumentacja firmy Microsoft"
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
ms.assetid: ba0798c5-3574-4434-89f4-3d90be276001
caps.latest.revision: "47"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6218ba273b26243382d1e825b6da961d604917ab
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="date-and-time-strings-javascript"></a>Ciągi daty i godziny (JavaScript)
Szereg technik umożliwia Określ i formatowania kodu JavaScript ciągi daty i czasu.  
  
## <a name="formatting-dates-using-intldatetimeformat"></a>Formatowanie dat przy użyciu Intl.DateTimeFormat  
 Internet Explorer 11 wprowadzono obsługę [Intl.datetimeformat — obiekt](../javascript/reference/intl-datetimeformat-object-javascript.md), który jest częścią [specyfikacji interfejsu API internacjonalizacji ECMAScript](http://www.ecma-international.org/ecma-402/1.0/). Do formatowania daty, tego obiektu można używać bezpośrednio lub można użyć implementacji zaktualizowane [toLocaleDateString — metoda (Data)](../javascript/reference/tolocaledatestring-method-date-javascript.md) i [toLocaleTimeString — metoda (Data)](../javascript/reference/tolocaletimestring-method-date-javascript.md). Te metody [obiekt Date](../javascript/reference/date-object-javascript.md) użyj `Intl.DateTimeFormat` wewnętrznie w celu obsługi nowe parametry opcjonalne dla ustawień regionalnych i inne opcje formatowania.  
  
 Poniższy przykład przedstawia użycie `toLocaleDateString` i `toLocaleTimeString` do formatu daty i godziny. Pierwszy parametr przekazany do tych metod jest wartością ustawienia regionalne, takie jak "en-us". W przypadku, gdy istnieje, drugi parametr określa opcje formatowania, takie jak długich fragmentów dla dnia tygodnia.  
  
```JavaScript  
var date = new Date(Date.UTC(2013, 1, 1, 14, 0, 0));  
var options = {  
    weekday: "long", year: "numeric", month: "short",  
    day: "numeric", hour: "2-digit", minute: "2-digit"  
};  
  
document.write(date.toLocaleDateString("en-US"));  
document.write(date.toLocaleTimeString("en-us", options));  
document.write(date.toLocaleDateString("ja-JP"));  
document.write(date.toLocaleTimeString("ja-JP", options));  
  
// Output:  
// ‎2‎/‎1‎/‎2013  
// ‎Friday‎, ‎Feb‎ ‎1‎, ‎2013‎ ‎06‎:‎00‎ ‎AM  
// ‎2013‎年‎2‎月‎1‎日‎  
// ‎2013‎年‎2‎月‎1‎日 ‎金曜日‎ ‎06‎:‎00  
```  
  
 Aby uzyskać pełną listę opcji formatowania, zobacz [Intl.datetimeformat — obiekt](../javascript/reference/intl-datetimeformat-object-javascript.md).  
  
## <a name="formatting-dates"></a>Formatowanie dat  
 Przed programu Internet Explorer 11 języka JavaScript nie ma określonych metod formatowania daty i godziny. Aby podać własne Data formatowania w poprzednich wersjach przeglądarki, należy użyć [getDay — metoda (Data)](../javascript/reference/getday-method-date-javascript.md), [getDate — metoda (Data)](../javascript/reference/getdate-method-date-javascript.md), [getMonth — metoda (Data)](../javascript/reference/getmonth-method-date-javascript.md)i [getFullYear — metoda (Data)](../javascript/reference/getfullyear-method-date-javascript.md) metody. ( [GetYear — metoda (Data)](../javascript/reference/getyear-method-date-javascript.md) jest przestarzały i nie powinna być używana.)  
  
```JavaScript  
var myDate = new Date("February 3, 2001");  
var myDate = new Date("February 3 2001");  
document.write((myDate.getMonth() + 1) + "-" + myDate.getDate() + "-" + myDate.getFullYear());  
document.write("<br/>");  
document.write((myDate.getMonth() + 1) + "/" + myDate.getDate() + "/" + myDate.getFullYear());  
  
//Output:  
// 2-3-2001  
// 2/3/2001  
```  
  
 Możesz podać własne formatowanie przy użyciu czasu [getHours — metoda (Data)](../javascript/reference/gethours-method-date-javascript.md), [getMinutes — metoda (Data)](../javascript/reference/getminutes-method-date-javascript.md), [getSeconds — metoda (Data)](../javascript/reference/getseconds-method-date-javascript.md), i [ getMilliseconds — metoda (Data)](../javascript/reference/getmilliseconds-method-date-javascript.md) metody.  
  
```JavaScript  
myDate = new Date();  
myDate.setHours(10, 30, 53, 400);  
  
document.write(myDate.getHours() + ":" + myDate.getMinutes() + ":" + myDate.getSeconds() +   
":" + myDate.getMilliseconds());  
  
// Output:   
// 10:30:53:400  
```  
  
## <a name="converting-strings-to-dates"></a>Konwertowanie ciągów na daty  
 Można określić parametry do skonstruowania `Date` obiektów za pomocą `Date(dateStr)` lub `Date.parse(dateStr)`. JavaScript do analizowanie ciągów daty stosowane są następujące reguły:  
  
-   Po raz pierwszy próbuje można przeanalizować ciągu daty przy użyciu [Format daty ISO](#ISO).  
  
    > [!NOTE]
    >  JavaScript używa się uproszczonej wersji rozszerzony format ISO 8601.  
  
-   Jeśli ciąg daty nie jest w formacie ISO, JavaScript próbuje przeanalizować daty przy użyciu innych [inne formaty daty](#OtherDateFormats).  
  
<a name="ISO"></a>   
## <a name="iso-date-format"></a>Format danych ISO  
 ISO format jest uproszczenie rozszerzony format ISO 8601. Format jest następujący:  
  
 `YYYY-MM-DDTHH:mm:ss.sssZ`  
  
> [!IMPORTANT]
>  Format daty ISO nie jest obsługiwany w trybie standardów programu Internet Explorer 8 i tryb Osobliwości.  
  
 W poniższej tabeli opisano części tego formatu.  
  
|Symbol|Opis|Wartości|  
|------------|-----------------|------------|  
|`-`, `:`, `.`, `T`|Znaki faktycznie w ciągu. `T`Określa godzinę uruchomienia.||  
|`YYYY`|Rok. Rozszerzone roku można zamiast rok 4-cyfrowego. Aby uzyskać więcej informacji, zobacz [rozszerzony lat](../javascript/date-and-time-strings-javascript.md#bkmk_extend) dalszej części tego tematu.||  
|`MM`|Miesiąc|01 do 12|  
|`DD`|Dzień miesiąca.|01 do 31.|  
|`HH`|Godziny|00 – 24|  
|`mm`|minut|od 00 do 59|  
|`ss`|Liczba sekund. Sekundach i milisekundach są opcjonalne, jeśli określono godzinę.|od 00 do 59|  
|`sss`|w milisekundach|00 do 999.|  
|`Z`|Wartość w tej pozycji może być jedną z następujących czynności. W przypadku pominięcia wartości jest używany czas UTC.<br /><br /> -   `Z`Wskazuje czas UTC.<br />-   `+hh:mm`Wskazuje, że wprowadzona godzina jest określone przesunięcie po upływie czasu UTC.<br />-   `-hh:mm`Wskazuje, że wprowadzona godzina jest wartość bezwzględna określone przesunięcie przed czasem UTC.||  
  
 Ciąg może zawierać datę, tak jak następujących formatów: `YYYY`, `YYYY-MM`, `YYYY-MM-DD`.  
  
 Format obrazu ISO nie obsługuje nazw strefy czasowej. Można użyć `Z` pozycji, aby określić przesunięcie od czasu UTC. Jeśli nie ma wartości w `Z` umieść UTC zostanie użyta godzina.  
  
 Można określić północy, za pomocą 00:00 lub przy użyciu 24:00 w poprzednim dniu. Jednocześnie określić następujące dwa ciągi: 2010-05-25T00:00 i 2010-05-24T24:00.  
  
 Zwraca datę w formacie ISO, umożliwia [toISOString — metoda (Data)](../javascript/reference/toisostring-method-date-javascript.md).  
  
<a name="bkmk_extend"></a>   
### <a name="extended-years"></a>Rozszerzone lata  
 *Rozszerzonej roku* ma 6 cyfr zamiast 4 cyfry i jest poprzedzony ze znakiem plus lub minus. Przykład rozszerzonej roku `+002010`, który jest odpowiednikiem `2010`. Rozszerzone roku służy do reprezentowania lat przed rokiem 0 lub po 9999.  
  
 Jeśli używasz 6-cyfrowy format plus lub znak minus musi być obecny. Gdy używasz formatu 4 cyfry, znaki muszą być nieobecne. W związku z tym `0000` i `+000000` są akceptowane, ale `000000` i `-0001` spowodować wystąpienie błędu. Rozszerzone roku 0 jest traktowany jako dodatnią i w związku z tym prefiksem ze znakiem plus.  
  
 [ToISOString — metoda (Data)](../javascript/reference/toisostring-method-date-javascript.md) zawsze używa formatu roku rozszerzonej lat, które są przed 0 i po 9999.  
  
> [!NOTE]
>  [!INCLUDE[jsv9](../javascript/includes/jsv9-md.md)]  
  
<a name="OtherDateFormats"></a>   
## <a name="other-date-formats"></a>Inne formaty daty  
 Jeśli ciąg daty nie jest w formacie ISO [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] stosowane są następujące reguły można go przeanalizować.  
  
 Krótkiej daty  
  
-   Format wykonaj kolejności miesiąc/dzień/rok, na przykład "2010-06-08".  
  
-   Albo "/" lub "-" może być używany jako separator.  
  
 Długie dat  
  
-   Rok, miesiąc i dzień można w dowolnej kolejności. "8 czerwca 2010" i "2010 czerwca 8" są prawidłowe.  
  
-   Rok może mieć dwie lub cztery cyfry. Jeśli roku ma dwie cyfry, musi być co najmniej 70.  
  
-   Miesiąc i dzień nazwy muszą mieć co najmniej dwa znaki. Dwie nazwy znaków, które nie są unikatowe są kojarzone zgodnego nazwiska. Na przykład "Ju" Określa lipca, nie czerwca.  
  
-   Dzień tygodnia jest ignorowana, jeśli jest on niezgodny z resztą podanej daty. Na przykład "Wtorek listopada 1996 9" jest rozpoznawany jako "Piątek listopada 1996 9" ponieważ piątek jest poprawny dzień tygodnia dla tej daty.  
  
 Godziny  
  
-   Godziny, minuty i sekundy są oddzielone przecinkami. Jednak niektóre części można pominąć. Poniżej przedstawiono prawidłowe: "10:", "10:11" i "10: 11:12".  
  
-   Jeśli określono PM i godzina określona jest co najmniej 13, zwracany jest NaN. Na przykład "23:15 będzie" zwraca NaN.  
  
 Ogólne  
  
-   Ciąg, który zawiera nieprawidłową datę zwraca NaN. Na przykład ciąg, który zawiera dwa lata lub dwóch miesięcy zwraca NaN.  
  
-   [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]obsługuje wszystkie strefy (czas standardowy) i uniwersalny czas koordynowany (UTC) i czas uniwersalny Greenwich (GMT). (Format obrazu ISO nie obsługuje stref czasowych).  
  
-   Tekst w nawiasach jest traktowany jako komentarz. Mogą być zagnieżdżane nawiasów.  
  
-   Przecinkami i spacje są traktowane jako ograniczników. Ograniczniki wielu są dozwolone.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia wyniki analizy ciągów różnych daty i godziny.  
  
```  
document.writeln((new Date("2010")).toUTCString());   
  
document.writeln((new Date("2010-06")).toUTCString());  
  
document.writeln((new Date("2010-06-09")).toUTCString());  
  
 // Specifies Z, which indicates UTC time.  
document.writeln((new Date("2010-06-09T15:20:00Z")).toUTCString());  
  
 // Specifies -07:00 offset, which is equivalent to Pacific Daylight time.  
document.writeln((new Date("2010-06-09T15:20:00-07:00")).toGMTString());  
  
// Specifies a non-ISO Long date.  
document.writeln((new Date("June 9, 2010")).toUTCString());  
  
// Specifies a non-ISO Long date.  
document.writeln((new Date("2010 June 9")).toUTCString());  
  
// Specifies a non-ISO Short date and time.  
document.writeln((new Date("6/9/2010 3:20 pm")).toUTCString());  
  
// Output:  
// Fri, 1 Jan 2010 00:00:00 UTC  
// Tue, 1 Jun 2010 00:00:00 UTC  
// Wed, 9 Jun 2010 00:00:00 UTC  
// Wed, 9 Jun 2010 15:20:00 UTC  
// Wed, 9 Jun 2010 22:20:00 UTC  
// Wed, 9 Jun 2010 07:00:00 UTC  
// Wed, 9 Jun 2010 07:00:00 UTC  
// Wed, 9 Jun 2010 22:20:00 UTC  
```  
  
 W przypadku, gdy określono godzin czasu lokalnego, wynik zależy od strefy czasowej.  
  
> [!IMPORTANT]
>  Format daty ISO nie jest obsługiwany w trybie standardów programu Internet Explorer 8 i tryb Osobliwości.  
  
## <a name="see-also"></a>Zobacz też  
 [Date — obiekt](../javascript/reference/date-object-javascript.md)   
 [Date.Parse — funkcja](../javascript/reference/date-parse-function-javascript.md)