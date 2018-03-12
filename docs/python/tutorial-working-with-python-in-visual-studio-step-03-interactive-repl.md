---
title: "Praca z języka Python w programie Visual Studio, w kroku 3, w oknie interaktywny REPL | Dokumentacja firmy Microsoft"
description: "Krok 3 samouczka core do pracy z języka Python w programie Visual Studio, obejmujące okno Python interaktywny REPL."
ms.custom: 
ms.date: 01/16/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: 
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 598aa6332d69f7818f9f67134c3207a9bd365757
ms.sourcegitcommit: 3285243d6c0521266053340fe06505885d12178b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2018
---
# <a name="step-3-using-the-interactive-repl-window"></a>Krok 3: W oknie interaktywny REPL

**Poprzedni krok: [kodu napisanego i uruchomione](tutorial-working-with-python-in-visual-studio-step-02-writing-code.md)**

Visual Studio *okna interaktywnego* dla języka Python zapewnia obsługę sformatowanego odczytu oceny drukowania pętli (REPL), który znacznie skraca comiesięcznych edytowania, kompilowania i debugowania. Okno interaktywne zawiera wszystkie funkcje środowisko REPL wiersza polecenia języka Python. On również ułatwia bardzo wymiany kodu z plików źródłowych w programie Visual Studio edytora, które w przeciwnym razie jest skomplikowane przy użyciu wiersza polecenia.

1. Otwórz okno interaktywne, klikając prawym przyciskiem myszy projekt środowiska Python w Eksploratorze rozwiązań (na przykład "Python 3,6 (32-bitowy)" pokazano na rysunku wcześniej) i wybierając **Otwórz okno interaktywne**. Możesz również wybrać **Widok > inne okna > Windows interakcyjne Python** z poziomu menu głównego programu Visual Studio.

1. Otwiera okno interaktywne poniżej edytora ze standardem `>>>` wiersza REPL dla języka Python. **Środowiska** listy rozwijanej można wybrać określonego interpreter do pracy z. Często również mają być okno interaktywne większe, co można zrobić, przeciągając separatora między dwoma systemu windows:

    ![Okno interaktywne Python i przeciągając zmiany rozmiaru](media/vs-getting-started-python-11-interactive1b.png)

    > [!Tip]
    > Możesz zmienić rozmiar wszystkich okien w programie Visual Studio przez przeciągnięcie granicznych separatorów. Można również przeciągnij windows niezależnie od ramki Visual Studio i rozmieszczenia w dowolny sposób w ramce. Aby uzyskać szczegółowe informacje, zobacz [dostosowywanie układów okien](../ide/customizing-window-layouts-in-visual-studio.md).

1. Wprowadź kilka instrukcje, takie jak `print("Hello, Visual Studio")` i wyrażenia, takich jak `123/456` natychmiastowego wyników:

    ![Python okna interaktywnego bezpośrednich wyników](media/vs-getting-started-python-12-interactive2.png)

1. Po rozpoczęciu zapisywania wielowierszowy instrukcji, takie jak definicja funkcji, okno interaktywne pokazuje języka Python `...` Monituj o kontynuowanie wierszy, które, w przeciwieństwie do wiersza polecenia REPL, umożliwia automatyczne wcięcia:

    ![Okno interaktywne Python z kontynuacji — instrukcja](media/vs-getting-started-python-13-interactive3.png)

1. Okno interaktywne zapewnia pełną historię wszystko, co wprowadzono i poprawia wiersza polecenia REPL z elementów historii wielowierszowy. Na przykład można łatwo Odwołaj całą definicję `f` działać jako pojedyncza jednostka i łatwo zmienić nazwę `make_double`, zamiast ponownego tworzenia funkcja wiersz po wierszu.

1. Visual Studio można wysłać wiele wierszy kodu w oknie edytora do okna interaktywnego. Ta funkcja umożliwia Obsługa kodu w pliku źródłowym i łatwe wysyłanie Wybieranie części do okna interaktywnego. Następnie można pracować z tych fragmentów kodu w szybkie środowisko REPL zamiast konieczności uruchamiania całego programu. Aby wyświetlić tę funkcję, Zastąp najpierw `for` pętli w `PythonApplication1.py` pliku następującym kodem:

    ```python
    # Create a string with spaces proportional to a cosine of x in degrees
    def make_dot_string(x):
        return ' ' * int(20 * cos(radians(x)) + 20) + 'o'
    ```

