---
title: Interaktywny REPL Python w programie Visual Studio | Dokumentacja firmy Microsoft
description: "Jak używać okno interaktywne (REPL) dla języka Python kodu w programie Visual Studio dla rozwoju szybkie kodu."
ms.custom: 
ms.date: 07/13/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: 
ms.topic: article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: e41e4af21a524215550c581b1e29efc2261aaa8f
ms.sourcegitcommit: a07b789cc41ed72664f2c700c1f114476e7b0ddd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2018
---
# <a name="working-with-the-python-interactive-window"></a>Praca z okno interaktywne Python

Program Visual Studio udostępnia okno interaktywne odczytu oceny Drukuj pętli (REPL) dla każdego środowiska Python, które poprawia REPL pobrać o `python.exe` w wierszu polecenia. Okno interaktywne (otwartej z **Widok > inne okna > &lt;środowiska&gt; Interactive** polecenia menu) pozwala wprowadzić dowolny kod języka Python i wyświetlania wyników bezpośrednim. Ten sposób kodowania pomaga informacje i Poeksperymentuj z interfejsów API i bibliotek oraz interakcyjnie tworzenie pracy kodu do uwzględnienia w projektach.

![Okno interaktywne Python](media/interactive-window.png)

Visual Studio zawiera szereg trybów REPL dla języka Python do wyboru:

| REPL | Opis | Edytowanie | Debugowanie | Obrazy |
| --- | --- | --- | --- | --- |
| Standard | Domyślne REPL, rozmów bezpośrednio Python. | Standard edycji (multiline itp.). | Tak, za pomocą `$attach` | Nie |
| Debugowanie | Domyślne REPL, rozmów na debugowanym procesie Python | Standardowa edycji | Tylko debugowania | Nie |
| IPython | REPL komunikuje się IPython wewnętrznej bazy danych | Polecenia IPython, udogodnień Pylab | Nie | Tak, wbudowane w REPL |
| IPython bez Pylab | REPL komunikuje się IPython wewnętrznej bazy danych | Standardowe IPython | Nie | Tak, strona potwierdzenia | 

W tym temacie opisano **standardowe** i **debugowania** REPL trybów. Aby uzyskać więcej informacji o trybach IPython, zobacz [przy użyciu IPython REPL](interactive-repl-ipython.md).

Aby uzyskać szczegółowe wskazówki, wraz z przykładami, w tym interakcji w edytorze, np. Ctrl + Enter, zobacz [samouczek krok 3: Korzystanie z okna interaktywny REPL](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md). 

|   |   |
|---|---|
| ![Ikona aparatu film wideo](../install/media/video-icon.png "obejrzeć film wideo") | [Obejrzyj film (Microsoft Virtual Academy)](https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Python-Interactive-Window-gJYKY5LWE_4605918567) na okno interaktywne (2 m 22s).|

## <a name="opening-an-interactive-window"></a>Otwieranie okna interaktywnego

Istnieje kilka sposobów, aby otworzyć okno interaktywne dla środowiska.

