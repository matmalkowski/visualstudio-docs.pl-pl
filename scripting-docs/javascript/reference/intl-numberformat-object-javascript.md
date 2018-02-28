---
title: "Intl.numberformat — obiekt (JavaScript) | Dokumentacja firmy Microsoft"
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
- NumberFormat
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 820bc90f-f1e7-457a-b90d-487dfc3a736d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0dcb02dbe0d7a7eef88750c440a4fbcdde3ea7ee
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="intlnumberformat-object-javascript"></a>Intl.NumberFormat — Obiekt (JavaScript)
Udostępnia formatowanie liczb specyficzne dla ustawień regionalnych.  
  
## <a name="syntax"></a>Składnia  
  
```  
numberFormatObj = new Intl.NumberFormat([locales][, options])  
```  
  
#### <a name="parameters"></a>Parametry  
 `numberFormatObj`  
 Wymagany. Nazwa zmiennej można przypisać `NumberFormat` do obiektu.  
  
 `locales`  
 Opcjonalny. Tablica ciągów ustawień regionalnych, które zawiera jeden lub więcej tagów języka lub ustawień regionalnych. Jeśli dołączysz więcej niż jeden ciąg ustawień regionalnych na listę w kolejności priorytetu tak, aby pierwszy wpis preferowanych ustawień regionalnych. Jeśli ten parametr zostanie pominięty, domyślne ustawienia regionalne środowiska wykonawczego języka JavaScript jest używany. Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.  
  
 `options`  
 Opcjonalny. Obiekt, który zawiera co najmniej jednej właściwości, które określają opcje formatowania liczb. Zobacz szczegółowe informacje można znaleźć w sekcji uwag.  
  
## <a name="remarks"></a>Uwagi  
 `locales` Parametru musi być zgodna z [BCP 47](http://tools.ietf.org/html/rfc5646) tagi język lub ustawienia regionalne, takie jak "en US" i "zh-CN". Tag może obejmować języka, region, kraj i variant. Przykłady języka tagów, zobacz [dodatek a.](http://tools.ietf.org/html/rfc5646#appendix-A) 47 BCP. Aby uzyskać `NumberFormat`, można dodać **-u** tag podrzędny następuje - licz, aby określić numerowania rozszerzenia systemu:  
  
 "*języka*-*region*-u-licz -*numberingsystem*"  
  
 gdzie *numberingsystem* może być jedną z następujących: Emiraty, arabext, bali, beng, deva, fullwide, gujr, guru, hanidec, khmr, knda, laoo, latn, kończyny, mylm, mong, mymr, orya, tamldec, telu, tajski, tibt.  
  
 `options` Parametr może zawierać następujące właściwości:  
  
|Właściwość|Opis|Możliwe wartości|Wartość domyślna|  
|--------------|-----------------|---------------------|-------------------|  
|`localeMatcher`|Określa algorytm dopasowania ustawień regionalnych do użycia.|"wyszukiwanie", "optymalnie"|"najlepszego dopasowania"|  
|`style`|Określa styl format liczb.|"%", "decimal", "currency"|"decimal"|  
|`currency`|Określa wartość waluty ISO 4217 jako alfabetyczne kod. Jeśli `style` jest ustawiona na "currency", ta wartość jest wymagana.|Zobacz ISO [waluty i środków kodu listy](http://www.currency-iso.org/en/home/tables/table-a1.html).|Niezdefiniowana|  
|`currencyDisplay`|Określa, czy mają być wyświetlane jako kod alfabetyczne waluty ISO 4217, symbol waluty zlokalizowanych lub nazwę waluty zlokalizowanych waluty. Ta wartość jest używana tylko wtedy, gdy `style` ma ustawioną wartość "currency".|"code", "symbol", "name"|"symbol"|  
|`useGrouping`|Określa, czy separator grupowania powinien być używany.|wartość true, false|`true`.|  
|`minimumIntegerDigits`|Określa minimalną liczbę cyfr integralną do użycia.|1-21.|21|  
|`minimumFractionDigits`|. Określa minimalną liczbę cyfr ułamkowych do użycia.|0 do 20.|0|  
|`maximumFractionDigits`|Określa maksymalną liczbę cyfr ułamkowych do użycia.|Ta wartość może należeć do zakresu od `minimumFractionDigits` do 20.|20.|  
|`minimumSignificantDigits`|Określa minimalną liczbę cyfr ułamkowych ma być wyświetlany.|Ta wartość może należeć do zakresu od 1 do 21.|1|  
|`maximumSignificantDigits`|Określa maksymalną liczbę cyfr ułamkowych ma być wyświetlany.|Ta wartość może należeć do zakresu od `minimumSignificantDigits` do 21.|21|  
  
## <a name="properties"></a>Właściwości  
 W poniższej tabeli wymieniono właściwości `NumberFormat` obiektu.  
  
|||  
|-|-|  
|Właściwość|Opis|  
|[Konstruktor](../../javascript/reference/constructor-property-intl-numberformat.md)|Określa funkcję, która tworzy numer obiektem programu formatującego.|  
|[Format](../../javascript/reference/format-property-intl-numberformat.md)|Zwraca funkcję, która formatuje liczbę przy użyciu numeru ustawień programu formatującego.|  
|[Prototyp](../../javascript/reference/prototype-property-intl-numberformat.md)|Zwraca odwołanie do prototypu dla elementu formatującego numer.|  
  
## <a name="methods"></a>Metody  
 W poniższej tabeli przedstawiono metody `NumberFormat` obiektu.  
  
|||  
|-|-|  
|Metoda|Opis|  
|[resolvedOptions](../../javascript/reference/resolvedoptions-method-intl-numberformat.md)|Zwraca obiekt, który zawiera właściwości i wartości numerów obiektem programu formatującego.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy `NumberFormat` obiektu dla ustawień regionalnych pl pl z podanych opcji formatowania.  
  
```JavaScript  
var nf = new Intl.NumberFormat(["en-US"], {  
    style: "currency",  
    currency: "CNY",  
    currencyDisplay: "symbol",  
    maximumFractionDigit: 1  
});  
  
if (console && console.log) {  
    console.log(nf.format(100)); // Returns ¥100.00  
}  
```  
  
## <a name="example"></a>Przykład  
 W poniższych przykładach pokazano wyniku przy użyciu kilku różnych ustawień regionalnych i opcje.  
  
```JavaScript  
var number = 123456789;  
var options1 = { style: "percent" };  
var options2 = { style: "currency", currency: "INR" };  
  
if (console && console.log) {  
    console.log(new Intl.NumberFormat("en-US").format(number));  
    // Returns 123,456,789  
    console.log(new Intl.NumberFormat("ja-JP").format(number));  
    // Returns 123,456,789  
    console.log(new Intl.NumberFormat("ar-SA", options1).format(number));  
    // Returns ١٢,٣٤٥,٦٧٨,٩٠٠ %  
    console.log(new Intl.NumberFormat("hi-IN", options2).format(number));  
    // Returns ₹ 12,34,56,789.00  
}  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [toLocaleString (numer)](../../javascript/reference/tolocalestring-number.md)   
 [Intl.Collator — obiekt](../../javascript/reference/intl-collator-object-javascript.md)   
 [Intl.datetimeformat — obiekt](../../javascript/reference/intl-datetimeformat-object-javascript.md)