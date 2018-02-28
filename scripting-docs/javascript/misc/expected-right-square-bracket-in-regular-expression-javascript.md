---
title: "Oczekiwano &#39;] &#39; w wyrażeniu regularnym (JavaScript) | Dokumentacja firmy Microsoft"
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
- VS.WebClient.Help.SCRIPT5019
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1ca2079a-44dd-479f-a1e3-e04a14d0739e
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4c59dcbeea91a1bc01e870d0a49fd22cace6562d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="expected-3939-in-regular-expression-javascript"></a>Oczekiwano &#39;] &#39; w wyrażeniu regularnym (JavaScript)
Podjęto próbę utworzenia klasy znaku dla wyrażenia regularnego dopasowanie, ale nie zawiera prawego nawiasu. Kombinacje poszczególnych znak mogą być włączane do klas znaków, umieszczając je w nawiasach kwadratowych. Klasy znaku dopasowuje dowolny pojedynczy znak, który zawiera. Na przykład / [abc] / pasuje do dowolnego litery "a", "b", lub "c".  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Dodaj prawego nawiasu do wyrażenia regularnego.  
  
    > [!NOTE]
    >  Jeśli chcesz odpowiada jednej nawiasu sekwencji ucieczki kreski ułamkowej odwróconej - \\[— tak nie jest interpretowany jako znak specjalny przez [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="see-also"></a>Zobacz też  
 [Obiekt będący wyrażeniem regularnym](../../javascript/reference/regular-expression-object-javascript.md)   
 [Składnia wyrażeń regularnych (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)