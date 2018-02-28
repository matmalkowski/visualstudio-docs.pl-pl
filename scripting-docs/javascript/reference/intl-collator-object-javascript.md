---
title: "Intl.Collator — obiekt (JavaScript) | Dokumentacja firmy Microsoft"
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
- Collator
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: acbb9461-f956-4b5b-ae5f-6a47815ae15c
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b9a41507face20285124257be95197ef5ea53ef6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="intlcollator-object-javascript"></a>Intl.Collator — Obiekt (JavaScript)
Udostępnia ciąg ustawień regionalnych porównania.  
  
## <a name="syntax"></a>Składnia  
  
```  
collatorObj = new Intl.Collator([locales][, options])  
```  
  
#### <a name="parameters"></a>Parametry  
 `collatorObj`  
 Wymagany. Nazwa zmiennej można przypisać `Collator` do obiektu.  
  
 `locales`  
 Opcjonalny. Tablica ciągów ustawień regionalnych, które zawiera jeden lub więcej tagów języka lub ustawień regionalnych. Jeśli dołączysz więcej niż jeden ciąg ustawień regionalnych na listę w kolejności priorytetu tak, aby pierwszy wpis preferowanych ustawień regionalnych. Jeśli ten parametr zostanie pominięty, domyślne ustawienia regionalne środowiska wykonawczego języka JavaScript jest używany. Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.  
  
 `options`  
 Opcjonalny. Obiekt, który zawiera jeden lub więcej właściwości, które opcje porównania. Zobacz szczegółowe informacje można znaleźć w sekcji uwag.  
  
## <a name="remarks"></a>Uwagi  
 `locales` Parametru musi być zgodna z [BCP 47](http://tools.ietf.org/html/rfc5646) tagi język lub ustawienia regionalne, takie jak "en US" i "Hans-zh-CN". Tag może obejmować języka, region, kraj i variant. Aby uzyskać listę języków, zobacz [przez organizację IANA języka tag podrzędny rejestru](http://go.microsoft.com/fwlink/p/?linkid=227303). Przykłady języka tagów, zobacz [dodatek a.](http://tools.ietf.org/html/rfc5646#appendix-A) 47 BCP. Aby uzyskać `Collator`, można uwzględnić rozszerzenia -u w ciągu ustawień regionalnych, aby określić jedną lub więcej z następujących rozszerzeń Unicode:  
  
-   Ko - Aby określić sortowania variant (specyficzne dla ustawień regionalnych): "*języka*-*region*-u-ko -*wartość*".  
  
-   -kn, aby określić porównanie liczbowe: "*języka*-*region*- u kn burzy &#124; false".  
  
-   -kf, aby określić, czy sortowania najpierw wielkich i małych znaków: "*języka*-*region*- u-kf wyższy &#124; małe &#124; false"). To rozszerzenie nie jest obecnie obsługiwane.  
  
 Aby określić porównanie liczbowe, można ustawić rozszerzenia -kn w ciągu ustawień regionalnych lub użyć `numeric` właściwości w `options` parametru. Jeśli używasz `numeric` właściwości wartości -kn nie będą stosowane.  
  
 `options` Parametr może zawierać następujące właściwości:  
  
-   `localeMatcher`. Określa algorytm dopasowania ustawień regionalnych do użycia. Możliwe wartości to "wyszukiwanie" i "optymalnie". Wartość domyślna to "najlepszego dopasowania".  
  
-   `usage`. Określa, czy celem porównania jest sortowania lub wyszukiwania. Możliwe wartości to "sortowania" i "wyszukiwanie". Wartość domyślna to "sortowanie".  
  
-   `sensitivity`. Określa rozdzielnika czułości. Możliwe wartości to "podstawowy", "akcent", "case" i "variant". Wartość domyślna to `undefined`.  
  
-   `ignorePunctuation`. Określa, czy znaki interpunkcyjne jest ignorowane w porównaniu. Możliwe wartości to "true" i "false". Wartość domyślna to `false`.  
  
-   `numeric`. Określa, czy jest używane sortowanie numeryczne. Możliwe wartości to "true" i "false". Wartość domyślna to `false`.  
  
-   `caseFirst`. Nie są obecnie obsługiwane.  
  
## <a name="properties"></a>Właściwości  
 W poniższej tabeli wymieniono właściwości `Collator` obiektu.  
  
|||  
|-|-|  
|Właściwość|Opis|  
|[Porównaj](../../javascript/reference/compare-property-intl-collator.md)|Zwraca funkcję, która porównuje dwa ciągi za pomocą rozdzielnika kolejności sortowania.|  
|[Konstruktor](../../javascript/reference/constructor-property-intl-collator.md)|Określa funkcję, która tworzy rozdzielnika.|  
|[Prototyp](../../javascript/reference/prototype-property-intl-collator.md)|Zwraca odwołanie do prototyp rozdzielnika.|  
  
## <a name="methods"></a>Metody  
 W poniższej tabeli przedstawiono metody `Collator` obiektu.  
  
|||  
|-|-|  
|Metoda|Opis|  
|[resolvedOptions](../../javascript/reference/resolvedoptions-method-intl-collator.md)|Zwraca obiekt, który zawiera właściwości i wartości rozdzielnika.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy `Collator` obiektu i przeprowadza porównanie.  
  
```JavaScript  
var co = new Intl.Collator(["de-DE"]);  
co.compare("a", "b"); // Returns -1  
  
```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Collator` obiektów, aby posortować tablicy. Ten przykład przedstawia różnice specyficzne dla ustawień regionalnych.  
  
```JavaScript  
var co1 = new Intl.Collator(["de-DE-u-co-phonebk"]);  
var co2 = new Intl.Collator(["de-DE"]);  
var co3 = new Intl.Collator(["en-US"]);  
  
var arr = ["ä", "ad", "af", "a"];  
  
if (console && console.log) {  
    console.log(arr.sort(co1.compare));  // Returns a,ad,ä,af  
    console.log(arr.sort(co2.compare));  // Returns a,ä,ad,af  
    console.log(arr.sort(co3.compare));  // Returns a,ä,ad,af  
}  
```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Collator` obiektu do wyszukania ciągu i określa opcje porównania.  
  
```JavaScript  
// String to search  
var arr = ["ä", "ad", "af", "a"];  
// String searched for  
var s = "af";  
  
var co = new Intl.Collator("de-DE", { usage: "search" });  
var matches = arr.filter(function (i) {  
    return co.compare(i, s) === 0;  
});  
  
if (console && console.log) {  
    console.log(matches);  // Returns af  
}  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [localeCompare — metoda (ciąg)](../../javascript/reference/localecompare-method-string-javascript.md)   
 [Intl.datetimeformat — obiekt](../../javascript/reference/intl-datetimeformat-object-javascript.md)   
 [Intl.numberformat — obiekt](../../javascript/reference/intl-numberformat-object-javascript.md)