---
title: Praca z C++ i języku Python
description: Kroki procesu amd zapisu rozszerzenia C++ lub modułu dla języka Python w programie Visual Studio
ms.custom: ''
ms.date: 04/03/2018
ms.technology:
- devlang-python
dev_langs:
- python
- C++
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: d7545f22f7fd19d37cfdbe90839ff83bd9d0ec38
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="creating-a-c-extension-for-python"></a>Tworzenie rozszerzenia C++ dla języka Python

Modułów napisany w języku C++ (lub C) są często używane, aby rozszerzyć możliwości również interpreter języka Python umożliwiający dostęp do funkcji niskiego poziomu systemu operacyjnego. Istnieją trzy typy podstawowe modułów:

- Moduły akceleratora: ponieważ interpretacji języka Python, niektóre fragmenty kodu mogą być napisane w C++ większą wydajność.
- Moduły otoki: Udostępnianie istniejących interfejsów C/C++ do kodu Python lub ujawnić więcej interfejsu API "Pythonic", który jest łatwy w użyciu w języku Python.
- Moduły dostęp niskiego poziomu systemu: utworzone dostęp do funkcji o niższym poziomie środowiska uruchomieniowego języka CPython systemu operacyjnego i używanego sprzętu.

W tym artykule przedstawiono kompilowania modułu rozszerzenia C++ dla języka CPython, który oblicza tangens hiperboliczny i wywołuje ona z kodu języka Python. Procedura zaimplementowano najpierw w języku Python, aby zademonstrować korzyści względną wydajność wdrażania tej samej procedury w języku C++.

