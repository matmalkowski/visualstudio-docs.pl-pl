---
title: Debugowanie kodu języka Python
description: Przewodnik po funkcji debugowania w programie Visual Studio dla kodu Python, w tym ustawiania punktów przerwania, przechodzenie krok po kroku, sprawdzania wartości, patrząc wyjątków i debugowania w oknie interaktywnym.
ms.date: 07/13/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 14716aa85245dcbd7c1ba0bc85824f5a53bece2d
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/17/2018
ms.locfileid: "39079826"
---
# <a name="debug-your-python-code"></a>Debugowanie kodu w języku Python

Program Visual Studio udostępnia kompleksowe środowisko debugowania dla języka Python, dołączanie do uruchomionego procesu, w tym oceny wyrażenia w oknach wyrażenie kontrolne i bezpośredniego systemu windows, sprawdzanie zmiennych lokalnych, punkty przerwania, krok ustawić następnej instrukcji w/out/tryb failover Instrukcji i nie tylko.

Zobacz też następujące artykuły debugowania specyficzne dla scenariusza:

- [Zdalne debugowanie w systemie Linux](debugging-python-code-on-remote-linux-machines.md)
- [Zdalne debugowanie platformy Azure](debugging-remote-python-code-on-azure.md)
- [Debugowanie w trybie mieszanym języków Python/C++](debugging-mixed-mode-c-cpp-python-in-visual-studio.md)
- [Symbole debugowania w trybie mieszanym](debugging-symbols-for-mixed-mode-c-cpp-python.md)

|   |   |
|---|---|
| ![Ikona aparatu film wideo](../install/media/video-icon.png "Obejrzyj klip wideo") | [Obejrzyj film wideo (Microsoft Virtual Academy)](https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Debugging-Python-Ep5dp5LWE_3805918567) demonstracyjne (3 m 32s) debugowania języka Python.|

<a name="debugging-without-a-project"></a>

