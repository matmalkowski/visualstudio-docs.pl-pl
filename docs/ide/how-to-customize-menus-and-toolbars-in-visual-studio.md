---
title: 'Porady: Dostosowywanie menu i pasków zadań w programie Visual Studio | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.renametoolbar
- vs.customize.toolbars
- vs.buttoneditor
- vs.customize.commands
- vs.newtoolbar
helpviewer_keywords:
- captions, customizing toolbar
- custom toolbars [Visual Studio]
- command buttons, customizing toolbar
- labels, customizing toolbar
- images [Visual Studio], toolbar buttons
- buttons [Visual Studio], custom toolbars
- toolbars [Visual Studio], creating in the IDE
- icons [Visual Studio], customizing toolbar
- commands [Visual Studio], customizing environment
- customizing toolbars
- toolbars [Visual Studio], customizing
- toolbars [Visual Studio], customizing in the IDE
ms.assetid: b570ae2f-5302-45dc-9cc9-8d4d1ad50603
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d8c28218f7dd2e695508fabb6410d05530438e94
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-customize-menus-and-toolbars-in-visual-studio"></a>Porady: Dostosowywanie menu i pasków zadań w Visual Studio
Visual Studio można dostosowywać, nie tylko przez dodawanie i usuwanie menu paska menu i pasków narzędzi, ale również przez dodawanie i usuwanie poleceń w dowolnym danym narzędzi lub paska menu.  
  
> [!WARNING]
>  Po dostosowaniu paska narzędzi lub menu, upewnij się, że pole wyboru pozostanie wybrany w **Dostosuj** okno dialogowe. W przeciwnym razie zmiany nie są zachowywane po zamknięciu i ponownym otwarciu Visual Studio.
  
## <a name="adding-removing-or-moving-a-menu-on-the-menu-bar"></a>Dodawanie, usuwanie lub przenoszenie menu na pasku menu  
  
1.  Na pasku menu wybierz **narzędzia**, **Dostosuj**.  
  
     **Dostosuj** zostanie otwarte okno dialogowe.  
  
2.  Na **polecenia** karcie, pozostaw **paska Menu** wybrany przycisk opcji, pozostaw **paska Menu** zaznaczony na liście obok tej opcji, a następnie wykonaj jedną z następujących zestawów kroki:  
  
    -   Aby dodać menu, wybierz **dodać nowego Menu** przycisku, wybierz **Modyfikuj zaznaczenie** przycisk, a następnie nazwą menu, które chcesz dodać.  
  
        ![Dostosuj — okno dialogowe przedstawiająca sposób dodać menu](../ide/media/addmenu.png "DodajMenu")  
  
    -   Aby usunąć menu, wybierz go w **formanty** listy, a następnie wybierz pozycję **usunąć** przycisku.  
  
    -   Aby przenieść menu na pasku menu, wybierz w menu **formanty** listy, a następnie wybierz pozycję **Przenieś w górę** lub **Przenieś w dół** przycisku.  
  
## <a name="adding-removing-or-moving-a-toolbar"></a>Dodawanie, usuwanie lub przenoszenie paska narzędzi  
  
1.  Na pasku menu wybierz **narzędzia**, **Dostosuj**.  
  
     **Dostosuj** zostanie otwarte okno dialogowe.  
  
2.  Na **narzędzi** karcie, wykonaj jedną z następujących zestawów czynności:  
  
    -   Aby dodać paska narzędzi, wybierz **nowy** przycisku, określ nazwę dla narzędzi, które chcesz dodać, a następnie wybierz pozycję **OK** przycisku.  
  
        ![Dostosuj — okno dialogowe przedstawiająca sposób dodawania paska narzędzi](../ide/media/addtoolbar.png "AddToolbar")  
  
    -   Aby usunąć niestandardowego paska narzędzi, wybierz go w **paski narzędzi** listy, a następnie wybierz pozycję **usunąć** przycisku.  
  
        > [!IMPORTANT]
        >  Możesz usunąć paski narzędzi, które utworzyłeś, ale nie domyślne paski narzędzi.  
  
    -   Aby przenieść inną lokalizację dokowania paska narzędzi, wybierz go w **paski narzędzi** wybierz **Modyfikuj zaznaczenie** przycisk, a następnie wybierz lokalizację na liście.  
  
        Możesz również przeciągnąć pasek narzędzi za jego lewą krawędź, aby przenieść go w dowolne miejsce w głównym obszarze dokowania.  
  
        > [!NOTE]
        >  Aby uzyskać więcej informacji o sposobie poprawić użyteczność i dostępności pasków narzędzi, zobacz [porady: Ustawianie opcji ułatwień dostępu IDE](../ide/reference/how-to-set-ide-accessibility-options.md).  
  
## <a name="customizing_menu">Dostosowywanie menu lub pasek narzędzi</a>
  
1.  Na pasku menu wybierz **narzędzia**, **Dostosuj**.  
  
    **Dostosuj** zostanie otwarte okno dialogowe.  
  
2.  Na **polecenia** , wybierz pozycję przycisk opcji dla elementu, który chcesz dostosować.  
  
3.  Na liście dla tego typu elementu wybierz menu lub pasek narzędzi, który chcesz dostosować, a następnie wykonaj jeden z następujących zbiorów czynności:  
  
    -   Aby dodać polecenia, wybierz **polecenia Add** przycisku.  
  
        W **polecenia Add** okno dialogowe, wybierz element w **kategorii** wybierz element **polecenia** listy, a następnie wybierz pozycję **OK**przycisku.  
  
        ![Dodaj polecenie — Okno dialogowe w programie Visual Studio](../ide/media/addcommand.png "AddCommand")  
  
    -   Aby usunąć polecenie, wybierz go w **formanty** listy, a następnie wybierz pozycję **usunąć** przycisku.  
  
    -   Aby zmienić kolejność poleceń, wybierz polecenie w **formanty** listy, a następnie wybierz pozycję **Przenieś w górę** lub **Przenieś w dół** przycisku.  
  
    -   Do grupy poleceń w linii poziomej, wybierz polecenie pierwszy w **formanty** wybierz **Modyfikuj zaznaczenie** przycisk, a następnie wybierz pozycję **Rozpocznij grupę** w wyświetlonym menu.  
  
## <a name="resetting-a-menu-or-a-toolbar"></a>Resetowanie menu lub paska narzędzi  
  
1.  Na pasku menu wybierz **narzędzia**, **Dostosuj**.  
  
    **Dostosuj** zostanie otwarte okno dialogowe.  
  
2.  Na **polecenia** , wybierz pozycję przycisk opcji dla typu elementu, który chcesz zresetować.  
  
3.  Na liście dla tego typu elementu wybierz menu lub pasek narzędzi, który chcesz zresetować.  
  
4.  Wybierz **Modyfikuj zaznaczenie** przycisk, a następnie wybierz pozycję **zresetować** w wyświetlonym menu.  
  
    Możesz zresetować wszystkie menu i pasków narzędzi, wybierając **zresetować wszystkie** przycisku.

## <a name="see-also"></a>Zobacz także
[Personalizowanie środowiska IDE](../ide/personalizing-the-visual-studio-ide.md)  
[Dopasowywanie edytora](../ide/customizing-the-editor.md)