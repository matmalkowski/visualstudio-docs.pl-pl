---
title: Implementuje klasę abstrakcyjną w programie Visual Studio
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: e89fb94b8c68bd4ac1219b675b8e77df206bf806
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31945444"
---
# <a name="implement-an-abstract-class-in-visual-studio"></a>Implementuje klasę abstrakcyjną w programie Visual Studio

Dotyczy to generowanie kodu:

- C#

- Visual Basic

**Co:** pozwala natychmiast wygenerować kod wymagany do zaimplementowania klasy abstrakcyjnej.

**Kiedy:** ma być dziedziczona z klasy abstrakcyjnej.

**Dlaczego:** ręcznie można zaimplementować wszystkich abstrakcyjne elementy członkowskie jeden po drugim, jednak funkcja ta automatycznie wygeneruje wszystkie podpisy metod.

## <a name="how-to"></a>Porada

1. Umieść kursor w wierszu przypadku red wężyk, który wskazuje ma odziedziczony z klasy abstrakcyjnej, ale nie zostały zaimplementowane wszystkich wymaganych elementów członkowskich.

   - C#:

    ![Wyróżniony kod C#](media/abstract-highlight-cs.png)

   - Visual Basic:

    ![Wyróżniony Kod VB](media/abstract-highlight-vb.png)

1. Następnie wykonaj jedną z następujących czynności:

   - **Keyboard**
     - Naciśnij klawisz **Ctrl**+**.** Aby wyzwalacz **szybkie akcje i Refaktoryzacje** menu.
   - **Myszy**
     - Kliknij prawym przyciskiem myszy i wybierz **szybkie akcje i Refaktoryzacje** menu.
     - Umieść kursor nad czerwona falista, a następnie kliknij przycisk ![Żarówka](media/bulb-cs.png) ikonę, która jest wyświetlana.
     - Kliknij ikonę ![Żarówka](media/bulb-cs.png) ikonę, która jest wyświetlana na lewym marginesie, gdy kursor tekstu jest już w wierszu zawierającym czerwona falista.

   ![Implementacja klasy podglądu](media/abstract-preview-cs.png)

1. Wybierz **implementacji klasy abstrakcyjnej** z menu rozwijanego.

   > [!TIP]
   > - Użyj **podgląd zmian** łącze umieszczone u dołu okna podglądu [aby zobaczyć wszystkie zmiany](../../ide/preview-changes.md) która zostanie podjęta przed dokonaniem wyboru.
   > - Użyj **dokumentu**, **projektu**, i **rozwiązania** łącza w dolnej części okna podglądu do tworzenia podpisów odpowiedniej metody w wielu klas, które dziedziczą z Klasa abstrakcyjna.

   Metoda abstrakcyjna podpisy są tworzone i są gotowe do implementacji.

   - C#:

      ![Implementacja klasy wynik C#](media/abstract-result-cs.png)

   - Visual Basic:

      ![Implementacja klasy wynik VB](media/abstract-result-vb.png)

## <a name="see-also"></a>Zobacz także

- [Generowanie kodu](../code-generation-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)