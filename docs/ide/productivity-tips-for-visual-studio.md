---
title: "Wskazówki dotyczące produktywności dla programu Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ccc5e543-7dcf-465c-97dd-e133e869800c
caps.latest.revision: "28"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f4778bde9903ce3e264f0209c147eedc227b7d8d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="productivity-tips-for-visual-studio"></a>Visual Studio — wskazówki dotyczące produktywności
Wykonując te wskazówki można można szybkie i wydajne zapisu, przejdź i debugowanie kodu w programie Visual Studio. Aby uzyskać więcej informacji o typowych skróty klawiaturowe, zobacz [porady i wskazówki](../ide/tips-and-tricks-for-visual-studio.md). Aby uzyskać bardziej szczegółowy wykaz, zobacz [zidentyfikowanie i dostosowywanie skrótów klawiaturowych](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md) i [domyślne skróty klawiaturowe](../ide/default-keyboard-shortcuts-in-visual-studio.md).  
  
 Ten temat zawiera następujące sekcje:  
  
 [Uzyskiwanie dostępu do narzędzi Visual Studio Tools](../ide/productivity-tips-for-visual-studio.md#BKMK_Access)  
  
 [Pisanie kodu](../ide/productivity-tips-for-visual-studio.md#BKMK_Writing)  
  
 [Poruszanie się w obrębie kodu](../ide/productivity-tips-for-visual-studio.md#BKMK_Navigating)  
  
 [Szybsze znajdowanie elementów](../ide/productivity-tips-for-visual-studio.md#BKMK_Finding)  
  
 [Debugowanie kodu](../ide/productivity-tips-for-visual-studio.md#BKMK_Debugging)  
  
 [Zarządzanie plikami, paski narzędzi i systemu Windows](../ide/productivity-tips-for-visual-studio.md#BKMK_Managing)  
  
##  <a name="BKMK_Access"></a>Uzyskiwanie dostępu do narzędzi Visual Studio Tools  
 Jeśli przypniesz na ekranie startowym lub pasku zadań można łatwiej dostępu wiersza polecenia dewelopera lub innego narzędzia.  
  
1.  Na ekranie startowym wpisz `Visual Studio Tools`, a następnie wybierz klawisz Enter.  
  
2.  W **Eksploratora plików**, otwórz menu skrótów dla elementów, które chcesz:  
  
    -   Tworzenie powiadomień  
  
    -   Menedżer pakietów możliwością debugowania  
  
    -   Wiersz polecenia dla VS2013 deweloperów  
  
    -   Microsoft Feedback Client 2013  
  
    -   VS2013 ARM Cross narzędzia wiersza polecenia  
  
    -   VS2013 x64 dla wielu narzędzi wiersza polecenia  
  
    -   VS2013 x64 natywnych narzędzi wiersza polecenia  
  
    -   VS2013 x86 natywnych narzędzi wiersza polecenia  
  
3.  Wybierz **Przypnij do ekranu startowego** lub **Przypnij do paska zadań**.  
  
##  <a name="BKMK_Writing"></a>Pisanie kodu  
 Szybsze pisanie kodu przy użyciu następujących funkcji.  
  
-   **Użyj przykładowych aplikacji**. Można przyspieszyć programowanie aplikacji przez pobranie i zainstalowanie przykładowe aplikacje z galerii kodu MSDN. Można też uzyskać określonej technologii lub koncepcji programowania, pobierając i eksploracja przykładowy pakiet dla tego obszaru.  
  
-   **Używanie IntelliSense**. Po wprowadzeniu kodu w edytorze, zostanie wyświetlone informacje funkcji IntelliSense, takie jak listy elementów członkowskich, informacje o parametrach szybka podpowiedź, pomoc podpisu i całe słowo. Obsługuje te funkcje dopasowywania rozmytego tekstu; na przykład listy wyników dla członków listy zawiera nie tylko wpisy rozpoczynających się od znaków czy zostały wprowadzone, ale także wpisów, zawierające kombinację znaków w dowolnym miejscu ich nazw. Aby uzyskać więcej informacji, zobacz [za pomocą funkcji IntelliSense](../ide/using-intellisense.md).  
  
-   **Zmień automatyczne wstawianie Opcje IntelliSense podczas wpisywania kodu**. Przełączanie IntelliSense do tryb sugestii, można określić, że opcje IntelliSense są wstawiane tylko wtedy, gdy jawnie je.  
  
     Aby włączyć tryb sugestii, wybierz polecenie Ctrl + Alt + spacja kluczy lub na pasku menu wybierz **Edytuj**, **IntelliSense**, **Przełącz tryb uzupełniania**.  
  
-   **Wstawki kodu za pomocą**. Można użyć wbudowanych wstawki lub utworzyć własne wstawki.  
  
     Aby wstawić fragment kodu, na pasku menu wybierz polecenie **Edytuj**, **IntelliSense**, **wstawić fragment** lub Otwórz menu skrótów w pliku i wybierz polecenie **wstawić fragment kodu** . Aby uzyskać więcej informacji, zobacz [wstawki kodu](../ide/code-snippets.md).  
  
-   **Usuń kodu wbudowanego błędy**. Szybkie akcje pozwalają łatwo zrefaktoryzuj, generowanie lub modyfikację kodu za pomocą jednej akcji. Można zastosować te akcje za pomocą ikoną żarówki ![małych ikon żarówki](media/vs2015_lightbulbsmall.png "VS2017_LightBulbSmall"), lub naciskając klawisz **Alt + Enter** lub **Ctrl +.** gdy kursor znajduje się na odpowiedni wiersz kodu. Zobacz [szybkie akcje](quick-actions.md) Aby uzyskać więcej informacji.  

-   **Wyświetlanie i edytowanie definicji elementu kodu**. Można szybko wyświetlić i edytować modułu, w którym jest zdefiniowany element kodu, takie jak element członkowski, zmiennej lub lokalnego.  
  
     Aby otworzyć okno podręczne definicji, zaznacz element, a następnie wybierz pozycję **Alt + F12** kluczy, lub Otwórz menu skrótów dla elementu, a następnie wybierz pozycję **definicji wglądu**. Aby otworzyć definicję w oknie oddzielny kod, otwórz menu skrótów dla elementu, a następnie wybierz **przejdź do definicji**.  
  
##  <a name="BKMK_Navigating"></a>Poruszanie się w obrębie kodu  
 Znajdź i przejdź do określonych lokalizacji w kodzie szybciej, można użyć różnych technik.  
  
-   **Zakładki wierszy kodu**. Zakładki można użyć, aby szybko przejść do określonych wierszy kodu w pliku.  
  
     Aby ustawić zakładki, na pasku menu, wybierz **Edytuj**, **zakładki**, **przełączająca**. Można wyświetlić wszystkie zakładki w rozwiązaniu w **zakładki** okna. Aby uzyskać więcej informacji, zobacz [ustawienie zakładek w kodzie](../ide/setting-bookmarks-in-code.md).  
  
-   **Wyszukaj definicje symbolu w pliku**. Umożliwia wyszukiwanie w ramach rozwiązania, aby zlokalizować definicji symbolu i nazwy pliku, ale wyniki wyszukiwania nie uwzględniają przestrzeni nazw lub zmiennych lokalnych.  
  
     Aby uzyskać dostęp do tej funkcji, na pasku menu wybierz **Edytuj**, **przejdź do**.  
  
-   **Przeglądaj ogólną strukturę kodu**. W **Eksploratora rozwiązań**, można wyszukiwać i przeglądać klasy i ich typy i składniki w projektach. Można również wyszukiwania symboli, Wyświetl hierarchię wywołań metody, Znajdź odwołania do symboli i wykonywać inne zadania. Jeśli wybierzesz element kodu w **Eksploratora rozwiązań**, skojarzony plik zostanie otwarty w **Podgląd** kartę i przesuwa kursor do elementu w pliku. Aby uzyskać więcej informacji, zobacz [wyświetlanie struktury kodu](../ide/viewing-the-structure-of-code.md).  
  
##  <a name="BKMK_Finding"></a>Szybsze znajdowanie elementów  
 Można wyszukiwać w IDE dla poleceń, plików i opcji, oprócz filtrowanie zawartości okna narzędzi, aby wyświetlić tylko informacje istotne dla bieżącego zadania.  
  
-   **Filtrowanie zawartości okna narzędzi**. Można wyszukiwać w treści wiele okien narzędzi, takich jak **przybornika**, **właściwości** okno i **Eksploratora rozwiązań**, ale wyświetlania tylko elementy, których nazwy zawiera znaki, które określisz.  
  
-   **Wyświetlanie błędów ma adres**. Jeśli wybierzesz **filtru** znajdującego się na **listy błędów** narzędzi można zmniejszyć liczbę błędów, które są widoczne w **listy błędów** okna. Możesz wyświetlić tylko błędów w plikach, które są otwarte w edytorze, tylko błędy w bieżącym pliku lub tylko błędy w bieżącym projekcie. Można także przeszukać w oknie Lista błędów, aby znaleźć określone błędy.  
  
-   **Znajdź w oknach dialogowych, menu poleceń i opcji**. W [Szybkie uruchamianie, środowisko, opcje — Okno dialogowe](../ide/reference/quick-launch-environment-options-dialog-box.md) wprowadź słowa kluczowe lub wyrażenia dla elementów, które próbujesz odnaleźć. Na przykład następujące opcje są wyświetlane po wprowadzeniu `new project`:  
  
     Rysunek 3: Lista wyników szybkiego uruchamiania dla`new project`  
  
     ![Szybkie uruchamianie wyniki dla "nowego projektu"](../ide/media/productivity_quicklaunch.png "Productivity_QuickLaunch")  
  
     **Szybkie uruchamianie** zawiera łącza do **nowy projekt** okno dialogowe **Dodaj nowy element** okno dialogowe i strony projektów i rozwiązań w **opcje** okno dialogowe, między innymi. Szybkie uruchamianie wyników można także pliki projektu i okien narzędzi.  
  
##  <a name="BKMK_Debugging"></a>Debugowanie kodu  
 Debugowanie mogą zajmować dużo czasu, ale poniższe porady mogą pomóc przyspieszyć proces.  
  
-   **Testowanie strony, aplikacji lub witryny w różnych przeglądarkach**. Jak można debugować kodu, można łatwo przełączać między przeglądarek sieci web zainstalowany, w tym [narzędzie Page Inspector (Visual Studio)](http://msdn.microsoft.com/Library/65880969-1ad2-47be-85b9-bb12c81bf209), bez konieczności otwierania **przeglądanie za pomocą** okno dialogowe. Można użyć **docelowego debugowania** listę, która znajduje się na **standardowe** narzędzi dalej, aby **Rozpocznij debugowanie** przycisk, aby szybko sprawdzić, które przeglądarki jako debugowania lub Wyświetl strony.  
  
     ![Wybierz opcje debugowania w przeglądarce sieci Web](../ide/media/webbrowserdropdowntoolbar.png "WebBrowserDropDownToolbar")  
  
-   **Ustaw punkty przerwania tymczasowego**. Można utworzyć tymczasowego punktu przerwania w bieżącym wierszu kodu i jednocześnie uruchomienia debugera. Gdy naciśniesz wiersza kodu debugera przejdzie do trybu przerwania. Aby uzyskać więcej informacji, zobacz [nawigowanie po kodzie za pomocą debugera](../debugger/navigating-through-code-with-the-debugger.md).  
  
     Aby użyć tej funkcji, wybierz polecenie Ctrl + F10 kluczy lub Otwórz menu skrótów wiersza kodu, na którym chcesz przerwać, a następnie wybierz **Uruchom do kursora**.  
  
-   **Przenieś punkt wykonywania podczas debugowania**. Można przenieść do bieżącego punkt wykonywania do innej sekcji kodu i ponownie uruchom debugowanie z tego punktu. Ta metoda jest przydatna, jeśli chcesz debugować części kodu bez konieczności ponownego tworzenia wszystkich kroków, które są wymagane do uzyskania tej sekcji. Aby uzyskać więcej informacji, zobacz [nawigowanie po kodzie za pomocą debugera](../debugger/navigating-through-code-with-the-debugger.md).  
  
     Aby przenieść punkt wykonywania, przeciągnij żółty grot do lokalizacji, w której chcesz ustawić następnej instrukcji z tego samego pliku źródłowego, a następnie wybierz klawisz F5, aby kontynuować debugowanie.  
  
-   **Przechwytywanie informacji o wartości zmiennych**. Możesz dodać etykietki danych do zmiennej w kodzie i przypiąć go, dzięki czemu można uzyskać dostępu do ostatniej znanej wartości zmiennej, po zakończeniu debugowania. Aby uzyskać więcej informacji, zobacz [wyświetlić wartości danych w poradach dotyczących](../debugger/view-data-values-in-data-tips-in-the-code-editor.md).  
  
     Aby dodać etykietki danych, debuger musi być w trybie przerwania. Umieść kursor w zmiennej, a następnie wybierz przycisk numeru pin na etykietek danych, która jest wyświetlana. Po zatrzymaniu debugowania w pliku źródłowym obok wiersza kodu, która zawiera zmienną pojawi się ikona niebieski numeru pin. Jeśli wskażesz niebieski numeru pin, pojawi się wartość zmiennej z ostatniej sesji debugowania.  
  
-   **Wyczyść okna bezpośredniego**. Można wymazać zawartość [oknie bezpośrednim](../ide/reference/immediate-window.md) w czasie projektowania, wprowadzając `>cls` lub`>Edit.ClearAll`  
  
     Aby uzyskać więcej informacji o dodatkowe polecenia, zobacz [programu Visual Studio — aliasy poleceń](../ide/reference/visual-studio-command-aliases.md).  
  
##  <a name="BKMK_Managing"></a>Zarządzanie plikami, paski narzędzi i systemu Windows  
 W dowolnym momencie może być Praca w wielu plikach kodu i przenoszenia między kilka okien narzędzi podczas opracowywania aplikacji. Można zachować organizowane przy użyciu następujących wskazówek.  
  
-   **Widoczne pliki, które są często używane w edytorze**. Pliki do lewej strony karty można przypiąć również tak, że są one widoczne niezależnie od tego, ile plików jest otwarty w edytorze.  
  
     Aby przypiąć plik, wybierz kartę pliku, a następnie wybierz pozycję **stan przypięcia Przełącz** przycisku.  
  
-   **Przenoszenie dokumentów i systemu windows na inne monitory**. Jeśli używasz więcej niż jeden monitor podczas tworzenia aplikacji, można pracować na części aplikacji łatwiej przenosząc pliki, które są otwarte w edytorze inny monitor. Można również przenieść okna narzędzi, takich jak okna debugera do innego monitora i karty dokowanie okien dokumentów i narzędzia, aby utworzyć "kopie robocze." Aby uzyskać więcej informacji, zobacz [dostosowywanie układów okien w programie Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md).  
  
     Można również zarządzać plikami łatwiej tworząc inne wystąpienie **Eksploratora rozwiązań** i przeniesienie ich na inny monitor. Aby utworzyć inne wystąpienie programu **Eksploratora rozwiązań**, otwórz menu skrótów w **Eksploratora rozwiązań**, a następnie wybierz pozycję **nowy widok Eksploratora rozwiązania**.  
  
-   **Dostosowywanie czcionek, które są wyświetlane w programie Visual Studio**. Można zmienić krój czcionki, rozmiar i kolor, który jest używany dla tekstu w IDE. Na przykład można dostosować kolor elementów kodu określonych w edytorze i krój czcionki w narzędzia windows lub w środowisku IDE. Aby uzyskać więcej informacji, zobacz [porady: zmiana czcionek i kolorów](../ide/how-to-change-fonts-and-colors-in-visual-studio.md) i [porady: zmiana czcionek i kolorów w edytorze](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Domyślne skróty klawiaturowe dla często używanych poleceń](../ide/default-keyboard-shortcuts-for-frequently-used-commands-in-visual-studio.md)   
 [Porady: Dostosowywanie menu i pasków narzędzi](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md)   
 [Wskazówki: Tworzenie prostej aplikacji](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md)   
 [Ułatwienia dostępu porady i wskazówki](../ide/reference/accessibility-tips-and-tricks.md)