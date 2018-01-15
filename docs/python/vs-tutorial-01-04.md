---
title: "Praca z języka Python w programie Visual Studio, krok 4. | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 09/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: get-started-article
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 8d7368bea476a980a196480c4750f0afee57b907
ms.sourcegitcommit: 11740fed01cc602252ef698aaa11c07987b00570
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2018
---
# <a name="step-4-running-code-in-the-debugger"></a>Krok 4: Uruchamianie kodu w debugerze

**Poprzedni krok: [za pomocą okna interaktywny REPL](vs-tutorial-01-03.md)**

Oprócz zarządzania projektami, zapewniając zaawansowanej edycji środowisko i okno interaktywne programu Visual Studio udostępnia kompletne debugowania kodu języka Python. W debugerze można uruchomić kod krok po kroku, w tym każdej iteracji pętli. Można również wstrzymać program zawsze, gdy określone warunki są spełnione. W dowolnym momencie, gdy program jest wstrzymana w debugerze, można zbadać stanu całego programu i zmieniać wartości zmiennych. Takie akcje są istotne dla Śledzenie usterek programu, a także udostępnić pomocy bardzo przydatne uważnie następujące przepływem dokładne programu.

1. Zastąp kod w `PythonApplication1.py` pliku następującym kodem. Ta różnica kod rozszerza `make_dot_string` , dzięki czemu można sprawdzić jego odrębny kroków w debugerze. Pulpit zapewnia również `for` pętli do `main` funkcji i uruchamia go jawnie przez wywołanie tej funkcji:

    ```python
    import sys
    from math import sin, cos, radians

    # Create a string with spaces proportional to a cosine of x in degrees
    def make_dot_string(x):
        rad = radians(x)                             # cos works with radians
        numspaces = int(20 * cos(radians(x)) + 20)   # scale to 0-40 spaces
        str = ' ' * numspaces + 'o'                  # place 'o' after the spaces
        return str

    def main():
        for i in range(0, 1800, 12):
            s = make_dot_string(i)
            print(s)

    main()
    ```

1. Sprawdź, czy kod działa poprawnie naciśnięcie klawisza F5 lub wybierając **Debuguj > Rozpocznij debugowanie** polecenia menu. To polecenie uruchamia kod w debugerze, ale ponieważ nie została jeszcze wykonana żadnych czynności, aby wstrzymać program jest uruchomiona, po prostu Wyświetla szablon wave dla kilku iteracji. Naciśnij dowolny klawisz, aby zamknąć okno danych wyjściowych.

    > [!Tip]
    > Aby zamknąć okno danych wyjściowych automatycznie po zakończeniu program, należy zastąpić `main()` wywołania z następującym kodem:
    >
    > ```python
    > if __name__ == "__main__":
    >     sys.exit(int(main() or 0))
    > ```

1. Ustaw punkt przerwania w `for` instrukcji, klikając szary marginesie tego wiersza lub umieszczając karetki w tym wierszu i przy użyciu **Debuguj > Przełącz punkt przerwania** polecenia (F9). Czerwonej kropki pojawia się na marginesie szary, aby wskazać punkt przerwania (wspomnianego strzałką poniżej):

    ![Ustawienia punktu przerwania](media/vs-getting-started-python-18-debugging1.png)

1. Uruchom ponownie debuger (F5) i ten kod zatrzymuje uruchomione na wiersz z tego punktu przerwania. W tym miejscu możesz sprawdzić wywołanie stosu i sprawdź, czy zmiennych. Zmienne, które są w zakresie są wyświetlane w **automatycznych** okno podczas definiowania; możesz także przełącznik **zmiennych lokalnych** widoku w dolnej części tego okna, aby wyświetlić wszystkie zmienne tego programu Visual Studio znajduje się w bieżący zakres (między innymi funkcji), nawet przed definiowania:

    ![Punkt przerwania możliwości interfejsu użytkownika dla języka Python](media/vs-getting-started-python-19-debugging2b.png)

1. Obserwować debugowania paska narzędzi (pokazana poniżej) wzdłuż górnej części okna programu Visual Studio. Ten pasek narzędzi zapewnia szybki dostęp do najczęściej używanych poleceń debugowania (które również znajdują się na **debugowania** menu):

    ![Istotne debugowania przycisków paska narzędzi](media/vs-getting-started-python-20-debugging3.png)

    Przyciski od lewej do prawej w następujący sposób:
    - **Kontynuować** (F5) uruchamia program, aż do następnego punktu przerwania lub do momentu zakończenia programu.
    - **Przerwij wszystkie** program długotrwałe wstrzymuje (Ctrl + Alt + Break).
    - **Zatrzymaj debugowanie** (Shift + F5) zatrzymuje program, wszędzie tam, gdzie jest i kończy działanie debugera.
    - **Uruchom ponownie** (Ctrl + Shift + F5) zatrzymuje program, wszędzie tam, gdzie jest i ponownie go uruchamia od początku w debugerze.
    - **Pokaż następną instrukcję** (Alt + Num *) przełącza do następnego wiersza kodu do uruchomienia. Jest to najbardziej przydatne w przypadku, gdy nawigację w kodzie podczas sesji debugowania i chcesz szybko powrócić do punktu, w której debuger jest wstrzymana.
    - **Step Into** (F11) uruchamia kolejny wiersz kodu, wprowadzić w nazwie funkcji.
    - **Step Over** (F10) jest uruchamiana w następnym wierszu kodu bez wprowadzania do funkcji o nazwie.
    - **Step Out** (Shift + F11) jest uruchamiana w pozostałej części bieżącej funkcji i zatrzymuje się w wywoływanym kodzie.

