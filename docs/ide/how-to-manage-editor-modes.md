---
title: Visual Studio pełny ekran i tryb obszaru wirtualnego
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- word wrap
- views, virtual space
- line numbers, displaying
- virtual space mode
- line numbers
- Code Editor, view and display options
- full screen mode
- Code Editor, modes
- views, splitting
- views, word wrapping
- fonts and size
- views, creating new windows
- views, line numbers
- views, changing mode
- views, outlining
ms.assetid: 1fb48027-d870-439f-8b72-4a0321390748
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 94bc99bf70340ef76639d0ae0f05e1f7737173a2
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-manage-editor-modes"></a>Porady: Zarządzanie trybami edytora

Edytor kodu programu Visual Studio można wyświetlić w różnych trybów wyświetlania.

> [!NOTE]
> Okna dialogowe i dostępne polecenia menu mogą różnić się od opisanych w tym artykule, w zależności od wersji lub aktywne ustawienia. Aby zmienić ustawienia, na przykład aby **ogólne** lub **Visual C++** ustawienia, wybierz **narzędzia** > **Import i eksport ustawień**, a następnie wybierz pozycję **zresetować wszystkie ustawienia**.

## <a name="enable-full-screen-mode"></a>Włącz tryb pełnoekranowy

Istnieje możliwość Ukryj wszystkie okna narzędzi i wyświetlić tylko okna dokumentów, włączając **pełnoekranowy** tryb.

-   Naciśnij klawisz **Alt**+**Shift**+**Enter** do wprowadzania lub zamknąć **pełnoekranowy** tryb.

     --lub--

-   Należy wydać polecenie `View.Fullscreen` w **polecenia** okna.

## <a name="enable-virtual-space-mode"></a>Włącz tryb obszaru wirtualnego

W **wirtualną przestrzeń** trybie spacje są dodawane na końcu każdego wiersza kodu. Wybierz tę opcję, aby umieść komentarzy w punkcie spójne obok kodu.

1.  Wybierz **opcje** z **narzędzia** menu.

2.  Rozwiń węzeł **Edytor tekstu** folderu i wybierz polecenie **wszystkie języki** globalnie Ustaw tę opcję, lub wybierz folder określonego języka. Na przykład, aby włączyć numery wierszy tylko w języku Visual Basic, wybierz **podstawowe** > **Edytor tekstu** węzła.

3.  Wybierz **ogólne** opcje, a następnie w obszarze **ustawienia**, wybierz pozycję **Włącz wirtualną przestrzeń**.

    > [!NOTE]
    > **Wirtualna spacja** jest włączone w **kolumn wybór** tryb. Gdy **wirtualną przestrzeń** nie jest włączony tryb są przenoszone punkt wstawiania na końcu jeden wiersz bezpośrednio do pierwszego znaku następnego.

## <a name="see-also"></a>Zobacz także

- [Dostosowywanie edytora](../ide/customizing-the-editor.md)
- [Dostosowywanie układów okien w programie Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md)
- [Czcionki i kolory, środowisko, opcje — Okno dialogowe](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)