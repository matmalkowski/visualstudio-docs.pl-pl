---
title: Nieoczekiwany kwantyfikator (JavaScript) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT5018
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ba6d34f9-2d6f-486c-a929-6cd9818be322
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fb6d6d3129057c399dd7369c6f69eb7396f07ab4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="unexpected-quantifier-javascript"></a>Nieoczekiwany kwantyfikator (JavaScript)
Tworząc wzorzec wyszukiwania z wyrażeniem regularnym utworzony element wzorzec współczynnik niedozwolony powtarzania. Na przykład wzorzec  
  
```  
/^+/  
```  
  
 jest niedozwolony, ponieważ element ^ (początku danych wejściowych) nie może mieć współczynnik powtarzania. W poniższej tabeli wymieniono elementy, które nie mogą mieć czynniki powtarzania.  
  
|Element|Opis|  
|-------------|-----------------|  
|^|Początku danych wejściowych|  
|$|Koniec danych wejściowych|  
|\b|Ogranicznik słowa|  
|\B|Granic non-word|  
|*|Zero lub więcej powtórzeń|  
|+|Co najmniej jeden powtórzeń|  
|?|Zero lub jeden powtórzeń|  
|{n}|n powtórzeń|  
|{n}|n lub więcej powtórzeń|  
|{n, m}|Od n do m powtórzeń, włącznie|  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Upewnij się, że tylko czynniki prawne powtarzania zawiera nazwę elementu wzorca wyszukiwania.  
  
## <a name="see-also"></a>Zobacz też  
 [Obiekt będący wyrażeniem regularnym](../../javascript/reference/regular-expression-object-javascript.md)   
 [Składnia wyrażeń regularnych (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)