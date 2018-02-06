---
title: Implementuje interfejs - generowania kodu (Visual Basic) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bebff2ad-25b6-4adc-8762-60d23bdd639a
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 990f87cd0f1abf9d4f62ecd321ef038d689b75f4
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2018
---
# <a name="implement-an-interface-in-visual-basic"></a>Zaimplementuj interfejs w języku Visual Basic
**Co:** umożliwia natychmiast generowania kodu wymaganego do implementacji interfejsu. 

**Kiedy:** ma być dziedziczona z interfejsu.  

**Dlaczego:** ręcznie można zaimplementować interfejsu wszystkich jeden po drugim, jednak funkcja ta automatycznie wygeneruje wszystkie podpisy — metoda. 

**Jak:**

1. Umieść kursor w wierszu przypadku czerwona falista wskazujący ma odwołanie do interfejsu, ale nie zostały zaimplementowane wszystkich wymaganych elementów.

   ![Wyróżniony kod](media/interface-highlight-vb.png)

1. Następnie wykonaj jedną z następujących czynności:
   * **Klawiatury**
     * Naciśnij klawisz **Ctrl +.** Aby wyzwalacz **szybkie akcje i Refaktoryzacje** menu i wybierz **implementować interfejs (jawnie)** z menu podręcznego okna podglądu.
   * **Myszy**
     * Kliknij prawym przyciskiem myszy i wybierz **szybkie akcje i Refaktoryzacje** menu i wybierz **(jawnie) implementować interfejs** z menu podręcznego okna podglądu.
     * Umieść kursor nad czerwona falista, a następnie kliknij przycisk ![Żarówka](media/bulb-vb.png) ikonę, która jest wyświetlana.
     * Kliknij przycisk ![Żarówka](media/bulb-vb.png) ikonę, która jest wyświetlana na lewym marginesie, gdy kursor tekstu jest już w wierszu zawierającym czerwona falista.

   ![Implementacja klasy podglądu](media/interface-preview-vb.png)

   >[!TIP]
   >Użyj [ **podgląd zmian** ](../../ide/preview-changes.md) łącze umieszczone u dołu okna podglądu, aby zobaczyć wszystkie zmiany wprowadzone przed dokonaniem wyboru.
   >
   >Ponadto można użyć **dokumentu**, **projektu**, i **rozwiązania** łącza w dolnej części okna podglądu do tworzenia podpisów odpowiedniej metody w wielu klasy, które implementują interfejs.

1. Podpisy metod interfejsu będzie automatycznie utworzone, gotowy do zaimplementowania.

   ![Implementacja klasy wyników](media/interface-result-vb.png)

## <a name="see-also"></a>Zobacz także

[Generowanie kodu](../code-generation-in-visual-studio.md)  
[Podgląd zmian](../../ide/preview-changes.md)