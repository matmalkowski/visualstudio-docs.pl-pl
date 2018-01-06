---
title: "Kontrolować wykonywanie aplikacji platformy uniwersalnej systemu Windows podczas sesji debugowania programu Visual Studio (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 60159535-61ec-466a-a4a6-115ec72a8af5
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: uwp
ms.openlocfilehash: 1e1e30400a630c7a5b01438e521b651f25ab3137
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="control-execution-of-a-uwp-app-in-a-visual-studio-debug-session-javascript"></a>Wykonanie kontroli aplikacji platformy uniwersalnej systemu Windows podczas sesji debugowania programu Visual Studio (JavaScript)
To szybki start pokazano, jak przechodzić w debugerze programu Visual Studio i sposób wyświetlania stanu programu w sesji.  
  
 Jest to szybki start dla deweloperów, którzy są nowe debugowania w programie Visual Studio i dla deweloperów, którzy chcą się dowiedzieć się więcej o nawigacji w programie Visual Studio sesji debugowania. Nie uczy grafikę sam debugowania. Funkcje w przykładowym kodzie są przeznaczone tylko do pokazują debugowania procedury opisane w tym temacie. Funkcje nie stosować najlepsze rozwiązania projekt aplikacji lub funkcji. W rzeczywistości szybko spowoduje odnalezienie czy funkcje i aplikacja, nie zostanie większość niczego w ogóle.  
  
 Sekcje to szybki start zostały zaprojektowane jako jako niezależny, jak to możliwe, można pominąć dowolną sekcję zawierającą informacje, które znasz już. Również nie są wymagane do tworzenia przykładowej aplikacji. Jednak zaleca go i zostały wykonane, wystarczy procesu.  
  
 **Debuger skrótów klawiaturowych.** Nawigacja w debugerze programu Visual Studio jest zoptymalizowany myszy i klawiatury. Klawisz skrótu lub skrótu klawiaturowego wiele kroków w tym temacie zawiera w nawiasach uwagi. Na przykład (klawiatury: F5) wskazuje, wpisując klawisza F5 uruchamia lub kontynuuje wykonywanie debugera.  
  
> [!NOTE]
>  **Wzorzec modułu**  
>   
>  Aplikacji platformy uniwersalnej systemu Windows często używają JavaScript *wzorzec modułu* celu hermetyzacji danych i funkcji na stronie. Wzorzec modułu używa zamknięcia pojedynczego własnym wykonywania i anonimowe być oddzielone od globalnej przestrzeni nazw funkcji strony. W tym temacie nazywamy funkcji *modułu*.  
  
