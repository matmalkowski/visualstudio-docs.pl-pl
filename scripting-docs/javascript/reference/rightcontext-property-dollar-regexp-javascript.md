---
title: "rightContext właściwość ($&#39;) (RegExp) (JavaScript) | Dokumentacja firmy Microsoft"
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
- $'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- rightContext property ($')
ms.assetid: 6999c056-d18c-4583-9dd9-8fbb6d3d0ee7
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d47ea5dd67de9d73ab59b615c567ad3a7a96fb7b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="rightcontext-property-39-regexp-javascript"></a>rightContext właściwość ($&#39;) (RegExp) (JavaScript)
Zwraca znaki od pozycji po ostatnim dopasowania do końca ciągu przeszukane. Tylko do odczytu.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
RegExp.rightContext  
```  
  
## <a name="remarks"></a>Uwagi  
 Obiekt skojarzony z tą właściwością jest zawsze globalnej `RegExp` obiektu.  
  
 Początkowa wartość **rightContext** właściwość jest ciągiem pustym. Wartość **rightContext** zmiany właściwości po każdej pomyślnego dopasowania.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie **rightContext** właściwości:  
  
```JavaScript  
// Create the regular expression pattern.  
var re = new RegExp("d(b+)(d)","ig");  
var str = "cdbBdbsbdbdz";  
  
// Perform the search.  
var arr = re.exec(str);  
  
// Print the output.  
var s = ""   
s += "$1: " + RegExp.$1 + "<br />";  
s += "$2: " + RegExp.$2 + "<br />";  
s += "$3: " + RegExp.$3 + "<br />";  
s += "input: " + RegExp.input + "<br />";  
s += "lastMatch: " + RegExp.lastMatch + "<br />";  
s += "leftContext: " + RegExp.leftContext + "<br />";  
s += "rightContext: " + RegExp.rightContext + "<br />";   
s += "lastParen: " + RegExp.lastParen + "<br />";  
  
document.write(s);  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Dotyczy**: [RegExp — obiekt](../../javascript/reference/regexp-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [$1... $9 — właściwości (RegExp)](../../javascript/reference/dollar-1-dot-dot-dot-dollar-9-properties-regexp-javascript.md)   
 [INDEX — właściwość (RegExp)](../../javascript/reference/index-property-regexp-javascript.md)   
 [Input — właściwość ($_) (RegExp)](../../javascript/reference/input-property-dollar-regexp-javascript.md)   
 [lastIndex właściwość (RegExp)](../../javascript/reference/lastindex-property-regexp-javascript.md)   
 [lastMatch właściwość ($&) (RegExp)](../../javascript/reference/lastmatch-property-dollar-regexp-javascript.md)   
 [lastParen właściwość ($ +) (RegExp)](../../javascript/reference/lastparen-property-dollar-regexp-javascript.md)   
 [leftContext właściwość ($') (RegExp)](../../javascript/reference/leftcontext-property-dollar-grave-regexp-javascript.md)