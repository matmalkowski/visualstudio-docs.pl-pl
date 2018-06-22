---
title: Porady i wskazówki w debugerze programu Visual Studio
description: Dowiedz się więcej o funkcji mniejszym znane obsługiwane przez debuger programu Visual Studio
ms.custom: ''
ms.date: 06/15/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- stepping
- debugging [Visual Studio], execution control
- execution, controlling in debugger
ms.assetid: 5262d8b1-2648-429e-85d5-90fcaadfb362
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b67722884a675dd991cad608ca22cf277e2d6777
ms.sourcegitcommit: 498e39e89a89ad7bf9dcb0617424fff999b1c3b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/21/2018
ms.locfileid: "36303084"
---
# <a name="learn-productivity-tips-and-tricks-for-the-debugger-in-visual-studio"></a>Dowiedz się więcej i porady dotyczące wydajności w debugerze programu Visual Studio

Przeczytaj ten temat, aby dowiedzieć się więcej i kilka porady dotyczące wydajności w debugerze programu Visual Studio. Aby przyjrzeć podstawowe funkcje debugera, zobacz [samouczek funkcji debugera](../debugger/debugger-feature-tour.md). W tym temacie opisano możemy pewne kwestie, które nie znajdują się w samouczku funkcji.

## <a name="pin-data-tips"></a>Etykietki danych numeru PIN

Jeśli często umieszczeniu na etykietki danych podczas debugowania, można przypiąć Porada danych zmiennej zapewnić sobie szybki dostęp. Zmienna pozostaje przypiętych nawet po ponownym uruchomieniu. Aby przypiąć Porada danych, kliknij ikonę pinezki podczas umieszczenie na nim wskaźnika. Można przypiąć wiele zmiennych.

![Przypinanie etykietki danych](../debugger/media/dbg-tips-data-tips-pinned.png "PinningDataTip")

## <a name="edit-your-code-and-continue-debugging-c-vb-c"></a>Edytuj kod i Kontynuuj debugowanie (C#, VB, C++)

W większości języków obsługiwanych przez program Visual Studio można edytować kodu w trakcie sesji debugowania i Kontynuuj debugowanie. Aby użyć tej funkcji, kliknij przycisk do kodu za pomocą kursora podczas wstrzymania w debugera, sprawdź zmiany i naciśnij klawisz **F5**, **F10**, lub **F11** aby kontynuować debugowanie.

![Edytuj i Kontynuuj debugowanie](../debugger/media/dbg-tips-edit-and-continue.gif "EditAndContinue")

Aby uzyskać więcej informacji o korzystaniu z funkcji i ograniczenia dotyczące funkcji, zobacz [Edytuj i Kontynuuj](../debugger/edit-and-continue.md).

## <a name="debug-issues-that-are-hard-to-reproduce"></a>Debugowanie problemów, które są trudne do odtworzenia

Jeśli jest trudne lub czasochłonne odtworzyć określonego stanu w aplikacji, należy wziąć pod uwagę czy ułatwiają korzystanie z warunkowych punktów przerwania. Można użyć [warunkowych punktów przerwania](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) i filtrowanie punktów przerwania, aby uniknąć dzielenia do kodu aplikacji, dopóki aplikacja przechodzi żądanego stanu (takich jak stan, w którym zmiennej jest przechowywana złe dane). Można ustawić warunki za pomocą wyrażenia, filtry liczby trafień i tak dalej.

#### <a name="to-create-a-conditional-breakpoint"></a>Aby utworzyć warunkowych punktów przerwania

1. Kliknij prawym przyciskiem myszy ikonę punktu przerwania (piłka czerwony) i wybierz polecenie **warunki**.

