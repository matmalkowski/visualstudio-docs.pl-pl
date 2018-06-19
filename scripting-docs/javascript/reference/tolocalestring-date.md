---
title: toLocaleString (Data) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 3472d7bd-b255-4804-8407-c4a1e419a5a3
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b6dc7b1f38f7e57d1c10f7197bb73b13b3545380
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791926"
---
# <a name="tolocalestring-date"></a>toLocaleString (Date)
Konwertuje datę w ciągu przy użyciu ustawień regionalnych bieżącego lub został określony.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
dateObj.toLocaleString([locales][, options])   
```  
  
#### <a name="parameters"></a>Parametry  
 `dateObj`  
 Wymagany. `Date` Obiektu do skonwertowania.  
  
 `locales`  
 Opcjonalny. Tablica ciągów ustawień regionalnych, które zawiera jeden lub więcej tagów języka lub ustawień regionalnych. Jeśli dołączysz więcej niż jeden ciąg ustawień regionalnych na listę w kolejności priorytetu tak, aby pierwszy wpis preferowanych ustawień regionalnych. Jeśli ten parametr zostanie pominięty, domyślne ustawienia regionalne środowiska wykonawczego języka JavaScript jest używany.  
  
 `options`  
 Opcjonalny. Obiekt, który zawiera jeden lub więcej właściwości, które opcje porównania.  
  
## <a name="remarks"></a>Uwagi  
 W programie Internet Explorer 11 `toLocaleString` używa `Intl.DateTimeFormat` wewnętrznie w celu porównania upewnij, które dodaje obsługę `locales` i `options` parametrów. Aby uzyskać więcej informacji na temat tych parametrów, zobacz [Intl.DateTimeFormat](../../javascript/reference/intl-datetimeformat-object-javascript.md).  
  
> [!IMPORTANT]
>  `locales` i `options` parametry nie są obsługiwane we wszystkich trybach dokumentu i wersji przeglądarki. Aby uzyskać więcej informacji zobacz sekcję wymagania.  
  
 Jeśli używasz `toLocaleString` w programie Internet Explorer 10 tryb, wcześniej tryby dokumentu i tryb Osobliwości dokumentu standardy:  
  
-   Zwraca `String` obiekt, który zawiera napisana bieżące ustawienia regionalne długi domyślny format daty.  
  
-   Dat między 1601 i 1999 r. N.E. Data jest sformatowany zgodnie z ustawień regionalnych użytkownika Panelu sterowania.  
  
> [!NOTE]
>  W przypadku pominięcia `locales` parametru, użyj `toLocaleString` tylko do wyświetlania wyników dla użytkownika; nigdy nie używaj go do obliczenia wartości w skrypcie, ponieważ zwrócony wynik jest specyficzne dla komputera.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `toLocaleString` metody.  
  
```JavaScript  
function toLocaleStrDemo(){     
   var d, s;                      //Declare variables.  
   d = new Date();                //Create Date object.  
   s = "Current setting is ";  
   s += d.toLocaleString();       //Convert to current locale.  
   return(s);                     //Return converted date  
}  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `toLocaleString` metody z podanych opcji regionalnych i porównania.  
  
```JavaScript  
var date = new Date(Date.UTC(2013, 1, 1, 14, 0, 0));  
var options = { weekday: "long", year: "numeric", month: "short",  
    day: "numeric" };  
  
// Using I18N toLocaleString  
document.write(date.toLocaleString("en-US"));  
document.write(date.toLocaleString("ja-JP"));  
document.write(date.toLocaleString("ar-SA", options));  
document.write(date.toLocaleString("hi-IN", options));  
  
// Output:  
// ‎2‎/‎1‎/‎2013‎ ‎6‎:‎00‎:‎00‎ ‎AM  
// ‎2013‎年‎2‎月‎1‎日‎ ‎6‎:‎00‎:‎00  
// ‏الجمعة‏, ‏٢٠‏ ‏ربيع الأول‏, ‏١٤٣٤  
// ‎शुक्रवार‎, ‎01‎ ‎फरवरी‎ ‎2013  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 `locales`i `options` parametry:  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [toLocaleDateString — metoda (Data)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)