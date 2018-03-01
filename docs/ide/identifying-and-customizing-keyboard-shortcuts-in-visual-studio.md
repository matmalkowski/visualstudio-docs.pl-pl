---
title: "Identyfikowanie i dostosowywanie skrótów klawiaturowych w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Environment.Keyboard
helpviewer_keywords:
- keyboard shortcuts [Visual Studio], customizing
- importing shortcut keys [Visual Studio]
- shortcut key combinations [Visual Studio]
- commands [Visual Studio], shortcut keys
- custom shortcut keys [Visual Studio]
- customizing keyboard shortcuts [Visual Studio]
- exporting shortcut keys [Visual Studio]
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 7258a1ba99764fa7af7ce73874f447db99b8b168
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="identifying-and-customizing-keyboard-shortcuts-in-visual-studio"></a>Identyfikowanie i dostosowywanie skrótów klawiaturowych w programie Visual Studio

Można zidentyfikować skróty klawiaturowe dla poleceń programu Visual Studio, dostosować te skróty i eksportować je dla innych użytkowników. Wiele skrótów zawsze wywołuje te same polecenia, ale zachowanie skrótu może zależeć od następujących warunków:

- Które domyślne ustawienia środowiska wybrano podczas pierwszego uruchomienia programu Visual Studio (na przykład ogólne ustawienia projektowania lub Visual C#).

- Czy dostosowywałeś zachowanie danego skrótu.

- W którym kontekście jesteś w momencie wybierania skrótu. Na przykład skrót F2 wywołuje polecenie Edit.EditCell, jeśli używasz Projektanta ustawień, i polecenie File.Rename, jeśli używasz Eksploratora zespołów.

Niezależnie od tego ustawienia, dostosowywanie i kontekstu można zawsze znaleźć i zmienić skrótów klawiaturowych w **opcje** okno dialogowe. Można także wyszukać domyślne skróty klawiaturowe dla kilku poleceń dozen w [domyślne skróty klawiaturowe dla często używane polecenia](../ide/default-keyboard-shortcuts-for-frequently-used-commands-in-visual-studio.md), i znajduje się pełna lista wszystkich skrótów domyślnych (na podstawie programowanie ogólne Ustawienia) w [domyślne skróty klawiaturowe](../ide/default-keyboard-shortcuts-in-visual-studio.md).

Jeśli skrót jest przypisany do polecenia wyłącznie w kontekście globalnym, ten skrót zawsze będzie wywoływał dane polecenie. Jednak skrót może być przypisany do jednego polecenia w kontekście globalnym i innego polecenia w określonym kontekście. Gdy korzystasz z takiego skrótu podczas pracy w określonym kontekście, skrót wywołuje polecenie odpowiadające temu kontekstowi, a nie kontekstowi globalnemu.

> [!NOTE]
> Twoje ustawienia i wersja programu Visual Studio mogą zmienić nazwy i lokalizacje poleceń menu oraz opcje, które pojawiają się w oknach dialogowych. W tym temacie jest oparta na **ogólne ustawienia środowiska deweloperskiego**.

## <a name="identifying-a-keyboard-shortcut"></a>Identyfikowanie skrótu klawiaturowego

1. Na pasku menu wybierz **narzędzia**, **opcje**.

2. Rozwiń węzeł **środowiska**, a następnie wybierz pozycję **klawiatury**.

   ![Wyświetlić skróty klawiaturowe w oknie dialogowym Opcje](../ide/media/optionskeyboard.png "OptionsKeyboard")

3. W **Pokaż polecenia zawierające** wpisz całość lub część nazwy polecenia, bez spacji.

   Na przykład można znaleźć polecenia `solutionexplorer`.

4. Na liście, wybierz odpowiednie polecenie.

    Na przykład można wybrać **View.SolutionExplorer**.

5. Jeśli polecenie ma skrót klawiaturowy, zostanie wyświetlony w **skrót(y) dla wybranego polecenia** listy.

   ![Wyświetl skrótu dla określonego polecenia](../ide/media/viewshortcut.png "ViewShortcut")

## <a name="customizing-a-keyboard-shortcut"></a>Dostosowywanie skrótu klawiaturowego

1. Na pasku menu wybierz **narzędzia**, **opcje**.

2. Rozwiń węzeł **środowiska** folder, a następnie wybierz pozycję **klawiatury**.

3. Opcjonalnie: Przefiltrować listę poleceń, wprowadzając całość lub część nazwy polecenia, bez spacji, w **Pokaż polecenia zawierające** pole.

4. Z listy wybierz polecenie, do którego chcesz przypisać skrót klawiaturowy.

W **Użyj nowego skrótu w** wybierz obszaru funkcji, w której chcesz użyć skrótu.

    For example, you can choose **Global** if you want the shortcut to work in all contexts. You can use any shortcut that isn't mapped (as Global) in another editor. Otherwise, the editor overrides the shortcut.

    > [!NOTE]
    > You can't assign the following keys as part of a keyboard shortcut in **Global**: Print Scrn/Sys Rq, Scroll Lock, Pause/Break, Tab, Caps Lock, Insert, Home, End, Page Up, Page Down, the Windows logo key, the Application key, any of the Arrow keys, or Enter; Num Lock, Delete, or Clear on the numeric keypad; the Ctrl+Alt+Delete key combination.

6. W **naciśnij klawisze skrótów** wprowadź skrót, który ma być używany.

    > [!NOTE]
    > Można utworzyć skrót, który łączy literę z klawiszem Alt, Ctrl lub oboma. Można też utworzyć skrót, który łączy klawisz Shift i literę z klawiszem Alt, Ctrl lub oboma.

     Jeśli skrót jest już przypisany do innego polecenia, zostanie wyświetlony w **skrót aktualnie używany przez** pole. W takim przypadku należy wybrać klawisz Backspace, aby usunąć skrót, przed wpisaniem innego.

    ![Określ inny skrót dla polecenia](../ide/media/reassignshortcut.png "ReassignShortcut")

7. Wybierz **przypisać** przycisku.

    > [!NOTE]
    > Jeśli określisz innej skrótów dla polecenia, wybierz **przypisać** przycisk, a następnie wybierz pozycję **anulować** przycisku, okno dialogowe zostanie zamknięte, ale zmiany nie jest przywrócony.

## <a name="sharing-custom-keyboard-shortcuts"></a>Udostępnianie niestandardowych skrótów klawiaturowych

Możesz udostępniać własne skróty, eksportując je do pliku, a następnie przekazując plik innym osobom, aby mogły importować dane.

### <a name="to-export-only-keyboard-shortcuts"></a>Aby wyeksportować tylko skróty klawiaturowe

1. Na pasku menu wybierz **narzędzia**, **Import i eksport ustawień**.

2. Wybierz **Eksportuj wybrane ustawienia środowiska**, a następnie wybierz pozycję **dalej** przycisku.

3. W obszarze **które ustawienia chcesz eksportować?**, wyczyść **wszystkie ustawienia** pole wyboru, rozwiń węzeł **opcje**, a następnie rozwiń węzeł **środowiska**.

4. Wybierz **klawiatury** pole wyboru, a następnie wybierz pozycję **dalej** przycisku.

    ![Eksport dostosowane tylko skróty klawiaturowe](../ide/media/exportshortcuts.png "ExportShortcuts")

5. W **co chcesz nazwać plik swoich ustawień?** i **Przechowuj plik moich ustawień w tym katalogu** pola, albo pozostaw wartości domyślne lub określić różne wartości, a następnie wybierz  **Zakończ** przycisku.

    Domyślnie skróty są zapisywane w pliku w folderze 2017\Settings w Studio %USERPROFILE%\Documents\Visual. Nazwa pliku odzwierciedla datę, kiedy zostały wyeksportowane ustawienia, a rozszerzenie to .vssettings.

### <a name="to-import-only-keyboard-shortcuts"></a>Aby zaimportować tylko skróty klawiaturowe

1. Na pasku menu wybierz **narzędzia**, **Import i eksport ustawień**.

2. Wybierz **Importuj wybrane ustawienia środowiska** przycisk opcji, a następnie wybierz pozycję **dalej** przycisku.

3. Wybierz **nie, tylko zaimportuj nowe ustawienia, zastępując Moje bieżące ustawienia** przycisk opcji, a następnie wybierz pozycję **dalej** przycisku.

4. W obszarze **Moje ustawienia**, wybierz plik zawierający skrótów, które chcesz zaimportować, lub wybierz **Przeglądaj** przycisk, aby zlokalizować poprawny plik.

5. Wybierz **dalej** przycisku.

6.  W obszarze **ustawienia, które chcesz zaimportować?**, wyczyść **wszystkie ustawienia** pole wyboru, rozwiń węzeł **opcje**, a następnie rozwiń węzeł **środowiska**.

7. Wybierz **klawiatury** pole wyboru, a następnie wybierz pozycję **Zakończ** przycisku.

    ![Importuj tylko dostosować skróty klawiaturowe](../ide/media/importshortcuts.png "ImportShortcuts")

## <a name="see-also"></a>Zobacz także

[Ułatwienia dostępu w Visual Studio](../ide/reference/accessibility-features-of-visual-studio.md)