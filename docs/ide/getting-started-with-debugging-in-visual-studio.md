---
title: Wprowadzenie do debugowania w programie Visual Studio | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c3a14d28-d811-4ff3-bd09-21dce14025ca
caps.latest.revision: "5"
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: 82bce617eec0f5038499a2eed370efa33d817e20
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="getting-started-with-debugging-in-visual-studio"></a>Wprowadzenie do debugowania w programie Visual Studio
Program Visual Studio udostępnia zaawansowany zestaw zintegrowanych kompilacji projektu oraz narzędzia debugowania. W tym temacie Dowiedz się, jak rozpocząć korzystanie z najprostszych zbiór debugowanie funkcji interfejsu użytkownika.  

 Uwaga: Łącza do bardziej zaawansowanych funkcji i tematy poszczególnych platform lub funkcji są u dołu tej strony.  

## <a name="my-code-doesnt-work-help-me-visual-studio"></a>Kod nie działa. Pomóż mi, Visual Studio!  
 Więc możesz już znalezienia edytora i po utworzeniu kodu. Teraz ma się rozpocząć debugowanie kodu. W programie Visual Studio, podobnie jak w przypadku większości IDEs są dwie fazy do debugowania: kompilowanie kodu zdołały wychwycić i rozwiąż problemy projektu i kompilatora; i uruchamianie kodu w środowisku zdołały wychwycić i usuń błędy środowiska wykonawczego i dynamicznych.  

### <a name="configuring-a-build"></a>Konfigurowanie kompilacji  
 Istnieją dwa typy podstawowe konfiguracji kompilacji: **debugowania** i **wersji**. Pierwsze konfiguracja daje wolniej, większy plik wykonywalny, który umożliwia bardziej zaawansowane funkcje interaktywne środowisko debugowania środowiska wykonawczego, ale nigdy nie zostanie wysłana. Drugi kompilacje szybsze, bardziej zoptymalizowanego pliku wykonywalnego, który jest odpowiedni na potrzeby wysłania (co najmniej z punktu widzenia kompilatora).  

 Domyślna konfiguracja kompilacji jest **debugowania**.  

 ![Visual Studio debugowanie kompilacji przycisk](../ide/media/vs_ide_gs_debug_build_type1.PNG "Vs_ide_gs_debug_build_type1")  

 Można również określić platformę określonej kompilacji do obiektu docelowego, takich jak **x86** (procesory Intel 32-bitowy), **x64** (procesory Intel 64-bitowy), a **ARM** (procesory ARM, obsługiwane tylko w przypadku niektórych aplikacji typy). Wartość domyślna to **x86** dla projektów zarządzanego i natywnego. Aby go zmienić, kliknij kompilacji listy rozwijanej platform i wybierz pozycję innej platformie lub **programu Configuration Manager...**  

 ![Okno Menedżera pliku konfiguracji programu Visual Studio](../ide/media/vs_ide_gs_debug_build_cf_mgr.PNG "Vs_ide_gs_debug_build_cf_mgr")  

 Można określić konfiguracji kompilacji docelowych przy użyciu **programu Configuration Manager**. Uruchom ją, kliknij przycisk **konfiguracji** lub **Procesora** listy rozwijanej i wybierz **nowy...**  do utworzenia nowej kompilacji lub platformy.  

 ![Menedżer konfiguracji programu Visual Studio okna](../ide/media/vs_ide_gs_debug_build_cf_mgr_2.PNG "Vs_ide_gs_debug_build_cf_mgr_2")  

 Uruchamianie, wystarczy użyć **debugowania** i **x86** jako konfigurację kompilacji i platformy, odpowiednio. Gdy wszystko będzie gotowe, kodowanie i debugowania, zmień konfigurację, aby **wersji** i docelowymi określonej platformy. (Starsze wersje programu Visual Studio, pod warunkiem **AnyCPU** domyślna platforma do projektów kodu .net.)  

 Uwaga: Podczas kompilowania projektu wartości Konfiguracja i platforma są również używane do ustalenia, jakie ścieżki katalogu projektu służy do przechowywania pliku wykonywalnego. Zazwyczaj jest to  **\<ścieżka do projektu >\\< Nazwa projektu >\\< konfiguracji\>\\< platforma\>**. Na przykład projektu z konfiguracją `Debug` i platforma `x86` będzie można znaleźć w obszarze `Projects\MyProjectNameHere\MyProjectNameHere\bin\Debug\x86`. Może to być przydatne w przypadku własnych narzędzi lub skryptów, które zarządzają tych skompilowanych plików wykonywalnych.  

