---
title: Usuń błędy programu i poprawić kod
description: W tym artykule opisano niektóre podstawowe sposoby Visual Studio ułatwia znajdowanie i rozwiązywanie problemów w kodzie, w tym błędy kompilacji, analizy kodu, narzędzi i testów jednostkowych debugowania.
ms.date: 05/02/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: c3a14d28-d811-4ff3-bd09-21dce14025ca
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 320615daa95ba9fad69fe48490f83c19ccf8e1ce
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/11/2018
---
# <a name="make-code-work-in-visual-studio"></a>Wprowadź kod działa w programie Visual Studio

Program Visual Studio udostępnia zaawansowany zestaw zintegrowanych kompilacji projektu oraz narzędzia debugowania. W tym artykule Dowiedz się, jak Visual Studio może pomóc w znalezieniu problemów w kodzie za pomocą danych wyjściowych kompilacji analizy kodu, narzędzia debugowania i testów jednostkowych.

Już znalezienia edytora i utworzyć kodu. Chcesz teraz, upewnij się, że kod działa prawidłowo. W programie Visual Studio, podobnie jak w przypadku większości IDEs są dwie fazy do wprowadzania pracy kodu: tworzenia kod, aby przechwycić i usuń błędy projektu i kompilatora i uruchamiania kod, aby znaleźć błędy środowiska wykonawczego i dynamicznych.

## <a name="build-your-code"></a>Tworzenie kodu

Istnieją dwa typy podstawowe konfiguracji kompilacji: **debugowania** i **wersji**. **Debugowania** konfiguracja daje wolniej, większy plik wykonywalny, który umożliwia bardziej zaawansowane funkcje interaktywne środowisko debugowania środowiska wykonawczego. **Debugowania** plik wykonywalny nigdy nie powinny być wysyłane. **Wersji** konfiguracji kompilacje szybsze, zoptymalizowanego pliku wykonywalnego, który jest odpowiedni na potrzeby wysłania (co najmniej z punktu widzenia kompilatora). Domyślna konfiguracja kompilacji jest **debugowania**.

Najprostszym sposobem, aby skompilować projekt jest naciśnij **F7**, ale można również uruchomić kompilacji, wybierając **kompilacji** > **Kompiluj rozwiązanie** z poziomu menu głównego.

![Opcja menu projektu kompilacji programu Visual Studio](../ide/media/vs_ide_gs_debug_build_menu_item.png)

Można obserwować proces kompilacji w **dane wyjściowe** okna w dolnej części interfejsu użytkownika programu Visual Studio. Operacje kompilacji, ostrzeżenia i błędy są wyświetlane tutaj. Jeśli masz błędów (lub w przypadku ostrzeżenia powyżej skonfigurowanego poziomu) kompilacji nie powiedzie się. Możesz kliknąć na błędy i ostrzeżenia, aby przejść do wiersza, w którym wystąpił. Ponownie skompiluj projekt przez albo naciskając klawisz **F7** ponownie (, aby ponownie skompilować tylko pliki z błędami) lub **Ctrl**+**Alt**+**F7**  (dla czystego i pełne ponowne tworzenie).

W oknie wyników poniżej edytorze istnieją dwa okna z kartami: **dane wyjściowe** okna, które zawiera kompilator pierwotnych danych wyjściowych (w tym komunikaty o błędach); i **listy błędów** okna, które zawiera Sortowanie i filtrowanie listy wszystkie błędy i ostrzeżenia.

Gdy kompilacja zakończy się pomyślnie, zobacz wyniki, tak jak poniżej w **dane wyjściowe** okno:

![Visual Studio pomyślnego utworzenia kompilacji w danych wyjściowych](../ide/media/vs_ide_gs_debug_success_build.png)

## <a name="review-the-error-list"></a>Przejrzyj listę błędów

