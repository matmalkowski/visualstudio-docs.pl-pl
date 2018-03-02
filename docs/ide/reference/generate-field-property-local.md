---
title: "Generowanie pola, właściwości lub zmiennej lokalnej w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/26/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 4e5da77f3053aabc2e8e4813c8ef5e7fb3407b5f
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2018
---
# <a name="generate-a-field-property-or-local-variable-in-visual-studio"></a>Generowanie pola, właściwości lub zmiennej lokalnej w programie Visual Studio

Dotyczy to generowanie kodu:

- C#

- Visual Basic

**Co:** umożliwia natychmiast generowania kodu dla poprzednio niezadeklarowany pola, właściwości lub lokalnego.

**Kiedy:** wprowadzenie nowego pola, właściwości lub lokalnego podczas pisania i aby poprawnie zadeklarować, automatycznie.

**Dlaczego:** przed użyciem, jednak ta funkcja zostanie Generowanie deklaracji i wpisz automatycznie można zadeklarować pola, właściwości lub lokalnego.

## <a name="how-to"></a>Porada

1. Umieść kursor w wierszu przypadku czerwona falista. Czerwona falista wskazuje pola, lokalne lub właściwość, która jeszcze nie istnieje.

   - C#:

    ![Wyróżniony kod C#](media/field-highlight-cs.png)

   - Visual Basic:

    ![Wyróżniony Kod VB](media/field-highlight-vb.png)

1. Następnie wykonaj jedną z następujących czynności:

   - **Keyboard**
     - Naciśnij klawisz **Ctrl**+**.** Aby wyzwalacz **szybkie akcje i Refaktoryzacje** menu.
   - **Myszy**
     - Kliknij prawym przyciskiem myszy i wybierz **szybkie akcje i Refaktoryzacje** menu.
     - Umieść kursor nad czerwona falista, a następnie kliknij przycisk ![Żarówka](media/bulb-cs.png) ikonę, która jest wyświetlana.
     - Kliknij przycisk ![Żarówka](media/bulb-cs.png) ikonę, która jest wyświetlana na lewym marginesie, gdy kursor tekstu jest już w wierszu zawierającym czerwona falista.

    ![Generowanie podglądu pola/właściwości/lokalnego](media/field-preview-cs.png)

1. Wybierz jedną z opcji generowania z menu rozwijanego.

   > [!TIP]
   > Użyj **podgląd zmian** łącze umieszczone u dołu okna podglądu [aby zobaczyć wszystkie zmiany](../../ide/preview-changes.md) która zostanie podjęta przed dokonaniem wyboru.

   Pola, właściwości lub lokalnym jest tworzony z typem wywnioskować na podstawie jej użycia.

   - C#:

      ![Generowanie wynik metody C#](media/field-result-cs.png)

   - Visual Basic:

      ![Generowanie wynik metody VB](media/field-result-vb.png)

## <a name="see-also"></a>Zobacz także

- [Generowanie kodu](../code-generation-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)
