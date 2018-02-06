---
title: "Implementuje klasę abstrakcyjną - generowania kodu (Visual Basic) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 96cfed7f-f090-4369-8a85-2dcd4c7cf12b
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 135c1edc6719c567e21496f047af45b7ce311d13
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2018
---
# <a name="implement-an-abstract-class-in-visual-basic"></a>Implementuje klasę abstrakcyjną w języku Visual Basic
**Co:** pozwala natychmiast wygenerować kod wymagany do zaimplementowania klasy abstrakcyjnej. 

**Kiedy:** ma być dziedziczona z klasy abstrakcyjnej.  

**Dlaczego:** ręcznie można zaimplementować wszystkich abstrakcyjne elementy członkowskie jeden po drugim, jednak funkcja ta automatycznie wygeneruje wszystkie podpisy metod. 

**Jak:**

1. Umieść kursor w wierszu przypadku czerwona falista wskazujący ma odziedziczony z klasy abstrakcyjnej, ale nie zostały zaimplementowane wszystkich wymaganych elementów.

   ![Wyróżniony kod](media/abstract-highlight-vb.png)

1. Następnie wykonaj jedną z następujących czynności:
   * **Klawiatury**
     * Naciśnij klawisz **Ctrl +.** Aby wyzwalacz **szybkie akcje i Refaktoryzacje** menu i wybierz **implementacji klasy abstrakcyjnej** z menu podręcznego okna podglądu.
   * **Myszy**
     * Kliknij prawym przyciskiem myszy i wybierz **szybkie akcje i Refaktoryzacje** menu i wybierz **implementacji klasy abstrakcyjnej** z menu podręcznego okna podglądu.
     * Umieść kursor nad czerwona falista, a następnie kliknij przycisk ![Żarówka](media/bulb-vb.png) ikonę, która jest wyświetlana.
     * Kliknij przycisk ![Żarówka](media/bulb-vb.png) ikonę, która jest wyświetlana na lewym marginesie, gdy kursor tekstu jest już w wierszu zawierającym czerwona falista.

   ![Implementacja klasy podglądu](media/abstract-preview-vb.png)

   >[!TIP]
   >Użyj [ **podgląd zmian** ](../../ide/preview-changes.md) łącze umieszczone u dołu okna podglądu, aby zobaczyć wszystkie zmiany wprowadzone przed dokonaniem wyboru.
   >
   >Ponadto można użyć **dokumentu**, **projektu**, i **rozwiązania** łącza w dolnej części okna podglądu do tworzenia podpisów odpowiedniej metody w wielu klasy, które dziedziczą z klasy abstrakcyjnej.

1. Sygnatury metody abstrakcyjnej będzie automatycznie utworzone, gotowy do zaimplementowania.

   ![Implementacja klasy wyników](media/abstract-result-vb.png)

## <a name="see-also"></a>Zobacz także

[Generowanie kodu](../code-generation-in-visual-studio.md)  
[Podgląd zmian](../../ide/preview-changes.md)