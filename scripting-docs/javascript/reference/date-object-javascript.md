---
title: "Date — obiekt (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Date
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Date object
- dates, determining
ms.assetid: ce2202bb-7ec9-4f5a-bf48-3a04feff283e
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eb5d53f3bddfeb3a3ed1ab36e2b4be822964eba5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="date-object-javascript"></a>Date — Obiekt (JavaScript)
Umożliwia podstawowe przechowywanie i pobieranie daty i godziny.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      dateObj = new Date()  
dateObj = new Date(dateVal)  
dateObj = new Date(year, month, date[, hours[, minutes[, seconds[,ms]]]])   
```  
  
## <a name="parameters"></a>Parametry  
 `dateObj`  
 Wymagany. Nazwa zmiennej, do której `Date` obiekt jest przypisany.  
  
 `dateVal`  
 Wymagany. Jeśli wartość liczbową `dateVal` reprezentuje liczbę milisekund uniwersalny czas koordynowany między określoną datą i północy 1 stycznia 1970. Jeśli ciąg, `dateVal` zostanie przeanalizowany zgodnie z regułami z [ciągów daty i godziny](../../javascript/date-and-time-strings-javascript.md). `dateVal` Argument można też wartość VT_DATE zwrócony z niektórych obiektów ActiveX.  
  
 `year`  
 Wymagany. Pełny rok, na przykład 1976 r. (i nie 76).  
  
 `month`  
 Wymagany. Miesiąc jako liczba całkowita z zakresu od 0 do 11 (od stycznia do grudnia).  
  
 `date`  
 Wymagany. Data jako liczba całkowita z przedziału od 1 do 31.  
  
 `hours`  
 Opcjonalny. Musi być dostarczona, jeśli `minutes` podano. Liczba całkowita z przedziału od 0 do 23 (północ do 23: 00) określająca godzinę.  
  
 minuty  
 Opcjonalny. Musi być dostarczona, jeśli `seconds` podano. Liczba całkowita z przedziału od 0 do 59 określająca minut.  
  
 `seconds`  
 Opcjonalny. Musi być dostarczona, jeśli `milliseconds` podano. Liczba całkowita z przedziału od 0 do 59 określająca sekund.  
  
 `ms`  
 Opcjonalny. Liczba całkowita z przedziału od 0 do 999 określająca milisekund.  
  
## <a name="remarks"></a>Uwagi  
 A `Date` obiektu zawiera wiele reprezentujący określonego błyskawicznych w czasie, aby w ramach milisekundy. Jeśli wartość argumentu jest większa niż jego zakres lub wartość ujemną, inne wartości przechowywane są odpowiednio zmienione. Na przykład jeśli określisz 150 sekund [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] ponownie definiuje tego numeru jako dwóch minut do 30 sekund.  
  
 Jeśli liczba jest `NaN`, obiekt nie reprezentuje określonych błyskawicznych czasu. W przypadku przekazania parametrów do `Date` obiektu, jest inicjowany do bieżącego czasu (UTC). Należy podać wartość do obiektu, przed jego użyciem.  
  
 Zakres dat, które mogą być reprezentowane w `Date` obiektu wynosi około 285,616 lat po obu stronach 1 stycznia 1970.  
  
 Zobacz [obliczanie dat i godzin (JavaScript)](../../javascript/calculating-dates-and-times-javascript.md) Aby uzyskać więcej informacji o sposobie używania `Date` obiektu oraz odpowiednich metod.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `Date` obiektu.  
  
```JavaScript  
var dateString = "Today's date is: ";  
  
var newDate = new Date();  
  
// Get the month, day, and year.  
dateString += (newDate.getMonth() + 1) + "/";  
dateString += newDate.getDate() + "/";  
dateString += newDate.getFullYear();  
  
document.write(dateString);  
  