### <a name="building-your-code"></a>Kompilowanie kodu  
 Z kompilacji skonfigurowane nadszedł czas na faktycznie skompilowanie projektu. Najłatwiejszym sposobem na jego naciśnij klawisz F7, ale można również uruchomić kompilacji, wybierając **kompilacji -> Kompiluj rozwiązanie** z poziomu menu głównego.  

 ![Wybieranie opcji z menu projektu kompilacji programu Visual Studio](../ide/media/vs_ide_gs_debug_build_menu_item.png "Vs_ide_gs_debug_build_menu_item")  

 Można obserwować proces kompilacji w **dane wyjściowe** okno stanu w dolnej części interfejsu użytkownika programu Visual Studio. Operacje kompilacji, ostrzeżenia i błędy są wyświetlane tutaj. Jeśli masz błędów (lub w przypadku ostrzeżenia powyżej skonfigurowanego poziomu) kompilacji zakończy się niepowodzeniem. Możesz kliknąć na błędy i ostrzeżenia, aby przejść do wiersza, w którym wystąpił. Ponownie skompiluj projekt, naciskając klawisz albo **F7** ponownie (, aby ponownie skompilować tylko pliki z błędami) lub **Ctrl + Alt + F7** (dla czystego i pełne ponowne tworzenie).  

 Istnieją dwa kompilacji z kartami systemu windows w oknie wyników poniżej edytora: **dane wyjściowe** okna, które zawiera kompilator pierwotnych danych wyjściowych (w tym komunikaty o błędach); i **listy błędów** okna, które Umożliwia sortowanie i filtrowanie listy wszystkie błędy i ostrzeżenia.  

 Po pomyślnie, zostanie wyświetlone wyniki, tak jak poniżej w **dane wyjściowe** okna.  

 ![Dane wyjściowe kompilacji programu Visual Studio pomyślnie](../ide/media/vs_ide_gs_debug_success_build.PNG "vs_ide_gs_debug_success_build")  

### <a name="reviewing-the-error-list"></a>Na liście błędów  
 Jeśli nie dokonano żadnych zmian do kodu, który została wcześniej i pomyślnie skompilowana prawdopodobnie wystąpił błąd. Jeśli jesteś nowym użytkownikiem kodowania, prawdopodobnie partii z nich. Błędy są czasami oczywiste, na przykład błąd składniowy prostego lub nieprawidłową nazwę zmiennej, a czasami ich są trudne do zrozumienia się one niezrozumiałe kod prowadzące. Czyszczący widoku problemy, przejdź do dolnej części kompilacji **dane wyjściowe** okna, a następnie kliknij przycisk **listy błędów** kartę. Przejście do bardziej zorganizowany widok błędów i ostrzeżeń dla projektu i udostępnia pewne dodatkowe opcje.  

 ![Dane wyjściowe programu Visual Studio i listy błędów](../ide/media/vs_ide_gs_debug_bad_build_error_list.PNG "Vs_ide_gs_debug_bad_build_error_list")  

 Kliknij przycisk błąd w wierszu **listy błędów** okno i skok do wiersza, ten błąd występuje w. (Lub Włącz numery wierszy, klikając w **Szybkie uruchamianie** paska w prawym górnym, wpisując "numerów linii" do niego i naciskając klawisz Enter. Jest to najszybszy sposób na uzyskanie dostępu do **opcje** wpis okna, gdzie można włączyć numerów wierszy. Dowiedz się, jak używać **Szybkie uruchamianie** pasek i zaoszczędzić dużo kliknięć interfejsu użytkownika!)  

 ![Visual Studio edytor z numery wierszy](../ide/media/vs_ide_gs_debug_line_numbers.png "Vs_ide_gs_debug_line_numbers")  

 ![Visual Studio liczbami opcja](../ide/media/vs_ide_gs_debug_options_line_numbers.png "Vs_ide_gs_debug_options_line_numbers")  

 Użyj klawiszy Ctrl + G, aby szybko przejść do numer wiersza, w którym wystąpił błąd.  

 Błąd jest identyfikowany przez czerwony znak podkreślenia "Zygzakowata". Umieść kursor nad go, aby uzyskać dodatkowe szczegóły. Wprowadzić poprawki i to możliwe, chociaż może powodować nowy błąd z korekty. (Jest to nazywane "regresji").  

 ![Visual Studio błąd hover](../ide/media/vs_ide_gs_debug_error_hover1.png "Vs_ide_gs_debug_error_hover1")  

 Przeprowadzenie listy błędów i rozwiąż wszystkie problemy występujące w kodzie.  

 ![Visual Studio Debugowanie błędów okna](../ide/media/vs_ide_gs_debug_error_list.PNG "Vs_ide_gs_debug_error_list")  

