---
title: "ignoreCase właściwość (wyrażenie regularne) (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: ignoreCase
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: IgnoreCase property
ms.assetid: 816f0df5-5a82-44a5-a4ab-dbc91fa76e61
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ae9fee8e6303fb944f59c11c173f9e8b7f7cc75a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="ignorecase-property-regular-expression-javascript"></a>ignoreCase Właściwość (wyrażenie regularne) (JavaScript)
Zwraca wartość logiczną wskazującą stan Flaga ignoreCase (**i**) używane z wyrażeniem regularnym. Domyślnie jest **false**. Tylko do odczytu.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
rgExp.ignoreCase  
```  
  
## <a name="remarks"></a>Uwagi  
 Wymagane `rgExp` odwołania jest wystąpieniem `RegExp` obiektu.  
  
 **IgnoreCase** zwraca **true** Jeśli flaga ignoreCase ustawiono dla wyrażenia regularnego i zwraca **false** Jeśli nie jest.  
  
 Flaga ignoreCase, gdy jest używany, wskazuje, że wyszukiwanie ignorować uwzględniana wielkość liter podczas dopasowywania wzorzec ciągu przeszukane.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie **ignoreCase** właściwości. Funkcji pokazano poniżej, w przypadku przekazania "gi", wszystkie wystąpienia wyrazu "" są zamienione wyraz "", w tym początkowej "". Jest to spowodowane z ustawioną flagą ignoreCase, wyszukiwanie ignoruje wszystkie uwzględniana wielkość liter. Dlatego "T" jest taka sama jak "t" na potrzeby dopasowywania.  
  
 Ta funkcja zwraca wartości logiczne, które wskazują stan flagi dopuszczalny wyrażenie regularne, które są **g**, **i**, i **m**. Funkcja również zwraca ciąg z wszystkie elementy zastępcze wprowadzone.  
  
```JavaScript  
function RegExpPropDemo(flag){  
    // The flag parameter is a string that contains  
    // g, i, or m. The flags can be combined.  
  
    // Check flags for validity.  
    if (flag.match(/[^gim]/))  
        {  
        return ("Flag specified is not valid");  
        }  
  
    // Create the string on which to perform the replacement.  
    var orig = "The batter hit the ball with the bat ";  
    orig += "and the fielder caught the ball with the glove.";  
  
    // Replace "the" with "a".  
    var re = new RegExp("the", flag);  
    var r = orig.replace(re, "a");          
  
    // Output the resulting string and the values of the flags.  
    var s = "";  
    s += "global: " + re.global.toString();  
    s += "<br />";  
    s += "ignoreCase: " + re.ignoreCase.toString();  
    s += "<br />";  
    s += "multiline: " + re.multiline.toString();  
    s += "<br />";  
    s += "Resulting String: " + r;  
    s += "<br />";  
    s += "<br />";  
    return (s);  
}  
  
document.write(RegExpPropDemo("gi"));  
document.write(RegExpPropDemo("g"));  
```  
  
## <a name="example"></a>Przykład  
 Poniżej przedstawiono dane wyjściowe.  
  
```JavaScript  
global: true  
ignoreCase: true  
multiline: false  
Resulting String: a batter hit a ball with a bat and a fielder caught a ball with a glove.  
  
global: true  
ignoreCase: false  
multiline: false  
Resulting String: The batter hit a ball with a bat and a fielder caught a ball with a glove.  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Dotyczy**: [obiektu będącego wyrażeniem regularnym](../../javascript/reference/regular-expression-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Global — właściwość (wyrażenie regularne)](../../javascript/reference/global-property-regular-expression-javascript.md)   
 [multiline — właściwość (wyrażenie regularne)](../../javascript/reference/multiline-property-regular-expression-javascript.md)   
 [Składnia wyrażeń regularnych (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)