Jeśli nie dokonano żadnych zmian do kodu, który została wcześniej i pomyślnie skompilowana prawdopodobnie wystąpił błąd. Jeśli jesteś nowym użytkownikiem kodowania, prawdopodobnie partii z nich. Błędy czasami są oczywiste, np. Błąd składniowy prostego lub nieprawidłową nazwę zmiennej, a czasami są trudne do zrozumienia się one niezrozumiałe kod prowadzące. Czyszczący widoku problemy, przejdź do dolnej części kompilacji **dane wyjściowe** okna, a następnie kliknij przycisk **listy błędów** kartę. Przejście do bardziej zorganizowany widok błędów i ostrzeżeń dla projektu i udostępnia pewne dodatkowe opcje.

![Dane wyjściowe programu Visual Studio i listy błędów](../ide/media/vs_ide_gs_debug_bad_build_error_list.png)

Kliknij przycisk błąd w wierszu **listy błędów** okna, aby przejść do wiersza błąd występuje w. (Lub Włącz numery wierszy, klikając w **Szybkie uruchamianie** paska w prawym górnym, wpisując "numerów linii" go, a naciśnięcie przycisku **Enter**. Jest to najszybszy sposób na uzyskanie dostępu do **opcje** okna dialogowego, w którym można włączyć numerów wierszy. Dowiedz się, jak używać **Szybkie uruchamianie** pasek i zaoszczędzić dużo kliknięć interfejsu użytkownika!)

![Visual Studio edytor z numery wierszy](../ide/media/vs_ide_gs_debug_line_numbers.png)

![Opcja numery wiersza w usłudze Visual Studio](../ide/media/vs_ide_gs_debug_options_line_numbers.png)

Naciśnij klawisz **Ctrl**+**G** Aby szybko przejść do numer wiersza, w którym wystąpił błąd.

Błąd jest identyfikowany przez czerwony znak podkreślenia "Zygzakowata". Umieść kursor nad go, aby uzyskać dodatkowe szczegóły. Wprowadzić poprawki i to możliwe, chociaż może powodować nowy błąd z korekty. (Jest to nazywane "regresji").

![Visual Studio błędów aktywacji](../ide/media/vs_ide_gs_debug_error_hover1.png)

Przeprowadzenie listy błędów i rozwiąż wszystkie problemy występujące w kodzie.

![Visual Studio Debugowanie błędów okna](../ide/media/vs_ide_gs_debug_error_list.png)

### <a name="review-errors-in-detail"></a>Przejrzyj błędy szczegółowe

Wiele błędów mogą nie ma sensu do Ciebie ma inną pisownię, ponieważ są one w kategoriach kompilatora. W takich przypadkach będą potrzebne dodatkowe informacje. Z **listy błędów** okna, możliwość automatycznego wyszukiwania usługi Bing, aby uzyskać więcej informacji na temat błędu lub ostrzeżenia. Kliknij prawym przyciskiem myszy na odpowiednim wpis wierszu, a następnie wybierz **Pokaż błąd pomóc** z menu kontekstowego, lub kliknij wartość kodu błędu Link w **kod** kolumny **listy błędów**.

![Lista błędów w usłudze Visual Studio wyszukiwania usługi Bing](../ide/media/vs_ide_gs_debug_error_list_error_help.png)

W zależności od ustawień przeglądarki sieci web wyświetla wyniki wyszukiwania dla kodu błędu i tekst albo karty zostanie otwarty w programie Visual Studio i wyświetla wyniki wyszukiwania usługi Bing. Wyniki są z różnych źródeł w Internecie, a nie wszystkie mogą być pomocne.

## <a name="use-code-analysis"></a>Użycie analizy kodu

Analizatorów kodu szukać typowe problemy kodu, które może prowadzić do błędów czasu wykonywania lub problemów w kodzie zarządzania.

### <a name="c-and-visual-basic-code-analysis"></a>Analiza kodu C# i Visual Basic

