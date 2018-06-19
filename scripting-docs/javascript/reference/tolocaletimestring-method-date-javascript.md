---
title: toLocaleTimeString — metoda (Data) (JavaScript) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- toLocaleTimeString
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toLocaleTimeString method
ms.assetid: 8ad75bf5-864c-4a2a-be90-220e87dce172
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 77d8ee8fb6757b13da22a3cf3a59d28a105292cb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791971"
---
# <a name="tolocaletimestring-method-date-javascript"></a>toLocaleTimeString — Metoda (Data) (JavaScript)
Zwraca godzinę jako wartość ciągu, która jest odpowiednia do środowiska hosta bieżących ustawień regionalnych lub określone ustawienia regionalne.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
dateObj.toLocaleTimeString([locales][, options])  
```  
  
#### <a name="parameters"></a>Parametry  
 `dateObj`  
 Wymagany. A `Date` obiektu.  
  
 `locales`  
 Opcjonalny. Tablica ciągów ustawień regionalnych, które zawiera jeden lub więcej tagów języka lub ustawień regionalnych. Jeśli dołączysz więcej niż jeden ciąg ustawień regionalnych na listę w kolejności priorytetu tak, aby pierwszy wpis preferowanych ustawień regionalnych. Jeśli ten parametr zostanie pominięty, domyślne ustawienia regionalne środowiska wykonawczego języka JavaScript jest używany.  
  
 `options`  
 Opcjonalny. Obiekt, który zawiera jeden lub więcej właściwości, które opcje porównania.  
  
## <a name="remarks"></a>Uwagi  
 W programie Internet Explorer 11 `toLocaleTimeString` używa `Intl.DateTimeFormat` wewnętrznie formatującej czas, który dodaje obsługę `locales` i `options` parametrów. Aby uzyskać więcej informacji na temat tych parametrów, zobacz [Intl.DateTimeFormat](../../javascript/reference/intl-datetimeformat-object-javascript.md).  
  
> [!IMPORTANT]
>  `locales` i `options` parametry nie są obsługiwane we wszystkich trybach dokumentu i wersji przeglądarki. Aby uzyskać więcej informacji zobacz sekcję wymagania.  
  
 Jeśli używasz `toLocaleTimeString` w programie Internet Explorer 10 tryb, wcześniej tryby dokumentu i tryb Osobliwości dokumentu standardy:  
  
-   Zwraca wartość ciągu, która zawiera czas w bieżącej strefy czasowej.  
  
-   Zwrócony przypada w domyślnym formacie bieżące ustawienia regionalne środowisku hosta.  
  
 W przypadku pominięcia `locales` parametru, zwracana wartość ta metoda nie może opierać się skrypty, ponieważ będą się różnić między komputerami. W tym scenariuszu należy użyć metody tylko format wyświetlania tekstu — nigdy nie w ramach obliczeń.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `toLocaleTimeString` metody z podanych opcji regionalnych i porównania.  
  
```JavaScript  
var date = new Date(Date.UTC(2013, 1, 1, 14, 0, 0));  
var options = { weekday: "long", year: "numeric", month: "short",  
    day: "numeric" };  
  
// Using I18N toLocaleString  
document.write(date.toLocaleTimeString("en-US"));  
document.write(date.toLocaleTimeString("ja-JP"));  
document.write(date.toLocaleTimeString("ar-SA", options));  
document.write(date.toLocaleTimeString("hi-IN", options));  
  
// Output:  
// ‎‎6‎:‎00‎:‎00‎ ‎AM ‎   
// 6‎:‎00‎:‎00‎  
// ‏الجمعة‏, ‏٢٠‏ ‏ربيع الأول‏, ‏١٤٣٤ ٠٦‎:‎٠٠‎:‎٠٠‎ ‎ص  
// ‎शुक्रवार‎, ‎01‎ ‎फरवरी‎ ‎2013 06:00:00  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 `locales`i `options` parametry:  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [toTimeString — metoda (Data)](../../javascript/reference/totimestring-method-date-javascript.md)   
 [toLocaleDateString — metoda (Data)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)