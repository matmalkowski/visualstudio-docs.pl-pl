---
title: "Oczekiwano &#39;) &#39; w wyrażeniu regularnym (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT5020
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 2087ba1d-9783-4d40-b609-e8542f579f7f
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ca4560c638cc0e9209141ba9b0878208eb84eb0c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="expected-3939-in-regular-expression-javascript"></a>Oczekiwano &#39;) &#39; w wyrażeniu regularnym (JavaScript)
Podjęto próbę utworzenia wyrażenia regularnego przechwytywania, potwierdzenia lub grupy, ale nie zawiera nawiasem zamykającym. Nawiasy ma kilka celów w wyrażeniach regularnych. Przede wszystkim, są one używane do przechwytywania wyrażeń podrzędnych, aby określić potwierdzeń lub aby zgrupować wzorców, tak aby elementy mogą być traktowane jako pojedyncza jednostka przez *, +,?, i tak dalej.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Dodaj nawiasów zamykających po prawej stronie.  
  
    > [!NOTE]
    >  Jeśli chcesz odpowiada jednej nawias sekwencji ucieczki kreski ułamkowej odwróconej - \\(— tak, aby nie jest interpretowany jako znak specjalny przez [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="see-also"></a>Zobacz też  
 [Obiekt będący wyrażeniem regularnym](../../javascript/reference/regular-expression-object-javascript.md)   
 [Składnia wyrażeń regularnych (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)