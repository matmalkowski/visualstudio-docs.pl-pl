---
title: "Pełny ekran programu Visual studio i tryb obszaru wirtualnego | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0f6535c656c512d5c849a8a5d8d2fb37319aa883
ms.sourcegitcommit: ec1c7e7e3349d2f3a4dc027e7cfca840c029367d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2017
---
# <a name="how-to-manage-editor-modes"></a>Porady: Zarządzanie trybami edytora
Edytor kodu programu Visual Studio można wyświetlić w różnych trybów wyświetlania.  
  
> [!NOTE]
> Okna dialogowe i dostępne polecenia menu mogą różnić się od opisanych w tym artykule, w zależności od wersji lub aktywne ustawienia. Aby zmienić ustawienia, na przykład aby **ogólne** lub **Visual C++** ustawienia, wybierz **narzędzia**, **Import i eksport ustawień**, a następnie Wybierz **zresetować wszystkie ustawienia**.
  
## <a name="enabling-full-screen-mode"></a>Włączanie trybu pełnego ekranu  
Istnieje możliwość Ukryj wszystkie okna narzędzi i wyświetlić tylko okna dokumentów, włączając **pełnoekranowy** tryb.  
  
#### <a name="to-enable-full-screen-mode"></a>Aby włączyć tryb pełnoekranowy  
  
-   Naciśnij klawisz **Alt**+**Shift**+**Enter** do wprowadzania lub zamknąć **pełnoekranowy** tryb.  
  
     --lub--  
  
-   Należy wydać polecenie `View.Fullscreen` w **polecenia** okna.  
  
## <a name="enabling-virtual-space-mode"></a>Włączanie tryb obszaru wirtualnego  
W **wirtualną przestrzeń** trybie spacje są dodawane na końcu każdego wiersza kodu. Wybierz tę opcję, aby umieść komentarzy w punkcie spójne obok kodu.  
  
#### <a name="to-enable-virtual-space-mode"></a>Aby włączyć tryb obszaru wirtualnego  
  
1.  Wybierz **opcje** z **narzędzia** menu.

2.  Rozwiń węzeł **Edytor tekstu** folderu i wybierz polecenie **wszystkie języki** globalnie Ustaw tę opcję, lub wybierz folder określonego języka. Na przykład aby włączyć numery wierszy tylko w języku Visual Basic, należy wybrać podstawowe, węźle edytor tekstowy.
  
3.  Wybierz **ogólne** opcje, a następnie w obszarze **ustawienia**, wybierz pozycję **Włącz wirtualną przestrzeń**.  
  
    > [!NOTE]
    >  **Wirtualna spacja** jest włączone w **kolumn wybór** tryb. Gdy **wirtualną przestrzeń** nie jest włączony tryb są przenoszone punkt wstawiania na końcu jeden wiersz bezpośrednio do pierwszego znaku następnego.  
  
## <a name="see-also"></a>Zobacz także
[Dopasowywanie edytora](../ide/customizing-the-editor.md)   
[Dostosowywanie układów okien w programie Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md)   
[Czcionki i kolory, środowisko, opcje — Okno dialogowe](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)