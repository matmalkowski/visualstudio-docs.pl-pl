---
title: "replace — metoda (ciąg) (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: replace
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- replacing strings
- Replace method
ms.assetid: 5f0e4765-df4d-4887-bd09-efe5e58251bf
caps.latest.revision: "28"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e78e17d4b9060a3a52498109a744c13cdf972abb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="replace-method-string-javascript"></a>replace — Metoda (Ciąg) (JavaScript)
Zastępuje tekst w ciągu przy użyciu wyrażenia regularnego lub ciągu wyszukiwania.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
stringObj. replace(rgExp, replaceText)  
```  
  
## <a name="parameters"></a>Parametry  
 `stringObj`  
 Wymagany. `String` Obiektu lub na którym należy wykonać zastępczy literału ciągu. Ten ciąg nie jest modyfikowany przez **Zastąp** metody. Wartością zwracaną tej metody jest ciąg powstały w wyniku operacji zastępowania.  
  
 `rgExp`  
 Wymagany. Wystąpienie **wyrażenia regularnego** obiektu zawierającego odpowiednie flagi i wzorzec wyrażenia regularnego. Można też `String` obiektu lub literału ciągu, który reprezentuje wyrażenie regularne. Jeśli `rgExp` nie jest wystąpieniem **wyrażenia regularnego** obiektu, jest konwertowana na ciąg i dokładne wyszukiwanie jest przeprowadzane dla wyników; nie są podejmowane próby można przekonwertować ciągu do wyrażenia regularnego.  
  
 `replaceText`  
 Wymagany. A `String` obiektu lub zawierający tekst, który ma zastąpić co pomyślnego dopasowania z literału ciągu `rgExp` w `stringObj`. W [!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] lub nowszym, `replaceText` argument może być również funkcję, która zwraca tekst zastępczy.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wynik **Zastąp** metody jest kopią `stringObj` po określonym zastępcze.  
  
## <a name="remarks"></a>Uwagi  
 Dowolna z następujących zmiennych dopasowania może służyć do identyfikowania najnowszych dopasowań i ciągów, z których pochodzą. Zmienne dopasowania mogą być używane w zastępowaniu tekstu, gdy ciąg zastępujący musi być określany dynamicznie.  
  
|Znaki|Znaczenie|  
|----------------|-------------|  
|**$$**|`$`([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] lub nowszy)|  
|**$&**|Określa część `stringObj` cały wzorzec jest zgodny. ([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] lub nowszy)|  
|`$``|Określa część `stringObj` czy poprzedza dopasowania opisanego przez  **$&** . ([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] lub nowszy)|  
|`$'`|Określa część `stringObj` następujący dopasowania opisanego przez  **$&** . ([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] lub nowszy)|  
|`$`  ***n***|*n* Th przechwycone submatch, gdzie  *n*  jest pojedynczą cyfrą dziesiętną z zakresu od 1 do 9. ([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] lub nowszy)|  
|`$`  ***nn***|*nn* Th przechwycone submatch, gdzie  *nn*  jest liczbą dziesiętną dwucyfrowe od 01 do 99. ([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] lub nowszy)|  
  
 Jeśli `replaceText` to funkcja, dla każdego podciąg funkcja jest wywoływana z następującymi *m* + 3 argumenty gdzie *m* jest liczba pozostałych Przechwytywanie nawiasów w `rgExp`. Pierwszy argument jest dopasowanym podciągiem. Następne *m* argumenty są wszystkie przechwytywania, które powstały w wyniku wyszukiwania. Argument *m* + 2 jest przesunięcie w `stringObj` którym wystąpił dopasowania, a argument *m* + 3 jest `stringObj`. Wynikiem jest wartość w postaci ciągu, powstałego w wyniku zastąpienia każdego dopasowanego podciągu wartością zwracaną z wywołania funkcji.  
  
 **Zastąp** metody aktualizuje właściwości globalne `RegExp` obiektu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie **Zastąp** metodę, aby zastąpić wszystkie wystąpienia wyrazu "", "a".  
  
```JavaScript  
var s = "the batter hit the ball with the bat";  
  
// Replace "the" with "a".  
var re = /the/g;  
var result = s.replace(re, "a");  
document.write(result);  
// Output: a batter hit a ball with a bat  
```  
  
 Ponadto **Zastąp** metody może również zastąpić użyto we wzorcu. Poniższy przykład przedstawia zamianę każdej pary słów w ciągu.  
  
```JavaScript  
  
var s = "The quick brown fox jumped over the lazy dog.";  
var re = /(\S+)(\s+)(\S+)/g;  
// Exchange each pair of words.  
var result = s.replace(re, "$3$2$1");  
document.write(result);  
  
// Output:  quick The fox brown over jumps lazy the dog.  
```  
  
 Poniższy przykład, który działa w [!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] i później, przedstawia sposób użycia funkcji, która zwraca tekst zastępczy. Zastępuje wszelkie wystąpienia liczby, po której występuje litera "F" na wartość będąca odpowiednikiem w stopniach Celsjusza.  
  
```JavaScript  
function f2c(s1) {  
    // Initialize pattern.  
    var test = /(\d+(\.\d*)?)F\b/g;  
  
    // Use a function for the replacement.  
    var s2 = s1.replace(test,  
      function($0,$1,$2)  
           {   
           return((($1-32) * 5/9) + "C");  
           }  
        )  
    return s2;  
}  
document.write(f2c("Water freezes at 32F and boils at 212F."));  
  
// Output: Water freezes at 0C and boils at 100C.  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Dotyczy**: [ciągu obiektu](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [exec — metoda (wyrażenie regularne)](../../javascript/reference/exec-method-regular-expression-javascript.md)   
 [Match — metoda (ciąg)](../../javascript/reference/match-method-string-javascript.md)   
 [RegExp — obiekt](../../javascript/reference/regexp-object-javascript.md)   
 [Search — metoda (ciąg)](../../javascript/reference/search-method-string-javascript.md)   
 [Test — metoda (wyrażenie regularne)](../../javascript/reference/test-method-regular-expression-javascript.md)   
 [Programowanie wyrażeniem regularnym (JavaScript)](http://msdn.microsoft.com/en-us/3b62e27c-4f07-4726-a95b-6e841807bfaf)   
 [Wyrażenia warunkowe i użyto (JavaScript)](http://msdn.microsoft.com/en-us/c59dd3e8-7fee-493e-9123-065af1e651ae)   
 [Odwołania wstecznego (JavaScript)](http://msdn.microsoft.com/en-us/5d8dbd5a-cd03-4548-850b-9d7bad2c839a)   
 [HTML5 przeciągnij i upuść przykładowej aplikacji](http://code.msdn.microsoft.com/Drag-and-drop-e2701a72)