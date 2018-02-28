---
title: "multiline — właściwość (wyrażenie regularne) (JavaScript) | Dokumentacja firmy Microsoft"
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
- multiline
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- multiline property
ms.assetid: ca7b276a-1fe2-4189-ac27-f089ab3e9974
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 289cb8d8e103d8c4ac1b1ef06714105d21cba743
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="multiline-property-regular-expression-javascript"></a>multiline — Właściwość (wyrażenie regularne) (JavaScript)
Zwraca wartość logiczną wskazującą stan flagi wielowierszowe (**m**) używane z wyrażeniem regularnym. Domyślnie jest **false**. Tylko do odczytu.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
rgExp.multiline  
```  
  
## <a name="remarks"></a>Uwagi  
 Wymagane `rgExp` argument jest wystąpieniem `RegExp` obiektu  
  
 **Wielowierszowy** zwraca **true** Jeśli flaga multiline ustawiono dla wyrażenia regularnego i zwraca **false** Jeśli nie jest. **Wielowierszowy** właściwość jest **true** Jeśli utworzono obiekt będący wyrażeniem regularnym **m** flagi.  
  
 Jeśli **wielowierszowy** jest **false**, "^" odpowiada pozycji na końcu ciągu pozycji na początku ciąg i dopasowania "$". Jeśli **wielowierszowy** jest **true**, "^" zgodny pozycja na początku ciąg również jako pozycji "\n" lub "\r" i "$" pasuje pozycji na końcu ciągu i pozycji poprzedzających "\n "lub"\r".  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia zachowanie **wielowierszowy** właściwości. W przypadku przekazania "m" w funkcji pokazano poniżej, wyraz "podczas" zastępuje słowem "i". Wynika to z faktu z ustawioną flagą wielowierszowy ustawiono i słowie "while" występuje na początku wiersza po znaku nowego wiersza. Flaga multiline umożliwia wyszukiwanie na ciągi wielowierszowe.  
  
```JavaScript  
function RegExpMultilineDemo(flag){  
   // The flag parameter is a string that contains  
   // g, i, or m.  The flags can be combined.  
  
   // Check flags for validity.  
   if (flag.match(/[^gim]/))  
      {  
      return ("Flag specified is not valid");  
      }  
  
   // Create the string on which to perform the replacement.  
   var ss = "The man hit the ball with the bat ";  
   ss += "\nwhile the fielder caught the ball with the glove.";  
  
   // Replace "while" with "and".  
   var re = new RegExp("^while", flag);  
   var r = ss.replace(re, "and");          
  
   // Output the multiline flag and the resulting string.  
   var s = "";  
   s += "Result for multiline = " + re.multiline.toString();  
   s += ": " + r;  
  
   return(s);  
  
}  
  
sa = RegExpMultilineDemo("m");  
sb = RegExpMultilineDemo("");  
document.write (sa + "<br />" + sb);  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Dotyczy**: [obiektu będącego wyrażeniem regularnym](../../javascript/reference/regular-expression-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Global — właściwość (wyrażenie regularne)](../../javascript/reference/global-property-regular-expression-javascript.md)   
 [ignoreCase właściwość (wyrażenie regularne)](../../javascript/reference/ignorecase-property-regular-expression-javascript.md)   
 [Składnia wyrażeń regularnych (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)