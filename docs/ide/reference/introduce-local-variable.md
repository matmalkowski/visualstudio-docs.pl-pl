---
title: Wprowadź zmienną lokalną w programie Visual Studio
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 05cf2d99f88fcf6d43674d837d62f2e6053470a9
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="introduce-a-local-variable-in-visual-studio"></a>Wprowadź zmienną lokalną w programie Visual Studio

Dotyczy to generowanie kodu:

- C#

- Visual Basic

**Co:** pozwala natychmiast wygenerować zmiennej lokalnej, aby zastąpić istniejącą wyrażenia.

**Kiedy:** kod, który można łatwo wykorzystywać później, jakby był w zmiennej lokalnej.

**Dlaczego:** można skopiuj i Wklej kod wielokrotnie będzie używane w różnych lokalizacjach, jednak byłoby lepiej wykonać tę operację jeszcze raz, zapisz wynik w zmiennej lokalnej i używać lokalnego throughought zmiennej.

## <a name="how-to"></a>Porada

1. Zaznacz wyrażenie, które ma zostać przypisany do zmiennej lokalnej.

   - C#:

    ![Wyróżniony kod C#](media/local-highlight-cs.png)

   - Visual Basic:

    ![Wyróżniony Kod VB](media/local-highlight-vb.png)

1. Następnie wykonaj jedną z następujących czynności:

   - **Keyboard**
     - Naciśnij klawisz **Ctrl**+**.** Aby wyzwalacz **szybkie akcje i Refaktoryzacje** menu.
   - **Myszy**
     - Kliknij prawym przyciskiem myszy i wybierz **szybkie akcje i Refaktoryzacje** menu.
     - Kliknij ikonę ![Żarówka](media/bulb-cs.png) ikonę, która jest wyświetlana na lewym marginesie, gdy kursor tekstu jest już w wierszu zawierającym czerwona falista.

   ![Wprowadzenie Podgląd lokalny](media/local-preview-cs.png)

1. Wybierz **wprowadź element lokalny dla (wszystkie wystąpienia) "*wyrażenie*"** z menu rozwijanego.

   > [!TIP]
   > Użyj **podgląd zmian** łącze umieszczone u dołu okna podglądu [aby zobaczyć wszystkie zmiany](../../ide/preview-changes.md) która zostanie podjęta przed dokonaniem wyboru.

   Zmienna lokalna jest tworzony z typem wywnioskować na podstawie jej użycia. Nadaj nowej zmiennej lokalnej nową nazwę.

   - C#:

      ![Zaimplementuj interfejs wynik C#](media/local-result-cs.png)

   - Visual Basic:

      ![Zaimplementuj interfejs wynik VB](media/local-result-vb.png)

   > [!NOTE]
   > Można użyć **.. wystąpień aplikacji...**  menu opcję, aby zastąpić wszystkie wystąpienia wybranego wyrażenia, nie tylko jedną, specjalnie wyróżnioną pozycją.

## <a name="see-also"></a>Zobacz także

- [Generowanie kodu](../code-generation-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)