### <a name="reviewing-errors-in-detail"></a>Przeglądanie błędy szczegółowe  
 Wiele błędów mogą nie ma sensu do Ciebie ma inną pisownię, ponieważ są one w kategoriach kompilatora. W takich przypadkach należy uzyskać dodatkowe informacje. Z **listy błędów** okna, możesz zrobić automatycznego wyszukiwania usługi Bing, aby uzyskać więcej informacji na temat błędu (lub ostrzeżenia) przez kliknięcie prawym przyciskiem myszy na odpowiednim wpis wierszu i wybierając **Pokaż błąd pomóc** z menu kontekstowe.  

 ![Lista błędów w usłudze Visual Studio wyszukiwania usługi Bing](../ide/media/vs_ide_gs_debug_error_list_error_help.png "Vs_ide_gs_debug_error_list_error_help")  

 Spowoduje to uruchomienie kartę w programie Visual Studio obsługującego wyniki Bing wyszukiwania błąd kodu i tekstu. Wyniki są z różnych źródeł w Internecie, a nie wszystkie mogą być pomocne.  

 Alternatywnie możesz kliknąć Link błąd wartość kodu w **kod** kolumny **listy błędów**. Spowoduje to uruchomienie wyszukiwania usługi Bing tylko kod błędu.  

### <a name="performing-static-code-analysis"></a>Wykonywanie statycznej analizy kodu  
 "Statycznej analizy kodu" jest dobrego sposobu informujący o tym "automatyczne sprawdzenie dostępności mój kod dla typowych problemów, które mogą prowadzić do błędów czasu wykonywania lub problemów w przystawce Zarządzanie kodu". Pobierz w celu przejrzenia po zostały wyczyszczone oczywiste błędy kompilacji uniemożliwia uruchomiony i zająć trochę czasu w celu rozwiązania ostrzeżeń, które może ona powodować. Będzie zaoszczędzić niektórych problemów występujących, a także dowiedzieć się kilka technik styl kodu.  

 Naciśnij klawisze Alt + F11 (lub wybierz **Analizuj -> Uruchom analizę kodu dla rozwiązania** z górnego menu) można uruchomić statycznej analizy kodu. Jeśli masz wiele kodu, może to potrwać pewien czas.  

 ![Z menu programu Visual Studio kod — analiza](../ide/media/vs_ide_gs_debug_run_code_analysis.png "Vs_ide_gs_debug_run_code_analysis")  

 Wszelkie ostrzeżenia, nowe lub zaktualizowane będą wyświetlane w **listy błędów** u dołu IDE. Polecenie ostrzeżenia, aby przejść do nich.  

 ![Visual Studio listy błędów z ostrzeżeniami](../ide/media/vs_ide_gs_debug_code_analysis_warning_error_list.PNG "vs_ide_gs_debug_code_analysis_warning_error_list")  

 Ostrzeżenia jest oznaczona symbolem jasny wężyk zielono-zamiast czerwony. Umieść kursor nad je, aby uzyskać więcej szczegółów, a następnie kliknij prawym przyciskiem myszy je, aby pobrać menu kontekstowe ułatwiających poprawki lub refaktoryzacji opcje.  

 ![Visual Studio kod analizy ostrzeżenia hover](../ide/media/vs_ide_gs_debug_code_analysis_warning_hover.png "vs_ide_gs_debug_code_analysis_warning_hover")  

