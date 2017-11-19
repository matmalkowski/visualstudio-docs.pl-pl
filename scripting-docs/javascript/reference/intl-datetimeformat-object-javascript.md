---
title: "Intl.datetimeformat — obiekt (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: DateTimeFormat
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: cc555ac2-f31c-4239-a612-b84c08e3a37f
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9c50d6d7d939ebe05ce3ff9b434111413803ea40
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="intldatetimeformat-object-javascript"></a>Intl.DateTimeFormat — Obiekt (JavaScript)
Udostępnia formatowania specyficzne dla ustawień regionalnych daty i godziny.  
  
## <a name="syntax"></a>Składnia  
  
```  
dateTimeFormatObj = new Intl.DateTimeFormat([locales][, options])  
```  
  
#### <a name="parameters"></a>Parametry  
 `dateTimeFormatObj`  
 Wymagany. Nazwa zmiennej można przypisać `DateTimeFormat` do obiektu.  
  
 `locales`  
 Opcjonalny. Tablica ciągów ustawień regionalnych, które zawiera jeden lub więcej tagów języka lub ustawień regionalnych. Jeśli dołączysz więcej niż jeden ciąg ustawień regionalnych na listę w kolejności priorytetu tak, aby pierwszy wpis preferowanych ustawień regionalnych. Jeśli ten parametr zostanie pominięty, domyślne ustawienia regionalne środowiska wykonawczego języka JavaScript jest używany. Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.  
  
 `options`  
 Opcjonalny. Obiekt, który zawiera co najmniej jednej właściwości, które określają opcje formatowania daty i godziny. Zobacz szczegółowe informacje można znaleźć w sekcji uwag.  
  