1. Wybierz tylko `import` i `from` instrukcje w `.py` pliku, kliknij prawym przyciskiem myszy i wybierz **przesyłają Interactive** (lub nacisnąć klawisze Ctrl + Enter). Fragment kodu jest natychmiast wklejane okno interaktywne i uruchom. Teraz wybierz `make_dot_string` funkcji i powtórz tego samego polecenia, które uruchamia ponownie ten fragment kodu. Ponieważ kod definiuje funkcję, można szybko sprawdzić tej funkcji, wywołując kilka razy:

    ![Wysyłanie kodu do okna interaktywnego i testowanie go](media/vs-getting-started-python-14-interactive4.png)

    > [!Tip]
    > Przy użyciu klawiszy Ctrl + Enter w edytorze *bez* zaznaczenia uruchamia bieżącego wiersza kodu w oknie interaktywnym i automatycznie umieszcza karetki w następnym wierszu. Przy użyciu tej funkcji naciskając klawisze Ctrl + Enter wielokrotnie oferują wygodny sposób do wykonania kroków opisanych swój kod, który nie jest możliwe przy użyciu wiersza polecenia języka Python. Umożliwia również wykonywać krokowo kodu bez uruchamiania debugera i niekoniecznie uruchamiania programu od początku.

1. Można również skopiować i wkleić wiele wierszy kodu do interaktywnego okna z dowolnego źródła, takich jak poniżej, fragment, który jest trudne do wykonania replikacja wiersza polecenia języka Python Po wklejeniu, okno interaktywne działa ten kod tak, jakby wpisał w:

    ```python
    for i in range(360):
        s = make_dot_string(i)
        print(s)
    ```

    ![Wklejanie wielu wierszy kodu za pomocą wysyłania interakcyjne](media/vs-getting-started-python-15-interactive5.png)

1. Jak widać, ten kod działa prawidłowo, ale jego dane wyjściowe nie jest bardzo inspiring. Krok różne wartości w `for` pętli czy Pokaż więcej cosinus wave. Na szczęście ponieważ cały `for` pętla jest w historii REPL jako pojedyncza jednostka, łatwo wrócić do poprzedniej strony i wprowadzanie niezależnie od zmian możesz chcieć, a następnie testować funkcji ponownie. Naciśnij klawisz strzałki w górę do pierwszego wycofywania `for` pętli. Następnie naciśnij klawisz strzałki lewo lub w prawo, aby rozpocząć nawigowanie w kodzie (dopiero po tym pracy i strzałki w dół w dalszym ciągu przechodzenie między historii). Przejdź do i zmienić `range` specyfikacja `range(0, 360, 12)`. Naciśnij klawisze Ctrl + Enter (w dowolnym miejscu kodu) aby uruchomić ponownie całej instrukcji:

    ![Edytowanie poprzednich instrukcji w oknie interaktywnym](media/vs-getting-started-python-16-interactive6.png)

1. Powtórz ten proces eksperymentować krok różne ustawienia, do momentu znalezienia wartość, która najlepiej. Można również ustawić wave powtarzania wydłużyć zakresu, na przykład `range(0, 1800, 12)`.
 
1. Po zakończeniu z kodem są zapisywane w oknie interaktywnym, zaznacz go, kliknij prawym przyciskiem myszy i wybierz **Kopiuj kod** (Ctrl + Shift + C), a następnie wkleić do edytora. Zwróć uwagę, jak to specjalne funkcji programu Visual Studio automatycznie pomija żadnych danych wyjściowych, jak również `>>>` i `...` monity. Na przykład na poniższym obrazie pokazano przy użyciu **Kopiuj kod** na zaznaczenie zawiera monity i dane wyjściowe:

    ![Polecenia kodu kopiowania okna interaktywnego wyboru z monitami i danych wyjściowych](media/vs-getting-started-python-17-interactive7.png)

    Możesz wkleić do edytora otrzymujesz jest tylko kod:

    ```python
    for i in range(0, 1800, 12):
        s = make_dot_string(i)
        print(s)
    ```

    Jeśli chcesz skopiować Pełna zawartość okna interaktywnego, w tym monity i dane wyjściowe, wystarczy użyć standardowego **kopiowania** polecenia.

1. Co to po prostu wykonaniu jest umożliwia szybkie środowiska REPL okno interaktywne wyglądają szczegóły dla małych fragment kodu, a następnie wygodnie dodany kod do pliku źródłowym projektu. Jeśli teraz wykonywania kodu ponownie z Ctrl + F5 (lub **debugowania > Uruchom bez debugowania**), zobacz dokładne wyniki potrzebujesz.

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Uruchamianie kodu w debugerze](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)

## <a name="going-deeper"></a>Przechodząc głębiej

- [Przy użyciu okna interaktywnego](python-interactive-repl-in-visual-studio.md)
- [Użycie IPython REPL](interactive-repl-ipython.md)