> [!Tip]
> Język Python w programie Visual Studio obsługuje debugowanie bez projektu. Autonomiczny plik w języku Python otwarty, kliknij prawym przyciskiem myszy w edytorze wybierz **rozpocząć debugowanie**, i Visual Studio uruchamia skrypt przy użyciu środowiska domyślnego globalnego (zobacz [środowiska Python](managing-python-environments-in-visual-studio.md)) i bez argumentów. Ale od tego momentu pełną obsługę debugowania.
>
> Aby kontrolować środowiska i argumenty, Utwórz projekt dla kodu, który można łatwo przeprowadzić za pomocą [za pomocą języka Python istniejącego kodu](managing-python-projects-in-visual-studio.md#creating-a-project-from-existing-files) szablonu projektu.

<a name="debugging-with-a-project"></a>

## <a name="basic-debugging"></a>Debugowanie podstawowe

Podstawowy przepływ pracy debugowania obejmuje ustawienia punktów przerwania, krokowe wykonywanie kodu, sprawdzania wartości i obsługa wyjątków, zgodnie z opisem w poniższych sekcjach.

Sesję debugowania, który rozpoczyna się od **Debuguj > Rozpocznij debugowanie** polecenia **Start** przycisk na pasku narzędzi lub klawisz F5. Te akcje Uruchom plik startowy projektu (pokazano w pogrubieniem w Eksploratorze rozwiązań) z projektu aktywnego środowiska i argumenty wiersza polecenia lub ścieżki wyszukiwania, które zostały określone we właściwościach projektu (zobacz [debugowania projektu opcje](#project-debugging-options). **Visual Studio 2017 w wersji 15.6** i później ostrzega, jeśli nie masz plik startowy, ustaw; wcześniejszych wersji może otworzyć okno danych wyjściowych z interpreter języka Python, uruchamianie lub w oknie danych wyjściowych krótko pojawi się i znika. W każdym przypadku, kliknij prawym przyciskiem myszy odpowiedni plik i wybierz **Ustaw jako plik startowy**.

> [!Note]
> Debuger zawsze zaczyna się od aktywnego środowiska Python dla projektu. Ku zmienianiu środowiska, wprowadzić inną aktywnych jeden, zgodnie z opisem na [zaznaczenie w środowisku Python dla projektu](selecting-a-python-environment-for-a-project.md).

### <a name="breakpoints"></a>Punkty przerwania

Punkty przerwania zatrzymać wykonywanie kodu w momencie oznaczone, dzięki czemu można sprawdzić stan programu. Ustawianie punktów przerwania, klikając w lewy margines edytora kodu lub klikając prawym przyciskiem myszy linię kodu i wybierając polecenie **punktu przerwania > Wstaw punkt przerwania**. Czerwona kropka pojawia się w każdym wierszu za pomocą punktu przerwania.

![Punkty przerwania w programie Visual Studio](media/debugging-breakpoints.png)

Klikając czerwona kropka, lub kliknij prawym przyciskiem myszy wiersz kodu i wybierając **punktu przerwania > Usuń punkt przerwania** Usuwa punkt przerwania. Można również wyłączyć ją bez usuwania go za pomocą **punktu przerwania > Wyłącz punkt przerwania** polecenia.

> [!Note]
> Niektóre punkty przerwania w języku Python może być Zaskakujące dla deweloperów, którzy pracowali z innymi językami programowania. W języku Python cały plik jest kodu wykonywalnego, więc Python jest uruchamiany plik, gdy jest ładowany w celu przetworzenia dowolnej najwyższego poziomu klasy lub definicji funkcji. Jeśli ustawiono punkt przerwania, może się okazać debuger istotnej części — sposób za pomocą deklaracji klasy. To zachowanie, które są prawidłowe, mimo że jest to czasami Zaskakujące.

Można dostosować warunków, w których punkt przerwania zostaje wyzwolona, takie jak przerywanie tylko wtedy, gdy zmienna jest ustawiona na określoną wartość lub wartości zakresu. Aby ustawić warunki, kliknij prawym przyciskiem myszy punkt przerwania czerwoną kropkę, wybierz **warunek**, następnie utwórz wyrażeń przy użyciu kodu w języku Python. Aby uzyskać szczegółowe informacje na temat tej funkcji w programie Visual Studio, zobacz [warunków punktu przerwania](../debugger/using-breakpoints.md#breakpoint-conditions)

Podczas ustawiania warunków, można również ustawić **akcji** i utworzyć komunikat do logowania się w oknie danych wyjściowych, opcjonalnie automatycznie kontynuowanie wykonywania. Rejestrowanie komunikatów tworzy tzw *śledzenia* bez dodawania kodu rejestrowania do aplikacji bezpośrednio:

![Tworzenie punktu śledzenia za pomocą punktu przerwania](media/debugging-tracepoint.png)

### <a name="stepping-through-code"></a>Krokowe wykonywanie kodu

Po zatrzymaniu w punkcie przerwania, możesz mieć różne sposoby, aby przejść przez kod lub uruchomić bloki kodu przed przerwaniem ponownie. Te polecenia są dostępne w wielu miejscach, w tym narzędzi debugowania najważniejsze **debugowania** menu w menu kontekstowym kliknij prawym przyciskiem myszy w edytorze kodu, a także za pośrednictwem skróty klawiaturowe (za pośrednictwem nie wszystkie polecenia są we wszystkich miejscach):

| Funkcja | Keystroke | Opis |
| --- | --- | --- |
| Kontynuuj | F5 | Uruchamia kod, aż do osiągnięcia następnego punktu przerwania. |
| Wkrocz | F11 | Uruchamia następnej instrukcji i zatrzymuje. Jeśli następna instrukcja jest wywołaniem funkcji, debuger zatrzymuje się w pierwszym wierszu wywoływanej funkcji. |
| Przekrocz nad | F10 | Uruchamia następnej instrukcji, łącznie z wywołania do funkcji (uruchomionego jego kodu) i zastosowanie wszelkich wartości zwracanej. Pominięcie pozwala łatwo pominąć funkcje, które nie trzeba do debugowania. |
| Wyjdź | Shift+F11 | Uruchamia kod aż do zakończenia bieżącej funkcji, a następnie kroki do instrukcji wywołujące.  To polecenie jest przydatne, gdy nie jest konieczne do debugowania w pozostałej części bieżącej funkcji. |
| Uruchom do kursora | Ctrl+F10 | Uruchamia kod do lokalizacji karetki w edytorze. To polecenie umożliwia łatwe pominąć segment kodu, który nie jest potrzebny do debugowania. |
| Ustaw następną instrukcję | Ctrl+Shift+F10 | Zmienia bieżący przebieg punktów w kodzie do lokalizacji karetki. Polecenie to pozwala na pominięcie segmentu kodu są uruchamiane w ogóle, np. kiedy kod jest uszkodzony lub tworzy i niechciane efekt uboczny. |
| Pokaż następną instrukcję | Alt+Num * | Powrót do następnej instrukcji do uruchomienia. To polecenie jest przydatne, jeśli został wyszukiwanie w kodzie, a nie pamiętasz, gdzie debuger został zatrzymany. |

### <a name="inspecting-and-modifying-values"></a>Sprawdzanie i modyfikowanie wartości

Po zatrzymaniu debugera, można sprawdzić i modyfikować wartości zmiennych. Okno czujki służy także do monitorowania poszczególnych zmiennych, jak również wyrażeń niestandardowych. (Zobacz [sprawdzanie zmiennych](../debugger/getting-started-with-the-debugger.md#inspect-variables-with-the-autos-and-locals-windows) Aby uzyskać ogólne informacje.)

Aby wyświetlić wartość, używając DataTips, po prostu umieść kursor myszy nad dowolnej zmiennej w edytorze. Możesz kliknąć na wartości, aby ją zmienić:

![Etykietki danych w debugerze](media/debugging-quick-tips.png)

Okno zmiennych automatycznych (**Debuguj > Windows > automatyczne**) zawiera zmienne i wyrażenia, które znajdują się blisko bieżącej instrukcji. Możesz kliknij dwukrotnie ikonę w kolumnie wartość lub wybierz i naciśnij klawisz F2, aby edytować wartość:

![Okno zmiennych automatycznych w debugerze](media/debugging-autos-window.png)

Okno zmiennych lokalnych (**Debuguj > Windows > lokalne**) Wyświetla wszystkie zmienne, które znajdują się w bieżącym zakresie i mogą być edytowane ponownie:

![Okno zmiennych lokalnych w debugerze](media/debugging-locals-window.png)

Aby uzyskać więcej informacji na temat używania zmiennych automatycznych i zmiennych lokalnych, zobacz [sprawdzanie zmiennych w zmiennych automatycznych i zmiennych lokalnych Windows](../debugger/autos-and-locals-windows.md).

Okna czujki (**Debuguj > Windows > Obejrzyj > Obejrzyj 1 – 4**) umożliwiają wprowadź dowolnego wyrażenia języka Python i wyświetlić wyniki. Wyrażenia są ponownie oceniane dla każdego kroku:

![Okno czujki w debugerze](media/debugging-watch-window.png)

Aby uzyskać więcej informacji na temat korzystania z Obejrzyj zobacz [Ustawianie wyrażenia kontrolnego na zmiennych przy użyciu wyrażenie kontrolne i QuickWatch Windows](../debugger/watch-and-quickwatch-windows.md).

Podczas kontroli wartość ciągu (`str`, `unicode`, `bytes`, i `bytearray` są wszystkie traktowane jako parametry w tym celu), ikonę lupy pojawia się po prawej stronie wartości. Klikając ikonę Wyświetla wartość ciągu bez cudzysłowów w oknie dialogowym okna podręcznego, opakowywanie i przewijanie, co jest przydatne dla ciągów długich. Ponadto, wybierając strzałkę listy rozwijanej na ikonie służy do wybierania zwykły tekst, HTML, XML i JSON wizualizacji:

![Wizualizatory ciągu](media/debugging-string-visualizers.png)

HTML, XML i JSON wizualizacje są wyświetlane w osobne okno podręczne windows za pomocą widoków wyróżniania i drzewa składni.

### <a name="exceptions"></a>Wyjątki

Jeśli wystąpi błąd w programie podczas debugowania, ale go nie masz obsługi wyjątków, debuger przerywa punkcie wyjątek:

![Okno podręczne wyjątku](media/debugging-exception-popup.png)

W tym momencie można sprawdzić stan programu, w tym stos wywołań. Jednak Jeśli spróbujesz przejść przez kod wyjątku będzie nadal jest zgłaszana, dopóki nie jest to obsługiwane lub kończy działanie programu.

**Debuguj > Windows > Ustawienia wyjątków** polecenia menu wyświetlenie okna, w którym możesz rozwinąć **wyjątki Python**:

![Okno wyjątków](media/debugging-exception-settings.png)

Pole wyboru dla każdej kontrolki wyjątku czy debugera *zawsze* przerwanie wykonywania przy jest zgłaszany. Zaznacz to pole wyboru, gdy chcesz przerwać częściej dla określonego wyjątku.

Domyślnie większość wyjątków Przerwij, gdy nie można odnaleźć obsługi wyjątków w kodzie źródłowym. Aby zmienić to zachowanie, kliknij prawym przyciskiem myszy każdy wyjątek i zmodyfikuj **kontynuować po nieobsługiwany w kodzie użytkownika** opcji. Wyczyść to pole, gdy chcesz przerwać rzadziej, dla wyjątku.

Aby skonfigurować wyjątek, który nie ma na tej liście, kliknij **Dodaj** przycisk, aby ją dodać. Nazwa musi odpowiadać imię i nazwisko wyjątku.

## <a name="project-debugging-options"></a>Opcje debugowania projektu

Domyślnie debuger zaczyna się od program standardowy uruchamianie języka Python, żadnych argumentów wiersza polecenia z i innych specjalnych ścieżek lub warunki. Opcje uruchamiania są zmieniane przy użyciu właściwości debugowania projektu dostępne przez kliknięcie prawym przyciskiem myszy projekt w Eksploratorze rozwiązań, wybierając **właściwości**i wybierając polecenie **debugowania** kartę.

![Właściwości debugowania projektu](media/debugging-project-properties.png)

### <a name="launch-mode-options"></a>Opcje trybu uruchamiania

| Opcja | Opis |
| --- | --- |
| Standardowa uruchamianie języka Python | Zastosowań debugowanie kodu napisanego w języku Python przenośny, zgodny z CPython, IronPython i wariantami, takimi jak Stackless języka Python. Zapewnia najlepsze środowisko do debugowania czystym kodzie języka Python. Po dołączeniu do uruchomionej `python.exe` procesu, uruchom ten jest używany. Udostępnia również w tym uruchamianie programu [debugowanie w trybie mieszanym](debugging-mixed-mode-c-cpp-python-in-visual-studio.md) CPython, co umożliwia bezproblemowe krok między kodu C/C++ oraz kodu w języku Python. |
| Uruchamianie w sieci Web | Uruchamia domyślną przeglądarkę w momencie uruchomienia i powoduje włączenie debugowania szablonów. Zobacz [debugowania szablonów sieci Web](python-web-application-project-templates.md#debugging) sekcji, aby uzyskać więcej informacji. |
| Uruchamianie z sieci Django Web | Taka sama jak uruchamiającego w sieci Web i wyświetlane tylko w przypadku zapewnienia zgodności. |
| IronPython (.NET) launcher | Używa debugera platformy .NET, które działa tylko w przypadku IronPython, ale umożliwia przechodzenie między każdego projektu języka .NET, w tym C# i VB. Uruchamianie tego programu jest używana, jeśli dołączanie do uruchomionego procesu .NET, który jest hostem Ironpythonu. |

### <a name="run-options-search-paths-startup-arguments-and-environment-variables"></a>Opcje uruchamiania (ścieżki wyszukiwania, argumenty uruchomienia i zmiennych środowiskowych)

| Opcja | Opis |
| --- | --- |
| Ścieżki wyszukiwania | Te wartości są zgodne, co to jest wyświetlana w węźle ścieżek wyszukiwania projektu w Eksploratorze rozwiązań. Możesz zmodyfikować tę wartość w tym miejscu, ale znacznie łatwiej używać Eksploratora rozwiązań, który pozwala na przeglądanie folderów i automatycznie konwertuje ścieżki względnej formularza. |
| Argumenty skryptu | Te argumenty zostaną dodane do polecenia używane do uruchomienia skryptu, pojawiające się po nazwę pliku skryptu. Pierwszy element w tym miejscu jest dostępne do skryptu jako `sys.argv[1]`, drugi jako `sys.argv[2]`i tak dalej. |
| Interpreter argumentów | Te argumenty zostaną dodane do wiersza polecenia uruchamiania przed nazwą skryptu. Są często używanych argumentów tutaj `-W ...` z ostrzeżeniami kontroli, `-O` nieco zoptymalizować program, i `-u` używać Niebuforowane we/wy. Użytkownicy języka IronPython prawdopodobnie to pole służy do przekazywania `-X` opcji, taką jak `-X:Frames` lub `-X:MTA`. |
| Cesta k Interpretu | Zastępuje ścieżkę skojarzoną z bieżącego środowiska.  wartość może być przydatne w przypadku uruchamiania skryptu za pomocą niestandardowych interpretera. |
| Zmienne środowiskowe | W tym wielowierszowego pola tekstowego, Dodaj wpisy formularza `NAME=VALUE`. Ponieważ to ustawienie zostanie zastosowane ostatnie, u góry, wszelkie istniejące zmienne środowiskowe globalnego i po `PYTHONPATH` jest ustawiona zgodnie z ustawieniem ścieżki wyszukiwania może służyć do ręcznie przezwyciężyć żadnego z tych innych zmiennych. |

<a name="the-debug-interactive-window"></a>

## <a name="immediate-and-interactive-windows"></a>Natychmiastowe i interaktywne systemu windows

Istnieją dwa okna interaktywnego, można użyć podczas sesji debugowania: standardowy programu Visual Studio bezpośrednim i oknie interaktywnym debugowania języka Python.

Okno bezpośrednie (**Debuguj > Windows > bezpośrednie**) jest używany do szybkiej oceny wyrażeń języka Python i inspekcji lub przypisania zmiennych w uruchomionego programu. Zobacz ogólne [bezpośrednim](../ide/reference/immediate-window.md) artykuł, aby uzyskać szczegółowe informacje.

Okna interaktywnego debugowania języka Python (**Debuguj > Windows > Python debugowanie interakcyjne**) jest bogatszy, ponieważ zapewnia pełną [interaktywna pętla REPL](python-interactive-repl-in-visual-studio.md) środowisko dostępne podczas debugowania, w tym pisania i uruchamianie kodu. Automatycznie łączy się żaden proces uruchomiony w debugerze, za pomocą uruchamiania standardowego języka Python (łącznie procesów dołączonym za pośrednictwem **Debuguj > Dołącz do procesu**). Nie, jednak jest dostępne podczas debugowania języka C/C++ w trybie mieszanym.

![Okno interaktywne debugowania języka Python](media/debugging-interactive.png)

Debugowanie interakcyjne okno obsługuje specjalne meta polecenia oprócz [standardowe polecenia REPL](python-interactive-repl-in-visual-studio.md#meta-commands):

| Polecenie | Argumenty | Opis |
| --- | --- | --- |
| `$continue`, `$cont`, `$c` | Zostanie uruchomiony program z bieżącej instrukcji. |
| `$down`, `$d` | Przenieś bieżące ramce jeden poziom w dół w ślad stosu. |
| `$frame` | | Wyświetla bieżący identyfikator ramki.
| `$frame` | Identyfikator ramki | Zmienia bieżące ramce do ramki o określonym identyfikatorze.
| `$load` | Ładuje poleceń z pliku i uruchamia do czasu ukończenia |
| `$proc` |  | Wyświetla bieżący identyfikator procesu. |
| `$proc` | Identyfikator procesu | Zmienia bieżący proces na identyfikator określonego procesu. |
| `$procs` | | Wyświetla listę aktualnie debugowanych procesów. |
| `$stepin`, `$step`, `$s` | Kroki opisane w następnym wywołaniu funkcji, jeśli jest to możliwe. |
| `$stepout`, `$return`, `$r` | Kroki poza bieżącą funkcję. |
| `$stepover`, `$until`, `$unt` | Pomija wywołanie funkcji next. |
| `$thread` | | Wyświetla bieżący identyfikator wątku. |
| `$thread` | Identyfikator wątku | Zmienia bieżący wątek na identyfikator określonego wątku. |
| `$threads` | | Wyświetla listę wątków obecnie debugowane. |
| `$up`, `$u` | | Przenieś bieżący poziom jednej ramki w górę ślad stosu. |
| `$where`, `$w`, `$bt` | Wyświetla listę ramki dla bieżącego wątku. |

Należy pamiętać, że okien debugera standardowych, takich jak procesy, wątki i stos wywołań nie są zsynchronizowane z okna interaktywnego debugowania. Zmiana aktywnego procesu, wątku lub ramki w oknie interaktywnym debugowania nie wpływa na innych oknach debugera. Podobnie zmianę aktywnego procesu, wątku lub ramki w oknach debugera nie wpływa na debugowanie interakcyjne okno.

Debugowanie interakcyjne okno ma swój własny zestaw opcji, które są dostępne za pośrednictwem **Narzędzia > Opcje > Python Tools > debugowanie interakcyjne okno**. W przeciwieństwie do regularnych okno interaktywne języka Python ma oddzielnego wystąpienia dla każdego środowiska Python, istnieje tylko jeden debugowanie interakcyjne okno i zawsze używa interpretera języka Python dla debugowanego procesu. Zobacz [opcje - Opcje debugowania](python-support-options-and-settings-in-visual-studio.md#debugging-options).

![Okno interaktywne opcje debugowania](media/debugging-interactive-options.png)

## <a name="use-the-experimental-debugger"></a>Używaj debugera eksperymentalnego

Począwszy od programu Visual Studio 2017 (wersja zapoznawcza) 4.0, możesz zdecydować się na użyciu "debugera eksperymentalnego", który jest oparty na wersji ptvsd 4.1 lub nowszym. Aby włączyć, wybierz pozycję **narzędzia** > **opcje** menu polecenia, a następnie przejdź do **Python** > **eksperymentalne**w okno dialogowe Opcje i wybierz pozycję **używaj debugera eksperymentalnego.**

Debugera eksperymentalnego jest zgodny z tylko ograniczony środowiska Python, zgodnie z opisem w poniższej tabeli:

| Wersja języka Python | Zgodne z debugera eksperymentalnego |
| --- | --- |
| 2.6 | Nie |
| 2.7 | Tak |
| 3.1 lub 3.4 | Nie |
| 3.5 i nowsze | Tak |
| IronPython | Nie |

Jeśli spróbujesz używaj debugera eksperymentalnego niezgodne środowisko programu Visual Studio pokazuje błąd, "Niezgodne z tym środowiskiem jest debugera":

![Debuger jest niezgodne z powodu następującego błędu środowiska, korzystając z debugera eksperymentalnego](media/debugging-experimental-incompatible-error.png)

Wybierz **wyłączyć debugera eksperymentalnego** polecenia, które czyści **używaj debugera eksperymentalnego** opcji.

> [!Note]
> To ostrzeżenie nie jest obecnie wyświetlany dla języka Python 3.3 i 3.4.

Jeśli po zainstalowaniu starszej wersji ptvsd w bieżącym środowisku (na przykład starszej wersji 4.0.x wersji 3.x wymagane do zdalnego debugowania), Visual Studio wyświetla błąd "debugera nie można załadować pakietu" albo ostrzeżenie "debuger pakiet są nieaktualne":

![Pakiet debugera nie można załadować błąd przy użyciu debugera eksperymentalnego](media/debugging-experimental-version-error.png)

![Pakiet debugera jest nieaktualna, ikona ostrzeżenia, gdy za pomocą debugera eksperymentalnego](media/debugging-experimental-version-warning.png)

Aby zarządzać ptvsd instalację, należy użyć **pakietów** karcie **środowiska Python** okna lub użyj następujących poleceń w wierszu polecenia:

```ps
# Uninstalling ptvsd causes VS to default to its bundled 4.1.x version.
pip uninstall ptvsd

# Upgrading ptvsd gives you the latest version, which may be newer than the bundled version.
# -pre is required to allow pre-release versions as currently required by the experimental debugger.
pip install --upgrade ptvsd -pre
```

> [!Important]
> Mimo że można zignorować to ostrzeżenie dla niektórych wersji ptvsd, Visual Studio mogą nie działać poprawnie.

## <a name="see-also"></a>Zobacz także

Aby uzyskać szczegółowe informacje dotyczące debugera programu Visual Studio, zobacz [debugowania w programie Visual Studio](../debugger/debugger-feature-tour.md).