W tym miejscu podejście jest to, że dla standardowych rozszerzeń języka CPython zgodnie z opisem w [dokumentacji Python](https://docs.python.org/3/c-api/). Porównanie między tą i innych środków została opisana w sekcji [alternatywnych metod](#alternative-approaches) na końcu tego artykułu.

Ukończono próbka z tego przewodnika można znaleźć w [python — przykłady vs-cpp — rozszerzenie](https://github.com/Microsoft/python-sample-vs-cpp-extension) (GitHub).

## <a name="prerequisites"></a>Wymagania wstępne

- Visual Studio 2017 zarówno **projektowania aplikacji w języku C++** i **programowania Python** obciążeń zainstalowane z opcji domyślnych.
- W **programowania Python** obciążenie, również zaznaczyć pole po prawej stronie dla **Python natywnych narzędzi**. Ta opcja konfiguruje większość ustawień konfiguracji opisanych w tym artykule. (Ta opcja także obciążenie C++ automatycznie.)

    ![Wybranie opcji narzędzia natywnych języka Python](media/cpp-install-native.png)

    > [!Tip]
    > Instalowanie **nauki dane i aplikacje analitycznych** obciążenie obejmuje również Python i **Python natywnych narzędzi** opcji domyślnie.

Aby uzyskać więcej informacji, zobacz [instalowanie obsługę języka Python dla programu Visual Studio](installing-python-support-in-visual-studio.md), łącznie z innych wersji programu Visual Studio. Po zainstalowaniu Python oddzielnie, pamiętaj o wybraniu **Pobierz symbole debugowania** i **pliki binarne debugowania pobierania** w obszarze **zaawansowane opcje** w Instalatorze. Ta opcja zapewnia ma dostępne biblioteki debugowania konieczne, jeśli użytkownik chce wykonać kompilację debugowania.

## <a name="create-the-python-application"></a>Tworzenie aplikacji Python

1. Utwórz nowy projekt języka Python w programie Visual Studio, wybierając **Plik > Nowy > Projekt**. Wyszukaj "Python", wybierz **aplikacji Python** szablonu, nadaj mu odpowiednią nazwę i lokalizację, a następnie wybierz **OK**.

1. Praca z C++ wymaga 32-bitowy interpreter języka Python (Python 3,6 zalecane). W **Eksploratora rozwiązań** okno programu Visual Studio rozwiń węzeł projektu, a następnie rozwiń węzeł **środowiska Python** węzła. Jeśli nie widzisz 32-bitowego środowiska domyślnie (albo w pogrubione lub etykietą z "domyślnej globalnej"), postępuj zgodnie z instrukcjami na [wybranie środowisku Python dla projektu](selecting-a-python-environment-for-a-project.md). Jeśli nie masz interpreter 32-bitowy, zainstalowane, zobacz [tłumaczy instalowanie Python](installing-python-interpreters.md).

1. W projekcie `.py` plików, wklej następujący kod, który wzorców obliczenia tangens hiperboliczny (zaimplementowana bez korzystania z biblioteki matematyczne ułatwia porównanie). Możesz także wprowadzić kod ręcznie, aby zgłaszać niektóre [Python funkcje edytowania](editing-python-code-in-visual-studio.md).

    ```python
    from itertools import islice
    from random import random
    from time import perf_counter

    COUNT = 500000  # Change this value depending on the speed of your computer
    DATA = list(islice(iter(lambda: (random() - 0.5) * 3.0, None), COUNT))

    e = 2.7182818284590452353602874713527

    def sinh(x):
        return (1 - (e ** (-2 * x))) / (2 * (e ** -x))

    def cosh(x):
        return (1 + (e ** (-2 * x))) / (2 * (e ** -x))

    def tanh(x):
        tanh_x = sinh(x) / cosh(x)
        return tanh_x

    def sequence_tanh(data):
        '''Applies the hyperbolic tangent function to map all values in
        the sequence to a value between -1.0 and 1.0.
        '''
        result = []
        for x in data:
            result.append(tanh(x))
        return result

    def test(fn, name):
        start = perf_counter()
        result = fn(DATA)
        duration = perf_counter() - start
        print('{} took {:.3f} seconds\n\n'.format(name, duration))

        for d in result:
            assert -1 <= d <= 1, " incorrect values"

    if __name__ == "__main__":
        print('Running benchmarks with COUNT = {}'.format(COUNT))

        test(sequence_tanh, 'sequence_tanh')

        test(lambda d: [tanh(x) for x in d], '[tanh(x) for x in d]')
    ```

1. Uruchom program używając **debugowania > Uruchom bez debugowania** (Ctrl + F5), aby wyświetlić wyniki. Można dostosować `COUNT` zmiennej do zmiany, jak długo wykonać testów porównawczych, aby uruchomić. Na potrzeby tego przewodnika ustaw wartość licznika każdego testu porównawczego trwa około dwóch sekund.

## <a name="create-the-core-c-project"></a>Tworzenie projektu C++ core

1. Kliknij prawym przyciskiem myszy rozwiązanie w Eksploratorze rozwiązań i wybierz **Dodaj > Nowy projekt...** . Rozwiązanie programu Visual Studio może zawierać zarówno Python i C++ projektów razem (które jest jednym z zalet funkcji programu Visual Studio dla języka Python).

1. Wyszukaj frazę "C++", wybierz **pusty projekt**, określ nazwę (w tym artykule używa "superfastcode") i wybierz **OK**.

    > [!Tip]
    > Z **Python natywnych narzędzi** zainstalowany w programie Visual Studio 2017 r, można uruchomić z poziomu **Python rozszerzenie modułu** szablonu, który zawiera większość opisany poniżej już w miejscu. W ramach tego przewodnika, począwszy od pusty projekt pokazano tworzenie modułu rozszerzenia krok po kroku. Po zrozumieniu procesu zapisuje szablonu podczas obliczania czasu pomocą samodzielnie napisanych rozszerzeń.

1. Utwórz plik C++ w nowym projekcie, klikając prawym przyciskiem myszy **pliki źródłowe** węzła, następnie wybierz **Dodaj > Nowy element... "**, wybierz pozycję **plik C++**, nadaj jej nazwę `module.cpp`, i Wybierz **OK**.

    > [!Important]
    > Plik o `.cpp` rozszerzenie jest konieczne włączyć na stronach właściwości C++ w kolejnych krokach.

1. Kliknij prawym przyciskiem myszy projekt C++ w rozwiązaniu, wybierz **właściwości**.

1. W górnej części **strony właściwości** okno dialogowe zostanie wyświetlone, ustaw **konfiguracji** do **wszystkie konfiguracje** i **platformy** do **Win32**.

1. Ustaw określone właściwości, zgodnie z opisem w poniższej tabeli, a następnie wybierz **OK**.

    | Tab | Właściwość | Wartość |
    | --- | --- | --- |
    | Ogólne | Ogólne > nazwa docelowa | Określ nazwę modułu, jak chcesz odwołuje się do niego w języku Python w `from...import` instrukcje. W języku C++ będą używać tej samej nazwie, definiując modułu dla języka Python. Jeśli chcesz użyć nazwy projektu z nazwą modułu, pozostaw wartość domyślną `$(ProjectName)`. |
    | | Ogólne > celem rozszerzenia | .pyd |
    | | Domyślne ustawienia projektu > typ konfiguracji | Dynamiczna Biblioteka (dll) |
    | C/C++ > Ogólne | Dodatkowe katalogi dołączenia | Dodaj Python `include` folder na potrzeby instalacji, na przykład `c:\Python36\include`.  |
    | C/C++ > preprocesora | Definicje preprocesora | Dodaj `Py_LIMITED_API;` na początku ciąg (w tym średnik). Ta definicja ogranicza niektórych funkcji, można wywołać w języku Python i sprawia, że kod przenośną między różnymi wersjami programu Python. |
    | C/C++ > Generowanie kodu | Biblioteka środowiska uruchomieniowego | Biblioteki DLL wielowątkowych (/ MD) (zobacz poniżej ostrzeżenia) |
    | Konsolidator > Ogólne | Katalogi bibliotek dodatkowe | Dodaj Python `libs` folder zawierający `.lib` pliki jako odpowiednią dla tej instalacji, na przykład `c:\Python36\libs`. (Pamiętaj wskazywał `libs` folder zawierający `.lib` pliki, i *nie* `Lib` folder zawierający `.py` pliki.) |

    > [!Tip]
    > Jeśli nie widzisz karcie C/C++ we właściwościach projektu, jest on, ponieważ projekt nie zawiera żadnych plików, które identyfikuje go jako pliki źródłowe C/C++. Ten stan może wystąpić w przypadku tworzenia pliku źródłowego bez `.c` lub `.cpp` rozszerzenia. Na przykład, jeśli przypadkowo wprowadzono `module.coo` zamiast `module.cpp` nowego elementu wcześniej w oknie dialogowym, następnie Visual Studio tworzy plik, ale nie ustawiono typ pliku "C / C + kodu," czyli co aktywuje kartę właściwości C/C++. Takie misidentification pozostaje wielkość liter, nawet jeśli zmienisz nazwę pliku z `.cpp`. Aby poprawnie zainstalować ten typ pliku, kliknij prawym przyciskiem myszy plik w Eksploratorze rozwiązań wybierz **właściwości**, a następnie ustaw **typ pliku** do **kodu C/C++**.

    > [!Warning]
    > Zawsze wartość **C/C++ > Generowanie kodu > Biblioteka środowiska uruchomieniowego** opcje "DLL wielowątkowych (/ MD)", nawet dla konfiguracji debugowania, ponieważ jest to ustawienie, co pliki binarne Python bez debugowania są tworzone za. W przypadku ustawić "wielowątkowych debugowania biblioteki DLL (/ MDd)" opcja tworzenia konfiguracji debugowania powoduje błąd *C1189: Py_LIMITED_API jest niezgodny z Py_DEBUG, Py_TRACE_REFS i Py_REF_DEBUG*. Ponadto jeśli usuniesz `Py_LIMITED_API` Aby uniknąć błędów kompilacji, Python ulega awarii podczas próby zaimportowania z modułu. (Awarię (crash) to następuje w wywołaniu DLL `PyModule_Create` zgodnie z opisem później, z komunikatu wyjściowego z *błąd krytyczny Python: PyThreadState_Get: nie bieżącego wątku*.)
    >
    > Opcja/mdd jest używany do tworzenia plików binarnych debugowania języka Python (na przykład python_d.exe), ale nadal wybierając ją z rozszerzeniem DLL powoduje błąd kompilacji z `Py_LIMITED_API`.

1. Kliknij prawym przyciskiem myszy projekt C++, a następnie wybierz **kompilacji** do testowania konfiguracji (Debug i Release). `.pyd` Pliki znajdują się w *rozwiązania* folder **debugowania** i **wersji**, nie folder projektu C++ samej siebie.

1. Dodaj następujący kod do projektu C++ `module.cpp` pliku:

    ```cpp
    #include <Windows.h>
    #include <cmath>

    const double e = 2.7182818284590452353602874713527;

    double sinh_impl(double x) {
        return (1 - pow(e, (-2 * x))) / (2 * pow(e, -x));
    }

    double cosh_impl(double x) {
        return (1 + pow(e, (-2 * x))) / (2 * pow(e, -x));
    }

    double tanh_impl(double x) {
        return sinh_impl(x) / cosh_impl(x);
    }
    ```

1. Tworzenie projektu C++ ponownie, aby potwierdzić, że kod jest poprawny.

## <a name="convert-the-c-project-to-an-extension-for-python"></a>Konwertowanie projektu C++ do rozszerzenia dla języka Python

Aby C++ DLL do rozszerzenia dla języka Python, najpierw zmodyfikować wyeksportowanych metod wchodzić w interakcje z typów języka Python. Następnie dodaj funkcję, która eksportuje modułu, wraz z definicjami metod modułu.

W tle, na które zostaną uwzględnione w tej sekcji dla języka Python 3.x, odwoływać się do [Python/C API Reference Manual](https://docs.python.org/3/c-api/index.html) i szczególnie [obiektów modułu](https://docs.python.org/3/c-api/module.html) na python.org (należy pamiętać wybrać wersji języka Python z Kontrolka listy rozwijanej w prawym górnym rogu, aby wyświetlić poprawne dokumentację).

Jeśli pracujesz z Python 2.7, zapoznaj się zamiast tego [rozszerzanie Python 2.7 z C lub C++](https://docs.python.org/2.7/extending/extending.html) i [eksportowanie rozszerzenia moduły do języka Python 3](https://docs.python.org/2.7/howto/cporting.html) (python.org).

1. W pliku C++ obejmują `Python.h` u góry:

    ```cpp
    #include <Python.h>
    ```

1. Modyfikowanie `tanh_impl` metody, aby zaakceptować i zwracanych typów języka Python ( `PyOjbect*`, która jest):

    ```cpp
    PyObject* tanh_impl(PyObject *, PyObject* o) {
        double x = PyFloat_AsDouble(o);
        double tanh_x = sinh_impl(x) / cosh_impl(x);
        return PyFloat_FromDouble(tanh_x);
    }
    ```

1. Struktury, który definiuje sposób C++ `tanh_impl` funkcja jest udostępniana Python:

    ```cpp
    static PyMethodDef superfastcode_methods[] = {
        // The first property is the name exposed to Python, fast_tanh, the second is the C++
        // function name that contains the implementation.
        { "fast_tanh", (PyCFunction)tanh_impl, METH_O, nullptr },

        // Terminate the array with an object containing nulls.
        { nullptr, nullptr, 0, nullptr }
    };
    ```

1. Dodaj struktura, która definiuje modułu, w których chcesz odwołuje się do niego w kodzie języka Python, szczególnie w przypadku korzystania z `from...import` instrukcji. (To pasuje do wartości we właściwościach projektu w obszarze **właściwości konfiguracji > Ogólne > Nazwa docelowego**.) W poniższym przykładzie nazwa modułu "superfastcode" oznacza, że można użyć `from superfastcode import fast_tanh` w języku Python, ponieważ `fast_tanh` jest zdefiniowany w `superfastcode_methods`. (Wpływu są wewnętrzne dla projektów C++, takie jak module.cpp, nazwy plików).

    ```cpp
    static PyModuleDef superfastcode_module = {
        PyModuleDef_HEAD_INIT,
        "superfastcode",                        // Module name to use with Python import statements
        "Provides some functions, but faster",  // Module description
        0,
        superfastcode_methods                   // Structure that defines the methods of the module
    };
    ```

1. Dodaj metodę, która wywołuje Python ładuje moduł, który musi mieć nazwę `PyInit_<module-name>`, gdzie *&lt;nazwa_modułu&gt;* dokładnie odpowiada projektu C++ **ogólne > Nazwa docelowego** właściwości (to znaczy, że jest on zgodny nazwę pliku `.pyd` skompilowanego przez projekt).

    ```cpp
    PyMODINIT_FUNC PyInit_superfastcode() {
        return PyModule_Create(&superfastcode_module);
    }
    ```

1. Ustawienia konfiguracji docelowej "Wersja" i skompiluj projekt C++ ponownie w celu zweryfikowania kodu. Jeśli wystąpią błędy, sprawdź następujących przypadkach:
    - Nie można zlokalizować Python.h (*E1696: nie można otworzyć pliku źródłowego "Python.h"* i/lub *C1083: nie można dołączyć Otwórz plik: "Python.h": Brak pliku lub katalogu*): Upewnij się, że ścieżka w **C/C++ > Ogólne > Dodatkowe katalogi dołączenia** w punktach właściwości projektu do instalacji języka Python `include` folderu. Zobacz krok 6 w obszarze [Tworzenie projektu core C++](#create-the-core-c-project).
    - Nie można zlokalizować biblioteki Python: Upewnij się, że ścieżka w **konsolidatora > Ogólne > Dodatkowe katalogi bibliotek** w punktach właściwości projektu do instalacji języka Python `libs` folderu. Zobacz krok 6 w obszarze [Tworzenie projektu core C++](#create-the-core-c-project).
    - Konsolidator błędy związane z Architektura docelowa: Zmień architektura projektu docelowego C++ odpowiadać instalacji języka Python. Na przykład jeśli docelowych x64 z projektu C++, ale instalacja Python jest x86, Zmień projekt C++ pod kątem x86.

## <a name="test-the-code-and-compare-the-results"></a>Testowanie kodu i porównywania wyników

Teraz, gdy masz DLL strukturze rozszerzenia języka Python, zapoznaj się z jego projektów języka Python, zaimportuj moduł, a jego metody.

### <a name="make-the-dll-available-to-python"></a>Udostępnia biblioteki DLL języka Python

Istnieją dwa sposoby, aby udostępnić biblioteki DLL języka Python.

Pierwsza metoda działa, jeśli projekt Python i projektu C++ znajdują się w tym samym rozwiązaniu. Przejdź do Eksploratora rozwiązań, kliknij prawym przyciskiem myszy **odwołania** węzła w projekcie języka Python, a następnie wybierz **Dodaj odwołanie**. W wyświetlonym oknie dialogowym wybierz **projekty** wybierz opcję **superfastcode** projektu (lub korzystania z dowolnym wybraną nazwę), a następnie **OK**.

![Dodawanie odwołania do projektu superfastcode](media/cpp-add-reference.png)

Alternatywna metoda, opisane w poniższych krokach instaluje moduł globalnego środowiska Python, udostępnianie innych projektów języka Python. (Dlatego zazwyczaj wymaga aby odświeżyć bazy danych uzupełniania IntelliSense dla tego środowiska w Visual Studio 2017 wersji 15.5 i starszych. Odświeżanie jest także niezbędne podczas usuwania modułu ze środowiska.)

1. Jeśli używasz programu Visual Studio 2017 r, uruchom Instalatora programu Visual Studio wybierz **Modyfikuj**, wybierz pozycję **pojedynczych składników > kompilatorów kompilacji narzędzia i środowisk uruchomieniowych > zestaw narzędzi w wersji 140 Visual C++ 2015.3**. Ten krok jest niezbędny, ponieważ języka Python (dla systemu Windows) jest skompilowanej za pomocą programu Visual Studio 2015 (wersja 14.0) i oczekuje, że te narzędzia są dostępne podczas kompilowania rozszerzeń za pomocą metody opisanej w tym miejscu. (Należy pamiętać, że należy zainstalować 32-bitowej wersji środowiska Python i docelowymi biblioteki DLL, Win32, a nie x64).

1. Utwórz plik o nazwie `setup.py` projektu C++ prawym przyciskiem myszy projekt i wybierając **Dodaj > Nowy element...** . Następnie wybierz pozycję "Plik C++ (.cpp)", określ nazwę pliku `setup.py`i wybierając **OK** (nazwy pliku z `.py` rozszerzenie powoduje, że program Visual Studio rozpoznać jej jako szablonu pliku Python pomimo przy użyciu języka C++). Gdy plik zostanie wyświetlony w edytorze, wklej następujący kod do niej:

    ```python
    from distutils.core import setup, Extension, DEBUG

    sfc_module = Extension('superfastcode', sources = ['module.cpp'])

    setup(name = 'superfastcode', version = '1.0',
        description = 'Python Package with superfastcode C++ extension',
        ext_modules = [sfc_module]
        )
    ```

    Zobacz [rozszerzenia budynku C i C++](https://docs.python.org/3/extending/building.html) (python.org) dokumentację dotyczącą tego skryptu.

1. `setup.py` Kod nakazuje Python do tworzenia rozszerzenia przy użyciu zestawu narzędzi Visual Studio 2015 C++, gdy jest używany z wiersza polecenia. Otwórz wiersz polecenia z podwyższonym poziomem uprawnień, przejdź do folderu zawierającego projektu C++ (czyli folderu, który zawiera `setup.py`), a następnie wprowadź następujące polecenie:

    ```command
    pip install .
    ```

### <a name="call-the-dll-from-python"></a>Wywołanie biblioteki DLL w języku Python

Po wykonaniu dowolnej z metod powyżej można teraz wywołać `fast_tanh` funkcji z kodu Python i porównać jego wydajność, aby Python implementacji:

1. Dodaj następujące wiersze w Twojej `.py` pliku do wywołania `fast_tanh` metody wyeksportowane z biblioteki DLL i wyświetlić dane wyjściowe.

    ```python
    from superfastcode import fast_tanh
    test(lambda d: [fast_tanh(x) for x in d], '[fast_tanh(x) for x in d]')
    ```

1. Uruchom program języka Python (**debugowania > Uruchom bez debugowania** lub Ctrl + F5) i sprawdź procedury C++ szybciej niż implementacji Python uruchamia 5 do 20 razy. Dane wyjściowe zazwyczaj wygląda następująco:

    ```output
    Running benchmarks with COUNT = 500000
    sequence_tanh took 1.542 seconds

    [tanh(x) for x in d] took 1.087 seconds

    [fast_tanh(x) for x in d] took 0.158 seconds
    ```

1. Spróbuj zwiększyć `COUNT` zmiennej, dzięki czemu większa różnice. Kompilację debugowania modułu C++ również działa wolniej niż kompilacji wydania ponieważ Kompilacja debugowania mniej jest zoptymalizowany i zawiera różne sprawdzanie błędów. Swobodnie przełączać się między te konfiguracje do porównania.

## <a name="debug-the-c-code"></a>Debugowanie kodu C++

Program Visual Studio obsługuje debugowania kodu Python i C++ razem.

1. Kliknij prawym przyciskiem myszy projekt języka Python w Eksploratorze rozwiązań, wybierz **właściwości**, wybierz pozycję **debugowania** , a następnie wybierz **Debuguj > Włącz debugowanie kodu natywnego** opcji.

    > [!Tip]
    > Gdy włączone jest debugowanie kodu natywnego, w oknie danych wyjściowych Python może zniknąć natychmiast po zakończeniu program bez umożliwiając zwykle Wstrzymaj "Naciśnij dowolny klawisz, aby kontynuować...". Aby wymusić przerwie, Dodaj `-i` opcji w celu **Uruchom > argumenty Interpreter** na **debugowania** karcie, gdy włączone jest debugowanie kodu natywnego. Ten argument umieszcza interpreter języka Python w trybie interakcyjnym, po zakończeniu kodu, w którym czeka na naciśnij klawisz Enter, aby zakończyć Ctrl + Z. (, Jeśli nie stanowi modyfikowanie kodu języka Python, możesz dodać `import os` i `os.system("pause")` instrukcje w końcu program. Ten kod duplikatów oryginalnego wiersza Wstrzymaj).

1. Wybierz **Plik > Zapisz** można zapisać zmian właściwości.

1. Ustawienie konfiguracji kompilacji na "Debugowanie" na pasku narzędzi programu Visual Studio.

    ![Ustawienie konfiguracji kompilacji debugowania](media/cpp-set-debug.png)

1. Ponieważ kod zwykle trwa dłużej, w debugerze, można zmienić `COUNT` zmiennej w Twojej `.py` pliku o pięć razy mniejsza wartość (na przykład zmienić go z `500000` do `100000`).

1. W kodzie C++ Ustaw punkt przerwania w pierwszym wierszu `tanh_impl` metody, a następnie uruchomienia debugera (F5 lub **Debuguj > Rozpocznij debugowanie**). Debuger zatrzymywana, gdy kod jest wywoływana. Jeśli nie zostaje trafiony punkt przerwania, sprawdź, czy konfiguracja jest ustawiona na debugowanie i zapisaniu projektu (który nie jest wykonywane automatycznie podczas uruchamiania debugera).

    ![Zatrzymywanie w punkcie przerwania w kodzie C++](media/cpp-debugging.png)

1. W tym momencie można wykonywać krokowo kodu C++, Sprawdź zmienne i tak dalej. Te funkcje są wyszczególnione w [debugowanie C++ i Python razem](debugging-mixed-mode-c-cpp-python-in-visual-studio.md).

## <a name="alternative-approaches"></a>Alternatywnych metod

Istnieją różne sposoby tworzenia rozszerzenia języka Python, zgodnie z opisem w poniższej tabeli. Pierwszy wpis języka CPython jest, co zostało omówione w tym artykule już.

| Podejście | Zbioru | Przedstawiciel użytkowników | Pro(s) | CON(s) |
| --- | --- | --- | --- | --- |
| Moduły rozszerzenia C/C++ dla języka CPython | 1991 | Standardowa biblioteka | [Szczegółową dokumentację i samouczki](https://docs.python.org/3/c-api/). Pełną kontrolę. | Kompilacja, przenośność, zarządzanie odwołania. Wysoka C wiedzy. |
| [pybind11](https://github.com/pybind/pybind11) (zalecane dla języka C++) | 2015 |  | Biblioteka niewielka, tylko nagłówek do tworzenia powiązań Python z istniejącego kodu C++. Kilka zależności. Zgodność PyPy. | Nowsze, mniej dojrzała. Dużego wykorzystania funkcji C ++ 11. Krótką listę obsługiwanych kompilatory (Visual Studio jest dołączony). |
| Cython (Recommnded dla języka C) | 2007 | [gevent](http://www.gevent.org/), [kivy](https://kivy.org/) | Notacji języka Python. Wysoce dojrzała. Wysoka wydajność. | Kompilacja, nowej składni, nowy łańcuch narzędzi. |
| [Boost.Python](https://www.boost.org/doc/libs/1_66_0/libs/python/doc/html/index.html) | 2002 | | Współdziała z prawie każdego kompilator języka C++. | Pakiet dużych i złożonych bibliotek; zawiera wiele obejścia kompilatory stary. |
| ctypes | 2003 | [oscrypto](https://github.com/wbond/oscrypto) | Nie kompilacji szeroki dostępności. | Uzyskiwanie dostępu do i mutacja struktury C skomplikowane i błąd podatnych na błędy. |
| SWIG | 1996 | [crfsuite](http://www.chokkan.org/software/crfsuite/) | Generowanie jednocześnie powiązania dla wielu języków. | Nadmierne obciążenie w przypadku języka Python tylko docelowy. |
| cffi | 2013 | [Kryptografia](https://cryptography.io/en/latest/), [pypy](http://pypy.org/) | Łatwa integracja, PyPy zgodności. | Nowsze, mniej dojrzała. |

## <a name="see-also"></a>Zobacz także

Ukończono próbka z tego przewodnika można znaleźć w [python — przykłady vs-cpp — rozszerzenie](https://github.com/Microsoft/python-sample-vs-cpp-extension) (GitHub).