---
title: localeCompare — metoda (ciąg) (JavaScript) | Dokumentacja firmy Microsoft
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
- localeCompare
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- localeCompare method
ms.assetid: 66914079-12dd-4393-a84c-c05f58231c36
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 056a440d26c4ebf48bd762968fa32ea1efdfb443
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791374"
---
# <a name="localecompare-method-string-javascript"></a>localeCompare — Metoda (ciąg) (JavaScript)
Określa, czy dwa ciągi, które są równoważne w bieżących ustawień regionalnych.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
stringVar.localeCompare(stringExp[, locales][, options])   
```  
  
## <a name="parameters"></a>Parametry  
 `stringVar`  
 Wymagany. Pierwszy ciąg do porównania.  
  
 `stringExp`  
 Wymagany. Drugi ciąg do porównania.  
  
 `locales`  
 Opcjonalny. Tablica ciągów ustawień regionalnych, które zawiera jeden lub więcej tagów języka lub ustawień regionalnych. Jeśli dołączysz więcej niż jeden ciąg ustawień regionalnych na listę w kolejności priorytetu tak, aby pierwszy wpis preferowanych ustawień regionalnych. Jeśli ten parametr zostanie pominięty, domyślne ustawienia regionalne środowiska wykonawczego języka JavaScript jest używany. Ten parametr musi być zgodna z [BCP 47](http://tools.ietf.org/html/rfc5646) standardów; zobacz [Intl.Collator — obiekt](../../javascript/reference/intl-collator-object-javascript.md) szczegółowe informacje.  
  
 `options`  
 Opcjonalny. Obiekt, który zawiera jeden lub więcej właściwości, które opcje porównania. zobacz [Intl.Collator — obiekt](../../javascript/reference/intl-collator-object-javascript.md) szczegółowe informacje.  
  
## <a name="remarks"></a>Uwagi  
 Dla porównania ciągów, należy określić albo `String` obiektów lub literałów ciągów.  
  
 W programie Internet Explorer 11 `localeCompare` używa `Intl.Collator` obiekt wewnętrznie do porównania, która dodaje obsługę `locales` i `options` parametrów. Aby uzyskać więcej informacji na temat tych parametrów, zobacz [Intl.Collator](../../javascript/reference/intl-collator-object-javascript.md) i [Intl.Collator.compare](../../javascript/reference/compare-property-intl-collator.md).  
  
> [!IMPORTANT]
>  `locales` i `options` parametry nie są obsługiwane we wszystkich trybach dokumentu i wersji przeglądarki. Aby uzyskać więcej informacji zobacz sekcję wymagania.  
  
 `localeCompare` Metoda przeprowadza porównanie ciągu zależne od ustawień regionalnych `stringVar` i `stringExp` i zwraca jedną z następujących wyników, w zależności od porządek sortowania dla domyślnych ustawień regionalnych systemu:  
  
-   -1, gdy `stringVar` sortuje przed `stringExp`.  
  
-   + 1, gdy `stringVar` sortuje po `stringExp`.  
  
-   0 (zero), jeśli dwa ciągi są równoważne.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia sposób użycia `localeCompare`.  
  
```JavaScript  
var str1 = "def";  
var str2 = "abc"  
  
document.write(str1.localeCompare(str2) + "<br/>");  
  
// Output: 1  
var str3 = "ghi";  
  
document.write(str1.localeCompare(str3)+ "<br/>");  
  
// Output: -1  
var str4 = "def";  
  
document.write(str1.localeCompare(str4));  
  
// Output: 0  
```  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia sposób użycia `localeCompare` z ustawieniami regionalnymi niemiecki (Niemcy).  
  
```JavaScript  
var str1 = "a";  
var str2 = "b";  
  
document.write(str1.localeCompare(str2, "de-DE"));  
  
// Output  
// - 1  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `localeCompare` z ustawień regionalnych niemiecki (Niemcy) i rozszerzenie ustawień regionalnych, które określa porządek sortowania dla niemieckim książki telefonicznej. Ten przykład przedstawia różnice specyficzne dla ustawień regionalnych.  
  
```JavaScript  
var arr = ["ä", "ad", "af", "a"];  
  
document.write(arr[0].localeCompare(arr[1], "de-DE-u-co-phonebk"));  // Returns 1  
document.write (arr[0].localeCompare(arr[2], "de-DE-u-co-phonebk"));  // Returns -1  
document.write (arr[0].localeCompare(arr[3], "de-DE-u-co-phonebk"));  // Returns 1  
  
document.write (arr[0].localeCompare(arr[1], "de-DE"));  // Returns -1  
document.write (arr[0].localeCompare(arr[2], "de-DE"));  // Returns -1  
document.write (arr[0].localeCompare(arr[3], "de-DE"));  // Returns 1  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 `locales`i `options` parametry:  
  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [toLocaleString — metoda (obiekt)](../../javascript/reference/tolocalestring-method-object-javascript.md)