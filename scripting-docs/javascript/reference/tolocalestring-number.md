---
title: toLocaleString (numer) | Dokumentacja firmy Microsoft
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
ms.assetid: 42c05252-13c1-4943-b1a4-b33285aeab3e
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9b5e6378ec94e032c908a3502c0324c2a5a91b26
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="tolocalestring-number"></a>toLocaleString (Number)
Konwertuje liczbę na ciąg przy użyciu ustawień regionalnych bieżącego lub został określony.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
numberObj.toLocaleString([locales][, options])   
```  
  
#### <a name="parameters"></a>Parametry  
 `numberObj`  
 Wymagany. `Number` Obiektu do skonwertowania.  
  
 `locales`  
 Opcjonalny. Tablica ciągów ustawień regionalnych, które zawiera jeden lub więcej tagów języka lub ustawień regionalnych. Jeśli dołączysz więcej niż jeden ciąg ustawień regionalnych na listę w kolejności priorytetu tak, aby pierwszy wpis preferowanych ustawień regionalnych. Jeśli ten parametr zostanie pominięty, domyślne ustawienia regionalne środowiska wykonawczego języka JavaScript jest używany.  
  
 `options`  
 Opcjonalny. Obiekt, który zawiera jeden lub więcej właściwości, które opcje porównania.  
  
## <a name="remarks"></a>Uwagi  
 W programie Internet Explorer 11 `toLocaleString` używa `Intl.NumberFormat` wewnętrznie w celu porównania upewnij, które dodaje obsługę `locales` i `options` parametrów. Aby uzyskać więcej informacji na temat tych parametrów, zobacz [Intl.NumberFormat](../../javascript/reference/intl-numberformat-object-javascript.md).  
  
> [!IMPORTANT]
>  `locales` i `options` parametry nie są obsługiwane we wszystkich trybach dokumentu i wersji przeglądarki. Aby uzyskać więcej informacji zobacz sekcję wymagania.  
  
> [!NOTE]
>  W przypadku pominięcia `locales` parametru, użyj `toLocaleString` tylko do wyświetlania wyników dla użytkownika; nigdy nie używaj go do obliczenia wartości w skrypcie, ponieważ zwrócony wynik dotyczące komputera (metoda zwraca bieżące ustawienia regionalne).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `toLocaleString` metody bez parametrów.  
  
```JavaScript  
var n, s;  
n = new Number(100);  
s = "Current locale value is: ";  
s += n.toLocaleString();                 
document.write(s);  
  
// Output:  
// The value 100 as represented by the current locale.  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `toLocaleString` metody z podanych opcji regionalnych i porównania.  
  
```JavaScript  
var number = 123456789;  
var options1 = { style: "percent" };  
var options2 = { style: "currency", currency: "INR" };  
  
document.write(number.toLocaleString("en-US"));  
// 123,456,789  
document.write(number.toLocaleString("ja-JP"));  
// 123,456,789  
document.write(number.toLocaleString("ar-SA", options1));  
// ١٢,٣٤٥,٦٧٨,٩٠٠ %  
document.write(number.toLocaleString("hi-IN", options2));  
// ₹ 12,34,56,789.00  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 `locales`i `options` parametry:  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [toLocaleDateString — metoda (Data)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)