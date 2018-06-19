---
title: Switch — instrukcja (JavaScript) | Dokumentacja firmy Microsoft
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
- switch_JavaScriptKeyword
- default_JavaScriptKeyword
- case_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- switch statement
ms.assetid: 61f80e8b-3739-4146-a893-c2832d92b28c
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a301fc8bcc72b48c6ba8e999c0ebb70fe9d92b41
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791905"
---
# <a name="switch-statement-javascript"></a>switch — Instrukcja (JavaScript)
Umożliwia wykonywanie operacji jedną lub więcej instrukcji, gdy wartość określonego wyrażenia jest zgodna z etykiety.  
  
## <a name="syntax"></a>Składnia  
  
```  
switch (expression) {  
    case label :  
        statementlist  
    case label :  
    default :  
        statementlist  
}   
```  
  
## <a name="parameters"></a>Parametry  
 `expression`  
 Wyrażenie do obliczenia.  
  
 `label`  
 Identyfikator, aby zostać dopasowany szablon `expression`. Jeśli `label` jest `expression`, rozpoczyna się od wykonania `statementlist` natychmiast po dwukropku i kontynuuje aż do napotkania albo `break` instrukcja, która jest opcjonalny, lub na końcu `switch` instrukcji.  
  
 `statementlist`  
 Jedna lub więcej instrukcji do wykonania.  
  
## <a name="remarks"></a>Uwagi  
 Użyj `default` klauzuli zapewnienie instrukcję do wykonania, jeśli brak etykiety wartości dopasowań `expression`. Go może występować w dowolnym miejscu w `switch` blok kodu.  
  
 Zero lub więcej `label` bloki może być określona. Jeśli nie `label` odpowiada wartości `expression`, a `default` case nie jest podany, wykonywane są żadnych instrukcji.  
  
 Wykonanie przechodzi przez `switch` instrukcji w następujący sposób:  
  
-   Ocena `expression` i przyjrzyj się `label` w kolejności, aż do znalezienia dopasowania.  
  
-   Jeśli `label` wartością `expression`, wykonaj jego towarzyszące `statementlist`.  
  
     Kontynuować działanie do momentu `break` napotkano instrukcji lub `switch` końce instrukcji. Oznacza to, że wiele `label` bloki są wykonywane, jeśli `break` instrukcja nie jest używany.  
  
-   Jeśli nie `label` jest równe `expression`, przejdź do `default` case. W przypadku nie `default` wielkość liter, przejdź do ostatniego kroku.  
  
-   Kontynuować działanie w instrukcji od końca `switch` blok kodu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład testów dla tego typu obiektu.  
  
```JavaScript  
function MyObjectType(obj) {  
    switch (obj.constructor) {  
        case Date:  
            document.write("Object is a Date.");  
            break;  
        case Number:  
            document.write("Object is a Number.");  
            break;  
        case String:  
            document.write("Object is a String.");  
            break;  
        default:  
            document.write("Object is unknown.");  
    }  
}  
  
// Output when obj is a Date:  
// Object is a Date.  
  
// Output when obj is a Number:  
// Object is a Number.  
  
// Output when obj is a String:  
// Object is a String.  
  
// Output when obj is something other than a Date, Number, or String:  
// Object is unknown.  
  
```  
  
## <a name="example"></a>Przykład  
 Poniższy kod pokazuje, co się stanie, jeśli nie używasz `break` instrukcji.  
  
```JavaScript  
function MyObjectType(obj) {  
    switch (obj.constructor) {  
        case Date:  
            document.write("Object is a Date.");  
        case Number:  
            document.write("Object is a Number.");  
        case String:  
            document.write("Object is a String.");  
        default:  
            document.write("Object is unknown.");  
    }  
}  
  
// Output when obj is a Date:  
// Object is a Date.Object is a Number.Object is a String.Object is unknown.  
  
// Output when obj is a Number:  
// Object is a Number.Object is a String.Object is unknown.  
  
// Output when obj is a String:  
// Object is a String.Object is unknown.  
  
// Output when obj is something other than a Date, Number, or String:  
// Object is unknown.  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcja BREAK](../../javascript/reference/break-statement-javascript.md)   
 [IF... else — instrukcja](../../javascript/reference/if-dot-dot-dot-else-statement-javascript.md)