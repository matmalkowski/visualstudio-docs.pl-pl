---
title: "toLocaleDateString — metoda (Data) (JavaScript) | Dokumentacja firmy Microsoft"
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
- toLocaleDateString
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toLocaleDateString method
ms.assetid: 0b83715c-8ced-4bd7-8940-a8007d002d10
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d6b4b019ad329a73bec13766932fbcadfa2ed133
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="tolocaledatestring-method-date-javascript"></a>toLocaleDateString — Metoda (Data) (JavaScript)
Zwraca datę, jako wartość ciągu, która jest odpowiednia do środowiska hosta bieżących ustawień regionalnych lub określone ustawienia regionalne.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
dateObj.toLocaleDateString( [locales][, options])   
```  
  
#### <a name="parameters"></a>Parametry  
 `dateObj`  
 Wymagany. A `Date` obiektu.  
  
 `locales`  
 Opcjonalny. Tablica ciągów ustawień regionalnych, które zawiera jeden lub więcej tagów języka lub ustawień regionalnych. Jeśli dołączysz więcej niż jeden ciąg ustawień regionalnych na listę w kolejności priorytetu tak, aby pierwszy wpis preferowanych ustawień regionalnych. Jeśli ten parametr zostanie pominięty, domyślne ustawienia regionalne środowiska wykonawczego języka JavaScript jest używany.  
  
 `options`  
 Opcjonalny. Obiekt, który zawiera jeden lub więcej właściwości, które opcje porównania.  
  
## <a name="remarks"></a>Uwagi  
 W programie Internet Explorer 11 `toLocaleDateString` używa `Intl.DateTimeFormat` wewnętrznie w celu formatowania daty, która dodaje obsługę `locales` i `options` parametrów. Aby uzyskać więcej informacji na temat tych parametrów, zobacz [Intl.DateTimeFormat](../../javascript/reference/intl-datetimeformat-object-javascript.md).  
  
> [!IMPORTANT]
>  `locales` i `options` parametry nie są obsługiwane we wszystkich trybach dokumentu i wersji przeglądarki. Aby uzyskać więcej informacji zobacz sekcję wymagania.  
  
 Jeśli używasz `toLocaleDateString` w programie Internet Explorer 10 tryb, wcześniej tryby dokumentu i tryb Osobliwości dokumentu standardy:  
  
-   Zwraca wartość ciągu, która zawiera datę w bieżącej strefy czasowej.  
  
-   Zwrócony Data jest w domyślnym formacie bieżące ustawienia regionalne środowisku hosta.  
  
 W przypadku pominięcia `locales` parametru, zwracana wartość ta metoda nie może opierać się skrypty, ponieważ będą się różnić między komputerami. W tym scenariuszu należy użyć metody tylko format wyświetlania tekstu — nigdy nie w ramach obliczeń.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `toLocaleDateString` metody z podanych opcji regionalnych i porównania.  
  
```JavaScript  
var date = new Date(Date.UTC(2013, 1, 1, 14, 0, 0));  
var options = { weekday: "long", year: "numeric", month: "short",  
    day: "numeric" };  
  
// Using I18N toLocaleString  
document.write(date.toLocaleDateString("en-US"));  
document.write(date.toLocaleDateString("ja-JP"));  
document.write(date.toLocaleDateString("ar-SA", options));  
document.write(date.toLocaleDateString("hi-IN", options));  
  
// Output:  
// ‎2‎/‎1‎/‎2013‎   
// ‎2013‎年‎2‎月‎1‎日‎  
// ‏الجمعة‏, ‏٢٠‏ ‏ربيع الأول‏, ‏١٤٣٤  
// ‎शुक्रवार‎, ‎01‎ ‎फरवरी‎ ‎2013  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 `locales`i `options` parametry:  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [toDateString — metoda (Data)](../../javascript/reference/todatestring-method-date-javascript.md)   
 [toLocaleTimeString — metoda (Data)](../../javascript/reference/tolocaletimestring-method-date-javascript.md)