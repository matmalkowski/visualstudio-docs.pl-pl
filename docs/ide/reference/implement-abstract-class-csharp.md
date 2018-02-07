---
title: "Implementuje klasę abstrakcyjną - generowania kodu (C#) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 96cfed7f-f090-4369-8a85-2dcd4c7cf12b
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: f089ffbe33d4a36e84d6d39abb3b3db3c4b2aeb7
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/06/2018
---
# <a name="implement-an-abstract-class-in-c"></a>Implementuje klasę abstrakcyjną w języku C# #
**Co:** pozwala natychmiast wygenerować kod wymagany do zaimplementowania klasy abstrakcyjnej. 

**Kiedy:** ma być dziedziczona z klasy abstrakcyjnej.  

**Dlaczego:** ręcznie można zaimplementować wszystkich abstrakcyjne elementy członkowskie jeden po drugim, jednak funkcja ta automatycznie wygeneruje wszystkie podpisy metod. 

**Jak:**

1. Umieść kursor w wierszu przypadku czerwona falista wskazujący ma odziedziczony z klasy abstrakcyjnej, ale nie zostały zaimplementowane wszystkich wymaganych elementów.

   ![Wyróżniony kod](media/abstract-highlight-cs.png)

1. Następnie wykonaj jedną z następujących czynności:
   * **Keyboard**
     * Naciśnij klawisz **Ctrl +.** Aby wyzwalacz **szybkie akcje i Refaktoryzacje** menu i wybierz **implementacji klasy abstrakcyjnej** z menu podręcznego okna podglądu.
   * **Myszy**
     * Kliknij prawym przyciskiem myszy i wybierz **szybkie akcje i Refaktoryzacje** menu i wybierz **implementacji klasy abstrakcyjnej** z menu podręcznego okna podglądu.
     * Umieść kursor nad czerwona falista, a następnie kliknij przycisk ![Żarówka](media/bulb-cs.png) ikonę, która jest wyświetlana.
     * Kliknij przycisk ![Żarówka](media/bulb-cs.png) ikonę, która jest wyświetlana na lewym marginesie, gdy kursor tekstu jest już w wierszu zawierającym czerwona falista.

   ![Implementacja klasy podglądu](media/abstract-preview-cs.png)

   >[!TIP]
   >Użyj [ **podgląd zmian** ](../../ide/preview-changes.md) łącze umieszczone u dołu okna podglądu, aby zobaczyć wszystkie zmiany wprowadzone przed dokonaniem wyboru.
   >
   >Ponadto można użyć **dokumentu**, **projektu**, i **rozwiązania** łącza w dolnej części okna podglądu do tworzenia podpisów odpowiedniej metody w wielu klasy, które dziedziczą z klasy abstrakcyjnej.

1. Sygnatury metody abstrakcyjnej będzie automatycznie utworzone, gotowy do zaimplementowania.

   ![Implementacja klasy wyników](media/abstract-result-cs.png)

## <a name="see-also"></a>Zobacz także

[Generowanie kodu](../code-generation-in-visual-studio.md)  
[Podgląd zmian](../../ide/preview-changes.md)
