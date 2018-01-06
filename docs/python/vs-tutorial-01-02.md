---
title: "Praca z języka Python w programie Visual Studio, krok 2 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 10/16/2017
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
ms.workload: python
ms.openlocfilehash: 964ed265f4e2587a1bef4812797987c47d52fa80
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="step-2-writing-and-running-code"></a>Krok 2: Pisania i uruchamiania kodu

**Poprzedni krok: [tworzenia nowego projektu języka Python](vs-tutorial-01-01.md)**

Mimo że Eksplorator rozwiązań zarządza się pliki projektu *edytor* okno jest zwykle miejsca pracy *zawartość* plików, takich jak kodu źródłowego. Edytor zna kontekstowej typ pliku, edytowania, w tym języku programowania (na podstawie pliku rozszerzenia), i udostępnia funkcje właściwe dla danego języka, takie jak kolorowanie składni i automatycznego uzupełniania za pomocą funkcji IntelliSense.

1. Po utworzeniu nowego projektu "Python aplikacji", wartości domyślnej pusty plik o nazwie `PythonApplication1.py` jest otwarty w edytorze programu Visual Studio. 

1. W edytorze, zacznij pisać `print("Hello, Visual Studio")` i zwróć uwagę, jak Visual Studio IntelliSense wyświetla opcje automatycznego uzupełniania wzdłuż sposób. Obramowane opcji na liście rozwijanej jest zakończenie domyślny używany po naciśnięciu klawisza Tab. Uzupełnienia to najbardziej przydatne w przypadku dłużej instrukcji lub identyfikatorów.

    ![Menu podręczne automatycznego uzupełniania IntelliSense](media/vs-getting-started-python-04-IntelliSense1b.png)

1. IntelliSense zawiera różne informacje w zależności od instrukcji, którego używasz, funkcji, do której jest wywołaniem i tak dalej. Z `print` działanie, wpisując `(` po `print` wskazująca funkcję wywołania Wyświetla informacje o użyciu pełny dla tej funkcji. IntelliSense wyskakującego okienka przedstawiono również bieżącego argument pogrubioną czcionką (**wartość** w sposób pokazany poniżej):

    ![Menu podręczne automatycznego uzupełniania IntelliSense dla funkcji](media/vs-getting-started-python-05-IntelliSense2b.png)

1. Wykonaj instrukcję tak, aby odpowiadała następujące czynności:

    ```python
    print("Hello, Visual Studio")
    ```

1. Zwróć uwagę, zabarwienie składni, który odróżnia instrukcji `print` w argumencie `"Hello Visual Studio"`. Ponadto tymczasowo usunąć ostatni `"` na ciąg i zwróć uwagę, jak Visual Studio wyświetli czerwoną linią kod który występują błędy składniowe. Następnie zastąp `"` Aby naprawić kod.

    ![Kolorowanie składni IntelliSense i błąd podświetlania](media/vs-getting-started-python-06-IntelliSense3b.png)

    > [!Tip]
    > Ponieważ osoby środowisko projektowe polega na bardzo osobistych, Visual Studio umożliwia pełną kontrolę nad wygląd i zachowanie programu Visual Studio. Wybierz **Narzędzia > Opcje** menu poleceń i eksplorować ustawienia w obszarze **środowiska** i **Edytor tekstu** karty. Domyślnie zostanie wyświetlony tylko pewna liczba opcji; Aby wyświetlić każdej opcji dla każdego języka programowania, wybierz **Pokaż wszystkie ustawienia** w dolnej części okna dialogowego. 

1. Uruchom kod napisanych w tym punkcie naciskając klawisze Ctrl + F5 lub wybranie **debugowania > Uruchom bez debugowania** elementu menu. Visual Studio wyświetli ostrzeżenie, jeśli nadal występują błędy w kodzie.

1. Po uruchomieniu programu, zostanie wyświetlone okno konsoli wyświetlania wyników, tak jakby należy uruchomić interpreter języka Python z `PythonApplication1.py` z wiersza polecenia. Naciśnij dowolny klawisz, aby zamknąć okno i powrócić do edytora programu Visual Studio.

    ![Dane wyjściowe dla pierwszego uruchomienia programu](media/vs-getting-started-python-07-output.png)

1. Oprócz zakończeń instrukcje i funkcje, IntelliSense Podaj zakończeń dla języka Python `import` i `from` instrukcje. Ukończenia te mogą pomóc Ci łatwo wykryć, które moduły są dostępne w Twoim środowisku oraz członkami tych modułów. W edytorze, Usuń `print` wiersza i zacznij wpisywać ciąg `import `. Po wpisaniu miejsce, zostanie wyświetlona lista modułów:

    ![IntellSense pokazujący dostępne moduły instrukcji importu](media/vs-getting-started-python-08-import1.png)

1. Zakończenie wiersza, wpisując lub wybierając `sys`.

1. W następnym wierszu, wpisz `from` ponownie wyświetlić listę modułów:

    ![IntellSense pokazujący dostępne moduły dla instrukcji](media/vs-getting-started-python-09-import2.png)

1. Wybierz lub wpisz `math`, pracując ze spacją i `import`, który zawiera elementy członkowskie modułu:

    ![Elementy członkowskie modułu przedstawiający IntellSense](media/vs-getting-started-python-10-import3.png)

1. Zakończ importując `sin`, `cos`, i `radians` członków, po raz pierwszy automatycznie zakończeń dostępne dla każdego. Gdy wszystko będzie gotowe, kod powinien wyglądać następująco:

    ```python
    import sys
    from math import sin, cos, radians
    ```

    > [!Tip]
    > Ukończenia mogą współpracować z podciągów wpisz dopasowanie części słowa, liter na początku słowa i nawet pominięte znaków. Zobacz [edytowanie kodu - zakończeń](code-editing.md#completions) szczegółowe informacje.

1. Dodaj nieco więcej kodu wartości cosinus 360 stopni:

    ```python 
    for i in range(360):
        print(cos(radians(i)))
    ```

1. Ponownie uruchom program z Ctrl + F5 lub **Debuguj > Rozpocznij bez debugowanie**. Zamknij okno dane wyjściowe, gdy wszystko będzie gotowe.

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [W oknie interaktywny REPL](vs-tutorial-01-03.md)

## <a name="going-deeper"></a>Przechodząc głębiej

- [Edytowanie kodu](code-editing.md)
- [Formatowanie kodu](code-formatting.md)
- [Refaktoryzacji kodu](code-refactoring.md)
- [Używanie PyLint](code-pylint.md)
