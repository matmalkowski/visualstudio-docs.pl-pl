---
title: "Za pomocą definicji wglądu w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/10/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 5a7465b8432d00df83638dbfa98a36cf8dee469a
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2018
---
# <a name="how-to-view-and-edit-code-by-using-peek-definition-altf12"></a>Porady: wyświetlanie i edytowanie kodu za pomocą definicji wglądu (Alt + F12)

Można użyć **definicji wglądu** polecenie, aby wyświetlić i edytować kod bez przełączania od pisania kodu. **Podgląd definicji** i **przejdź do definicji** wyświetlane te same informacje, ale **definicji wglądu** zawiera go w oknie podręcznym i **przejdź do definicji** zawiera kod w oknie oddzielne kodu. **Przejdź do definicji** powoduje, że kontekst (oznacza to, że kod active okna, bieżącego wiersza, a pozycja kursora) przejść do definicji okna kodu. Za pomocą **definicji wglądu**, można wyświetlać i edytować definicję i poruszanie się w pliku definicji przy zachowaniu Twoje miejsce w oryginalnym pliku kodu.

Można użyć **definicji wglądu** z kodem C#, Visual Basic i C++. W języku Visual Basic **definicji wglądu** zawiera łącze do **przeglądarki obiektów** symboli, które nie mają definicji metadanych (na przykład, .NET Framework typy, które są wbudowane w).

## <a name="working-with-peek-definition"></a>Praca z funkcją Zobacz definicję

### <a name="to-open-a-peek-definition-window"></a>Aby otworzyć okno Zobacz definicję

1. Możesz uzyskać wgląd definicji, wybierając **definicji wglądu** z menu kontekstowego dla typu lub elementu członkowskiego, który chcesz zapoznać. W Visual Studio 2017 wersji 15,4 i nowszych, jeśli opcja jest włączona, możesz również uzyskać wgląd definicji za pomocą myszy, naciskając **Ctrl** (lub innego modyfikatora) i kliknij nazwę elementu członkowskiego. Lub z klawiatury, naciśnij klawisz **Alt**+**F12**.

     Na ilustracji przedstawiono **definicji wglądu** Windows metody o nazwie `Print()`:

     ![Podgląd okna](../ide/media/peekwindow.png "PeekWindow")

     Okno definicji pojawia się poniżej `printer.Print("Hello World!")` wiersza w oryginalnym pliku. Okno nie ukrywa żadnego kodu w pliku oryginalnym. Wiersze, które należy wykonać `printer.Print("Hello World!")` są wyświetlane w oknie definicji.

1. Kursor jest w różnych lokalizacjach w oknie definicji wglądu. Możesz nadal można poruszanie się w oryginalnej okna kodu.

1. Można skopiować ciąg z okna definicji i wkleić go w kodzie oryginalnym. Możesz również przeciągać i upuszczać ciąg z okna definicji do oryginalnego kodu bez usuwania go z okna definicji.

1. Możesz zamknąć okno definicji, wybierając **Esc** klucza lub **zamknąć** przycisk na karcie okna definicji.

### <a name="open-a-peek-definition-window-from-within-a-peek-definition-window"></a>Otwórz okno Wybieranie definicji z okna definicji wglądu

Jeśli masz już **definicji wglądu** okna otwarte, należy wywołać **definicji wglądu** ponownie na kodzie w danym przedziale. Otwiera się inne okno definicji. Zestaw łączy do stron nadrzędnych obok karty w oknie definicji, służący do nawigacji między oknami definicji. Etykietka narzędzia na każdej kropce ukazuje nazwę pliku i ścieżkę pliku definicji, którą ta kropka reprezentuje.

   ![Okno podglądu okna podglądu](../ide/media/peekwithinpeek.png "PeekWithinPeek")

### <a name="peek-definition-with-multiple-results"></a>Definicji wglądu z wieloma wynikami

Jeśli używasz **definicji wglądu** na kod, który ma więcej niż jednej definicji (na przykład klasy częściowej), zostanie wyświetlona lista wyników, z prawej strony widoku definicji kodu. Możesz wybrać dowolny wynik na liście, aby wyświetlić jego definicję.

   ![W oknie Peek wiele wyników](../ide/media/peekmultiple.png "PeekMultiple")

### <a name="edit-inside-the-peek-definition-window"></a>Edytuj w oknie Wybieranie definicji

Po rozpoczęciu edycji wewnątrz **definicji wglądu** okna, pliku, który modyfikacji automatycznie otwiera się jako osobnej karcie w edytorze kodu i odzwierciedla zmiany, które zostały wprowadzone. Możesz dokonać, Cofnij i Zapisz zmiany w **definicji wglądu** okna i na karcie nadal odzwierciedlenia tych zmian. Nawet jeśli zamkniesz **definicji wglądu** okna bez zapisywania zmian, można wprowadzić, Cofnij i zapisać zmiany na karcie Pobieranie dokładnie którym została pozostawiona w **definicji wglądu** okna.

   ![Edytowanie okna podglądu](../ide/media/peekedit.png "PeekEdit")

### <a name="to-change-options-for-peek-definition"></a>Aby zmienić opcje dla definicji wglądu

1. Przejdź do **narzędzia** > **opcje** > **Edytor tekstu** > **ogólne**.

1. Wybierz opcję **Otwórz definicję w widoku peek**.

1. Kliknij przycisk **OK** zamknąć **opcje** okno dialogowe.

   ![Ustawienie opcji definicji wglądu kliknięcia myszą](../ide/media/editor_options_peek_view.png)  

### <a name="keyboard-shortcuts-for-peek-definition"></a>Skróty klawiaturowe dla definicji wglądu

Można użyć tych skrótów klawiaturowych z **definicji wglądu** okno:

|Funkcja|Skrót klawiaturowy|
|-------------------|:-----------------------:|
|Otwórz okno definicji|Alt+F12|
|Zamknij okno definicji|Esc|
|Promuj okno definicji do karty zwykłego dokumentu|Shift+Alt+Home|
|Przechodzenie między oknami definicji|Ctrl+Alt+- i Ctrl+Alt+=|
|Przechodzenie między wieloma wynikami|F8 i Shift + F8|
|Przełączanie się między oknem edytora kodu i oknem definicji|Shift + Esc|

> [!NOTE]
> Umożliwia także te same skróty klawiaturowe do edycji kodu w **definicji wglądu** okno używany w innym miejscu w programie Visual Studio.

## <a name="see-also"></a>Zobacz także

[Nawigowanie po kodzie](../ide/navigating-code.md)  
[Polecenia Przejdź do definicji i Zobacz definicję](../ide/go-to-and-peek-definition.md)  
[Wskazówki dotyczące produktywności](../ide/productivity-tips-for-visual-studio.md)