---
title: Debugowanie kodu Python | Dokumentacja firmy Microsoft
description: Wskazówki dotyczące funkcji debugowania w programie Visual Studio specjalnie z myślą o kod języka Python, w tym ustawianie punktów przerwania, wykonywanie krok po kroku, sprawdzania wartości, patrzeć wyjątków i debugowanie w oknie interaktywnym.
ms.custom: ''
ms.date: 03/05/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: a9e8cf75bcdf11994f549be3ef47d5a95868eeef
ms.sourcegitcommit: 29ef88fc7d1511f05e32e9c6e7433e184514330d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2018
---
# <a name="debugging-your-python-code"></a>Debugowanie kodu języka Python

Program Visual Studio oferuje kompleksowe środowisko debugowania dla języka Python, dołączanie do uruchomionego procesu, w tym obliczenia wyrażenia w czujki i bezpośredniego systemu windows, sprawdzania zmiennych lokalnych, punkty przerwania, kroku instrukcje w/out/w, ustaw dalej Instrukcja i inne.

Zobacz także następujące artykuły debugowania specyficzne dla scenariusza:

- [Debugowanie zdalne systemu Linux](debugging-python-code-on-remote-linux-machines.md)
- [Zdalne debugowanie platformy Azure](debugging-remote-python-code-on-azure.md)
- [Debugowanie w trybie mieszanym Python/C++](debugging-mixed-mode-c-cpp-python-in-visual-studio.md)
- [Symbole debugowania w trybie mieszanym](debugging-symbols-for-mixed-mode-c-cpp-python.md)

|   |   |
|---|---|
| ![Ikona aparatu film wideo](../install/media/video-icon.png "obejrzeć film wideo") | [Obejrzyj film (Microsoft Virtual Academy)](https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Debugging-Python-Ep5dp5LWE_3805918567) do pokazania Python debugowanie (3 m 32s).|

<a name="debugging-without-a-project"></a>