## <a name="in-this-topic"></a>W tym temacie:  
 Aby dowiedzieć się jak:  
  
 [Tworzenie przykładowej aplikacji](#BKMK_Create_the_sample_app)  
  
 [Ustaw i uruchom do punktu przerwania Wkrocz do funkcji, sprawdź dane programu](#BKMK_Set_and_run_to_a_breakpoint__step_into_a_function__and_examine_program_data)  
  
 [Krok do, za pośrednictwem i z funkcji](#BKMK_Step_into__over__and_out_of_functions)  
  
 [Ustaw punkt przerwania warunkowego, uruchom do kursora i wizualizacji zmiennej](#BKMK_Set_a_conditional_breakpoint__run_to_the_cursor__and_visualize_a_variable)  
  
 [Widok danych zmiennej w oknie zmienne lokalne](#BKMK_View_variable_data_in_the_Locals_window)  
  
-   [Wyświetlanie danych zmiennej i łańcuch prototypu obiektu](#BKMK_View_variable_data_and_the_prototype_chain_of_an_object)  
  
-   [Sprawdź dane łańcucha zakresu](#BKMK_Examine_scope_chain_data)  
  
 [Przechodzenie do kodu przy użyciu okna stosu wywołań](#BKMK_Navigate_to_code_by_using_the_Call_Stack_window)  
  
##  <a name="BKMK_Create_the_sample_app"></a>Tworzenie przykładowej aplikacji  
 Debugowanie jest dotyczące kodu, więc Przykładowa aplikacja używa framework aplikacji platformy uniwersalnej systemu Windows tylko w celu utworzenia pliku źródłowego, w którym widać, jak działa nawigowanie po sesji debugowania i jak zbadać stan programu. Cały kod, które zostaną wywołane jest wywoływana z `module` funkcja pliku default.js kod. Żadne formanty nie są dodawane i zdarzenia nie są obsługiwane.  
  
1.  **Utwórz pustą aplikację platformy uniwersalnej systemu Windows JavaScript.** Otwórz program Visual Studio. Na stronie głównej wybierz **nowy projekt** łącza. Na **nowy projekt** oknie dialogowym wybierz **JavaScript** w **zainstalowana** listy, a następnie wybierz pozycję **uniwersalnych systemu Windows**. Na liście szablony projektów, wybierz **pusta aplikacja (uniwersalna systemu Windows)**. Visual Studio tworzy nowe rozwiązanie i projektu i wyświetla pliku default.htm w edytorze kodu.  
  
     Należy pamiętać, pliki skryptów, które są ładowane do strony.  
  
    -   `base.js` i `ui.js` utworzyć pliki **biblioteka systemu Windows dla języka JavaScript**. Biblioteka systemu Windows dla języka JavaScript jest zestawem JavaScript i plików CSS, które ułatwiają tworzenie aplikacji platformy uniwersalnej systemu Windows przy użyciu języka JavaScript. Można go użyć HTML, CSS i środowiska wykonawczego systemu Windows do utworzenia aplikacji.  
  
    -   Kod uruchamiany w `default.js` pliku.  
  
2.  **Otwórz plik źródłowy default.js.** W Eksploratorze rozwiązań Otwórz **js** węzeł i wybierz polecenie `default.js`.  
  
3.  **Zamień zawartość strony przykładowy kod.** Usuń całą zawartość z `default.js` pliku. Tego łącza: [debugera nawigacji przykładowy kod (JavaScript)](https://github.com/MicrosoftDocs/visualstudio-docs/raw/master/docs/debugger/samples/debugger-navigation-sample-code-javascript.js), a następnie skopiuj kod przedstawiony w sekcji JavaScript do Schowka. (Wybierz **ponownie** w przeglądarce lub podglądu pomocy, aby powrócić do tej strony szybki start.) W edytorze programu Visual Studio, Wklej kod do pustych teraz `default.js`. Wybierz **Ctrl + S** można zapisać pliku.  
  
 Teraz można wykonać wraz z przykładami w tym temacie.  
  
##  <a name="BKMK_Set_and_run_to_a_breakpoint__step_into_a_function__and_examine_program_data"></a>Ustaw i uruchom do punktu przerwania Wkrocz do funkcji, sprawdź dane programu  
 Najbardziej typowe sposób, aby rozpocząć sesję debugowania jest wybranie **Rozpocznij debugowanie** z **debugowania** menu (klawiatury: F5). Aplikacja rozpoczyna się i kontynuuje wykonywanie do momentu osiągnięciu punktu przerwania, możesz ręcznie Wstrzymaj wykonywanie, wystąpi wyjątek, lub kończy się aplikacja.  
  
 Podczas wykonywania jest wstrzymana w debugerze, można wyświetlić wartość zmiennej active w etykietce danych przez umieszczenie wskaźnika myszy na zmiennej.  
  
 Po wstrzymaniu wykonywania aplikacji (nazywane również przerwanie w debugerze), możesz kontrolować sposób, który wykonuje pozostałej części kodu programu. Przenoszenie z wywołania funkcji do funkcji, można kontynuować wiersz po wierszu lub wywoływana funkcja może zostać uruchomiony w ramach jednego kroku. Te procedury są nazywane krokowe wykonywanie aplikacji. Można również wznowić wykonywania standardowych aplikacji systemem na następny punkt przerwania ustawiony lub do wiersza, w którym znajduje się kursor. Można zatrzymać sesji debugowania w dowolnym momencie. Debuger jest przeznaczona do wykonania niezbędnych operacji oczyszczania i zakończyć wykonywanie.  
  
###  <a name="BKMK_Example_1"></a>Przykład 1  
 W tym przykładzie należy ustawić punkt przerwania w treści `module` działać w `default.js` jako wywołuje pierwszej instrukcji naszych użytkowników. Następnie krok do funkcji, wyświetlanie wartości zmiennych w poradach dotyczących debugera, a następnie zatrzymać debugowanie.  
  
1.  **Ustaw punkt przerwania.** Ustaw punkt przerwania w instrukcji `callTrack = "module function";` występuje bezpośrednio po wywołaniu `app.start()`. Wybierz wiersz w przyciemnione odstępu edytora kodu źródłowego (klawiatury: Umieść kursor w wierszu i wybierz polecenie **F9** klucza).  
  
     ![Ustaw punkt przerwania w example1](../debugger/media/dbg_jsnav_example1_breakpoint.png "DBG_JSNAV_example1_breakpoint")  
  
     Ikona punktu przerwania jest wyświetlana w odstępu.  
  
2.  **Uruchom do punktu przerwania.** Uruchom sesję debugowania, wybierając **Rozpocznij debugowanie** na **debugowania** menu (klawiatury: F5).  
  
     Aplikacja rozpoczyna wykonywanie i wstrzymuje wykonywanie bezpośrednio przed instrukcji, w którym można ustawić punktu przerwania. Bieżąca ikona wiersza w odstępu identyfikuje Twojej lokalizacji i zostanie wyróżniona bieżącej instrukcji.  
  
     ![Uruchom do punktu przerwania](../debugger/media/dbg_jsnav_example1_run_to_breakpoint.png "DBG_JSNAV_example1_run_to_breakpoint")  
  
     Kontrola wykonywania aplikacji jest teraz i można sprawdzić stan programu, jak krok za pomocą instrukcji programu.  
  
3.  **Krok do funkcji.** Na **debugowania** menu, wybierz **Step Into** (klawiatury: **F11**).  
  
     ![Wkrocz do wiersza kodu](../debugger/media/dbg_jsnav_example1_step_into.png "DBG_JSNAV_example1_step_into")  
  
     Należy pamiętać, że debuger przechodzi do następnego wiersza, który jest wywołanie `example1` funkcji. Wybierz **Step Into** ponownie. Przejście do pierwszego wiersza kodu debugera `example1` funkcji. Wyróżniony wiersz nie zostało wykonane, ale funkcja został załadowany w stosie wywołań i przydzielonej pamięci dla zmiennych lokalnych.  
  
4.  Debuger Wkrocz wiersz kodu, wykonuje jeden z następujących czynności:  
  
    -   Następna instrukcja nie jest wywołanie funkcji w rozwiązaniu, debuger wykonuje instrukcję, przechodzi do następnej instrukcji, a następnie wstrzymuje wykonywanie.  
  
    -   Jeśli instrukcja jest wywołanie funkcji w rozwiązaniu, debuger przenosi do pierwszego wiersza wywołana funkcja, a następnie wstrzymuje wykonywanie.  
  
     Przejdź do kroku do raportów o `example1` dopóki został osiągnięty punkt wyjścia. Debuger prezentuje zamykający nawias klamrowy funkcji.  
  
5.  **Wyświetlanie wartości zmiennych w etykietek danych.** Przejdź do kroku do raportów o `example1` dopóki został osiągnięty punkt wyjścia. Debuger prezentuje zamykający nawias klamrowy funkcji. W przypadku wstrzymania myszy na nazwę zmiennej, nazwę i wartość zmiennej są wyświetlane w etykietki danych.  
  
     ![Wyświetlanie wartości zmiennych w etykietce danych](../debugger/media/dbg_jsnav_data_tip.png "DBG_JSNAV_data_tip")  
  
6.  **Dodawanie watch zmiennej callTrack.** `callTrack` Zmienna jest używana w tym szybki start do wyświetlenia funkcji o nazwie w przykładach. Aby ułatwić wyświetlić wartość zmiennej, należy go dodać do okna czujki. Wybierz nazwę zmiennej w edytorze, a następnie wybierz pozycję **Dodaj wyrażenie kontrolne** z menu skrótów.  
  
     ![Obejrzyj zmiennej](../debugger/media/dbg_jsnav_watch_window.png "DBG_JSNAV_watch_window")  
  
     Możesz obserwować wiele zmiennych w okno czujki. Wartości zmiennych monitorowane, takie jak wartości w systemie windows Porada danych są aktualizowane przy każdym wykonanie jest wstrzymana. Monitorowane zmiennych są zapisywane w sesji debugowania.  
  
7.  **Zatrzymaj debugowanie.** Na **debugowania** menu, wybierz **Zatrzymaj debugowanie** (klawiatury: **Shift + F5**). To kończy się sesja debugowania.  
  
##  <a name="BKMK_Step_into__over__and_out_of_functions"></a>Krok do, za pośrednictwem i z funkcji  
 W przeciwieństwie do Wkraczanie do funkcji wywoływanych przez funkcję nadrzędnej, pominięcie funkcję wykonuje funkcji podrzędnych i następnie wstrzymuje wykonywanie w funkcji wywołującej jako wznawia nadrzędnego. Może być Przekrocz nad funkcję, po zapoznaniu się z sposób funkcja działa i pewności, że jego wykonanie nie wpłynie na ten problem, który rozpatrujesz.  
  
 Pominięcie wiersza kodu, który nie zawiera wywołanie funkcji wykonuje wiersza, podobnie jak wykonywanie krok po kroku, w wierszu.  
  
 Krokowe wykonywanie funkcji podrzędnych kontynuuje wykonywanie funkcji, a następnie wstrzymuje wykonywanie po funkcja zwraca jego wywołania funkcji. Może wychodzenia z długo funkcja, gdy określono rest funkcji nie jest znacząca.  
  
 Pominięcie, a także wykonywanie krok po kroku, poza funkcją wykonywania funkcji.  
  
 ![Krok do, za pośrednictwem i z metody](../debugger/media/dbg_basics_stepintooverout.png "DBG_Basics_StepIntoOverOut")  
  
###  <a name="BKMK_Example_2"></a>Przykład 2  
 W tym przykładzie kroku do, za pośrednictwem i z funkcji.  
  
1.  **Wywołanie funkcji przykład2 w funkcji modułu.** Edytuj `module` funkcji i Zastąp następujący wiersz `var callTrack = "module function"` z `example2();`.  
  
     ![Wywołanie funkcji przykład2](../debugger/media/dbg_jsnav_example2.png "DBG_JSNAV_example2")  
  
2.  **Uruchom do punktu przerwania.** Uruchom sesję debugowania, wybierając **Rozpocznij debugowanie** na **debugowania** menu (klawiatury: F5). Debuger wstrzymuje wykonywanie na punkt przerwania.  
  
3.  **Przekrocz nad wiersz kodu.** Na **debugowania** menu, wybierz **Step Over** (klawiatury: F10). Wykonuje debuger `var callTrack = "module function"` instrukcji w taki sam sposób jak wykonywanie krok po kroku w instrukcji.  
  
4.  **Wkrocz przykład2 i example2_a.** Wybierz **F11** klucza Wkrocz do `example2` funkcji. Przejdź do kroku do `example2` instrukcje, aż zostanie wyświetlony wiersz `var x = example2_a();`. Ponownie wkroczyć do tego wiersza, aby przejść do punktu wejścia `example2_a`. Przejdź do kroku w każdej instrukcji z `example2_a` aby powrócić do `example2`.  
  
     ![Przekrocz nad funkcji](../debugger/media/dbg_jsnav_example2_a.png "DBG_JSNAV_example2_a")  
  
5.  **Przekrocz nad funkcji.** Należy pamiętać, że następnego wiersza w `example2`, `var y = example2_a();` jest zasadniczo taki sam jak w poprzednim wierszu. Można bezpiecznie przejść za pośrednictwem tego wiersza. Wybierz **F10** klawisz, aby przejść z wznowienie `example2` do tego drugie wywołanie `example2_a`. Należy pamiętać, że `callTrack` ciąg wskazuje `example2_a` funkcja wykonano dwa razy.  
  
6.  **Wychodzenia z funkcją.** Wybierz **F11** klucza Wkrocz do `example2_b` funkcji. Należy pamiętać, że `example2_b` nie jest bardzo różnią się od `example2_a`. Do wychodzenia z funkcji, wybierz **Wyjdź** na **debugowania** menu (klawiatury: **Shift + F11**). Należy pamiętać, że `callTrack` zmienna oznacza to, że `example2_b` zostało wykonane i zwróconą przez debuger do punktu gdzie `example2` wznawia.  
  
7.  **Zatrzymaj debugowanie.** Na **debugowania** menu, wybierz **Zatrzymaj debugowanie** (klawiatury: **Shift + F5**). To kończy się sesja debugowania.  
  
##  <a name="BKMK_Set_a_conditional_breakpoint__run_to_the_cursor__and_visualize_a_variable"></a>Ustaw punkt przerwania warunkowego, uruchom do kursora i wizualizacji zmiennej  
 Punkt przerwania warunkowego określa warunek, który powoduje, że debuger wstrzymania wykonywania. Warunek jest określona przez dowolne wyrażenie kodu, które może przyjąć wartość PRAWDA lub FAŁSZ. Na przykład można użyć do sprawdzenia stanu programu w często wywołana funkcja tylko wtedy, gdy zmienna osiągnie wartość warunkowych punktów przerwania.  
  
 Uruchamianie do kursora przypomina ustawienie jednorazowe punktu przerwania. Podczas wykonywania jest wstrzymana, można wybrać wiersz w źródle i wznowić wykonywanie do momentu osiągnięcia wybranego wiersza. Na przykład może być krokowe wykonywanie pętli w funkcji i ustalić, czy kod w pętli działa poprawnie. Zamiast krokowe każdej iteracji pętli, możesz uruchomić kursor, który znajduje się po wykonaniu pętli.  
  
 Czasami trudno jest wyświetlanie wartości zmiennej w wierszu etykietki danych lub inne okno danych. Debuger można wyświetlić ciągów, HTML i Xml w narzędzia text visualizer prezentuje sformatowany Wyświetl wartości w oknie przewijanego.  
  
###  <a name="BKMK_Example_3"></a>Przykład 3  
 W tym przykładzie należy ustawić warunkowe punkt przerwania dzielone w określonych iteracji pętli, a następnie uruchom do kursora, który znajduje się po pętli. Możesz również wyświetlić wartość zmiennej w narzędzia text visualizer.  
  
1.  **Wywołanie funkcji example3 w funkcji modułu.** Edytuj `module` funkcji i Zastąp następujący wiersz `var callTrack = "module function";` z linią `example3();`.  
  
     ![Wywołanie example3](../debugger/media/dbg_jsnav_example3.png "DBG_JSNAV_example3")  
  
2.  **Uruchom do punktu przerwania.** Uruchom sesję debugowania, wybierając **Rozpocznij debugowanie** na **debugowania** menu (klawiatury: **F5**). Debuger wstrzymuje wykonywanie na punkt przerwania w `module` funkcji.  
  
3.  **Krok do funkcji example3.** Wybierz **Step Into** na **debugowania** menu (klawiatury: **F11**) można przenieść do punktu wejścia `example3` funkcji. Kontynuować wykonywanie krok po kroku do funkcji dopóki ma iterowane jednego lub dwóch pętli `for` bloku. Należy pamiętać, że może upłynąć możesz długi czas do wykonania kroków opisanych wszystkich iteracji 1000.  
  
4.  **Ustaw punkt przerwania warunkowego.** W lewym odstępu okna kodu, kliknij prawym przyciskiem myszy linię `s += i.toString() + "\n";` , a następnie wybierz **warunku** menu skrótów.  
  
     Wybierz **warunku** pole wyboru, a następnie wpisz `i == 500;` w polu tekstowym. Wybierz **ma wartość true** opcję i wybierz polecenie **OK**. Punkt przerwania umożliwia sprawdzanie wartość iteracji 500th `for` pętli. Ikona warunkowych punktów przerwania można zidentyfikować przy jego między białym znakiem.  
  
     ![Ikona punktu przerwania blokada](../debugger/media/dbg_jsnav_breakpoint_condition_icon.png "DBG_JSNAV_Breakpoint_Condition_icon")  
  
5.  **Uruchom do punktu przerwania.** Na **debugowania** menu, wybierz **Kontynuuj** (klawiatury: **F5**). Zatrzymaj się na `i` potwierdzić, że bieżąca wartość `i` wynosi 500. Należy również zauważyć, że zmienna `s` jest reprezentowany jako pojedynczy wiersz i jest znacznie większa od okna Porada danych.  
  
6.  **Wizualizuj zmienna typu ciąg.** Kliknij ikonę lupy w danych końca `s`.  
  
     Zostanie wyświetlone okno narzędzia Text Visualizer, a wartość ciągu jest udostępniana jako ciąg wiele wierszy.  
  
     ![Debugowanie narzędzia text visualizer](../debugger/media/dbg_jsnav_text_visualizer.png "DBG_JSNAV_Text_Visualizer")  
  
7.  **Uruchom do kursora.** Wybierz wiersz `callTrack += "->example3";` , a następnie wybierz **Uruchom do kursora** menu skrótów (klawiatury: **Ctrl + F10**). Debuger kończy iteracji pętli, a następnie wstrzymuje wykonywanie w wierszu.  
  
8.  **Zatrzymaj debugowanie.** Na **debugowania** menu, wybierz **Zatrzymaj debugowanie** (klawiatury: **Shift + F5**). To kończy się sesja debugowania.  
  
###  <a name="BKMK_Use_Run_to_Cursor_to_return_to_your_code_and_delete_a_breakpoint"></a>Używaj polecenia do kursora, aby powrócić do kodu i usunąć punkt przerwania  
 Uruchamianie do kursora może być bardzo przydatne, gdy mają przeprowadził do biblioteki kodu od firmy Microsoft lub innych firm. Krokowe wykonywanie kodu biblioteki mogą być informacyjny, często może potrwać długo. I zwykle znacznie bardziej planuje w swoim własnym kodem. Tego ćwiczenia pokazuje, jak to zrobić.  
  
1.  **Ustaw punkt przerwania w wywołaniu app.start.** W `module` funkcji, należy ustawić punkt przerwania w wierszu`app.start()`  
  
2.  **Uruchom do punktu przerwania, a następnie do funkcji biblioteki.**  
  
     Jeśli krok do `app.start()`, Edytor wyświetla kod w `base.js`. Krok na kilka więcej wierszy.  
  
3.  **Krok w i poza funkcji.** Jak Przekrocz nad (**F10**) i kroku poza (**SHIFT + F11**) kodu w `base.js`, można trafić do wniosku, sprawdzając złożoność i długość funkcja start jest nieodpowiednia do realizacji.  
  
4.  **Ustaw kursor w kodzie i uruchom, aby go.** Przywraca `default.js` plik w edytorze kodu. Wybierz pierwszy wiersz kodu po `app.start()` (nie można uruchomić komentarz lub pusty wiersz). Wybierz **Uruchom do kursora** z menu skrótów. Debuger kontynuuje wykonywanie funkcji app.start i wstrzymuje wykonywanie na punkt przerwania.  
  
##  <a name="BKMK_View_variable_data_in_the_Locals_window"></a>Widok danych zmiennej w oknie zmienne lokalne  
 Zmienne lokalne systemu windows jest parametrów i zmiennych w łańcuchu zakres funkcji aktualnie wykonywane w widoku drzewa.  
  
###  <a name="BKMK_View_variable_data_and_the_prototype_chain_of_an_object"></a>Wyświetlanie danych zmiennej i łańcuch prototypu obiektu  
  
1.  **Dodaj obiekt array funkcji modułu.** Edytuj `module` funkcji i Zastąp następujący wiersz `var callTrack = "module function"` z`var myArray = new Array(1, 2, 3);`  
  
     ![Definicja myArray](../debugger/media/dbg_jsnav_myarray.png "DBG_JSNAV_myArray")  
  
2.  **Uruchom do punktu przerwania.** Uruchom sesję debugowania, wybierając **Rozpocznij debugowanie** na **debugowania** menu (klawiatury: **F5**). Debuger wstrzymuje wykonywanie na punkt przerwania. Wkrocz do wiersza.  
  
3.  **Otwórz okno zmiennych lokalnych.** Na **debugowania** menu wskaż **Windows**, a następnie wybierz pozycję **zmiennych lokalnych**. (Klawiatury: Alt + 4).  
  
4.  **Sprawdź zmienne lokalne w funkcji modułu** windows zmienne lokalne są wyświetlane zmienne aktualnie wykonywane funkcji ( `module` funkcji) jako najwyższego poziomu węzły drzewa. Po wprowadzeniu funkcji JavaScript tworzy wszystkie zmienne i przekazuje im wartości `undefined`. Funkcje, które są zdefiniowane w funkcji ma ich tekstu jako wartość.  
  
     ![Okno zmiennych lokalnych](../debugger/media/dbg_jsnav_locals_window.png "DBG_JSNAV_Locals_window")  
  
5.  **Przejrzyj kroki definicje callTrack i myArray.** Znajdź zmienne callTrack i myArray w oknie zmienne lokalne. Przekrocz nad (**F10**) dwie definicje i zwróć uwagę, że **wartość** i **typu** pola są zmieniane. Okno zmiennych lokalnych wyróżniono wartości zmiennych, które uległy zmianie od czasu ostatniej przerwy.  
  
6.  **Badają obiekt myArray** rozwiń `myArray` zmiennej. Każdy element tablicy jest wymieniony **[prototypu]** węzła, który zawiera hierarchię dziedziczenia `Array` obiektu. Rozwiń ten węzeł.  
  
     ![Łańcuch prototypów w oknie zmienne lokalne](../debugger/media/dbg_jsnav_locals_proto_chain.png "DBG_JSNAV_Locals_proto_chain")  
  
    -   **Metody** węzeł zawiera wszystkie metody `Array` obiektu.  
  
    -   **[Prototypu]** węzeł zawiera prototyp `Object` obiektu, z którego `Array` pochodzi. **[prototypu]**  węzłów może mieć wartość recursive. Każdy obiekt nadrzędny w hierarchii obiektów jest opisany w **[prototypu]** węzła jego elementu podrzędnego.  
  
7.  **Zatrzymaj debugowanie.** Na **debugowania** menu, wybierz **Zatrzymaj debugowanie** (klawiatury: Shift + F5). To kończy się sesja debugowania.  
  
##  <a name="BKMK_Examine_scope_chain_data"></a>Sprawdź dane łańcucha zakresu  
 *Zakres łańcucha* funkcji obejmuje wszystkie zmienne, które są aktywne i osiągalny przez funkcję. Zmienne globalne są częścią łańcucha zakresu są wszystkie obiekty (w tym funkcji), zdefiniowane w funkcji, która definiuje funkcję aktualnie wykonywane. Na przykład `callTrack` zmiennej, która jest zdefiniowana w `module` funkcji `default.js` jest dostępny za pomocą dowolnej funkcji, która jest zdefiniowana w `module` funkcji. Każdego zakresu jest wyświetlany osobno w oknie zmienne lokalne.  
  
-   Zmienne funkcja aktualnie wykonywane są wyświetlane w górnej części okna.  
  
-   Zmienne każdego zakresu funkcji w łańcuchu w zakresie są wyświetlane w obszarze **[zakres]** węzła dla funkcji. Zasięg funkcje są wyświetlane według ich kolejności w łańcuchu z funkcji, który definiuje bieżącej funkcji najbardziej zewnętrzną funkcję łańcucha.  
  
-   **[Globals]** węzła listy obiektów globalnych, zdefiniowanych poza żadnych funkcji.  
  
 Zakres łańcuchów może być trudne i najlepiej przedstawiono w przykładzie. W poniższym przykładzie widać, jak `module` funkcja tworzy własny zakres i sposób tworzenia innego poziomu zakresu przez utworzenie zamknięcia.  
  
###  <a name="BKMK_Example_4"></a>Przykład 4  
  
1.  **Wywołanie funkcji example4 z funkcji modułu.** Edytuj `module` funkcji i Zastąp następujący wiersz `var callTrack = "module function"` z `example4()`:  
  
     ![Wywołanie example4](../debugger/media/dbg_jsnav_example4.png "DBG_JSNAV_example4")  
  
2.  **Uruchom do punktu przerwania.** Uruchom sesję debugowania, wybierając **Rozpocznij debugowanie** na **debugowania** menu (klawiatury: **F5**). Debuger wstrzymuje wykonywanie na punkt przerwania.  
  
3.  **Otwórz okno zmiennych lokalnych.** W razie potrzeby na **debugowania** menu wskaż **Windows**, a następnie wybierz pozycję **zmiennych lokalnych**. (Klawiatury: **Alt + 4**). Należy pamiętać, że okno wyświetla listę wszystkich zmiennych i funkcji w `module` działać, a także zawiera **[Globals]** węzła.  
  
4.  **Sprawdź, czy zmienne globalne.** Rozwiń węzeł **[Globals]** węzła. Obiekty i zmienne globalne zostały określone przez bibliotekę systemu Windows dla języka JavaScript. Własne zmienne można dodawać do globalnego zakresu.  
  
5.  **Wkrocz example4 i sprawdź jej lokalnego oraz zakres zmienne** Wkrocz (klawiatury: **F11**) `example4` funkcji. Ponieważ `example4` jest zdefiniowany w `module` funkcji `module` funkcji staje się w zakresie nadrzędnym. `example4`mogą wywoływać funkcje w `module` działać, a dostęp do jego zmiennych. Rozwiń węzeł **[zakres]** węzeł w oknie zmienne lokalne i należy pamiętać, że zawiera takie same i zmienne `module` funkcji.  
  
     ![Zakresy metody example4](../debugger/media/dbg_jsnav_locals_example4_scope.png "DBG_JSNAV_Locals_example4_scope")  
  
6.  **Wkrocz example4_a i sprawdź jej lokalnego oraz zakres zmienne** przejdź do kroku do `example4` i w wywołaniu `example4_a`. Należy pamiętać, że zmienne lokalne są teraz z `example4_a`oraz że **[zakres]** węzła nadal zmienne `module` funkcji. Mimo że zmienne `example4` są aktywne, nie może być osiągnięta poprzez `example4_a` i nie są już częścią łańcucha zakresu.  
  
7.  **Wkrocz multipyByA i sprawdź jej lokalnego oraz zakres zmienne** kroków reszty `example4_a` i do wiersza `var x = multilpyByA(b);`.  
  
     Zmienna funkcji `multipyByA` została ustawiona jako `multiplyClosure` funkcja, która jest *zamknięcia*. `multipyClosure`definiuje i zwraca funkcję wewnętrzny `mulitplyXby`i przechwytywanie (zamyka za pośrednictwem) jego parametrów i zmiennych. W zamknięcia zwracane funkcja wewnętrzna ma dostęp do danych zewnętrznych funkcji i dlatego tworzy poziomu zakresu.  
  
     Gdy wkroczyć do `var x = multilpyByA(b);`, Przenieś do `return a * b;` wiersz w `mulitplyXby` funkcji wewnętrznej.  
  
8.  W oknie zmienne lokalne tylko parametr `b` jest wymienione jako zmienną lokalną w `multiplyXby`, ale nowy **[zakres]** poziomie został dodany. Rozwinięcie tego węzła, zobaczysz, że zawiera parametry, funkcje i zmienne `multiplyClosure`, takie jak `a` zmiennej o nazwie w pierwszym wierszu `multiplyXby`. Szybkie sprawdzenie drugiego **[zakres]** węzła ujawnia zmiennych funkcji modułu, którego `multiplyXby` uzyskuje dostęp do jego następnego wiersza.  
  
     ![Zakresy zamknięcia w oknie zmienne lokalne](../debugger/media/dbg_jsnav_scope_mulitplyxby.png "DBG_JSNAV_scope_mulitplyXby")  
  
9. **Zatrzymaj debugowanie.** Na **debugowania** menu, wybierz **Zatrzymaj debugowanie** (klawiatury: **Shift + F5**). To kończy się sesja debugowania.  
  
##  <a name="BKMK_Navigate_to_code_by_using_the_Call_Stack_window"></a>Przechodzenie do kodu przy użyciu okna stosu wywołań  
 Stos wywołań jest strukturą danych, który zawiera informacje na temat funkcji, które są wykonywane w bieżącym wątku aplikacji. Po trafieniu punktu przerwania, stos wywołań okna wyświetla listę wszystkich funkcji, które są aktywne na stosie. Funkcja aktualnie wykonywane jest na początku listy okna stosu wywołań. Funkcję, która inicjuje wątek jest w dolnej części listy. Funkcje między Pokaż ścieżkę wywołania z funkcji inicjujący do bieżącej funkcji.  
  
 Oprócz przedstawiający ścieżki wywołanie funkcji aktualnie wykonywane, stos wywołań okna można nawigować do kodu w edytorze kodu. Ta funkcja może być przydatny podczas pracy z wieloma plikami i chcesz szybko przejść do danej funkcji.  
  
###  <a name="BKMK_Example_5"></a>Przykład 5  
 W tym przykładzie krok na ścieżkę wywołania, który zawiera pięć funkcje zdefiniowane przez użytkownika.  
  
1.  **Wywołanie funkcji example5 w funkcji modułu.** Edytuj `module` funkcji i Zastąp następujący wiersz `var callTrack = "module function";` z linią `example5();`.  
  
     ![Wywołanie example5](../debugger/media/dbg_jsnav_example5.png "DBG_JSNAV_example5")  
  
2.  **Uruchom do punktu przerwania.** Uruchom sesję debugowania, wybierając **Rozpocznij debugowanie** na **debugowania** menu (klawiatury: **F5**). Debuger wstrzymuje wykonywanie na punkt przerwania w funkcji modułu.  
  
3.  **Otwórz okno stos wywołań.** Na **debugowania** menu, wybierz **Windows**, a następnie wybierz pozycję **stos wywołań** (klawiatury: Alt + 7). Należy pamiętać, że stos wywołań okna zawiera dwie funkcje:  
  
    -   **Kod globalny** jest punkt wejścia `module` funkcji w dolnej części stosu wywołań.  
  
    -   **Funkcja anonimowa** zawiera wiersz w `module` funkcja, której wykonywanie jest wstrzymana. Jest to ze szczytu stosu wywołań.  
  
4.  **Krok do funkcji w celu osiągnięcia funkcja example5_d.** Wybierz **Step Into** na **debugowania** menu (klawiatury: **F11**) do wykonywania wywołań w ścieżce wywołanie, aż do punktu wejścia funkcji example5_d. Należy pamiętać, że zawsze czy funkcja wywołuje funkcję, numer wiersza funkcji wywołującej jest zapisywana i wywołana funkcja znajduje się na szczycie stosu. Numer wiersza funkcji wywołującej jest punktem jaką funkcji wywołującej wstrzymał wykonywania. Żółta strzałka wskazuje funkcja aktualnie wykonywane.  
  
     ![Stos wywołań, okno](../debugger/media/dbg_jsnav_callstack_windows.png "DBG_JSNAV_CallStack_windows")  
  
5.  **Korzystanie z okna stosu wywołań można nawigować do kodu example5_a i ustaw punkt przerwania.** W oknie stos wywołań, wybierz `example5_a` elementu listy, a następnie wybierz pozycję **przejdź do źródła** menu skrótów. Edytor kodu ustawia jego kursor w wierszu zwrotny funkcji. Ustaw punkt przerwania w tym wierszu. Uwaga bieżącego wiersza wykonywania nie ulega zmianie. Gdy kursor edytora zostały przeniesione.  
  
6.  **Krok do funkcji, a następnie uruchom do punktu przerwania.** Kontynuuj wykonywanie krok po kroku do `example5_d`. Należy pamiętać, że po powrocie z funkcji jest traktowana stosu wywołań. Naciśnij klawisz **F5** do kontynuowania wykonywania programu. Można zatrzymać na punkt przerwania utworzony w poprzednim kroku.  
  
7.  **Zatrzymaj debugowanie.** Na **debugowania** menu, wybierz **Zatrzymaj debugowanie** (klawiatury: **Shift + F5**). To kończy się sesja debugowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Uruchom sesję debugowania (JavaScript)](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md)   
 [Szybki Start: Debuger nawigacji (JavaScript)](../debugger/control-execution-of-a-store-app-in-a-visual-studio-debug-session-for-windows-store-apps-javascript.md)   
 [Szybki Start: Debugowanie kodu HTML i CSS](../debugger/quickstart-debug-html-and-css.md)   
 [Wyzwalanie wstrzymania, wznowienia i zdarzeń dla aplikacji platformy uniwersalnej systemu Windows w tle)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)   
 [Debugowanie aplikacji w programie Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)