Visual Studio 2017 zawiera zestaw wbudowanych [analizatorów platformy kompilatora .NET](../code-quality/roslyn-analyzers-overview.md) który badanie kodu C# i Visual Basic podczas pisania. Można zainstalować dodatkowe analizatorów jako rozszerzenia programu Visual Studio lub pakietu NuGet. W przypadku znalezienia naruszeń zasady są raportowane zarówno w edytorze kodu jako dowolnym kształcie kodem ataku i w **listy błędów**.

### <a name="c-code-analysis"></a>Analiza kodu C++

Aby przeanalizować kod w języku C++, uruchom [statycznej analizy kodu](../code-quality/quick-start-code-analysis-for-c-cpp.md). Pobierz w celu przejrzenia po zostały wyczyszczone oczywiste błędy, które uniemożliwiają pomyślnego utworzenia kompilacji i zająć trochę czasu w celu rozwiązania ostrzeżeń, które może ona powodować jego uruchomieniem. Zaoszczędzisz samodzielnie niektórych problemów występujących i mogą dowiedzieć się kilka technik styl kodu.

Naciśnij klawisz **Alt**+**F11** (lub wybierz **Analizuj** > **uruchamiania analizy kodu dla rozwiązania** z górnego menu) do Uruchom statycznej analizy kodu.

![Z menu programu Visual Studio kod — analiza](../ide/media/vs_ide_gs_debug_run_code_analysis.png)

Wszelkie nowe lub zaktualizowane ostrzeżenia są wyświetlane w **listy błędów** u dołu IDE. Polecenie ostrzeżenia, aby przejść do nich w kodzie.

![Lista błędów programu Visual Studio z ostrzeżeniami](../ide/media/cpp-code-analysis-warning.png)

## <a name="use-light-bulbs-to-fix-or-refactor-code"></a>Użyj żarówki do naprawienia lub zrefaktoryzuj kod

[Szybkie akcje](../ide/quick-actions.md), dostępne z żarówkę lub ikonę śrubokręt let Refaktoryzuj wbudowanego kodu. Są one łatwe rozwiązać typowe ostrzeżenia szybkie i skuteczne w kodzie C#, C++ i Visual Basic. Aby uzyskiwać do nich dostęp, kliknij prawym przyciskiem myszy na wężyk ostrzeżenie i wybierz **szybkie akcje i refaktoryzacje**. Lub, gdy kursor znajduje się w wierszu kolorowe wężyk, naciśnij klawisz **Ctrl**+**.** lub wybierz żarówkę lub ikonę śrubokręt na marginesie. Zobaczysz listę możliwych poprawki lub refaktoryzacje, które można zastosować do wiersza kodu.

![Visual Studio żarówki podglądu](../ide/media/quick-actions-options.png)

Szybkie akcje można tam, gdzie analizatorów kodu określić istnieje możliwość napraw zrefaktoryzuj, lub zwiększyć kodu. Kliknij w każdym wierszu kodu, kliknij prawym przyciskiem myszy, aby otworzyć menu kontekstowe i wybierz **szybkie akcje i refaktoryzacje**. Jeśli dostępne są opcje refaktoryzacji lub poprawy jakości, zostaną one wyświetlone. W przeciwnym razie komunikat **tutaj dostępne nie szybkie akcje** wyświetla w lewym dolnym rogu IDE.

![Brak dostępnych tekstu szybkie akcje](../ide/media/vs_ide_gs_debug_light_bulb_no_options.png)

Z obsługą, można szybko użyj klawiszy strzałek i **Ctrl**+**.** Aby sprawdzić możliwości refaktoryzacji łatwe i czyszczenie kodu!

## <a name="debug-your-running-code"></a>Debugowanie kodu uruchomione