### <a name="using-light-bulbs-to-fix-or-refactor-code"></a>Aby naprawić lub Zrefaktoryzuj kod przy użyciu żarówki  
 Żarówki to nowa funkcja programu Visual Studio, które umożliwiają Refaktoryzuj wbudowanego kodu. Są one łatwe rozwiązać typowe ostrzeżenia szybkie i skuteczne. Aby uzyskać do nich dostęp, kliknij prawym przyciskiem myszy na wężyk ostrzeżenie (lub naciśnij klawisze Ctrl +. Podczas kursora myszy nad wężyk), a następnie wybierz **szybkie akcje**.  

 ![Opcje języka Visual Studio żarówki szybkie](../ide/media/vs_ide_gs_debug_light_bulb1.png "Vs_ide_gs_debug_light_bulb1")  

 Zostanie wyświetlona lista możliwych poprawki lub refactors, które można zastosować do wiersza kodu.  

 ![Visual Studio żarówki Podgląd](../ide/media/vs_ide_gs_debug_light_bulb_preview_changes.PNG "Vs_ide_gs_debug_light_bulb_preview_changes")  

 Żarówki można tam, gdzie analizatorów kodu określić istnieje możliwość napraw zrefaktoryzuj, lub zwiększyć kodu. Kliknij w każdym wierszu kodu, kliknij prawym przyciskiem myszy, aby otworzyć menu kontekstowe i wybierz **szybkich** (lub, ponownie, jeśli wolisz wydajności, naciśnij klawisze Ctrl +). Jeśli obszar dostępne opcje refaktoryzacji lub ulepszenia, będą one wyświetlane; w przeciwnym razie komunikat `No quick options available here` będą wyświetlane w ramką lewym dolnym rogu IDE.  

 ![Visual Studio żarówki żadna opcja tekst](../ide/media/vs_ide_gs_debug_light_bulb_no_options.PNG "Vs_ide_gs_debug_light_bulb_no_options")  

 Środowisko można szybko użyj klawiszy strzałek i Ctrl +. Sprawdź, czy opcja szybkiego refaktoryzacji możliwości i czyszczenie kodu!  

 Aby uzyskać więcej informacji dotyczących żarówki, przeczytaj [szybkie wykonywanie akcji dzięki żarówkom](../ide/perform-quick-actions-with-light-bulbs.md).  

### <a name="debugging-your-running-code"></a>Debugowanie kodu uruchomiona  
 Teraz, gdy został pomyślnie skompilowany kod i wykonać nieco oczyszczanie, uruchom go, naciskając klawisz F5 lub wybranie **debugowanie -> Rozpocznij debugowanie**. Spowoduje to uruchomienie aplikacji w środowisku debugowania, więc można obserwować jego zachowanie szczegółowo. Zmiany środowiska IDE programu Visual Studio uruchomionej aplikacji: **dane wyjściowe** okno zostało zastąpione przez dwa nowe (w oknie Konfiguracja domyślna), **automatycznych/zmienne lokalne/moduły/oglądanie** kartach okna i  **Wywołania/punktów przerwania/wyjątek witryny Stack ustawienia/wyjścia** okno z kartami. Te okna, ma wiele kart, które można sprawdzić i oceny zmiennych aplikacji, wątki stosy wywołań i różnych innych zachowań podczas jego wykonywania.  

 ![Automatycznych programu Visual Studio i wywołanie stosu Windows](../ide/media/vs_ide_gs_debug_autos_and_call_stack.PNG "Vs_ide_gs_debug_autos_and_call_stack")  

 Spróbuj różnego rodzaju akcje z aplikacją i obserwować zmiany. Jeśli pojawi się coś nietypowego, wstrzymać aplikacji, naciskając klawisze Ctrl + Alt + Break (lub kliknij **wstrzymać** przycisku).  

 ![Visual Studio Przerwij wszystkie przycisk](../ide/media/vs_ide_gs_debug_break_all_button.png "vs_ide_gs_debug_break_all_button")  

 Naciśnij klawisz F5, aby kontynuować uruchamianie aplikacji (lub kliknij przycisk **Kontynuuj** przycisku).  

 ![Visual Studio debugowanie kontynuować przycisk](../ide/media/vs_ide_gs_debug_continue_button.png "Vs_ide_gs_debug_continue_button")  

 Można zatrzymać aplikację, naciskając klawisz Shift + F5 lub przez kliknięcie przycisku **zatrzymać** przycisku. Alternatywnie możesz po prostu zamknąć główne okno aplikacji (lub okno wiersza polecenia).  

 Jeśli kod został uruchomiony idealnie i dokładnie jako oczekiwane, Gratulacje! Zmień konfigurację kompilacji, aby **wersji** i skompiluj go ponownie dla wdrożenia! (Może wystąpić potrzeba szybkiego dostępu do bitu w testów jednostkowych na końcu, mimo że specjalistów). Jednak jeśli zawiesił, lub awaria lub udostępniła Ci pewnych wyników dziwne, należy odnaleźć źródła tych problemów i napraw błędy.  

