---
title: Nieoczekiwany kwantyfikator (JavaScript) | Dokumentacja firmy Microsoft
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
- VS.WebClient.Help.SCRIPT5018
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ba6d34f9-2d6f-486c-a929-6cd9818be322
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ef0955bac35009d9b6c82f1856bb9005a08043ad
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44282270"
---
# <a name="unexpected-quantifier-javascript"></a>Nieoczekiwany kwantyfikator (JavaScript)
Podczas redagowania kryteria wyszukiwania wyrażeń regularnych, utworzono element wzorca z czynnikiem niedozwolony powtórzenia. Na przykład wzorzec  
  
```  
/^+/  
```  
  
 jest niedozwolony ponieważ element ^ (początku danych wejściowych) nie może mieć współczynnik powtórzenia. W poniższej tabeli wymieniono elementy, które nie może być powtórzenie czynników.  
  
|Element|Opis|  
|-------------|-----------------|  
|^|Początku danych wejściowych|  
|$|Koniec danych wejściowych|  
|\b|Granica słowa|  
|\B|Granica wyrazu nie|  
|*|Zero lub więcej powtórzeń|  
|+|Co najmniej powtórzeń|  
|?|Zero lub jeden powtórzeń|  
|{n}|n powtórzeń|  
|{n}|n lub więcej powtórzeń|  
|{n, m}|Od n do m powtórzeń, (włącznie)|  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Upewnij się, że Twoje element wzorzec wyszukiwania zawiera tylko czynniki prawne powtórzenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Obiekt będący wyrażeniem regularnym](../../javascript/reference/regular-expression-object-javascript.md)   
 [Składnia wyrażeń regularnych (JavaScript)](https://msdn.microsoft.com/library/1400241x)