Teraz, gdy został pomyślnie skompilowany kod i wykonać nieco oczyszczanie, uruchom go przez naciśnięcie przycisku **F5** lub wybierając **debugowania** > **Rozpocznij debugowanie**. Spowoduje to uruchomienie aplikacji w środowisku debugowania, można zaobserwować jego zachowanie szczegółowo. Środowiska IDE programu Visual Studio zmian w uruchomionej aplikacji: **dane wyjściowe** okno zostało zastąpione przez dwa nowe (w oknie Konfiguracja domyślna), **automatycznych/zmienne lokalne/oglądanie** kartach okna i **Wywołać/punktów przerwania/wyjątek witryny Stack ustawienia/wyjścia** okno z kartami. Te okna, ma wiele kart, które można sprawdzić i oceny zmiennych aplikacji, wątki stosy wywołań i różnych innych zachowań podczas jego wykonywania.

![Automatycznych programu Visual Studio i Windows stosu wywołań](../ide/media/vs_ide_gs_debug_autos_and_call_stack.png)

Zatrzymaj aplikację, naciskając klawisz **Shift**+**F5** lub przez kliknięcie przycisku **zatrzymać** przycisku. Alternatywnie możesz po prostu zamknąć główne okno aplikacji (lub okno wiersza polecenia).

Jeśli kod został uruchomiony idealnie i dokładnie jako oczekiwane, Gratulacje! Jednak jeśli zawiesił, lub awaria lub udostępniła Ci pewnych wyników dziwne, należy odnaleźć źródła tych problemów i napraw błędy.

### <a name="set-simple-breakpoints"></a>Ustaw punkty przerwania proste

[Punkty przerwania](../debugger/using-breakpoints.md) są najbardziej podstawowa i podstawowych funkcji niezawodne debugowanie. Punkt przerwania wskazuje, gdzie programu Visual Studio należy zawiesić kodu uruchomionej, aby móc przeglądać wartości zmiennych, ani zachowanie pamięci lub czy jest pobieranie uruchamiana gałąź kodu. Nie ma potrzeby Odbuduj projekt po ustawiania i usuwania punktów przerwania.

Ustaw punkt przerwania, klikając na marginesie daleko wiersza miejscu podziału wystąpienia lub naciśnij klawisz **F9** można ustawić punktu przerwania w bieżącym wierszu kodu. Po uruchomieniu kodu wstrzyma (lub *podziału*) przed wykonaniem instrukcji ten wiersz kodu.

![Visual Studio punktu przerwania.](../ide/media/vs_ide_gs_debug_breakpoint1.png)

Najczęstsze zastosowania dla punktów przerwania obejmują:

- Aby zawęzić źródło awarię lub zawieszenie, wykres punktowy punktów przerwania w całym i wokół kod wywołania metody, które zdaniem użytkownika powoduje awarię. W momencie uruchamiania kodu w debugerze Usuń, a następnie zresetować punktów przerwania bliżej razem do momentu znalezienia ataku wiersz kodu. Zobacz następną sekcję, aby dowiedzieć się, jak uruchamianie kodu w debugerze.

- Podczas wprowadzania nowy kod, ustaw punkt przerwania na początku, a następnie uruchom kod, aby upewnić się, że zachowuje się zgodnie z oczekiwaniami.

- Jeśli zostały zaimplementowane skomplikowane zachowanie, ustaw punkty przerwania algorytmicznego kodu, więc możesz sprawdzić wartości zmiennych i danych, gdy program dzieli.

- Jeśli pisania kodu języka C lub C++ Użyj punktów przerwania, aby zatrzymać kod, więc można zbadać wartości adresów (poszukaj NULL) oraz liczby odwołań podczas debugowania dla błędów związanych z pamięcią.

Aby uzyskać więcej informacji na temat używania punktów przerwania odczytu [używanie punktów przerwania](../debugger/using-breakpoints.md).

### <a name="inspect-your-code-at-run-time"></a>Sprawdź kod w czasie wykonywania

