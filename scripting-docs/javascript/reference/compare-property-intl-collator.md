---
title: "COMPARE — właściwość (Intl.Collator) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 59f274dc-6e52-4344-8d5c-b9f0000b66e0
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5bfd222ac8d2c94efe279177e7f4d8ffdf850f44
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="compare-property-intlcollator"></a>compare — Właściwość (Intl.Collator)
Zwraca funkcję, która porównuje dwa ciągi za pomocą rozdzielnika kolejności sortowania.  
  
## <a name="syntax"></a>Składnia  
  
```JavaScript  
collatorObj.compare  
```  
  
#### <a name="parameters"></a>Parametry  
 `collatorObj`  
 Wymagany. Nazwa `Collator` obiektu na potrzeby porównania.  
  
## <a name="remarks"></a>Uwagi  
 Funkcja zwrócony przez `compare` właściwość przyjmuje dwa argumenty `x` i `y`i zwraca wynik porównania ustawień regionalnych `x` i `y` przy użyciu określonego w opcji `Collator` obiekt.  
  
 Wynik porównania będzie:  
  
-   -1, gdy `x` przed `y` w kolejności sortowania.  
  
-   0 (zero), jeśli `x` jest równa `y` w kolejności sortowania.  
  
-   1, gdy `x` po `y` w kolejności sortowania.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy `Collator` obiektu i przeprowadza porównanie.  
  
```JavaScript  
var co = new Intl.Collator(["de-DE-u-co-phonebk"]);  
  
if (console && console.log) {  
    console.log(co.compare("a", "b")); // Returns -1  
}  
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
 W poniższym przykładzie użyto `Collator` wyszukiwanego ciągu obiektu.  
  
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
 [Intl.Collator — obiekt](../../javascript/reference/intl-collator-object-javascript.md)