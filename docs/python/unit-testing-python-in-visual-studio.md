---
title: Testu jednostkowego dla języka Python
description: Ustawienie testu jednostkowego dla kodu języka Python w programie Visual Studio do w pełni korzystać z funkcji Eksploratora testów do odnajdywania, uruchamiane i Debuguj testy.
ms.date: 07/13/2017
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: e75a689f3c03d7ad358da6dc9413f70aaf2c4eab
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="setting-up-unit-testing-for-python-code"></a>Ustawienia testu jednostkowego dla kodu języka Python

Testy jednostkowe są fragmenty kodu, które przetestować innych jednostek kodu w aplikacji, funkcje zwykle izolowanym, klasy i tak dalej. Gdy aplikacja przechodzi wszystkie testy jednostkowe, może co najmniej zaufania, czy jego niskiego poziomu funkcjonalności jest poprawna.

Python często używa testów jednostkowych do weryfikacji scenariuszy podczas projektowania programu. Obsługa języka Python w programie Visual Studio obejmuje odnajdywania, wykonywanie i debugowanie testów jednostkowych w ramach procesu tworzenia, bez konieczności uruchamiania testów oddzielnie.

Ten artykuł zawiera krótki konspektu jednostki testowanie możliwości programu Visual Studio z języka Python. Aby uzyskać więcej informacji na temat testowania ogólnie jednostek zobacz [kod testu jednostkowego](../test/unit-test-your-code.md).

|   |   |
|---|---|
| ![Ikona aparatu film wideo](../install/media/video-icon.png "obejrzeć film wideo") | [Obejrzyj film (Microsoft Virtual Academy)](https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Testing-Python-hb46k6LWE_405918567) w jednostce testowania w języku Python (2 m 31s). |

## <a name="discovering-and-viewing-tests"></a>Wykrywanie i wyświetlanie testów

Konwencja, Visual Studio identyfikuje testów jako metody, których nazwy rozpoczynają się od `test`. Aby wyświetlić ten problem, wykonaj następujące czynności:

1. Otwórz [projektów języka Python](managing-python-projects-in-visual-studio.md) załadowane w programie Visual Studio, kliknij prawym przyciskiem myszy projekt, wybierz **Dodaj > Nowy element...** , a następnie wybierz pozycję **testu jednostkowego języka Python** następuje **Dodaj**.

1. Ta akcja tworzy `test1.py` pliku z kodem, który importuje standardowego `unittest` modułu, pochodzi z klasy testowej `unittest.TestCase`i wywołuje `unittest.main()` Jeśli bezpośrednio uruchomić skrypt:

    ```python
    import unittest

    class Test_test1(unittest.TestCase):
        def test_A(self):
            self.fail("Not implemented")

    if __name__ == '__main__':
        unittest.main()
    ```

1. Zapisz plik w razie potrzeby, a następnie Otwórz Eksplorator testów z **testu > Windows > Narzędzia Eksplorator testów** polecenia menu.

1. Eksplorator testów wyszukuje projekt dla testów i wyświetla je, jak pokazano poniżej. Dwukrotne kliknięcie testu spowoduje otwarcie pliku źródłowego.

    ![Test_A domyślne przedstawiający Eksploratora testów](media/unit-test-A.png)

1. W miarę dodawania większej liczby testów do projektu, można zorganizować widok Eksploratora testów, używając grupy menu na pasku narzędzi:

    ![Grupy Eksploratora testów przez menu paska narzędzi](media/unit-test-group-menu.png)

1. Możesz też wprowadzić tekst w polu wyszukiwania, aby filtrować testy według nazwy.

Aby uzyskać więcej informacji na temat `unittest` modułu i pisanie testów, zobacz [dokumentacji Python 2.7](https://docs.python.org/2/library/unittest.html) lub [dokumentację języka Python 3.4](https://docs.python.org/3/library/unittest.html) (python.org).

## <a name="running-tests"></a>Uruchamianie testów

W Eksploratorze testów można uruchomić testy na różne sposoby:

- **Uruchom wszystkie** wyraźnie uruchamia wszystkie testy pokazano (zgodnie z filtrami).
- **Uruchom...**  menu zawiera polecenia do uruchomienia testów nie powiodło się, przekazany lub nie uruchomiono jako grupa.
- Można wybrać jeden lub więcej testów, kliknij prawym przyciskiem myszy, a następnie wybierz **Uruchom wybrane testy**.

Testy wykonywane w tle i Eksploratora testów aktualizuje stan każdego z testów po ukończeniu:

- Przekazywanie wykaże zielony rick i czasu potrzebnego do uruchomienia testu:

    ![test_A przekazany stanu](media/unit-test-A-pass.png)

- Testy nie powiodły się Pokaż czerwony krzyżyk z **dane wyjściowe** link, który zawiera dane wyjściowe konsoli i `unittest` dane wyjściowe z uruchomienia testu:

    ![Stan test_A nie powiodło się](media/unit-test-A-fail.png)

    ![nie powiodło się z powodu test_A](media/unit-test-A-fail-reason.png)

## <a name="debugging-tests"></a>Debugowanie testów

Ponieważ testy jednostkowe są fragmenty kodu, podlegają usterki, podobnie jak inne kodu i czasami należy uruchomić w debugerze. W debugerze można ustawić punktów przerwania, Sprawdź zmienne i krokowo kodu. Visual Studio udostępnia narzędzia diagnostyczne dla testów jednostkowych.

Aby rozpocząć debugowania, ustaw początkowy punkt przerwania w kodzie, a następnie kliknij prawym przyciskiem myszy testu (lub zaznaczenie) w Eksploratorze testów i wybierz **Debuguj zaznaczone testy**. Visual Studio uruchomienie debugera języka Python, jak w przypadku kodu aplikacji.

![Debugowanie testu](media/unit-test-debugging.png)

Można również użyć **Analizuj pokrycie kodu dla wybrane testy** i **profil testu** poleceń, w zależności od używanej wersji programu Visual Studio (zobacz [macierzy funkcji](overview-of-python-tools-for-visual-studio.md#features-matrix)).

### <a name="known-issues"></a>Znane problemy

- Podczas uruchamiania debugowania programu Visual Studio pojawi się, aby uruchomić i zatrzymać debugowanie, a następnie uruchom ponownie. To zachowanie jest oczekiwane.
- Podczas debugowania wielu testów, każdej z nich jest uruchamiana niezależnie, który przerwania sesji debugowania.
- Visual Studio sporadycznie nie można uruchomić testu, podczas debugowania. Zwykle próbą debugowania ponownie test zakończy się pomyślnie.
- Podczas debugowania, jest możliwe do kroku poza testu do `unittest` implementacji. Zwykle następnym krokiem jest uruchamiany na końcu program i Zatrzymaj debugowanie.