> [!Tip]
> Python w programie Visual Studio obsługuje debugowanie bez projektu. Z autonomicznego pliku Python otwarty, kliknij prawym przyciskiem myszy w edytorze, wybierz **rozpoczynać debugowanie**, i Visual Studio uruchamia skrypt z globalnego domyślnego środowiska (zobacz [środowiska Python](managing-python-environments-in-visual-studio.md)) i bez argumentów. Ale następnie pełną obsługę debugowania.
>
> Aby kontrolować środowiska i argumentów, utworzyć projekt kodu, który jest łatwo zrobić za pomocą [z istniejących Python code](managing-python-projects-in-visual-studio.md#creating-a-project-from-existing-files) szablonu projektu.

<a name="debugging-with-a-project"></a>

## <a name="basic-debugging"></a>Debugowanie podstawowe

Podstawowy przepływ pracy debugowania obejmuje ustawienia punktów przerwania, krokowe wykonywanie kodu, sprawdzania wartości i obsługa wyjątków, zgodnie z opisem w poniższych sekcjach.

Rozpoczyna się od sesji debugowania **Debuguj > Rozpocznij debugowanie** polecenia, **Start** przycisku paska narzędzi lub klawisz F5. Te akcje Uruchom plik uruchomienia projektu (pokazano pogrubienia w Eksploratorze rozwiązań) z projektu aktywnego środowiska i argumenty wiersza polecenia lub ścieżki wyszukiwania, które zostały określone we właściwościach projektu (zobacz [debugowania projektu opcje](#project-debugging-options). **Visual Studio 2017 wersji 15,6** i później ostrzega użytkownika, jeśli nie masz pliku uruchamiania Ustaw; wcześniejszych wersji może otworzyć okno danych wyjściowych z interpreter języka Python uruchomiona, lub w oknie danych wyjściowych krótko pojawia się i znika. W każdym przypadku, kliknij prawym przyciskiem myszy odpowiedni plik i wybierz **Ustaw jako plik uruchamiania**.

> [!Note]
> Debuger zawsze rozpoczyna się od aktywnego środowiska Python dla projektu. Zmian w środowisku, aby różne aktywne jeden zgodnie z opisem na [wybranie środowisku Python dla projektu](selecting-a-python-environment-for-a-project.md).

### <a name="breakpoints"></a>Punkty przerwania

Punkty przerwania Zatrzymaj wykonywanie kodu w momencie zaznaczone, możesz sprawdzić stan programu. Ustaw punkty przerwania, klikając prawym przyciskiem myszy linię kodu i wybierając na lewym marginesie edytora kodu lub **punktu przerwania > Wstaw punktu przerwania**. Czerwonej kropki pojawia się w każdym wierszu z punktu przerwania.

![Punkty przerwania w programie Visual Studio](media/debugging-breakpoints.png)

Klikając czerwonej kropki lub klikając wiersz kodu prawym przyciskiem myszy i wybierając **punktu przerwania > Usuń punkt przerwania** powoduje usunięcie punktu przerwania. Można również wyłączyć go bez usuwania go przy użyciu **punktu przerwania > Wyłącz punkt przerwania** polecenia.

> [!Note]
> Niektórych punktów przerwania w języku Python można zaskakująco dla deweloperów, którzy pracowali z innymi językami programowania. W języku Python cały plik jest kodu wykonywalnego, więc Python uruchamia plik, gdy jest ładowany do przetworzenia najwyższego poziomu klasy lub definicji funkcji. Jeśli punkt przerwania, może się okazać debuger podziału części sposób za pomocą deklaracji klasy. To zachowanie, które są prawidłowe, nawet jeśli jest czasami zaskakująco.

Można dostosować warunki, w jakich wyzwoleniu punkt przerwania, takich jak podział tylko wtedy, gdy zmienna jest ustawiana niektórych wartości lub wartości zakresu. Ustaw warunki, kliknij prawym przyciskiem myszy punkt przerwania czerwonej kropki, wybierz **warunku**, następnie utwórz wyrażenia przy użyciu kodu języka Python. Aby uzyskać szczegółowe informacje na temat tej funkcji w programie Visual Studio, zobacz [warunków punktu przerwania](../debugger/using-breakpoints.md#breakpoint-conditions)

Podczas ustawiania warunki, można również ustawić **akcji** i utworzyć komunikat do dziennika w oknie danych wyjściowych, opcjonalnie kontynuowanie wykonania automatycznie. Rejestrowanie wiadomości tworzy tak zwany *śledzenia* bez dodawania rejestrowania kodu bezpośrednio do aplikacji:

![Tworzenie śledzenia z punktu przerwania](media/debugging-tracepoint.png)

### <a name="stepping-through-code"></a>Krokowe wykonywanie kodu

Po zatrzymana w punkcie przerwania, są różne sposoby krokowo kodu lub uruchom bloki kodu przed przerwaniem ponownie. Te polecenia są dostępne w wielu miejscach, w tym narzędzi debugowania top **debugowania** menu, w menu kontekstowym kliknij prawym przyciskiem myszy w edytorze kodu i za pośrednictwem skróty klawiaturowe (za pośrednictwem nie wszystkie polecenia są we wszystkich miejscach):

| Funkcja | Keystroke | Opis |
| --- | --- | --- |
| Kontynuuj | F5 | Uruchamia kod, aż do osiągnięcia następnego punktu przerwania. |
| Wkrocz | F11 | Uruchamia następnej instrukcji i zatrzymuje. Następnej instrukcji w przypadku wywołania funkcji, debuger zatrzymuje się w pierwszym wierszu wywoływanej funkcji. |
| Przekrocz | F10 | Uruchamia następnej instrukcji, łącznie z wywołania funkcji (uruchomionego jego kodu) i stosowanie wartości zwracanych. Pominięcie umożliwia łatwe pominąć funkcje, które nie należy do debugowania. |
| Wyjdź | Shift+F11 | Uruchamia kod do końca bieżącej funkcji, a następnie kroki do wywoływania instrukcji.  To polecenie jest przydatne, gdy nie jest konieczne do debugowania w pozostałej części bieżącej funkcji. |
| Uruchom do kursora | Ctrl+F10 | Uruchamia kod do lokalizacji karetki w edytorze. To polecenie umożliwia łatwe pominąć segment kodu, który nie należy do debugowania. |
| Ustaw następną instrukcję | Ctrl+Shift+F10 | Zmienia bieżący przebieg punktu kodu w lokalizacji karetki. To polecenie umożliwia pominięcie segment kodu uruchamianego w ogóle, np. Jeśli znasz kod jest uszkodzony lub tworzy i niechciane efekt uboczny. |
| Pokaż następną instrukcję | Alt+Num * | Powrót do następnej instrukcji do uruchomienia. To polecenie jest przydatne, jeśli zostały wyszukiwania w kodzie i nie pamiętasz, gdy debuger został zatrzymany. |

### <a name="inspecting-and-modifying-values"></a>Sprawdzanie i modyfikowanie wartości

Po zatrzymaniu debugera, można sprawdzić i modyfikować wartości zmiennych. Okno czujki służy również do monitorowania poszczególnych zmiennych, jak również wyrażeń niestandardowych. (Zobacz [Sprawdź zmienne](../debugger/getting-started-with-the-debugger.md#inspect-variables-with-the-autos-and-locals-windows) szczegółowe informacje ogólne.)

Aby wyświetlić wartość przy użyciu etykietek danych, po prostu umieść kursor myszy nad dowolnej zmiennej w edytorze. Można kliknąć pozycję na wartość jego zmiany:

![Etykietki danych w debugerze](media/debugging-quick-tips.png)

Okno zmiennych automatycznych (**Debuguj > Windows > automatycznych**) zawiera zmiennych i wyrażeń, które wkrótce bieżącej instrukcji. Możesz kliknij dwukrotnie ikonę w kolumnie wartość lub wybierz i naciśnij klawisz F2, aby edytować wartość:

![Okno zmiennych automatycznych w debugerze](media/debugging-autos-window.png)

Okno zmiennych lokalnych (**Debuguj > Windows > Zmienne lokalne**) Wyświetla wszystkie zmienne, które znajdują się w bieżącym zakresie ponownie można edytowane:

![Okno zmiennych lokalnych w debugerze](media/debugging-locals-window.png)

Aby uzyskać więcej informacji na temat używania zmiennych automatycznych i zmiennych lokalnych zobacz [sprawdzania zmiennych w automatycznych i zmiennych lokalnych Windows](../debugger/autos-and-locals-windows.md).

Okien wyrażeń kontrolnych (**debugowania > Windows > Obejrzyj > Obejrzyj 1-4**) można wprowadzić dowolne wyrażeń języka Python i wyświetlić wyniki. Wyrażenia są ponownie oceniane dla każdego kroku:

![Okno czujki w debugerze](media/debugging-watch-window.png)

Aby uzyskać więcej informacji na temat używania czujki zobacz [ustawienie czujki zmiennych przy użyciu czujki i QuickWatch Windows](../debugger/watch-and-quickwatch-windows.md).

Podczas kontroli wartość ciągu (`str`, `unicode`, `bytes`, i `bytearray` są wszystkie traktowane jako ciągi w tym celu), ikonę lupy pojawia się po prawej stronie wartości. Kliknięcie ikony Wyświetla wartość ciągu bez cudzysłowów w oknie dialogowym menu podręczne, zawijania i przewijania, który jest przydatny dla ciągów długich. Ponadto wybierając strzałkę listy rozwijanej ikonę służy do wybierania zwykły tekst, HTML, XML i JSON wizualizacje:

![Wizualizatory ciągu](media/debugging-string-visualizers.png)

Wizualizacje HTML, XML i JSON są wyświetlane w okna podręczne oddzielne z widokami wyróżnianie i drzewa składni.

### <a name="exceptions"></a>Wyjątki

Jeśli wystąpi błąd w programie podczas debugowania, ale go nie masz obsługi wyjątków, debuger dzieli w punkcie wyjątek:

![Wyjątek podręcznego](media/debugging-exception-popup.png)

W tym momencie możesz sprawdzić stan programu, w tym stosu wywołań. Jednak próba krokowo kodu wyjątek nadal został zgłoszony do momentu albo zostanie obsłużony lub kończy pracę programu.

**Debugowania > Windows > Ustawienia wyjątków** polecenie powoduje wyświetlenie okna, w którym można rozwinąć **wyjątki Python**:

![Okno wyjątków](media/debugging-exception-settings.png)

Pole wyboru dla każdej kontrolki wyjątku czy debugera *zawsze* dzieli, gdy jest on uruchamiany. Zaznacz to pole wyboru, jeśli chcesz podzielić częściej dla określonego wyjątku.

Domyślnie większość wyjątki Przerwij, gdy nie można odnaleźć programu obsługi wyjątków w kodzie źródłowym. Aby zmienić to zachowanie, kliknij prawym przyciskiem myszy każdy wyjątek i zaznaczenie lub usunięcie zaznaczenia **kontynuować po nieobsługiwany w kodzie użytkownika**. Wyczyść to pole, jeśli chcesz podzielić rzadziej dla wyjątku.

Aby skonfigurować wyjątek, który nie ma na tej liście, kliknij przycisk **Dodaj** przycisk, aby dodać go. Nazwa musi odpowiadać Pełna nazwa wyjątku.

## <a name="project-debugging-options"></a>Projekt opcji debugowania

Domyślnie debuger programu rozpoczyna się od standardowego uruchamiania Python, żadnych argumentów wiersza polecenia z i innych ścieżek specjalnych lub warunków. Opcje uruchamiania są zmieniane przy użyciu właściwości debugowania projektu używane przez kliknięcie prawym przyciskiem myszy projekt w Eksploratorze rozwiązań, wybierając **właściwości**i wybierając **debugowania** kartę.

![Właściwości debugowania projektu](media/debugging-project-properties.png)

### <a name="launch-mode-options"></a>Opcje trybu uruchamiania

| Opcja | Opis |
| --- | --- |
| Standardowa uruchamiania Python | Używa debugowania kod napisany w języku Python przenośny, który jest zgodny z języka CPython, IronPython i odmiany takich jak Stackless Python. Zapewnia najlepsze środowisko do debugowania czyste kodu języka Python. Po dołączeniu do działającego `python.exe` proces, uruchom ten jest używany. Uruchom ten zawiera również [debugowanie w trybie mieszanym](debugging-mixed-mode-c-cpp-python-in-visual-studio.md) języka CPython, co umożliwia bezproblemowe krok między kodu C/C++ i kodem języka Python. |
| Uruchamianie sieci Web | Uruchamia domyślnej przeglądarki na uruchamianie i włącza debugowanie szablonów. Zobacz [debugowania szablonów sieci Web](python-web-application-project-templates.md#debugging) sekcji, aby uzyskać więcej informacji. |
| Django Web launcher | Taki sam jak uruchamianie sieci Web i wyświetlane tylko dla zapewnienia zgodności. |
| IronPython (.NET) launcher | Używa debugera platformy .NET, które działa wyłącznie z IronPython, ale umożliwia przechodzenie między żadnego projektu języka .NET, w tym C# i VB. Uruchamianie tego programu jest używana, gdy dołączanie do uruchomionego procesu .NET, który jest hostem IronPython. |

### <a name="run-options-search-paths-startup-arguments-and-environment-variables"></a>Opcje uruchamiania (ścieżki wyszukiwania, argumenty uruchomienia i zmiennych środowiskowych)

| Opcja | Opis |
| --- | --- |
| Ścieżki wyszukiwania | Te wartości są takie same, co jest wyświetlane w węźle ścieżek wyszukiwania projektu w Eksploratorze rozwiązań. Można zmodyfikować tej wartości w tym miejscu, ale jest łatwiejsze w Eksploratorze rozwiązań, który pozwala na przeglądanie folderów i automatycznie konwertuje ścieżki względnej formularza. |
| Argumenty skryptu | Argumenty są dodawane do polecenia używane do uruchomienia skryptu, pojawiające się po nazwę pliku skryptu. Pierwszy element w tym polu jest dostępne do skryptu jako `sys.argv[1]`, drugi jako `sys.argv[2]`i tak dalej. |
| Interpreter argumentów | Argumenty są dodawane do uruchamiania wiersza polecenia przed nazwą skryptu. Tutaj argumenty wspólnej `-W ...` umożliwiającej kontrolowanie ostrzeżeń `-O` do nieco zoptymalizowała program, i `-u` do użycia we/wy Niebuforowane. Użytkownicy IronPython są prawdopodobnie to pole służy do przekazywania `-X` opcje, takie jak `-X:Frames` lub `-X:MTA`. |
| Ścieżka interpretera | Zastępuje ścieżka skojarzona z bieżącym środowisku.  wartość może być przydatne w przypadku uruchamiania skryptu z niestandardowym interpreter. |
| Zmienne środowiskowe | W tym wielowierszowego pola tekstowego, Dodaj wpisy w postaci `NAME=VALUE`. Ponieważ to ustawienie jest stosowane, w górnej części istniejących zmiennych środowiskowych globalnej i po `PYTHONPATH` jest ustawiona zgodnie z ustawieniem ścieżki wyszukiwania może służyć do ręcznie przesłonić te inne zmienne. |

<a name="the-debug-interactive-window"></a>

## <a name="immediate-and-interactive-windows"></a>Natychmiastowe i interaktywne systemu windows

Istnieją dwa okna interaktywnego, możesz użyć podczas sesji debugowania: okno programu Visual Studio natychmiastowego standardowe i okno interaktywne debugowania języka Python.

W oknie bezpośrednim (**Debuguj > Windows > Immediate**) służy do szybkiej oceny wyrażeń języka Python i inspekcji lub przypisania zmiennych w uruchomiony program. Zobacz ogólne [oknie bezpośrednim](../ide/reference/immediate-window.md) artykułu, aby uzyskać szczegółowe informacje.

Okno interaktywne debugowania języka Python (**debugowania > Windows > Python debugowania interakcyjne**) jest bardziej zaawansowane funkcje, jak ułatwia pełnego [interaktywny REPL](python-interactive-repl-in-visual-studio.md) wystąpić dostępne podczas debugowania, w tym pisania i wykonywanie kodu. Automatycznie łączy się żaden proces uruchomiony w debugerze przy użyciu uruchamiania Standard języka Python (w tym procesy dołączonym za pośrednictwem **debugowania > dołączyć do procesu**). Nie, jednak jest dostępne w przypadku korzystania z debugowanie w trybie mieszanym C/C++.

![Okno interaktywne debugowania języka Python](media/debugging-interactive.png)

Okno interaktywne debugowania obsługuje specjalne meta polecenia oprócz [standardowe polecenia REPL](python-interactive-repl-in-visual-studio.md#meta-commands):

| Polecenie | Argumenty | Opis |
| --- | --- | --- |
| `$continue`, `$cont`, `$c` | Uruchomienie programu od bieżącej instrukcji. |
| `$down`, `$d` | Przenieść bieżącej ramki o jeden poziom w dół w ślad stosu. |
| `$frame` | | Wyświetla bieżący identyfikator ramki.
| `$frame` | Identyfikator ramki | Zmienia bieżącej ramki do identyfikatora określonej ramce.
| `$load` | Ładuje polecenia z pliku i jest wykonywana do czasu ukończenia |
| `$proc` |  | Wyświetla bieżący identyfikator procesu. |
| `$proc` | Identyfikator procesu | Zmienia bieżącego procesu na identyfikator określonego procesu. |
| `$procs` | | Wyświetla listę aktualnie debugowanych procesów. |
| `$stepin`, `$step`, `$s` | Kroki do następnego wywołania funkcji, jeśli to możliwe. |
| `$stepout`, `$return`, `$r` | Kroki poza bieżącą funkcję. |
| `$stepover`, `$until`, `$unt` | Pomija następnego wywołania funkcji. |
| `$thread` | | Wyświetla bieżący identyfikator wątku. |
| `$thread` | Identyfikator wątku | Zmienia bieżący wątek na identyfikator określonego wątku. |
| `$threads` | | Wyświetla listę aktualnie debugowanych wątki. |
| `$up`, `$u` | | Przenieś na bieżącym poziomie jedną ramkę w górę ślad stosu. |
| `$where`, `$w`, `$bt` | Wyświetla listę ramek bieżącego wątku. |

Należy pamiętać, że standardowego debugera systemu windows, takich jak procesy, wątki i stos wywołań nie są zsynchronizowane z okno interaktywne debugowania. Zmiana aktywnego procesu, wątku lub ramki okna debugowania interaktywnego nie ma wpływu na innych oknach debugera. Podobnie zmianę aktywnego procesu, wątku lub ramki, w oknach debugera nie wpływa na okno interaktywne debugowania.

Okno interaktywne debugowania ma swój własny zestaw opcji, które są dostępne za pośrednictwem **Narzędzia > Opcje > Narzędzia Python Tools > debugowanie okna interaktywnego**. W odróżnieniu od regularne okno interaktywne Python ma osobnego wystąpienia dla każdego środowiska Python, istnieje tylko jedno okno interaktywne debugowania i zawsze używa interpreter języka Python dla debugowanego procesu. Zobacz [opcji - opcji debugowania](python-support-options-and-settings-in-visual-studio.md#debugging-options).

![Okno interaktywne opcje debugowania](media/debugging-interactive-options.png)

## <a name="see-also"></a>Zobacz także

Aby uzyskać szczegółowe informacje o debugerze programu Visual Studio, zobacz [debugowania w programie Visual Studio](../debugger/debugging-in-visual-studio.md).