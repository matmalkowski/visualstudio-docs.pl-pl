---
title: "Throw musi występować wyrażenie w tym samym wierszu źródłowym | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT1035
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b03b7747-01a1-40c6-af80-a1dd70bc5781
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7179a22d2713c9ddc894618bd6921f3f873f2ad8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="throw-must-be-followed-by-an-expression-on-the-same-source-line"></a>Po instrukcji Throw musi występować wyrażenie w tym samym wierszu źródłowym
Możesz użyć `throw` — słowo kluczowe, ale nie wykonać go z wyrażeniem na tym samym wierszu źródłowym. A `throw` instrukcji składa się z dwóch części: `throw` — słowo kluczowe, a następnie wyrażenie, które ma zostać wygenerowany. Na przykład:  
  
```JavaScript  
if (denominator == 0) {  
 throw new DivideByZeroException();  
}  
```  
  
 Te dwa składniki nie można podzielić.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Upewnij się, że `throw` — słowo kluczowe i wyrażenie, które ma zostać zgłoszony, pojawi się w tym samym wierszu.  
  
## <a name="see-also"></a>Zobacz też  
 [Error — obiekt](../../javascript/reference/error-object-javascript.md)   
 [throw — instrukcja](../../javascript/reference/throw-statement-javascript.md)   
 [try... catch... finally — instrukcja](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)