---
title: '&#39; return &#39; Instrukcja poza funkcją | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT1018
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 03568f9f-5f4f-4a10-a738-9a73f3832b9e
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 07b633c87dc11b291a5a5783f8121b2a368996d6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24788908"
---
# <a name="39return39-statement-outside-of-function"></a>&#39; return &#39; Instrukcja poza funkcją
Możesz użyć `return` instrukcji w zakresie globalnym kodu. `return` Instrukcji powinna występować tylko w treści funkcji.  
  
 Wywoływanie funkcji z `()` operator jest wyrażenie. Wszystkie wyrażenia mają wartości; `return` instrukcji służy do określania wartości zwróconej przez funkcję. Ogólny kształt jest:  
  
```  
  
return [ expression ];  
```  
  
 Gdy `return` instrukcja jest wykonywana, *wyrażenie* jest obliczany i zwracany, jako wartość funkcji. Jeśli żadne wyrażenie **Niezdefiniowany** jest zwracany.  
  
 Zatrzymuje wykonanie funkcji, kiedy `return` instrukcja jest wykonywana, nawet jeśli istnieją inne instrukcje nadal pozostałych w treści funkcji. Wyjątkiem od tej reguły jest Jeśli **zwracać** występuje instrukcja w obrębie **spróbuj** bloku, i ma odpowiadającego **koniec** blok, kod w  **na koniec** bloku będą wykonywane przed funkcja zwraca wartość.  
  
 Jeśli funkcja zwraca ponieważ osiągnie koniec treści funkcji bez wykonywania `return` instrukcji, wartość zwracana jest **Niezdefiniowany** wartość (jest to wynik funkcji nie można użyć jako część większego wyrażenia ).  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Usuń `return` instrukcji z główną kodu (globalne).  
  
## <a name="see-also"></a>Zobacz też  
 [Return — instrukcja](../../javascript/reference/return-statement-javascript.md)   
 [Function — obiekt](../../javascript/reference/function-object-javascript.md)   
 [caller — właściwość (funkcja)](../../javascript/reference/caller-property-function-javascript.md)