---
title: Wskazówki dotyczące produktywności dla programu Visual Studio
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2aaa32de4742d5c3897ec2290e77223b0d6cdd56
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34752666"
---
# <a name="productivity-tips-for-visual-studio"></a>Wskazówki dotyczące produktywności dla programu Visual Studio

Ten temat zawiera różne porad ułatwiających zapisu, przejdź i debugowanie kodu szybkie i skuteczne.

Uzyskać informacji o typowych skróty klawiaturowe, zobacz [klawiatury porady](../ide/tips-and-tricks-for-visual-studio.md). Lub, aby uzyskać pełną listę skrótów klawiaturowych, zobacz [identyfikowanie i dostosowywanie skrótów klawiaturowych](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md) i [domyślne skróty klawiaturowe](../ide/default-keyboard-shortcuts-in-visual-studio.md).

## <a name="write-code"></a>Pisanie kodu

Szybsze pisanie kodu przy użyciu następujących funkcji.

- **Użyj poleceń wygody**. Visual Studio zawiera różne polecenia ułatwiające wykonywanie typowych zadań edycji szybciej. Na przykład w **programu Visual Studio 2017 wersji 15,6** i później, możesz wybrać polecenie łatwo zduplikowany wiersz kodu bez konieczności skopiuj go, zmienić położenie kursora, a następnie wklej go. Wybierz **Edytuj** > **zduplikowane** lub naciśnij klawisz **Ctrl**+**E**,**V**. Użytkownik może szybko rozwiń lub Zwiń zaznaczonego tekstu, wybierając **Edytuj** > **zaawansowane** > **rozwiń wybór** lub **Edytować** > **zaawansowane** > **wybór umowy**, lub naciskając klawisz **Shift** + **Alt** + **=** lub **Shift**+**Alt** + **-** (dostępne w **programu Visual Studio 2017 wersji 15,5 cala** i nowsze).

- **Używanie IntelliSense**. Po wprowadzeniu kodu w edytorze, zostanie wyświetlone informacje funkcji IntelliSense, takie jak listy elementów członkowskich, informacje o parametrach szybka podpowiedź, pomoc podpisu i całe słowo. Obsługuje te funkcje dopasowywania rozmytego tekstu; na przykład listy wyników dla członków listy zawiera nie tylko wpisy rozpoczynających się od znaków czy zostały wprowadzone, ale także wpisów, zawierające kombinację znaków w dowolnym miejscu ich nazw. Aby uzyskać więcej informacji, zobacz [Użyj IntelliSense](../ide/using-intellisense.md).

- **Zmień automatyczne wstawianie Opcje IntelliSense podczas wpisywania kodu**. Przełączanie IntelliSense do tryb sugestii, można określić, że opcje IntelliSense są wstawiane tylko wtedy, gdy jawnie je.

     Aby włączyć tryb sugestii, wybierz **Ctrl**+**Alt**+**spacja** kluczy lub na pasku menu wybierz **Edytuj**  >  **IntelliSense** > **Przełącz tryb uzupełniania**.

- **Wstawki kodu za pomocą**. Wbudowane wstawki za pomocą lub utworzyć własne fragmentów.

     Aby wstawić fragment kodu, na pasku menu wybierz polecenie **Edytuj** > **IntelliSense** > **wstawić fragment** lub **zfunkcjiOtoczprzez**, lub Otwórz menu skrótów w pliku i wybierz polecenie **fragment** > **wstawić fragment** lub **z funkcji Otocz przez**. Aby uzyskać więcej informacji, zobacz [wstawki kodu](../ide/code-snippets.md).

- **Usuń kodu wbudowanego błędy**. Szybkie akcje pozwalają łatwo zrefaktoryzuj, generowanie lub modyfikację kodu za pomocą jednej akcji. Można zastosować te akcje za pomocą śrubokręt ![ikona śrubokręt](media/screwdriver-icon.png) lub żarówki ![ikoną żarówki](media/light-bulb-icon.png) ikony lub naciskając klawisz **Alt** +  **Wprowadź** lub **Ctrl**+**.** gdy kursor znajduje się na odpowiedni wiersz kodu. Zobacz [szybkie akcje](quick-actions.md) Aby uzyskać więcej informacji.

