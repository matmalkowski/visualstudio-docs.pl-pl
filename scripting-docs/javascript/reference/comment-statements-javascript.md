---
title: "Komentarz dotyczący instrukcji (JavaScript) | Dokumentacja firmy Microsoft"
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
- Comment_JavaScript
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- comments, ignoring
- comment statements
ms.assetid: b604824f-ac17-49d3-bcdb-2a893ab5fff8
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c270379725550e116928bbecd69e6be51c34992f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="comment-statements-javascript"></a>Instrukcje komentarzy (JavaScript)
Powoduje, że komentarze, które mają być ignorowane przez [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] analizatora.  
  
## <a name="syntax"></a>Składnia  
  
```  
Single-line Comment:  
// comment   
```  
  
```  
Multiline Comment:  
/*  
comment  
*/  
```  
  
```  
Comments with conditional compilation:  
//@CondStatement   
  
/*@  
condStatement  
@*/  
```  
  
## <a name="remarks"></a>Uwagi  
 `comment` Argument jest tekst wszelkie komentarze, które mają zostać uwzględnione w skrypcie. `condStatement` Argument ma być używany, jeśli kompilacja warunkowa jest aktywna. Jeśli używane są jednowierszowego, komentarze, może istnieć bez spacji między "/ /" i "@" znaków.  
  
 Używając komentarzy, można zapobiec przez części skryptu [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] analizatora. Komentarze umożliwia umieścić uwagi wyjaśniające w programie.  
  
 Jeśli używane są jednowierszowego, komentarze, analizator ignoruje dowolny tekst od znacznika komentarza i na końcu wiersza. Jeśli używane są Komentarze wielowierszowe, analizator pomija wszelkie między znacznikami początku i na końcu.  
  
 Komentarze są używane do obsługi kompilacja warunkowa, zachowując zgodność z przeglądarkami, które nie obsługują tej funkcji. Te przeglądarki odpowiednio traktować te rodzaje komentarze jako jeden wiersz lub Komentarze wielowierszowe.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia najbardziej typowych zastosowań komentarze.  
  
```JavaScript  
/* This is a multiline comment that  
    can span as many lines as necessary.  */  
function myfunction(arg1, arg2){  
    var r;  
    // This is a single line comment.  
    r = arg1 + arg2  
    return(r);  
}  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie kompilacji warunkowej. W tym przykładzie użyto ograniczników do komentarzy specjalne, które są używane tylko wtedy, gdy kompilacja warunkowa jest aktywowany przez `@cc_on` instrukcji. Aparaty skryptów, które nie obsługują kompilacji warunkowej, znajdują jedynie komunikat informujący o tym, że kompilacja warunkowa nie jest obsługiwana.  
  
```JavaScript  
/*@cc_on @*/  
/*@if (@_jscript_version >= 4)  
    alert("JavaScript version 4 or better");  
    @else @*/  
    alert("Conditional compilation not supported by this scripting engine.");  
/*@end @*/  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]