Po kodzie uruchomionych trafienia punktu przerwania i wstrzymuje działanie, wiersz kodu oznaczone kolorem żółtym (bieżącej instrukcji) nie ma jeszcze wykonane. W tym momencie można wykonać bieżącej instrukcji, a następnie sprawdź zmienionymi wartościami. Można użyć kilku *krok* poleceń do wykonania kodu w debugerze. Kod oznaczone w przypadku wywołania metody, można krok do niego, naciskając **F11**. Możesz również *Przekrocz nad* wiersz kodu, naciskając klawisz **F10**. Aby uzyskać dodatkowe polecenia i szczegółowe informacje na temat krokowo kodu, przeczytaj [Przejdź kodu za pomocą debugera](../debugger/navigating-through-code-with-the-debugger.md).

![Visual Studio wartość czasu wykonywania inspekcji](../ide/media/vs_ide_gs_debug_hit_breakpoint.png)

Na powyższej ilustracji, można odtwarzać instrukcja debugera jeden naciskając albo **F10** lub **F11** (ponieważ nie Brak wywołania metody, zarówno polecenia mają ten sam rezultat).

Gdy debuger jest wstrzymana, można sprawdzić zmiennych i stosy, aby określić, co się dzieje wywołań. Czy wartości w zakresach, które chcesz wyświetlić? Są wykonywane w odpowiedniej kolejności wywołań?

![Visual Studio wartość czasu wykonywania inspekcji](../ide/media/vs_ide_gs_debug_inspect_value.png)

Umieść kursor nad zmiennej, aby zobaczyć jego bieżącej wartości i odwołań. Jeśli widzisz wartość, która Nieoczekiwane wyrażenie prawdopodobnie usterki w poprzednim lub wywołującego kodu. Aby uzyskać więcej szczegółowych informacji debugowania [więcej](../debugger/getting-started-with-the-debugger.md) o korzystanie z debugera.

Ponadto Wyświetla Visual Studio **narzędzia diagnostyczne** okna, w którym można obserwować użycia Procesora i pamięci aplikacji w czasie. Później podczas programowania aplikacji można użyć tych narzędzi do wyszukania nieprzewidziane duże obciążenie lub pamięci alokacji Procesora. Używany w połączeniu z **czujki** okno i punktów przerwania, aby określić przyczynę nieoczekiwany duże obciążenie lub Publikuj zasobów. Aby uzyskać więcej informacji, zobacz [profilowania samouczek funkcji](../profiling/profiling-feature-tour.md).

## <a name="run-unit-tests"></a>Uruchom testy jednostkowe

Testy jednostkowe są pierwszą linię obrony przed usterki kodu, ponieważ, jeśli zostaną prawidłowo wykonane, przetestować jeden kod, zwykle jednej funkcji "jednostki" i są łatwiejsze do debugowania niż pełne programu. Visual Studio instaluje struktur testowania jednostki firmy Microsoft dla kodu zarządzane i natywne. Do tworzenia testów jednostkowych, uruchom je i raportuje o wynikach tych testów, należy użyć framework testowania jednostki. Testów jednostkowych Uruchom ponownie po wprowadzeniu zmian, aby sprawdzić, czy kod nadal działa poprawnie. Za pomocą programu Visual Studio Enterprise edition można automatycznie uruchomić testy po każdej kompilacji.

Aby rozpocząć, przeczytaj [Generowanie testów jednostek dla kodu za pomocą IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md).

Aby dowiedzieć się więcej na temat testów jednostkowych w Visual Studio i sposób ich mogą pomóc tworzyć lepsze jakości kodu, przeczytaj [testu jednostkowego podstawy](../test/unit-test-basics.md).

## <a name="see-also"></a>Zobacz także

- [Przewodnik po funkcjach debugera](../debugger/debugger-feature-tour.md)
- [Dowiedz się więcej o korzystaniu z debugera](../debugger/getting-started-with-the-debugger.md)
- [Generowanie i napraw kodu](../ide/code-generation-in-visual-studio.md)