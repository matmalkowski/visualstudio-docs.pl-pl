---
title: "Porady: Page Up lub w dół w pamięci | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, paging up or down in memory
- memory, paging up or down
- Disassembly window, viewing memory space
- Memory window, paging up or down in memory
ms.assetid: 50b30a68-66f6-43f8-a48b-59ce12c95471
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 90e55a7a16731d6e4e501282d7b96293d0bc9acd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-page-up-or-down-in-memory"></a>Porady: stronicowanie w górę lub w dół w pamięci
Podczas wyświetlania zawartości pamięci w **pamięci** okna lub **dezasemblacji** okna, umożliwia pionowy pasek przewijania Przenieś w górę lub w dół w pamięci.  
  
### <a name="to-page-up-or-down-in-memory"></a>Stronę w górę lub w dół w pamięci  
  
1.  Aby stronę w dół (przejście do wyższych adres pamięci), kliknij przycisk pionowy pasek przewijania poniżej pola przewijania.  
  
2.  Stronę w górę (przejście do dolnej adres pamięci), kliknij przycisk pionowy pasek przewijania wyżej przycisku suwaka.  
  
 Można również zauważyć, że pionowy pasek przewijania działa w sposób niestandardowe. Przestrzeń adresowa nowoczesnych komputera jest bardzo duży i będzie łatwo uzyskać utracone dane przycisku przewijania suwaka i przeciągając go do losowo wybranej lokalizacji. Z tego powodu uchwytu jest "springloaded" i zawsze pozostaje w Centrum pasek przewijania. W aplikacjach kodu natywnego może strona w górę lub w dół, ale nie Przewiń o za darmo.  
  
 W zarządzanych aplikacjach dezasemblacji jest ograniczone do jednej funkcji, a podczas przewijania normalnie.  
  
 Można zauważyć, że wyższe adresy są wyświetlane w dolnej części okna. Aby wyświetlić adres wyższej, należy przenieść w dół, nie długości.  
  
#### <a name="to-move-up-or-down-one-instruction"></a>Aby przenieść w górę lub w dół jednej instrukcji  
  
-   Kliknij strzałkę u góry lub u dołu pionowy pasek przewijania.  
  
## <a name="see-also"></a>Zobacz też  
 [Okno pamięci](../debugger/memory-windows.md)   
 [Porady: Korzystanie z okna dezasemblacji](../debugger/how-to-use-the-disassembly-window.md)   
 [Wyświetlanie danych w debugerze](../debugger/viewing-data-in-the-debugger.md)