### <a name="setting-simple-breakpoints"></a>Ustawianie punktów przerwania proste  
 Punkty przerwania są najbardziej podstawowa i podstawowych funkcji niezawodne debugowanie. Punkt przerwania wskazuje, gdzie programu Visual Studio należy zawiesić kodu uruchomionej, aby móc przeglądać wartości zmiennych, ani zachowanie pamięci lub czy jest pobieranie uruchamiana gałąź kodu. NIE trzeba przeprowadzać Odbuduj projekt po ustawiania i usuwania punktów przerwania.  

 Ustaw punkt przerwania, klikając w miejscu podziału występują, lub wybierz wiersz kodu i naciśnij klawisz F9 daleko margines wiersza. Po uruchomieniu kodu przestanie przed wykonaniem instrukcji ten wiersz kodu.  

 ![Visual Studio punktu przerwania](../ide/media/vs_ide_gs_debug_breakpoint1.png "Vs_ide_gs_debug_breakpoint1")  

 Gdy kodu przerywa, oznaczony wiersz kodu nie została jeszcze wykonane. W tym momencie możesz wykonać instrukcje dotyczące wiersz kodu oznaczony przez punkt przerwania i sprawdzić zmienionymi wartościami. Jest to "Przechodzenie do" kod. Kod oznaczone w przypadku wywołania metody, można przejść do niego, naciskając klawisz F11. Użytkownik może również "Przekrocz nad" wiersz kodu, naciskając klawisz F10. Aby uzyskać więcej szczegółów na kod wykonywanie krok po kroku, przeczytaj [nawigowanie po kodzie za pomocą debugera](../debugger/navigating-through-code-with-the-debugger.md).  

 Najczęstsze zastosowania dla punktów przerwania obejmują:  

1.  Aby zawęzić źródło awarię lub zawieszenie, wykres punktowy je w całym i wokół kod wywołania metody, które zdaniem użytkownika powoduje awarię. Podczas wykonywania kroków do kodu, Usuń, a następnie zresetowaniu punktów przerwania bliżej razem do momentu znalezienia ataku wiersz kodu.  

2.  Podczas wprowadzania nowego kodu należy ustawić punkt przerwania na początku i kroków kod, aby upewnić się, że zachowuje się zgodnie z oczekiwaniami.  

3.  Jeśli zaimplementowano zachowanie skomplikowane, zbioru punktów przerwań dla kodu algorytmicznego, dlatego możesz sprawdzić wartości zmiennych i danych, gdy program dzieli.  

4.  Podczas pisania kodu języka C lub C++ Użyj punktów przerwania, aby zatrzymać kod, więc można zbadać wartości adresów (poszukaj NULL) oraz liczby odwołań podczas debugowania dla błędów związanych z pamięcią.  

 Aby uzyskać więcej informacji na temat używania punktów przerwania, przeczytaj [przy użyciu punktów przerwania](../debugger/using-breakpoints.md)  

