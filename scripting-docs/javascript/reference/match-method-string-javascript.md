---
title: "Match — metoda (ciąg) (JavaScript) | Dokumentacja firmy Microsoft"
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
- match
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Match method
ms.assetid: eda9ad27-4f9b-4cb1-8345-a0ae85979ca0
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 46727942d73779351f1c0cceaf2eb90a691a8ebe
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="match-method-string-javascript"></a>match — Metoda (Ciąg) (JavaScript)
Dopasowuje ciąg z wyrażeniem regularnym i zwraca tablicę zawierającą wyniki tego wyszukiwania.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
stringObj.match(rgExp)   
```  
  
## <a name="parameters"></a>Parametry  
 `stringObj`  
 Wymagany. `String` Obiektu lub na którym należy wykonać wyszukiwanie literału ciągu.  
  
 `rgExp`  
 Wymagany. Obiekt będący wyrażeniem regularnym zawierającego odpowiednie flagi i wzorzec wyrażenia regularnego. Może to być również w nazwie zmiennej ani zawierający wzorzec wyrażenia regularnego i flagi literału ciągu.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `match` — metoda nie znaleziono dopasowania, zwraca `null`. Jeśli znajdzie dopasowanie, `match` zwraca tablicę i właściwości globalne `RegExp` obiektu są aktualizowane w celu odzwierciedlenia wyniki dopasowania.  
  
 Jeśli flaga global (`g`) nie jest ustawiona, Element zero tablicy zawiera całego dopasowania, podczas gdy elementy 1 za pośrednictwem  *n*  zawierać żadnych submatches. To zachowanie jest taka sama jak zachowanie [exec — metoda (wyrażenie regularne)](../../javascript/reference/exec-method-regular-expression-javascript.md) gdy nie ustawiono flagi globalne. Jeśli globalne flaga jest ustawiona, elementy 0 za pomocą  *n*  zawierają wszystkie dopasowania, które wystąpiły.  
  
 Jeśli Flaga globalna nie jest ustawiona, tablica zwrócona przez `match` metoda ma dwie właściwości `input` i `index`. `input` Właściwość zawiera cały ciąg przeszukane. `index` Właściwość zawiera pozycja podciąg ciągu przeszukane ukończone.  
  
 Jeśli flaga `i` jest ustawiona, wyszukiwanie nie jest rozróżniana wielkość liter.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `match` metody.  
  
```JavaScript  
var src = "azcafAJAC";  
  
var re = /[a-c]/;  
  
var result = src.match(re);  
  
// The entire match is in array element 0.  
document.write(result[0] + "<br/>");  
  
// Now try the same match with the global flag.  
var reg = /[a-c]/g;  
result = src.match(reg);  
  
// The matches are in elements 0 through n.  
for (var index = 0; index < result.length; index++)  
{  
    document.write ("submatch " + index + ": " +  result[index]);  
    document.write("<br />");  
}  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Dotyczy**: [ciągu obiektu](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [exec — metoda (wyrażenie regularne)](../../javascript/reference/exec-method-regular-expression-javascript.md)   
 [RegExp — obiekt](../../javascript/reference/regexp-object-javascript.md)   
 [Obiekt będący wyrażeniem regularnym](../../javascript/reference/regular-expression-object-javascript.md)   
 [replace — metoda (ciąg)](../../javascript/reference/replace-method-string-javascript.md)   
 [Search — metoda (ciąg)](../../javascript/reference/search-method-string-javascript.md)   
 [Test — metoda (wyrażenie regularne)](../../javascript/reference/test-method-regular-expression-javascript.md)   
 [Programowanie wyrażeniem regularnym (JavaScript)](http://msdn.microsoft.com/en-us/3b62e27c-4f07-4726-a95b-6e841807bfaf)   
 [Wyrażenia warunkowe i użyto (JavaScript)](http://msdn.microsoft.com/en-us/c59dd3e8-7fee-493e-9123-065af1e651ae)   
 [Odwołania wstecznego (JavaScript)](http://msdn.microsoft.com/en-us/5d8dbd5a-cd03-4548-850b-9d7bad2c839a)