---
title: "exec — metoda (wyrażenie regularne) (JavaScript) | Dokumentacja firmy Microsoft"
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
- exec
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- matching strings
- Exec method
ms.assetid: 83092452-60cc-4218-b4ae-af9e3cb96c34
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 426cc1a8162b03090289cf737a03d64a75df77e9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="exec-method-regular-expression-javascript"></a>exec — Metoda (wyrażenie regularne) (JavaScript)
Wykonuje wyszukiwanie w ciągu przy użyciu wzorzec wyrażenia regularnego i zwraca tablicę zawierającą wyniki tego wyszukiwania.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
rgExp.exec(str)   
```  
  
## <a name="parameters"></a>Parametry  
 `rgExp`  
 Wymagany. Wystąpienie **wyrażenia regularnego** obiektu zawierającego odpowiednie flagi i wzorzec wyrażenia regularnego.  
  
 `str`  
 Wymagany. `String` Obiektu lub na którym należy wykonać wyszukiwanie literału ciągu.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `exec` — metoda nie znaleziono dopasowania, zwraca `null`. Jeśli znajdzie dopasowanie, `exec` zwraca tablicę i właściwości globalne `RegExp` obiektu są aktualizowane w celu odzwierciedlenia wyniki dopasowania. Element zero tablicy zawiera całego dopasowania, podczas gdy elementy 1 -  *n*  zawierać żadnych submatches, które wystąpiły w dopasowania. To zachowanie jest takie same jak zachowanie `match` metody bez flagi globalne (**g**) Ustaw.  
  
 Jeśli ustawiono flagi globalne wyrażenie regularne `exec` wyszukuje ciąg początek w pozycji wartość `lastIndex`. Jeśli nie ustawiono flagi globalne, `exec` ignoruje wartość `lastIndex` i wyszukiwanie od początku ciągu.  
  
 Tablica zwrócona przez `exec` metoda ma trzy właściwości **wejściowych**, **indeksu** i **lastIndex.** **Wejściowych** właściwość zawiera cały ciąg przeszukane. **Indeksu** właściwość zawiera pozycja podciąg ciągu przeszukane ukończone. `lastIndex` Właściwość zawiera pozycji po ostatnim znaku w dopasowania.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `exec` metody:  
  
```JavaScript  
function RegExpTest()  
{  
   var ver = Number(ScriptEngineMajorVersion() + "." + ScriptEngineMinorVersion())  
   if (ver < 5.5)  
   {  
      document.write("You need a newer version of JavaScript for this to work");  
      return;  
   }  
  
   var src = "The quick brown fox jumps over the lazy dog.";  
  
   // Create regular expression pattern with a global flag.  
   var re = /\w+/g;  
  
   // Get the next word, starting at the position of lastindex.  
   var arr;  
   while ((arr = re.exec(src)) != null)  
      {  
      // New line:  
      document.write ("<br />");    
      document.write (arr.index + "-" + arr.lastIndex + " ");  
      document.write (arr[0]);  
      }  
}  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Dotyczy**: [obiektu będącego wyrażeniem regularnym](../../javascript/reference/regular-expression-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Match — metoda (ciąg)](../../javascript/reference/match-method-string-javascript.md)   
 [RegExp — obiekt](../../javascript/reference/regexp-object-javascript.md)   
 [Składnia wyrażeń regularnych (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [Search — metoda (ciąg)](../../javascript/reference/search-method-string-javascript.md)   
 [Test — metoda (wyrażenie regularne)](../../javascript/reference/test-method-regular-expression-javascript.md)   
 [Programowanie wyrażeniem regularnym (JavaScript)](http://msdn.microsoft.com/en-us/3b62e27c-4f07-4726-a95b-6e841807bfaf)