// Output: Today's date is: <date>  
```  
  
## <a name="requirements"></a>Wymagania  
 `Date object` Została wprowadzona w systemie [!INCLUDE[jsv1text](../../javascript/reference/includes/jsv1text-md.md)]. Niektóre elementy członkowskie wymienione na poniższej liście zostały wprowadzone w nowszych wersjach. Aby uzyskać więcej informacji, zobacz [informacje o wersji](../../javascript/reference/javascript-version-information.md) lub dokumentacji dla poszczególnych elementów.  
  
## <a name="properties"></a>Właściwości  
 W poniższej tabeli wymieniono właściwości `Date Object`.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|[constructor — właściwość](../../javascript/reference/constructor-property-date.md)|Określa funkcję, która tworzy obiekt.|  
|[prototype — właściwość](../../javascript/reference/prototype-property-date.md)|Zwraca odwołanie do prototypu klasy obiektów.|  
  
## <a name="functions"></a>Funkcje  
 W poniższej tabeli wymieniono funkcje `Date Object`.  
  
|Funkcje|Opis|  
|---------------|-----------------|  
|[Funkcja Date.now](../../javascript/reference/date-now-function-javascript.md)|Zwraca liczbę milisekund między 1 stycznia 1970 bieżąca data i godzina.|  
|[Date.Parse — funkcja](../../javascript/reference/date-parse-function-javascript.md)|Analizuje ciąg zawierający daty i zwraca liczbę milisekund między tą datą a północy, 1 stycznia 1970.|  
|[Date.UTC — funkcja](../../javascript/reference/date-utc-function-javascript.md)|Zwraca liczbę milisekund między północy, 1 stycznia 1970 uniwersalnego czasu koordynowanego (UTC) (lub GMT) i podanej daty.|  
  
<a name="js56jsobjdatemeth"></a>   
## <a name="methods"></a>Metody  
 W poniższej tabeli przedstawiono metody `Date Object`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[getDate — metoda](../../javascript/reference/getdate-method-date-javascript.md)|Zwraca wartość dnia miesiąca, przy użyciu czasu lokalnego.|  
|[getDay — metoda](../../javascript/reference/getday-method-date-javascript.md)|Zwraca wartość dnia tygodnia przy użyciu czasu lokalnego.|  
|[getFullYear — metoda](../../javascript/reference/getfullyear-method-date-javascript.md)|Zwraca wartość roku przy użyciu czasu lokalnego.|  
|[getHours — metoda](../../javascript/reference/gethours-method-date-javascript.md)|Zwraca wartość godziny przy użyciu czasu lokalnego.|  
|[getMilliseconds — metoda](../../javascript/reference/getmilliseconds-method-date-javascript.md)|Zwraca wartość w milisekundach, przy użyciu czasu lokalnego.|  
|[getMinutes — metoda](../../javascript/reference/getminutes-method-date-javascript.md)|Zwraca wartość minut przy użyciu czasu lokalnego.|  
|[getMonth — metoda](../../javascript/reference/getmonth-method-date-javascript.md)|Zwraca wartość miesiąca przy użyciu czasu lokalnego.|  
|[getSeconds — metoda](../../javascript/reference/getseconds-method-date-javascript.md)|Zwraca wartość sekund przy użyciu czasu lokalnego.|  
|[getTime — metoda](../../javascript/reference/gettime-method-date-javascript.md)|Zwraca wartość w `Date` obiektu jako liczbę milisekund od północy 1 stycznia 1970.|  
|[getTimezoneOffset — metoda](../../javascript/reference/gettimezoneoffset-method-date-javascript.md)|Zwraca różnicę w minutach czas na komputerze hosta i uniwersalny czas koordynowany (UTC).|  
|[getUTCDate — metoda](../../javascript/reference/getutcdate-method-date-javascript.md)|Zwraca wartość dnia miesiąca, przy użyciu czasu UTC.|  
|[getUTCDay — metoda](../../javascript/reference/getutcday-method-date-javascript.md)|Zwraca wartość dnia tygodnia przy użyciu czasu UTC.|  
|[getUTCFullYear — metoda](../../javascript/reference/getutcfullyear-method-date-javascript.md)|Zwraca wartość roku przy użyciu czasu UTC.|  
|[getUTCHours — metoda](../../javascript/reference/getutchours-method-date-javascript.md)|Zwraca wartość godziny przy użyciu czasu UTC.|  
|[getUTCMilliseconds — metoda](../../javascript/reference/getutcmilliseconds-method-date-javascript.md)|Zwraca wartość w milisekundach, przy użyciu czasu UTC.|  
|[getUTCMinutes — metoda](../../javascript/reference/getutcminutes-method-date-javascript.md)|Zwraca wartość minut przy użyciu czasu UTC.|  
|[getUTCMonth — metoda](../../javascript/reference/getutcmonth-method-date-javascript.md)|Zwraca wartość miesiąca przy użyciu czasu UTC.|  
|[getUTCSeconds — metoda](../../javascript/reference/getutcseconds-method-date-javascript.md)|Zwraca wartość przy użyciu czasu UTC sekund.|  
|[getVarDate — metoda](../../javascript/reference/getvardate-method-date-javascript.md)|Zwraca wartość VT_DATE `Date` obiektu.|  
|[getYear — metoda](../../javascript/reference/getyear-method-date-javascript.md)|Zwraca wartość roku.|  
|[hasOwnProperty — metoda](../../javascript/reference/hasownproperty-method-object-javascript.md)|Zwraca wartość logiczną, która wskazuje, czy obiekt ma właściwość o określonej nazwie.|  
|[isPrototypeOf — metoda](../../javascript/reference/isprototypeof-method-object-javascript.md)|Zwraca wartość logiczną, która wskazuje, czy obiekt istnieje w łańcuchu prototypów innego obiektu.|  
|[propertyIsEnumerable — metoda](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|Zwraca wartość logiczną, która wskazuje, czy określona właściwość jest częścią obiektu i czy jest wyliczalna.|  
|[setDate — metoda](../../javascript/reference/setdate-method-date-javascript.md)|Ustawia liczbą dzień miesiąca przy użyciu czasu lokalnego.|  
|[setFullYear — metoda](../../javascript/reference/setfullyear-method-date-javascript.md)|Ustawia wartość roku przy użyciu czasu lokalnego.|  
|[setHours — metoda](../../javascript/reference/sethours-method-date-javascript.md)|Ustawia wartość godziny przy użyciu czasu lokalnego.|  
|[setMilliseconds — metoda](../../javascript/reference/setmilliseconds-method-date-javascript.md)|Ustawia wartość w milisekundach przy użyciu czasu lokalnego.|  
|[setMinutes — metoda](../../javascript/reference/setminutes-method-date-javascript.md)|Ustawia wartość minut przy użyciu czasu lokalnego.|  
|[setMonth — metoda](../../javascript/reference/setmonth-method-date-javascript.md)|Ustawia wartość miesiąca przy użyciu czasu lokalnego.|  
|[setSeconds — metoda](../../javascript/reference/setseconds-method-date-javascript.md)|Ustawia wartość przy użyciu czasu lokalnego sekund.|  
|[setTime — metoda](../../javascript/reference/settime-method-date-javascript.md)|Ustawia wartość daty i godziny w `Date` obiektu.|  
|[setUTCDate — metoda](../../javascript/reference/setutcdate-method-date-javascript.md)|Ustawia liczbą dzień miesiąca przy użyciu czasu UTC.|  
|[setUTCFullYear — metoda](../../javascript/reference/setutcfullyear-method-date-javascript.md)|Ustawia wartość roku przy użyciu czasu UTC.|  
|[setUTCHours — metoda](../../javascript/reference/setutchours-method-date-javascript.md)|Ustawia wartość godziny przy użyciu czasu UTC.|  
|[setUTCMilliseconds — metoda](../../javascript/reference/setutcmilliseconds-method-date-javascript.md)|Ustawia wartość w milisekundach przy użyciu czasu UTC.|  
|[setUTCMinutes — metoda](../../javascript/reference/setutcminutes-method-date-javascript.md)|Ustawia wartość minut przy użyciu czasu UTC.|  
|[setUTCMonth — metoda](../../javascript/reference/setutcmonth-method-date-javascript.md)|Ustawia wartość miesiąca przy użyciu czasu UTC.|  
|[setUTCSeconds — metoda](../../javascript/reference/setutcseconds-method-date-javascript.md)|Ustawia wartość przy użyciu czasu UTC sekund.|  
|[setYear — metoda](../../javascript/reference/setyear-method-date-javascript.md)|Ustawia wartość roku przy użyciu czasu lokalnego.|  
|[toDateString — metoda](../../javascript/reference/todatestring-method-date-javascript.md)|Zwraca daty w postaci wartości ciągu.|  
|[toGMTString — metoda](../../javascript/reference/togmtstring-method-date-javascript.md)|Zwraca datę, konwertowana na ciąg przy użyciu czas uniwersalny Greenwich (GMT).|  
|[toISOString — metoda](../../javascript/reference/toisostring-method-date-javascript.md)|Zwraca daty w postaci wartości ciągu w formacie ISO.|  
|[toJSON — metoda](../../javascript/reference/tojson-method-date-javascript.md)|Używany do transformacji danych typu obiektu przed serializacji JSON.|  
|[toLocaleDateString — metoda](../../javascript/reference/tolocaledatestring-method-date-javascript.md)|Zwraca daty w postaci ciągu wartość odpowiednią dla środowiska hosta bieżące ustawienia regionalne.|  
|[toLocaleString — metoda](../../javascript/reference/tolocalestring-date.md)|Zwraca obiekt konwertowana na ciąg przy użyciu bieżących ustawień regionalnych.|  
|[toLocaleTimeString — metoda](../../javascript/reference/tolocaletimestring-method-date-javascript.md)|Zwraca godzinę jako wartość ciągu odpowiednią dla środowiska hosta bieżące ustawienia regionalne.|  
|[toString — metoda](../../javascript/reference/tostring-method-date.md)|Zwraca reprezentację ciągu obiektu.|  
|[toTimeString — metoda](../../javascript/reference/totimestring-method-date-javascript.md)|Zwraca godzinę jako wartość ciągu.|  
|[toUTCString — metoda](../../javascript/reference/toutcstring-method-date-javascript.md)|Zwraca datę, konwertowana na ciąg przy użyciu czasu UTC.|  
|[valueOf — metoda](../../javascript/reference/valueof-method-date.md)|Zwraca wartość pierwotnych określonego obiektu.|  
  
## <a name="see-also"></a>Zobacz też  
 [Obliczanie dat i godzin (JavaScript)](../../javascript/calculating-dates-and-times-javascript.md)   
 [Ciągi daty i godziny](../../javascript/date-and-time-strings-javascript.md)