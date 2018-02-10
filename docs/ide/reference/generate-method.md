---
title: Generowanie metody w programie Visual Studio | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/26/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 6fbee2d6ea0a6d95d6d71114dc116cfaa1ede74e
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="generate-a-method-in-visual-studio"></a>Generowanie metody w programie Visual Studio

Dotyczy to generowanie kodu:

- C#

- Visual Basic

**Co:** można bezpośrednio dodać metodę do klasy.

**Kiedy:** wprowadzenie nowej metody i aby poprawnie zadeklarować, automatycznie.

**Dlaczego:** można deklarowaniu — metoda i parametry przed użyciem go, jednak funkcja ta automatycznie wygeneruje deklaracji.

## <a name="how-to"></a>Porada

1. Umieść kursor w wierszu przypadku czerwona falista. Czerwona falista wskazuje metodę, która jeszcze nie istnieje.

   - C#:

    ![Wyróżniony kod C#](media/method-highlight-cs.png)

   - Visual Basic:

    ![Wyróżniony Kod VB](media/method-highlight-vb.png)

1. Następnie wykonaj jedną z następujących czynności:

   - **Keyboard**
     - Naciśnij klawisz **Ctrl +.** Aby wyzwalacz **szybkie akcje i Refaktoryzacje** menu.
   - **Myszy**
     - Kliknij prawym przyciskiem myszy i wybierz **szybkie akcje i Refaktoryzacje** menu.
     - Umieść kursor nad czerwona falista, a następnie kliknij przycisk ![Żarówka](media/bulb-cs.png) ikonę, która jest wyświetlana.
     - Kliknij przycisk ![Żarówka](media/bulb-cs.png) ikonę, która jest wyświetlana na lewym marginesie, gdy kursor tekstu jest już w wierszu zawierającym czerwona falista.

    ![Generowanie podglądu — metoda](media/method-preview-cs.png)

1. Wybierz **wygenerować metody** z menu rozwijanego.

   > [!TIP]
   > Użyj **podgląd zmian** łącze umieszczone u dołu okna podglądu [aby zobaczyć wszystkie zmiany](../../ide/preview-changes.md) która zostanie podjęta przed dokonaniem wyboru.

   Metoda jest tworzony z parametrami wywnioskować na podstawie jego użycia.

   - C#:

      ![Generowanie wynik metody C#](media/method-result-cs.png)

   - Visual Basic:

      ![Generowanie wynik metody VB](media/method-result-vb.png)

## <a name="see-also"></a>Zobacz także

[Generowanie kodu](../code-generation-in-visual-studio.md)  
[Podgląd zmian](../../ide/preview-changes.md)