### <a name="setting-conditional-breakpoints"></a>Ustawienie warunkowe punkty przerwania  
 Jeśli masz punkt przerwania w pętli lub rekursji lub jeśli masz wiele punktów przerwania, które często krokowo, umożliwia upewnij się, że kod jest wstrzymana, tylko wtedy, gdy są spełnione określone warunki warunkowych punktów przerwania. W przeciwnym razie użytkownik będzie można naciśnięcie klawisza F11 awful partii.  

 Aby ustawić warunkowe punktu przerwania i zawiesić kodu, gdy zmienna ma ustawioną wartość lub przekazuje pewnej wartości progowej, kliknij na marginesie, aby ustawić punkt przerwania, a następnie wybierz "koło zębate" wyświetlonym menu aktywowany.  

 ![Ustawienia punktu przerwania programu Visual Studio](../ide/media/vs_ide_gs_debug_breakpoint_settings.png "Vs_ide_gs_debug_breakpoint_settings")  

 Pojawi się okno dialogowe, które wygląda następująco umożliwiające ustawienie określonych warunków przerwania występuje.  

 ![Visual Studio przerwania warunkowego](../ide/media/vs_ide_gs_debug_breakpoint_conditional.PNG "Vs_ide_gs_debug_breakpoint_conditional")  

 Aby uzyskać więcej szczegółów na temat sposobu zadeklarować wyrażenia używane do oceny warunkowych punktów przerwania, zapoznaj się z wideo Channel9 [obsługi konfiguracji punktu przerwania w programie Visual Studio](http://channel9.msdn.com/Events/Visual-Studio/Connect-event-2014/711).  

### <a name="inspecting-your-code-at-run-time"></a>Sprawdzanie kodu w czasie wykonywania  
 Po kodzie uruchomionych trafienia punktu przerwania i zatrzymanie, można sprawdzić zmiennych i stosy, aby określić, co się dzieje wywołań. Czy wartości w zakresach, które chcesz wyświetlić? Są wykonywane w odpowiedniej kolejności wywołań?  

 ![Visual Studio Uruchom &#45; kontroli wartość czasu](../ide/media/vs_ide_gs_debug_inspect_value.PNG "vs_ide_gs_debug_inspect_value")  

 Umieść kursor nad zmienną do wartości i odwołania, które aktualnie znajdują się w temacie. Jeśli widzisz wartość, która Nieoczekiwane wyrażenie prawdopodobnie usterki w poprzednim lub wywoływania wierszach kodu. Przenieś w górę punktów przerwania lub dodawanie warunków do istniejących punktów przerwania, aby zawęzić wyszukiwanie.  

 Ponadto program Visual Studio Wyświetla okno narzędzia diagnostyczne, w którym można obserwować aplikacji Procesora i wykorzystania pamięci w czasie. Ich używać do wyszukania nieprzewidziane duże obciążenie lub pamięci alokacji Procesora. Używany w połączeniu z **czujki** okno i punktów przerwania, aby określić przyczynę nieoczekiwany duże obciążenie lub Publikuj zasobów.  

 ![Visual Studio narzędzia diagnostyczne okna](../ide/media/vs_ide_gs_debug_diagnostic_tools.PNG "Vs_ide_gs_debug_diagnostic_tools")  

### <a name="running-unit-tests"></a>Przeprowadzanie testów jednostkowych  
 Testy jednostkowe są programami, które wykonuje ścieżki kodu w aplikacji lub usługi. Visual Studio instaluje struktur testowania jednostki firmy Microsoft dla kodu zarządzane i natywne. Do tworzenia testów jednostkowych, uruchom je i raportuje o wynikach tych testów, należy użyć framework testowania jednostki. Testów jednostkowych Uruchom ponownie podczas wprowadzania zmian, aby przetestować czy kodzie nadal działa poprawnie. Korzystając z programu Visual Studio Enterprise edition, można uruchomić testy automatycznie po każdej kompilacji.  

 Aby rozpocząć, przeczytaj [Generowanie testów jednostek dla kodu za pomocą IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md).  

 Aby dowiedzieć się więcej na temat testów jednostkowych w Visual Studio i sposób ich mogą pomóc tworzyć lepsze jakości kodu, przeczytaj [teście jednostkowym](../test/unit-test-basics.md).  

## <a name="see-also"></a>Zobacz też  
 [Przegląd funkcji debugera](../debugger/debugger-feature-tour.md)   
 [Ustawienia debugowania i przygotowanie](../debugger/debugger-settings-and-preparation.md)   
 [Debugowanie aplikacji 64-bitowych](../debugger/debug-64-bit-applications.md)   
 [Podstawowe informacje o debugerze](../debugger/debugger-basics.md)