- **Wyświetlanie i edytowanie definicji elementu kodu**. Można szybko wyświetlić i edytować modułu, w którym jest zdefiniowany element kodu, takie jak element członkowski, zmiennej lub lokalnego.

    Aby otworzyć okno podręczne definicji, zaznacz element, a następnie wybierz pozycję **Alt**+**F12** kluczy, lub Otwórz menu skrótów dla elementu, a następnie wybierz pozycję **wgląd Definicja**. Aby otworzyć definicję w oknie oddzielny kod, otwórz menu skrótów dla elementu, a następnie wybierz **przejdź do definicji**.

- **Użyj przykładowych aplikacji**. Można przyspieszyć programowanie aplikacji przez pobranie i zainstalowanie przykładowe aplikacje z [Microsoft Developer Network](https://code.msdn.microsoft.com/). Można też uzyskać określonej technologii lub koncepcji programowania, pobierając i eksploracja przykładowy pakiet dla tego obszaru.

## <a name="navigate-within-your-code"></a>Przejdź w kodzie

 Znajdź i przejdź do określonych lokalizacji w kodzie szybciej, można użyć różnych technik.

- **Zakładki wierszy kodu**. Zakładki można użyć, aby szybko przejść do określonych wierszy kodu w pliku.

    Aby ustawić zakładki, na pasku menu, wybierz **Edytuj** > **zakładki** > **przełączająca**. Można wyświetlić wszystkie zakładki w rozwiązaniu w **zakładki** okna. Aby uzyskać więcej informacji, zobacz [Ustawianie zakładek w kodzie](../ide/setting-bookmarks-in-code.md).

- **Wyszukaj definicje symbolu w pliku**. Umożliwia wyszukiwanie w ramach rozwiązania, aby zlokalizować definicji symbolu i nazwy pliku, ale wyniki wyszukiwania nie uwzględniają przestrzeni nazw lub zmiennych lokalnych.

   Aby uzyskać dostęp do tej funkcji, na pasku menu wybierz **Edytuj** > **przejdź do**.

- **Przeglądaj ogólną strukturę kodu**. W **Eksploratora rozwiązań**, można wyszukiwać i przeglądać klasy i ich typy i składniki w projektach. Można również wyszukiwania symboli, Wyświetl hierarchię wywołań metody, Znajdź odwołania do symboli i wykonywać inne zadania. Jeśli wybierzesz element kodu w **Eksploratora rozwiązań**, skojarzony plik zostanie otwarty w **Podgląd** kartę i przesuwa kursor do elementu w pliku. Aby uzyskać więcej informacji, zobacz [wyświetlanie struktury kodu](../ide/viewing-the-structure-of-code.md).

## <a name="find-items-faster"></a>Znajdź elementy szybciej

Można wyszukiwać w IDE dla poleceń, plików i opcji, oprócz filtrowanie zawartości okna narzędzi, aby wyświetlić tylko informacje istotne dla bieżącego zadania.

- **Filtrowanie zawartości okna narzędzi**. Można wyszukiwać w treści wiele okien narzędzi, takich jak **przybornika**, **właściwości** okno i **Eksploratora rozwiązań**, ale wyświetlania tylko elementy, których nazwy zawiera znaki, które określisz.

- **Wyświetlanie błędów ma adres**. Jeśli wybierzesz **filtru** znajdującego się na **listy błędów** narzędzi można zmniejszyć liczbę błędów, które są widoczne w **listy błędów** okna. Możesz wyświetlić tylko błędów w plikach, które są otwarte w edytorze, tylko błędy w bieżącym pliku lub tylko błędy w bieżącym projekcie. Można także przeszukać w **listy błędów** okno, aby znaleźć określone błędy.

- **Znajdź w oknach dialogowych, menu poleceń i opcji**. W [Szybkie uruchamianie](../ide/reference/quick-launch-environment-options-dialog-box.md) wprowadź słowa kluczowe lub wyrażenia dla elementów, które próbujesz odnaleźć. Na przykład następujące opcje są wyświetlane po wprowadzeniu `new project`:

    ![Szybkie uruchamianie wyniki dla "nowego projektu"](../ide/media/productivity_quicklaunch.png)

    **Szybkie uruchamianie** zawiera łącza do **nowy projekt** okno dialogowe **Dodaj nowy element** okno dialogowe i **projekty i rozwiązania** strony w **Opcje** okno dialogowe, między innymi. Szybkie uruchamianie wyników można także pliki projektu i okien narzędzi.

## <a name="debug-code"></a>Debugowanie kodu

Debugowanie mogą zajmować dużo czasu, ale poniższe porady mogą pomóc przyspieszyć proces.

- **Testowanie strony, aplikacji lub witryny w różnych przeglądarkach**. Jak można debugować kodu, można łatwo przełączać między przeglądarek sieci web zainstalowany, w tym [narzędzie Page Inspector (Visual Studio)](http://msdn.microsoft.com/Library/65880969-1ad2-47be-85b9-bb12c81bf209), bez konieczności otwierania **przeglądanie za pomocą** okno dialogowe. Można użyć **docelowego debugowania** listę, która znajduje się na **standardowe** narzędzi dalej, aby **Rozpocznij debugowanie** przycisk, aby szybko sprawdzić, które przeglądarki jako debugowania lub Wyświetl strony.

    ![Wybierz opcje debugowania w przeglądarce sieci Web](../ide/media/webbrowserdropdowntoolbar.png)

- **Ustaw punkty przerwania tymczasowego**. Można utworzyć tymczasowego punktu przerwania w bieżącym wierszu kodu i jednocześnie uruchomienia debugera. Gdy naciśniesz wiersza kodu debugera przejdzie do trybu przerwania. Aby uzyskać więcej informacji, zobacz [Nawigacja w kodzie za pomocą debugera](../debugger/navigating-through-code-with-the-debugger.md).

    Aby użyć tej funkcji, należy wybrać **Ctrl**+**F10** kluczy lub Otwórz menu skrótów wiersza kodu, na którym chcesz przerwać, a następnie wybierz **Uruchom do kursora** .

- **Przenieś punkt wykonywania podczas debugowania**. Można przenieść do bieżącego punkt wykonywania do innej sekcji kodu i ponownie uruchom debugowanie z tego punktu. Ta metoda jest przydatna, jeśli chcesz debugować części kodu bez konieczności ponownego tworzenia wszystkich kroków, które są wymagane do uzyskania tej sekcji. Aby uzyskać więcej informacji, zobacz [Nawigacja w kodzie za pomocą debugera](../debugger/navigating-through-code-with-the-debugger.md).

     Aby przenieść punkt wykonywania, przeciągnij żółty grot do lokalizacji, w której chcesz ustawić następnej instrukcji z tego samego pliku źródłowego, a następnie wybierz **F5** klawisz, aby kontynuować debugowanie.

- **Przechwytywanie informacji o wartości zmiennych**. Możesz dodać etykietki danych do zmiennej w kodzie i przypiąć go, dzięki czemu można uzyskać dostępu do ostatniej znanej wartości zmiennej, po zakończeniu debugowania. Aby uzyskać więcej informacji, zobacz [wyświetlić wartości danych w poradach dotyczących](../debugger/view-data-values-in-data-tips-in-the-code-editor.md).

     Aby dodać etykietki danych, debuger musi być w trybie przerwania. Umieść kursor w zmiennej, a następnie wybierz przycisk numeru pin na etykietek danych, która jest wyświetlana. Po zatrzymaniu debugowania w pliku źródłowym obok wiersza kodu, która zawiera zmienną pojawi się ikona niebieski numeru pin. Jeśli wskażesz niebieski numeru pin, pojawi się wartość zmiennej z ostatniej sesji debugowania.

- **Wyczyść okna bezpośredniego**. Można wymazać zawartość [oknie bezpośrednim](../ide/reference/immediate-window.md) w czasie projektowania, wprowadzając `>cls` lub `>Edit.ClearAll`

     Aby uzyskać więcej informacji o dodatkowe polecenia, zobacz [programu Visual Studio — aliasy poleceń](../ide/reference/visual-studio-command-aliases.md).

## <a name="access-visual-studio-tools"></a>Dostęp do narzędzi Visual Studio

Możesz szybko dojść wiersza polecenia dewelopera lub innego narzędzia Visual Studio, jeśli przypiąć go do Start menu i na pasku zadań.

1. W Eksploratorze Windows przejdź do `%ProgramData%\Microsoft\Windows\Start Menu\Programs\Visual Studio 2017\Visual Studio Tools`.

1. Kliknij prawym przyciskiem myszy lub Otwórz menu kontekstowe dla **wiersza polecenia dewelopera**, a następnie wybierz pozycję **Przypnij do ekranu startowego** lub **Przypnij do paska zadań**.

## <a name="manage-files-toolbars-and-windows"></a>Zarządzanie plikami, paski narzędzi i systemu windows

W dowolnym momencie może być Praca w wielu plikach kodu i przenoszenia między kilka okien narzędzi podczas opracowywania aplikacji. Można zachować organizowane przy użyciu następujących wskazówek.

- **Widoczne pliki, które są często używane w edytorze**. Pliki do lewej strony karty można przypiąć również tak, że są one widoczne niezależnie od tego, ile plików jest otwarty w edytorze.

     Aby przypiąć plik, wybierz kartę pliku, a następnie wybierz pozycję **stan przypięcia Przełącz** przycisku.

- **Przenoszenie dokumentów i systemu windows na inne monitory**. Jeśli używasz więcej niż jeden monitor podczas tworzenia aplikacji, można pracować na części aplikacji łatwiej przenosząc pliki, które są otwarte w edytorze inny monitor. Można również przenieść okna narzędzi, takich jak okna debugera do innego monitora i karty dokowanie okien dokumentów i narzędzia, aby utworzyć "kopie robocze." Aby uzyskać więcej informacji, zobacz [dostosowywanie układów okien w programie Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md).

     Można również zarządzać plikami łatwiej tworząc inne wystąpienie **Eksploratora rozwiązań** i przeniesienie ich na inny monitor. Aby utworzyć inne wystąpienie programu **Eksploratora rozwiązań**, otwórz menu skrótów w **Eksploratora rozwiązań**, a następnie wybierz pozycję **nowy widok Eksploratora rozwiązania**.

- **Dostosowywanie czcionek, które są wyświetlane w programie Visual Studio**. Można zmienić krój czcionki, rozmiar i kolor, który jest używany dla tekstu w IDE. Na przykład można dostosować kolor elementów kodu określonych w edytorze i krój czcionki w narzędzia windows lub w środowisku IDE. Aby uzyskać więcej informacji, zobacz [porady: zmiana czcionek i kolorów](../ide/how-to-change-fonts-and-colors-in-visual-studio.md) i [porady: zmiana czcionek i kolorów w edytorze](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md).

## <a name="see-also"></a>Zobacz także

- [Domyślne skróty klawiaturowe dla często używanych poleceń](../ide/default-keyboard-shortcuts-for-frequently-used-commands-in-visual-studio.md)
- [Porady: Dostosowywanie menu i pasków narzędzi](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md)
- [Wskazówki: Tworzenie prostej aplikacji](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md)
- [Ułatwienia dostępu porady i wskazówki](../ide/reference/accessibility-tips-and-tricks.md)