---
title: Nawigowanie po sesji debugowania w programie Visual Studio (Xaml i C#) | Dokumentacja firmy Microsoft
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
ms.assetid: 1da33203-333f-4a05-b4e2-8d407c497233
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0c69ff648e2a1ac8c60746f1e7879e80c2063c2a
ms.sourcegitcommit: ebe9fb5eda724936f7a059d35d987c29dffdb50d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2017
---
# <a name="navigate-a-debugging-session-in-visual-studio-xaml-and-c"></a>Nawigowanie po sesji debugowania w programie Visual Studio (Xaml i C#)
To szybki start przedstawiono, jak przechodzić sesji debugowania programu Visual Studio oraz do wyświetlania i zmieniania stanu programu w sesji.  
  
 Jest to szybki start dla deweloperów, którzy są nowe debugowania w programie Visual Studio i dla deweloperów, którzy chcą się dowiedzieć się więcej o nawigacji w programie Visual Studio sesji debugowania. Nie uczy grafikę sam debugowania. Metody w przykładowym kodzie mają tylko prezentacja debugowania procedury opisane w tym temacie. Metody nie stosować najlepsze rozwiązania projekt aplikacji lub funkcji. W rzeczywistości możesz szybko zauważyć, że metod i aplikacja, nie zostanie większość niczego na wszystkich.  
  
 Sekcje to szybki start zostały zaprojektowane jako jako niezależny, jak to możliwe, można pominąć dowolną sekcję zawierającą informacje, które znasz już. Również nie jest konieczne tworzenie przykładowej aplikacji; jednak zaleca go i zostały wykonane, wystarczy procesu.  
  
 **Debuger skrótów klawiaturowych.** Visual Studio debugger nawigacji jest zoptymalizowany myszy i klawiatury. Klawisz skrótu lub skrótu klawiaturowego wiele kroków w tym temacie zawiera w nawiasach uwagi. Na przykład (klawiatury: F5) wskazuje, wpisując klawisza F5 uruchamia lub kontynuuje wykonywanie debugera.  
  
## <a name="in-this-topic"></a>W tym temacie:  
 Aby dowiedzieć się jak:  
  
-   [Tworzenie przykładowej aplikacji](#BKMK_CreateTheApplication)  
  
-   [Ustaw i uruchom do punktu przerwania Wkrocz do metody, sprawdź dane programu](#BKMK_StepInto)  
  
-   [Krok do, za pośrednictwem i z metody](#BKMK_StepIntoOverOut)  
  
-   [Ustaw punkt przerwania warunkowego, uruchom do kursora i wizualizacji zmiennej](#BKMK_ConditionCursorVisualize)  
  
-   [Edytuj i Kontynuuj, odzyskanie Wystąpił wyjątek](#BKMK_EditContinueRecoverExceptions)  
  
##  <a name="BKMK_CreateTheApplication"></a>Tworzenie przykładowej aplikacji  
 Debugowanie jest dotyczące kodu, więc Przykładowa aplikacja używa framework aplikacji platformy uniwersalnej systemu Windows tylko w celu utworzenia pliku źródłowego, w którym widać, jak działa nawigowanie po sesji debugowania i jak można sprawdzić i zmienić stan programu. Cały kod, które zostaną wywołane jest wywoływana z konstruktora strony głównej; żadne formanty nie są dodawane i zdarzenia nie są obsługiwane.  
  
 **Tworzenie aplikacji platformy uniwersalnej systemu Windows C# domyślne.** Otwórz program Visual Studio. Na stronie głównej wybierz **nowy projekt** łącza. W oknie dialogowym Nowy projekt wybierz **Visual C#** w **zainstalowana** listy, a następnie wybierz pozycję **uniwersalnych systemu Windows**. Na liście szablony projektów, wybierz **pusta aplikacja (uniwersalna systemu Windows)**. Visual Studio tworzy nowe rozwiązanie i projektu i zostanie wyświetlona projektanta MainPage.xaml i edytora kodu XAML.  
  
 **Otwórz plik źródłowy MainPage.xaml.cs.** Kliknij prawym przyciskiem myszy w edytorze XAML, a następnie wybierz pozycję **kod widoku**. Zostanie wyświetlony plik CodeBehind MainPage.xaml.cs. Należy pamiętać, że tylko jedna metoda `MainPage()` konstruktora, znajduje się w pliku.  
  
 **Zamień Konstruktor MainPage przykładowy kod.** Usuń metodę MainPage(). Tego łącza: [debugera nawigacji przykładowy kod (Xaml i C#)](https://github.com/MicrosoftDocs/visualstudio-docs/raw/master/docs/debugger/samples/debugger-navigation-sample-code-xaml-and-csharp.cs), a następnie skopiuj kod przedstawiony w sekcji C# do Schowka. (Wybierz **ponownie** w przeglądarce lub podglądu pomocy, aby powrócić do tej strony szybki start.) W edytorze programu Visual Studio, Wklej kod w `partial class MainPage` bloku. Wybierz polecenie CTRL + s, aby zapisać plik.  
  
 Teraz można wykonać wraz z przykładami w tym temacie.  
  
##  <a name="BKMK_StepInto"></a>Ustaw i uruchom do punktu przerwania Wkrocz do metody, sprawdź dane programu  
 Najbardziej typowe sposób, że można uruchomić sesję debugowania jest wybranie **Rozpocznij debugowanie** z **debugowania** menu (klawiatury: F5). Wykonanie rozpoczyna się i będzie wykonywany do momentu osiągnięciu punktu przerwania, możesz ręcznie Wstrzymaj wykonywanie, wystąpi wyjątek, lub kończy się aplikacja.  
  
 Podczas wykonywania jest wstrzymana w debugerze, można wyświetlić wartość zmiennej active w etykietce danych, ustawiając kursor myszy nad zmiennej. Można również otworzyć windows zmiennych lokalnych i automatycznych, aby wyświetlić listę aktywnych zmienne i ich wartości. Dodawanie co najmniej jedną zmienną do temu okna czujki można skupić się na wartości zmiennych aplikacji kontynuuje wykonywanie.  
  
 Po wstrzymaniu wykonywania aplikacji (nazywane również przerwanie w debugerze), możesz kontrolować sposób, który jest wykonywany z resztą kodu programu. Można kontynuować wiersz po wierszu przenoszenie po wywołaniu metody, metody lub wywołaną metodę można wykonać w ramach jednego kroku. Te procedury są nazywane krokowe wykonywanie aplikacji. Można również wznowić wykonywania standardowych aplikacji systemem na następny punkt przerwania ustawiony lub do wiersza, w którym znajduje się kursor. Można zatrzymać sesji debugowania w dowolnym momencie. Debuger jest przeznaczona do wykonania niezbędnych operacji oczyszczania i zakończyć wykonywanie.  
  
### <a name="example-1"></a>Przykład 1  
 W tym przykładzie należy ustawić punkt przerwania w Konstruktorze MainPage w pliku MainPage.xaml.cs, Wkrocz pierwsza metoda, wyświetlanie wartości zmiennych i następnie zatrzymać debugowanie.  
  
 **Ustaw punkt przerwania.** Ustaw punkt przerwania w instrukcji `methodTrack = "Main Page";` w Konstruktorze MainPage. Wybierz wiersz w przyciemnione odstępu edytora kodu źródłowego (klawiatury: Umieść kursor w wierszu i wybierz opcję klucz F9).  
  
 ![Wkrocz](../debugger/media/dbg_basics_stepinto.png "DBG_Basics_StepInto")  
  
 Ikona punktu przerwania jest wyświetlana w odstępu.  
  
 **Uruchom do punktu przerwania.** Uruchom sesję debugowania, wybierając **Rozpocznij debugowanie** na **debugowania** menu (klawiatury: F5).  
  
 Aplikacja rozpoczyna wykonywanie i wstrzymuje wykonywanie bezpośrednio przed instrukcji, w którym można ustawić punktu przerwania. Bieżąca ikona wiersza w odstępu identyfikuje Twojej lokalizacji i zostanie wyróżniona bieżącej instrukcji.  
  
 ![Ustaw punkt przerwania](../debugger/media/dbg_basics_setbreakpoint.png "DBG_Basics_SetBreakpoint")  
  
 Kontrola wykonywania aplikacji jest teraz i można sprawdzić stan programu, jak krok za pomocą instrukcji programu.  
  
 **Krok do metody.** Na **debugowania** menu, wybierz **Step Into** (klawiatury: F11).  
  
 ![Bieżący wiersz](../debugger/media/dbg_basics_currentline.png "DBG_Basics_CurrentLine")  
  
 Należy pamiętać, że przejście do następnego wiersza, który jest wywołanie metody Example1 debugera. Ponownie wybrać Step Into. Debuger przenosi do metody Example1 punktu wejścia. Oznacza to, że metoda został załadowany w stosie wywołań i przydzielono pamięci dla zmiennych lokalnych.  
  
 Debuger Wkrocz wiersz kodu, wykonuje jeden z następujących czynności:  
  
-   Następna instrukcja nie jest wywołanie funkcji w rozwiązaniu, debuger wykonuje instrukcję, przechodzi do następnej instrukcji, a następnie wstrzymuje wykonywanie.  
  
-   Jeśli instrukcja jest wywołanie funkcji w rozwiązaniu, debuger przenosi do punktu wejścia funkcji o nazwie i następnie wstrzymuje wykonywanie.  
  
 Przejdź do kroku w instrukcjach example1, dopóki nie został osiągnięty punkt wyjścia. Debuger prezentuje zamykający nawias klamrowy metody.  
  
 **Sprawdź, czy wartości zmiennych w etykietek danych.** Gdy wskaźnik myszy nad nazwę zmiennej, nazwę, wartość oraz typ zmiennej jest wyświetlany w etykietce danych.  
  
 ![Porada danych debugera](../debugger/media/dbg_basics_datatip.png "DBG_Basics_DataTip")  
  
 Umieść kursor myszy nad zmiennej `a`. Należy pamiętać, wpisz nazwę, wartość oraz danych. Umieść kursor myszy nad zmiennej `methodTrack`. Ponownie należy pamiętać, wpisz nazwę, wartość oraz danych.  
  
 **Sprawdź, czy wartości zmiennych w oknie zmienne lokalne.** Na **debugowania** menu wskaż **Windows**, a następnie wybierz pozycję **zmiennych lokalnych**. (Klawiatury: Alt + 4).  
  
 ![Okno zmiennych lokalnych](../debugger/media/dbg_basics_localswindow.png "DBG_Basics_LocalsWindow")  
  
 Zmienne lokalne systemu windows jest widok drzewa parametry i zmienne funkcji. Węzły podrzędne samego obiektu są właściwości zmienna obiektu. `this` Zmienna jest ukryty parametr w każdej metody obiekt reprezentujący samego obiektu. W takim przypadku reprezentuje klasy MainPage. Ponieważ `methodTrack` jest elementem członkowskim typu klasy, jego wartość i dane MainPage są wymienione w wierszu poniżej `this`. Rozwiń węzeł `this` węzeł, aby wyświetlić `methodTrack` informacji.  
  
 **Dodawanie watch zmiennej methodTrack.** `methodWatch` Zmienna jest używana w tym szybki start do wyświetlenia metody wywołane w przykładach. Aby ułatwić wyświetlić wartość zmiennej, należy go dodać do okna czujki. Kliknij prawym przyciskiem myszy nazwę zmiennej w oknie zmienne lokalne, a następnie wybierz pozycję **Dodaj wyrażenie kontrolne**.  
  
 ![Okno czujki](../debugger/media/dbg_basics_watchwindow.png "DBG_Basics_WatchWindow")  
  
 Możesz obserwować wiele zmiennych w okno czujki. Wartości zmiennych monitorowane, takie jak wartości zmiennych lokalnych i danych Porada systemu windows, są aktualizowane przy każdym wykonanie jest wstrzymana. Zmienne można również dodawać do okna czujki w edytorze kodu. Wybierz zmienną do monitorowania, kliknij prawym przyciskiem myszy, a następnie wybierz pozycję **Dodaj wyrażenie kontrolne**.  
  
##  <a name="BKMK_StepIntoOverOut"></a>Krok do, za pośrednictwem i z metody  
 W przeciwieństwie do Przechodzenie do metody wywoływane przez metodę nadrzędną, przekraczanie metody wykonuje metodę podrzędnej, a następnie wstrzymuje wykonywanie w przypadku wywołania metody, jako element nadrzędny wznawia. Może być Przekrocz nad metody, gdy znasz sposób metody działa i pewności, że jego wykonanie nie wpłynie na ten problem, który rozpatrujesz.  
  
 Pominięcie wiersza kodu, który nie zawiera wywołania metody wykonuje wiersza, podobnie jak wykonywanie krok po kroku, w wierszu.  
  
 Wykonywanie krok po kroku, poza metodę podrzędnej kontynuuje wykonywanie metody, a następnie wstrzymuje wykonywanie po zwraca metodę do wywołania metody. Może wychodzenia z długo funkcja, gdy określono rest funkcji nie jest znacząca.  
  
 Pominięcie, a także wykonywanie krok po kroku, poza funkcją wykonywania funkcji.  
  
 ![Krok do, za pośrednictwem i z metody](../debugger/media/dbg_basics_stepintooverout.png "DBG_Basics_StepIntoOverOut")  
  
### <a name="example-2"></a>Przykład 2  
 W tym przykładzie kroku do, za pośrednictwem i z metod.  
  
 **Wywołaj metodę przykład2 w Konstruktorze MainPage.** Edytuj konstruktora MainPage i Zastąp następujący wiersz `methodTrack = String.Empty;` z `Example2();`.  
  
 ![Wywołaj metodę przykład2 z metody pokaz](../debugger/media/dbg_basics_callexample2.png "DBG_Basics_CallExample2")  
  
 **Uruchom do punktu przerwania.** Uruchom sesję debugowania, wybierając **Rozpocznij debugowanie** na **debugowania** menu (klawiatury: F5). Debuger wstrzymuje wykonywanie na punkt przerwania.  
  
 **Przekrocz nad wiersz kodu.** Na **debugowania** menu, wybierz **Step Over** (klawiatury: F10). Wykonuje debuger `methodTrack = "MainPage";` instrukcji w taki sam sposób jak wykonywanie krok po kroku w instrukcji.  
  
 **Wkrocz do przykład2 i Example2_A.** Wybierz klucz F11 Aby wkraczać do metody przykład 2. Przejdź do kroku w instrukcjach przykład2, aż zostanie wyświetlony wiersz `int x = Example2_A();`. Ponownie Wkrocz do tego wiersza, aby przejść do punktu wejścia Example2_A. Przejdź do kroku w każdej instrukcji Example2_A, aby powrócić do przykład2.  
  
 ![Przykład2](../debugger/media/dbg_basics_example2.png "DBG_Basics_Example2")  
  
 **Przekrocz nad funkcji.** Należy pamiętać, że następnego wiersza w przykład2, `int y = Example2_A();` jest zasadniczo taki sam jak w poprzednim wierszu. Można bezpiecznie przejść za pośrednictwem tego wiersza. Wybierz klucz F10, aby przenieść z wznowienie przykład2 Example2_A to drugie wywołanie. Wybierz F10, aby Przekrocz nad tej metody. Należy pamiętać, że `methodTrack` ciąg wskazuje metodę Example2_A wykonano dwa razy. Można również zauważyć, że debuger natychmiast przechodzi do następnego wiersza. Wstrzymuje wykonywanie w wznawia przykład2 punktu.  
  
 **Wychodzenia z funkcją.** Wybierz klucz F11 Aby wkraczać do metody Example2_B. Należy pamiętać, że nie jest bardzo różnią się od Example2_A Example2_B. Do wykonania kroków z metody, wybierz **Wyjdź** na **debugowania** menu (klawiatury: Shift + F11). Należy pamiętać, że `methodTrack` zmiennej wskazuje, czy wykonano Example2_B i że debuger powrócił do punktu, w którym wznawia przykład2.  
  
 **Zatrzymaj debugowanie.** W menu debugowania, wybierz polecenie Zatrzymaj debugowanie (klawiatury: Shift + F5). To kończy się sesja debugowania.  
  
##  <a name="BKMK_ConditionCursorVisualize"></a>Ustaw punkt przerwania warunkowego, uruchom do kursora i wizualizacji zmiennej  
 Punkt przerwania warunkowego określa warunek, który powoduje, że debuger wstrzymania wykonywania. Warunek jest określona przez dowolne wyrażenie kodu, które może przyjąć wartość PRAWDA lub FAŁSZ. Na przykład można użyć do sprawdzenia stanu programu w często wywołaną metodę tylko wtedy, gdy zmienna osiągnie wartość warunkowych punktów przerwania.  
  
 Uruchamianie do kursora przypomina ustawienie jednorazowe punktu przerwania. Podczas wykonywania jest wstrzymana, można wybrać wiersz w źródle i wznowić wykonywanie do momentu osiągnięcia wybranego wiersza. Na przykład może być krokowe wykonywanie pętli w metodzie i ustalić, czy kod w pętli działa poprawnie. Zamiast krokowe każdej iteracji pętli, możesz uruchomić kursor, który znajduje się po wykonaniu pętli.  
  
 Czasami trudno jest wyświetlanie wartości zmiennej w wierszu danych porady lub zmiennych systemu Windows. Debuger można wyświetlić ciągów, HTML i Xml w narzędzia text visualizer prezentuje sformatowany Wyświetl wartości w oknie przewijanego.  
  
### <a name="example-3"></a>Przykład 3  
 W tym przykładzie należy ustawić warunkowe punkt przerwania dzielone w określonych iteracji pętli, a następnie uruchom do kursora, który znajduje się po pętli. Możesz również wyświetlić wartość zmiennej w narzędzia text visualizer.  
  
 **Wywołaj metodę Example3 w Konstruktorze MainPage.** Edytuj konstruktora MainPage i Zastąp następujący wiersz `methodTrack = String.Empty;` z linią `Example3();`.  
  
 ![Wywołanie Example3 z metody pokaz](../debugger/media/dbg_basics_callexample3.png "DBG_Basics_CallExample3")  
  
 **Uruchom do punktu przerwania.** Uruchom sesję debugowania, wybierając **Rozpocznij debugowanie** na **debugowania** menu (klawiatury: F5). Debuger wstrzymuje wykonywanie na punkt przerwania w metodzie MainPage.  
  
 **Krok do metody Example3.** Wybierz **Step Into** na **debugowania** menu (klawiatury: F11) można przenieść do metody Example3 punktu wejścia. Kontynuuj wykonywanie krok po kroku do metody dopóki ma iterowane jednego lub dwóch pętli `for` bloku. Należy pamiętać, że może upłynąć możesz długi czas do wykonania kroków opisanych wszystkich iteracji 1000.  
  
 **Ustaw punkt przerwania warunkowego.** W lewym odstępu okna kodu, kliknij prawym przyciskiem myszy linię `x += i;` , a następnie wybierz **warunku**. Wybierz **warunku** pole wyboru, a następnie wpisz `i == 500;` w polu tekstowym. Wybierz **ma wartość true** opcję i wybierz polecenie **OK**. Punkt przerwania umożliwia sprawdzanie wartość iteracji 500th `for` pętli.  
  
 ![Okno dialogowe warunku punktu przerwania](../debugger/media/dbg_basics_breakpointcondition.png "DBG_Basics_BreakpointCondition")  
  
 Ikona warunkowych punktów przerwania można zidentyfikować przy jego między białym znakiem.  
  
 ![Punkt przerwania warunkowego](../debugger/media/dbg_basics_conditionalbreakpoint.png "DBG_Basics_ConditionalBreakpoint")  
  
 **Uruchom do punktu przerwania.** W menu debugowania, wybierz przycisk Kontynuuj (klawiatury: F5). W oknie zmienne lokalne, upewnij się, że bieżąca wartość `i` wynosi 500. Należy pamiętać, że zmienna `s` jest reprezentowany jako pojedynczy wiersz i jest znacznie większa niż okno.  
  
 **Visual zmienna typu ciąg.** Kliknij ikonę lupy w **wartość** kolumny `s`.  
  
 Zostanie wyświetlone okno narzędzia Text Visualizer, a wartość ciągu jest udostępniana jako ciąg wiele wierszy.  
  
 **Uruchom do kursora.** Kliknij prawym przyciskiem myszy linię `methodTrack += "->Example3";` , a następnie wybierz **Uruchom do kursora** (klawiatury: Przesuń kursor do wiersza; CTRL + F10). Debuger kończy iteracji pętli, a następnie wstrzymuje wykonywanie w wierszu.  
  
 **Zatrzymaj debugowanie.** W menu debugowania, wybierz polecenie Zatrzymaj debugowanie (klawiatury: Shift + F5). To kończy się sesja debugowania.  
  
##  <a name="BKMK_EditContinueRecoverExceptions"></a>Edytuj i Kontynuuj, odzyskanie Wystąpił wyjątek  
 W niektórych sytuacjach po przerwaniu do kodu w debugerze programu Visual Studio masz możliwość zmiany wartości zmiennych i nawet warunki logiczne instrukcji. Ta funkcja jest wywoływana Edytuj i Kontynuuj.  
  
 Edytuj i Kontynuuj może być szczególnie przydatne, gdy Przerwij przy Wystąpił wyjątek. Zamiast Zatrzymaj i ponownie uruchom debugowanie długich i zaangażowany procedury w celu uniknięcia wyjątek, możesz można wyjątku, aby przenieść wykonywania do punktu, bezpośrednio przed Wystąpił wyjątek "Odwiń", a następnie zmień ataku zmiennej lub instrukcji i kontynuować bieżącą sesję debugowania w stanie, który nie zgłasza wyjątek.  
  
 Mimo że można korzystanie z opcji Edytuj i Kontynuuj w wielu sytuacjach, konkretnego warunki, które nie obsługują Edytuj i Kontynuuj są trudno jest określić, ponieważ warunki są zależne od języka programowania, bieżący stan stosu program i możliwość debugera zmiany stanu bez uszkodzenia procesu. Najlepszy sposób, aby ustalić, czy zmiany edycji jest obsługiwane jest tylko próba debuger umożliwia od razu wiedzieć, czy zmiany nie jest obsługiwana.  
  
### <a name="example-4"></a>Przykład 4  
 W tym przykładzie, można uruchomić debugera wystąpił wyjątek rewind — wyjątek, popraw logiki metody, a następnie zmień wartość zmiennej, dzięki czemu można kontynuować wykonywania metody.  
  
 **Wywołaj metodę Example4 w Konstruktorze MainPage.** Edytuj konstruktora MainPage() i Zastąp następujący wiersz `methodTrack = String.Empty;` z linią `Example4();`.  
  
 ![Wywołanie Example4 z metody pokaz](../debugger/media/dbg_basics_callexample4.png "DBG_Basics_CallExample4")  
  
 **Uruchom wyjątek.** Uruchom sesję debugowania, wybierając **Rozpocznij debugowanie** na **debugowania** menu (klawiatury: F5). Naciśnij klawisz F5, aby wznowić wykonywanie. Debuger wstrzymuje wykonywanie na wyjątek w metodzie Example4 i wyświetla okno dialogowe wyjątku.  
  
 ![Okno dialogowe wyjątek](../debugger/media/dbg_basics_exceptiondlg.png "DBG_Basics_ExceptionDlg")  
  
 **Zmień logikę program.** Jest jasne, czy błąd jest `if` warunek: wartość `x` powinny być zmieniane podczas `x` jest równe 0; nie `x` nie jest równa zero. Wybierz **Podziel** ustalenie logiki metody. Podczas próby Edytuj wiersz, zostanie wyświetlone okno dialogowe innego.  
  
 ![Edytuj i Kontynuuj — okno dialogowe](../debugger/media/dbg_basics_editandcontinuedlg.png "DBG_Basics_EditAndContinueDlg")  
  
 Wybierz **Edytuj** , a następnie zmień wiersz `if (x != 0)` do `if (x == 0)`. Debuger będzie się powtarzał zmiany w logice programu w pliku źródłowym.  
  
 **Zmień wartość zmiennej.** Sprawdź wartość `x` etykietki danych lub w oknie zmienne lokalne. Nadal jest 0 (zero). Próba wykonania instrukcji, która spowodowała wyjątek oryginalnego go tylko zgłosi ponownie. Możesz zmienić wartość `x`. W oknie zmienne lokalne kliknij dwukrotnie **wartość** kolumny **x** wiersza. Zmień wartość z zakresu od 0 do 1.  
  
 ![Edytowanie wartości w oknie zmienne lokalne](../debugger/media/dbg_basics_editandcontinuefix.png "DBG_Basics_EditAndContinueFix")  
  
 Wybierz klucz F11 Aby wkraczać do instrukcji, która wcześniej wyjątek. Należy pamiętać, że wiersz jest wykonywany bez błędów. Wybierz F11 ponownie.  
  
 **Zatrzymaj debugowanie.** Na **debugowania** menu, wybierz **Zatrzymaj debugowanie** (klawiatury: Shift + F5). To kończy się sesja debugowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Uruchom sesję debugowania: (VB, C#, C++ i XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)   
 [Wyzwalanie wstrzymania, wznowienia i zdarzeń dla aplikacji platformy uniwersalnej systemu Windows w tle)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)   
 [Debugowanie aplikacji w programie Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)