1. Przekrocz nad `for` instrukcji przy użyciu **Step Over**. *Wykonywanie krok po kroku* oznacza, że debuger działa bieżącego wiersza kodu, w tym wszystkie wywołania funkcji i natychmiast wstrzymuje ponownie. Powiadomienie jak zmienna `i` teraz jest zdefiniowany w **zmiennych lokalnych** i **automatycznych** systemu windows.

1. Krok w następnym wierszu kodu, który wywołuje `make_dot_string` i zatrzymuje się. Step Over tutaj specjalnie oznacza, że debuger działa całej `make_dot_string` i zatrzymuje się podczas zwraca. Debuger nie zatrzymuje wewnątrz tej funkcji, chyba że istnieje oddzielne punktu przerwania.

1. Kontynuować pominięcie kodu kilka razy więcej i sprawdź, jak wartości w **zmiennych lokalnych** lub **automatycznych** okna zmiany.

1. W **zmiennych lokalnych** lub **automatycznych** okna, kliknij dwukrotnie w **wartość** kolumny albo `i` lub `s` zmienne, aby edytować wartość. Naciśnij klawisz Enter lub kliknij poza tę wartość, aby zastosować zmiany.

1. Kontynuować krokowe wykonywanie kodu za pomocą **Step Into**. Step Into oznacza, że debuger wprowadza wewnątrz każde wywołanie funkcji, dla którego ma debugowania informacje, takie jak `make_dot_string`. Raz wewnątrz `make_dot_string` możesz sprawdzić jej zmiennych lokalnych i w szczególności krokowo kodu.

1. Kontynuuj wykonywanie krok po kroku z Step Into i zwróć uwagę, że gdy dotrzeć do końca `make_dot_string`, następnym krokiem zwraca do `for` pętli przy użyciu nowej wartości zwracanych w `s` zmiennej. Podczas wykonywania kroków ponownie `print` instrukcji, powiadomienia tego kroku do na `print` nie wejdzie w tej funkcji. Jest to spowodowane `print` nie jest napisany w języku Python, ale jest raczej natywnego kodu wewnątrz środowiska uruchomieniowego języka Python.

1. Nadal używać Wkrocz do czasu ponownie tym do `make_dot_string`. Następnie użyj **Wyjdź** i zwróć uwagę, że można wrócić do `for` pętli. Step Out debugera jest uruchamiany w pozostałej części funkcji i automatycznie wstrzymuje w wywoływanym kodzie. Jest to bardzo przydatne, gdy już przeprowadził przez pewną część długich funkcji, którą chcesz debugować, ale nie ma potrzeby krokowo rest i nie chcesz ustawić jawne punktu przerwania w wywoływanym kodzie.

1. Aby kontynuować, program działa do momentu osiągnięcia następnego punktu przerwania, użyj **Kontynuuj** (F5). Ponieważ ma punkt przerwania w `for` pętli, Podziel przy następnej iteracji.

1. Krokowe wykonywanie setki iteracji pętli może być niewygodny, więc Visual Studio umożliwia dodanie *warunku* do punktu przerwania. Debuger następnie wstrzymuje program na punkt przerwania, tylko wtedy, gdy warunek jest spełniony. Na przykład można użyć warunku z punktu przerwania na `for` instrukcję, tak że wstrzymuje tylko gdy wartość `i` przekracza 1600. Aby ustawić ten warunek, kliknij prawym przyciskiem myszy red punktu przerwania kropki (.), a następnie wybierz **warunki...** (Alt + F9, C). W **ustawienia punktów przerwania** menu podręczne, zostanie wyświetlone, wprowadź `i > 1600` jako wyrażenie i wybierz **Zamknij**. Naciśnij klawisz F5, aby kontynuować i sprawdź, czy program ma być uruchamiany dużo iteracji, zanim następnej przerwy.

    ![Ustawienie warunku punktu przerwania](media/vs-getting-started-python-21-debugging4.png)

1. Aby uruchomić program do ukończenia, wyłącz punkt przerwania prawym przyciskiem myszy i wybierając **wyłączyć punkt przerwania** (Ctrl + F9). Następnie wybierz **Kontynuuj** (lub naciśnij klawisz F5) do uruchomienia programu. Po zakończeniu programu Visual Studio zatrzymuje sesję debugowania i powraca do trybu edycji. Należy pamiętać, że możesz także usunąć punkt przerwania, klikając jej kropką, ale to również usunięcie wszelkich warunek, który został skonfigurowany.

> [!Tip]
> W niektórych sytuacjach, takich jak Niepowodzenie uruchamiania interpreter języka Python, w oknie danych wyjściowych może są wyświetlane tylko chwilę, a następnie Zamknij automatycznie bez co daje możliwość zobaczyć komunikaty błędów. Jeśli tak się stanie, kliknij prawym przyciskiem myszy projekt w Eksploratorze rozwiązań wybierz **właściwości**, wybierz pozycję **debugowania** , a następnie dodaj `-i` do **argumenty Interpreter** pole. Ten argument powoduje, że interpreter przejść w trybie interakcyjnym, po zakończeniu programu, co utrzymywanie okna otwarte do momentu wprowadzenia Ctrl + Z Enter, aby wyjść.

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Instalowanie pakietów w środowisku Python](vs-tutorial-01-05.md)

### <a name="going-deeper"></a>Przechodząc głębiej

- [Debugowanie](debugging.md).
- [Debugowanie w programie Visual Studio](../debugger/debugging-in-visual-studio.md) zapewnia pełną dokumentację programu Visual Studio na debugowanie funkcji.