2. W **ustawienia punktów przerwania** okna, typu jako wyrażenia.

    ![Punkt przerwania warunkowego](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

3. Jeśli interesuje Cię innego typu warunku, wybierz **filtru** zamiast **wyrażenia warunkowego** w **ustawienia punktów przerwania** okno dialogowe, a następnie wykonać Porady dotyczące filtru.

## <a name="change-the-execution-flow"></a>Przepływ wykonania zmian

Z debugera wstrzymana na wiersz kodu, za pomocą myszy do pobrania wskaźnika żółta strzałka po lewej stronie. Przesuń wskaźnik żółta strzałka do innego punktu w ścieżce wykonywania kodu. Później należy użyć polecenia kroku lub F5 dalsze działanie aplikacji.

![Przesuń wskaźnik wykonywania](../debugger/media/dbg-tour-move-the-execution-pointer.gif "wskaźnika wykonywania")

Zmieniając przepływu wykonywania, możesz to zrobić rzeczy, takich jak przetestować różne ścieżki wykonywania lub uruchom ponownie kodu bez ponownego uruchamiania debugera.

> [!WARNING]
> Często należy zachować ostrożność przy użyciu tej funkcji i zostanie wyświetlone ostrzeżenie w etykietce narzędzia. Zbyt mogą pojawić się inne ostrzeżenia. Przesuń wskaźnik nie można przywrócić aplikację do wcześniejszego stanu aplikacji.

## <a name="track-an-out-of-scope-object-c-visual-basic"></a>Śledzenie obiekt poza zakresem (C#, Visual Basic)

Ułatwia wyświetlanie zmiennych za pomocą debugera systemu windows, takich jak **czujki** okna. Jednak po zmienną wykracza poza zakresem w **czujki** okna, można zauważyć, że jest szary. W niektórych scenariuszach aplikacji może zmienić wartość zmiennej, nawet jeśli zmienna jest poza zakresem i należy go ściśle Obejrzyj (na przykład zmienna może uzyskać bezużytecznych). Można śledzić zmiennej, tworząc Identyfikatora obiektu dla niego w **czujki** okna.

#### <a name="to-create-an-object-id"></a>Aby utworzyć identyfikator obiektu

1.  Ustaw punkt przerwania w pobliżu zmiennej, która mają być śledzone.

2.  Uruchom debuger (**F5**) i stop na punkt przerwania.

3. Znajdź zmiennej w **zmiennych lokalnych** okna (**debugowania > Windows > Zmienne lokalne**), kliknij prawym przyciskiem myszy zmienną i wybierz **wprowadzić identyfikator obiektu**.

    ![Tworzenie Identyfikatora obiektu](../debugger/media/dbg-tips-watch-create-object-id.png "CreateObjectID")
  
4.  Powinny pojawić się **$** plus liczbą **zmiennych lokalnych** okna. Ta zmienna jest identyfikatora obiektu.
  
5.  Kliknij prawym przyciskiem myszy obiekt Zmienna Identyfikatora i wybierz polecenie **Dodaj wyrażenie kontrolne**.

Aby uzyskać więcej informacji, zobacz [tworzenie Identyfikatora obiektu](../debugger/watch-and-quickwatch-windows.md#bkmk_objectIds).

## <a name="view-return-values-for-functions"></a>Wyświetl wartości zwracanych przez funkcje

Aby wyświetlić wartości zwracane dla funkcji, przyjrzeć się funkcje, które są widoczne w **automatycznych** okna, gdy są krokowe kodu. Aby wyświetlić wartości zwracanej przez funkcję, upewnij się, funkcja myślisz zostało już wykonane (naciśnij klawisz **F10** raz, jeśli są aktualnie zatrzymane na wywołanie funkcji). Jeśli okno jest zamknięty, użyj **debugowania > Windows > automatycznych** otworzyć **automatycznych** okna.

![Okno zmiennych automatycznych](../debugger/media/dbg-tips-autos-window.png "AutosWindow")

Ponadto można wprowadzić funkcje w **Immediate** okna, aby wyświetlić wartości zwracanych. (Otwórz za pomocą **Debuguj > Windows > Immediate**.)

![Okno bezpośrednie](../debugger/media/dbg-tips-immediate-window.png "ImmediateWindow")

Można również użyć [pseudovariables](../debugger/pseudovariables.md) w **czujki** i **Immediate** okna, takich jak `$ReturnValue`.

## <a name="string_visualizer"></a>Sprawdź ciągów w wizualizatora

Podczas pracy z ciągami, może być przydatne wyświetlić cały ciąg sformatowany. Aby wyświetlić zwykłego tekstu, ciąg XML, HTML lub JSON, kliknij ikonę lupy ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "ikona wizualizatora") podczas kursora myszy nad zmiennej zawierającej wartość ciągu.

![Otwórz Wizualizator ciągu](../debugger/media/dbg-tips-string-visualizers.png "OpenStringVisualizer")

Wizualizator ciągu może pomóc sprawdzić, czy ciąg jest nieprawidłowo sformułowany, w zależności od typu ciąg. Na przykład pusty **wartość** pole zawiera ciąg nie został rozpoznany przez typ wizualizatora. Aby uzyskać więcej informacji, zobacz [String Visualizer — okno dialogowe](../debugger/string-visualizer-dialog-box.md).

![Wizualizator ciągu JSON](../debugger/media/dbg-tips-string-visualizer-json.png "JSONStringVisualizer")

Kilka innych typów takich jak WPF obiekty, które są widoczne w oknach debugera można również otworzyć wizualizatorów.

## <a name="break-into-code-on-handled-exceptions"></a>Podziel na kod obsługiwanego wyjątków

Debuger dzieli się na kodzie w przypadku nieobsługiwanych wyjątków. Jednak obsługi wyjątków (takich jak wyjątków, które występują w ramach `try/catch` blok) również może być źródłem błędów i chcesz zbadać, kiedy występują. Można skonfigurować debugera, aby podzielić na kod również wyjątków obsłużonych przez skonfigurowanie opcji w **ustawienia wyjątków** okno dialogowe. Otwórz okno dialogowe, wybierając **debugowania > Windows > Ustawienia wyjątków**.

**Ustawienia wyjątków** okno dialogowe umożliwia wskazanie debugera podziału na kod dla określonych wyjątków. Na poniższej ilustracji debuger dzieli na kod zawsze, gdy `System.NullReferenceException` występuje. Aby uzyskać więcej informacji, zobacz [Zarządzanie wyjątkami](../debugger/managing-exceptions-with-the-debugger.md).

![Okno dialogowe Ustawienia wyjątków](../debugger/media/dbg-tips-exception-settings.png "ExceptionSettingsDialogBox")

## <a name="debug-deadlocks-and-race-conditions"></a>Zakleszczenie debugowania i sytuacja wyścigu

Jeśli musisz debugować rodzaje problemów, które są wspólne dla aplikacji wielowątkowych często pomaga można wyświetlić lokalizacji wątków podczas debugowania. Można to zrobić za pomocą **Pokaż wątki w źródle** przycisku.

#### <a name="to-show-threads-in-your-source-code"></a>Aby wyświetlić wątków w kodzie źródłowym

1.  Podczas debugowania, kliknij przycisk **Pokaż wątki w źródle** przycisk ![Pokaż wątki w źródle](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker") w **debugowania** paska narzędzi.
  
2.  Spójrz na odstępu w lewej części okna. W tym wierszu, zobacz *znacznika wątku* ikona ![znacznika wątku](../debugger/media/dbg-thread-marker.png "ThreadMarker") o podobny dwoma wątkami materiału. Znacznika wątku wskazuje, że wątek został zatrzymany w tej lokalizacji.

    Zwróć uwagę, że znacznika wątku może być częściowo ukrywane przez punkt przerwania.
  
3.  Umieść kursor nad znacznika wątku. Zostanie wyświetlone etykietek danych. Etykietek danych zawiera numer identyfikacyjny nazwy i wątków dla każdego zatrzymanego wątku.

    Można również wyświetlić lokalizacji wątków w [okna stosów równoległych](../debugger/get-started-debugging-multithreaded-apps.md).

## <a name="examine-payloads-for-web-services-and-network-resources-uwp"></a>Sprawdź ładunków dla usług sieci web i zasobów sieciowych (UWP)

W aplikacjach platformy uniwersalnej systemu Windows można analizować operacje sieciowe wykonywane przy użyciu `Windows.Web.Http` interfejsu API. To narzędzie służy do debugowania usług sieci web i zasobów sieciowych. Aby korzystać z narzędzia, wybierz **Debuguj > wydajności programu profilującego**. Wybierz **sieci**, a następnie wybierz pozycję **Start**. W aplikacji, przejdź przez scenariusz, który używa `Windows.Web.Http`, a następnie wybierz pozycję **zatrzymać zbieranie** do wygenerowania raportu.

![Narzędzia profilowania użycie sieci](../profiling/media/prof-tour-network-usage.png "NetworkUsageProfTool")

Wybierz operację w Podsumowanie widoku, aby wyświetlić więcej szczegółów.

![Szczegółowe informacje o w narzędziu użycie sieci](../profiling/media/prof-tour-network-usage-details.png "DetailedViewNetworkUsage")

Aby uzyskać więcej informacji, zobacz [użycie sieci](../profiling/network-usage.md).

## <a name="get-more-familiar-with-how-the-debugger-attaches-to-your-app"></a>Więcej zapoznać się z jak dołącza debuger do aplikacji

Aby dołączyć do uruchomionej aplikacji, debuger ładuje wygenerowanych dokładne kompilacji tej samej aplikacji, którą próbujesz debugować plików symboli (.pdb). W niektórych scenariuszach może być przydatna nieco wiedzy na temat plików symboli. Można sprawdzić, jak Visual Studio ładuje przy użyciu plików symboli **modułów** okna.

Otwórz **modułów** okno podczas debugowania, wybierając **debugowania > Windows > modułów**. **Modułów** okna można określić, które moduły debugera jest traktowanie jako kod użytkownika lub [ *mój kod*](../debugger/just-my-code.md)i symbol stanu modułu ładowania. W większości przypadków debuger automatycznie znajdzie pliki symboli dla kodu użytkownika, ale aby wkraczać do (lub debugowanie) kodu platformy .NET framework, kod systemu lub kod biblioteki innych firm, dodatkowe kroki są wymagane do uzyskania plików symboli poprawne.

![Wyświetl informacje o symbolach w oknie moduły](../debugger/media/dbg-tips-modules-window.png "ViewSymbolInformation")

Można załadować informacji o symbolach bezpośrednio z **modułów** okno prawym przyciskiem myszy i wybierając pozycję **załadować symbole**.

Czasami deweloperzy aplikacji składnikiem aplikacji bez pasujących plików symboli (Aby ograniczyć wpływ), ale zachować kopię zgodnych symboli plików dla kompilacji, tak aby ich później debugowania wydanej wersji.

Aby dowiedzieć się, jak debuger klasyfikuje kodu jako kodu użytkownika, zobacz [tylko mój kod](../debugger/just-my-code.md). Aby dowiedzieć się więcej na temat plików symboli, zobacz [Określ symboli (.pdb) i plików źródłowych w debugerze programu Visual Studio](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="learn-more"></a>Dowiedz się więcej

Aby uzyskać dodatkowe porady i wskazówki i bardziej szczegółowe informacje Zobacz wpisy na blogu:

- [7 mniejszym hacks znane do debugowania w programie Visual Studio](https://blogs.msdn.microsoft.com/visualstudio/2017/06/26/7-lesser-known-hacks-for-debugging-in-visual-studio/)
- [7 gems ukryte w programie Visual Studio](https://blogs.msdn.microsoft.com/visualstudio/2017/10/05/7-hidden-gems-in-visual-studio-2017/)

## <a name="see-also"></a>Zobacz też
[Skróty klawiaturowe](../ide/tips-and-tricks-for-visual-studio.md)