## <a name="remarks"></a>Uwagi  
 `locales` Parametru musi być zgodna z [BCP 47](http://tools.ietf.org/html/rfc5646) tagi język lub ustawienia regionalne, takie jak "en US" i "zh-CN". Tag może obejmować języka, region, kraj i variant. Przykłady języka tagów, zobacz [dodatek a.](http://tools.ietf.org/html/rfc5646#appendix-A) 47 BCP. Aby uzyskać `DateTimeFormat`, można dodać **-u** tag podrzędny w ciągu ustawień regionalnych na zawierają jedną lub obie następujące rozszerzenia Unicode:  
  
-   -Licz, aby określić numerowania rozszerzenia systemu: *języka*-*region*-u-licz -*numberingsystem*  
  
     gdzie *numberingsystem* może być jedną z następujących: Emiraty, arabext, bali, beng, deva, fullwide, gujr, guru, hanidec, khmr, knda, laoo, latn, kończyny, mylm, mong, mymr, orya, tamldec, telu, tajski, tibt.  
  
-   -ca określić kalendarz: *języka*-*region*-u-Kanada —*kalendarza*  
  
     gdzie *kalendarza* może być jedną z następujących: buddyjskiego, chiński, gregory Islamska, islamicc, japoński.  
  
 `options` Parametr może zawierać następujące właściwości:  
  
|Właściwość|Opis|Możliwe wartości|Wartość domyślna|  
|--------------|-----------------|---------------------|-------------------|  
|`localeMatcher`|Określa algorytm dopasowania ustawień regionalnych do użycia.|"wyszukiwanie", "optymalnie"|"najlepszego dopasowania"|  
|`formatMatcher`|Określa algorytm dopasowania formatu do użycia.|"basic", "optymalnie"|"najlepszego dopasowania"|  
|`hour12`|Określa, czy do korzystania z formatu 12-godzinnym dla godzin.|`true`(dla 12-godzinnym formacie) `false` (dla w formacie 24-godzinnym)||  
|`timeZone`|Określa strefę czasową. Co najmniej "UTC" zawsze jest obsługiwane.|Wartości strefy czasowej, takich jak "UTC".|"UTC"|  
|`weekday`|Określa format dnia tygodnia.|"zawęzić", "short", "long".|Niezdefiniowana|  
|`era`|Określa format ery.|"zawęzić", "short", "long"|Niezdefiniowana|  
|`year`|Określa format roku.|"2-cyfrowy", "numerycznego"|Niezdefiniowane lub "numerycznych"|  
|`month`|Określa format miesiąca.|"2-cyfrowy", "liczbowe", "wąskie", "krótka", "long"|Niezdefiniowane lub "numerycznych"|  
|`day`|Określa format dnia.|"2-cyfrowy", "numerycznego"|Niezdefiniowane lub "numerycznych"|  
|`hour`|Określa formatowanie godziny.|"2-cyfrowy", "numerycznego"|Niezdefiniowana|  
|`minute`|Określa format minutę.|"2-cyfrowy", "numerycznego"|Niezdefiniowana|  
|`second`|Określa formatowanie drugiego.|"2-cyfrowy", "numerycznego"|Niezdefiniowana|  
|`timeZoneName`|Określa format strefy czasowej. Ta właściwość nie jest obecnie obsługiwana.|"short", "long".|Ta właściwość nie jest obecnie obsługiwana.|  
  
 Wartości domyślne `weekday`, `era`, `year`, `month`, `day`, `hour`, `minute`, i `second` są `undefined`. Jeśli nie ustawisz tych właściwości formatowania "liczbowa" służy do `year`, `month`, i `day`.  
  
 Każdy ustawień regionalnych musi spełniać co najmniej następujących formatów:  
  
-   dzień tygodnia roku, miesiąca, dzień, godzina, minuty, sekundy  
  
-   dzień tygodnia, rok, miesiąc, dzień  
  
-   rok, miesiąc, dzień  
  
-   rok, miesiąc  
  
-   miesiąc, dzień  
  
-   Godzina, minuty, sekundy  
  
-   Godzina, minuta  
  
## <a name="properties"></a>Właściwości  
 W poniższej tabeli wymieniono właściwości `DateTimeFormat` obiektu.  
  
|||  
|-|-|  
|Właściwość|Opis|  
|[Konstruktor](../../javascript/reference/constructor-property-intl-datetimeformat.md)|Określa funkcję, która tworzy obiektem programu formatującego daty/godziny.|  
|[Format](../../javascript/reference/format-property-intl-datetimeformat.md)|Zwraca funkcję, która formaty daty specyficzne dla ustawień regionalnych przy użyciu ustawień programu formatującego daty/godziny.|  
|[Prototyp](../../javascript/reference/prototype-property-intl-datetimeformat.md)|Zwraca odwołanie do prototypu dla elementu formatującego daty/godziny.|  
  
## <a name="methods"></a>Metody  
 W poniższej tabeli przedstawiono metody `DateTimeFormat` obiektu.  
  
|||  
|-|-|  
|Metoda|Opis|  
|[resolvedOptions](../../javascript/reference/resolvedoptions-method-intl-datetimeformat.md)|Zwraca obiekt, który zawiera właściwości i wartości daty/godziny obiektem programu formatującego.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia wynik przekazywanie obiekt date do `DateTimeFormat` za pomocą różnych ustawień regionalnych.  
  
```JavaScript  
var date = new Date(Date.UTC(2013, 1, 1, 14, 0, 0));  
var options = { weekday: "long", year: "numeric", month: "short",  
    day: "numeric" };  
  
if (console && console.log) {  
    console.log(new Intl.DateTimeFormat("en-US").format(date));  
    // Returns ‎2‎/‎1‎/‎2013  
    console.log(new Intl.DateTimeFormat("ja-JP").format(date));  
    // Returns ‎2013‎年‎2‎月‎1‎日  
    console.log(new Intl.DateTimeFormat("ar-SA", options).format(date));  
    // Returns ‏الجمعة‏, ‏٢٠‏ ‏ربيع الأول‏, ‏١٤٣٤  
    console.log(new Intl.DateTimeFormat("hi-IN", options).format(date));  
    // Returns ‎शुक्रवार‎, ‎01‎ ‎फरवरी‎ ‎2013  
}  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy `DateTimeFormat` obiekt, który określa bieżącego dnia tygodnia w formacie długim przy użyciu ustawień regionalnych arabski (Arabia Saudyjska), Islamska kalendarza i Latin Numerowanie systemu.  
  
```JavaScript  
var dtf = new Intl.DateTimeFormat(["ar-SA-u-ca-islamic-nu-latn"], {  
    weekday: "long",  
    year: "numeric",  
    day: "numeric",  
    month: "long"  
});   
  
If (console && console.log) {  
    console.log(dtf.format(new Date()));  
    // Returns ‏الجمعة‏, ‏19‏ ‏رمضان‏, ‏1434  
}  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [toLocaleString (Data)](../../javascript/reference/tolocalestring-date.md)   
 [toLocaleDateString — metoda (Data)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)   
 [toLocaleTimeString — metoda (Data)](../../javascript/reference/tolocaletimestring-method-date-javascript.md)   
 [Intl.Collator — obiekt](../../javascript/reference/intl-collator-object-javascript.md)   
 [Intl.numberformat — obiekt](../../javascript/reference/intl-numberformat-object-javascript.md)