Po pierwsze, przejdź do okna środowiska Python (**Widok > inne okna > środowiska Python** lub Ctrl-K, Ctrl-") i wybierz **Otwórz okno interaktywne** polecenia lub przycisku dla wybranego środowiska .

![Interakcyjne łącze okna w oknie środowiska Python](media/interactive-window-opening.png)

Drugie w dolnej części **Widok > inne okna** menu jest **okna interaktywnego Python** polecenie dla danego środowiska domyślne, a także polecenia, aby przejść do okna środowiska:

![Menu okna interaktywnego elementy w widoku > inne okna](media/interactive-window-menu.png)

Trzecie, można otworzyć okna interaktywnego do uruchomienia pliku w projekcie, lub dla plików autonomicznych, wybierając **Debuguj > wykonanie [projektu | Pliku] w trybie interaktywnym Python** polecenia menu (Alt + Shift + F5):

![Wykonanie projektu w menu interaktywny język Python](media/interactive-execute-project.png)

Na koniec wybierz kod w pliku i użyć [Wyślij kod na polecenie interaktywne](#send-code-to-interactive-command) opisane poniżej.

## <a name="interactive-window-options"></a>Opcje interakcyjne okna

Można kontrolować różne aspekty okno interaktywne za pośrednictwem **Narzędzia > Opcje > Narzędzia Python Tools > Windows interakcyjne** (zobacz [opcje](python-support-options-and-settings-in-visual-studio.md)):

![Opcje interakcyjne okna języka Python](media/options-interactive-windows.png)

## <a name="using-the-interactive-window"></a>Przy użyciu okna interaktywnego

Po otwarciu okna interaktywnego rozpoczęciem wprowadzania kodu wiersz po wierszu w `>>>` wiersza. Okno interaktywne wykonuje każdego wiersza, jak wprowadzić go, co obejmuje importowanie modułów, definiowanie zmiennych i tak dalej:

![Okno interaktywne Python](media/interactive-window.png)

Wyjątek stanowi podczas dodatkowe wiersze kodu są potrzebne do podejmowania pełną instrukcję, takie jak kiedy `for` instrukcji kończy się dwukropkiem, jak pokazano powyżej. W takich przypadkach wiersza zmieni się na `...` wskazujący, że należy wprowadzić dodatkowe wiersze do bloku, jak pokazano w wierszach czwarty i piąty na rysunku powyżej. Po naciśnięciu klawisza Enter w pustym wierszu okno interaktywne zamyka bloku i uruchamia go w interpretera.

> [!Tip]
> Okno interaktywne poprawia zwykle Python wiersza polecenia REPL wystąpić przez automatycznie wcięcia instrukcji, które należą do zakresu otaczającego. Swoją historię (przypomnieć o strzałkę w górę) udostępnia również wielowierszowy elementów wiersza polecenia REPL stanowi tylko pojedynczych wierszy.

<a name="meta-commands"></a> Okno interaktywne obsługuje również kilka meta polecenia. Wszystkie polecenia meta rozpoczynać `$`, i można wpisać `$help` spowoduje wyświetlenie listy poleceń meta i `$help <command>` Aby uzyskać szczegóły obciążenia dla określonego polecenia.

| Meta-polecenia | Opis |
| --- | --- |
| `$$` | Wstawia komentarz, co jest przydatne do kodu komentarza w całej sesji. |
| `$attach` | Dołącza debuger programu Visual Studio do procesu okna REPL, aby włączyć debugowanie. |
| `$cls`, `$clear` | Czyści zawartość okna edytora, pozostawiając historię i kontekst wykonania bez zmian. |
| `$help` | Wyświetl listę poleceń, lub pomoc dotyczącą danego polecenia. |
| `$load` | Ładuje polecenia z pliku i jest wykonywana do czasu ukończenia. |
| `$mod` | Zmienia bieżący zakres na nazwę określonego modułu. |
| `$reset` | Przywraca stan początkowy środowiska wykonawczego, ale zachowuje historii. |
| `$wait` | Oczekuje na co najmniej określoną liczbę milisekund. |

Polecenia są również extensible przez rozszerzenia programu Visual Studio przez implementację i eksportowanie `IInteractiveWindowCommand` ([przykład](https://github.com/Microsoft/PTVS/blob/master/Python/Product/PythonTools/PythonTools/Repl/InteractiveWindowCommands.cs#L85)).

## <a name="switching-scopes"></a>Przełączanie zakresów

Domyślnie okno interaktywne dla projektu obejmuje pliku uruchomienia projektu tak, jakby korzystania z wiersza polecenia. Dla autonomicznego pliku tego zakresy do tego pliku. W dowolnym momencie jednak menu rozwijane u góry okna interaktywnego pozwala zmienić zakres w dowolnym momencie podczas sesji REPL:

![Okno interaktywne zakresów](media/interactive-scopes.png)

Po zaimportowaniu modułu, na przykład wpisanie `import importlib`, opcje dostępne w listy rozwijanej, aby przełączyć się do dowolnego zakresu, w tym module. Komunikat w oknie interaktywnym wskazuje także nowy zakres, co pozwala na śledzenie pochodzeniu niektórych stan podczas sesji.

Wprowadzanie `dir()` w zakresie Wyświetla prawidłowych identyfikatorów w tym zakresu, w tym funkcji nazw, klasy i zmienne. Na przykład za pomocą `import importlib` następuje `dir()` zawiera następujące:

![Okno interaktywne w zakresie importlib](media/interactive-importlib-scope.png)

<a name="sending-code-to-interactive"</a>

## <a name="send-code-to-interactive-command"></a>Wyślij kod na interakcyjne

Oprócz pracy do interaktywnego okna bezpośrednio, można wybrać kodu w edytorze, kliknij prawym przyciskiem myszy i wybierz polecenie **przesyłają Interactive** lub naciśnij klawisze Ctrl + Enter.

![Wyślij do interaktywnego polecenie](media/interactive-send-to.png)

To polecenie jest przydatne w przypadku tworzenia interakcyjnych lub ewolucyjny kodu, łącznie z testowaniem kodzie, jak w przypadku tworzenia. Na przykład po wysyłane do okna interaktywnego fragment kodu i widoczne dane wyjściowe, naciśnij klawisz strzałki w górę ponownie wyświetlić kod, zmodyfikuj go i przetestować go szybko przez naciśnięcie klawiszy Ctrl + Enter. (Naciśnij klawisz Enter na końcu danych wejściowych jest wykonywana, ale naciśnięcie klawisza Enter w trakcie wprowadzania wstawia nowy wiersz). Po utworzeniu kodu, który ma, można go łatwo skopiować do pliku projektu.

> [!Tip]
> Domyślnie program Visual Studio usuwa >>> i... REPL monity podczas wklejania do edytora kodu z okna interaktywnego. To zachowanie można zmienić na **Narzędzia > Opcje > Edytor tekstu > Python > Zaawansowane** karcie przy użyciu **Wklej usuwa monitów REPL** opcji. Zobacz [opcji - różne opcje](python-support-options-and-settings-in-visual-studio.md#miscellaneous-options).

<!-- After 15.3 is released, you can also press "Undo" after pasting to restore prompts. Press "Undo" a second time to remove the pasted code entirely. -->

Korzystając z pliku kodu jako Notatnik, często mają niewielki blok kodu, który chcesz wysłać jednocześnie. Aby zgrupować kodu, oznacz kodu jako *komórki kodu* przez dodanie komentarza począwszy `#%%` na początku komórki, która kończy się poprzedniego. Komórki kodu można zwinięte i rozwinięte, a w komórce kodu przy użyciu klawiszy Ctrl + Enter wysyła całą komórki do okna interaktywnego i przechodzi do następnego.

Visual Studio komórki kodu począwszy komentarze, takich jak funkcja wykrywa także `# In[1]:`, która jest format podczas eksportowania notesu Jupyter jako plik Python. Wykrywanie ułatwia Uruchom notesu z [notesów Azure](https://notebooks.azure.com/) pobierania jako plik Python, otwierając w programie Visual Studio i uruchamianie każdej komórki za pomocą klawiszy Ctrl + Enter.

![Komórki kodu interaktywnego](media/interactive-code-cells.png)

## <a name="intellisense-behavior"></a>Zachowanie funkcji IntelliSense

Okno interaktywne obejmuje IntelliSense oparte na obiekty na żywo, w przeciwieństwie do edytora kodu, w którym IntelliSense jest oparta na tylko analiza kodu źródłowego. Te sugestie dotyczą więcej prawidłowe w oknie interaktywnym, szczególnie w przypadku dynamicznie wygenerowanego kodu. Wadą jest to, że funkcje z efektami ubocznymi (np. rejestrowanie komunikatów) może mieć wpływ na Twoje środowisko programistyczne.

Jeśli to zachowanie jest problem, Zmień ustawienia w obszarze **Narzędzia > Opcje > Narzędzia Python Tools > interakcyjne Windows** w **tryb uzupełniania** grupy, zgodnie z opisem w [opcje — Opcje interakcyjne Windows](python-support-options-and-settings-in-visual-studio.md#interactive-windows-options).
