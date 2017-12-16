---
title: "Praca z C++ i języku Python w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 09/28/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: get-started-article
description: "Kroki procesu amd zapisu rozszerzenia C++ lub modułu dla języka Python w programie Visual Studio"
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: 703197b9ad51334afaffdb057911f75587efb570
ms.sourcegitcommit: f36eb7f989efbdbed0d0a087afea8ffe27d8ca15
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2017
---
# <a name="creating-a-c-extension-for-python"></a>Tworzenie rozszerzenia C++ dla języka Python

Modułów napisany w języku C++ (lub C) są często używane, aby rozszerzyć możliwości również interpreter języka Python umożliwiający dostęp do funkcji niskiego poziomu systemu operacyjnego. Istnieją trzy typy podstawowe modułów:

- Moduły akceleratora: ponieważ interpretacji języka Python, niektóre fragmenty kodu mogą być napisane w C++ większą wydajność. 
- Moduły otoki: otoki ujawnia istniejących interfejsów C/C++ do kodu Python lub ujawnić więcej interfejsu API "Pythonic", który jest łatwy w użyciu w języku Python.
- Moduły dostęp niskiego poziomu systemu: utworzone dostęp do funkcji o niższym poziomie środowiska uruchomieniowego języka CPython systemu operacyjnego i używanego sprzętu. 

W tym temacie przedstawiono kompilowania modułu rozszerzenia C++ dla języka CPython, który oblicza tangens hiperboliczny i wywołuje ona z kodu języka Python. Procedura zaimplementowano najpierw w języku Python, aby zademonstrować bardziej wydajne stosowania tej samej procedury w języku C++.

W tym miejscu podejście jest to, że dla standardowych rozszerzeń języka CPython zgodnie z opisem w [dokumentacji Python](https://docs.python.org/3/c-api/). Porównanie między tą i innych środków została opisana w sekcji [alternatywnych metod](#alternative-approaches) na końcu tego tematu.

## <a name="prerequisites"></a>Wymagania wstępne

- Visual Studio 2017 zarówno **projektowania aplikacji w języku C++** i **programowania Python** obciążeń zainstalowane z opcji domyślnych. 
- W **programowania Python** obciążenie, również zaznacz pole w odpowiedniej dla **Python natywnych narzędzi**, który konfiguruje większość opcji opisanych w tym temacie. (Ta opcja także obciążenie C++ automatycznie.) 

![Wybranie opcji narzędzia natywnych języka Python](media/cpp-install-native.png)

- Instalowanie **nauki dane i aplikacje analitycznych** obciążenie obejmuje również Python i **Python natywnych narzędzi** opcji domyślnie.

Aby uzyskać więcej informacji, zobacz [instalowanie obsługę języka Python dla programu Visual Studio](installation.md), łącznie z innych wersji programu Visual Studio. Po zainstalowaniu Python oddzielnie, pamiętaj o wybraniu **Pobierz symbole debugowania** i **pliki binarne debugowania pobierania** w obszarze **zaawansowane opcje** w Instalatorze. Ta opcja zapewnia ma dostępne biblioteki debugowania konieczne, jeśli użytkownik chce wykonać kompilację debugowania.

## <a name="create-the-python-application"></a>Tworzenie aplikacji Python

1. Utwórz nowy projekt języka Python w programie Visual Studio, wybierając **Plik > Nowy > Projekt**. Wyszukaj "Python", wybierz **aplikacji Python** szablonu, nadaj mu odpowiednią nazwę i lokalizację, a następnie wybierz **OK**.

1. W projekcie `.py` plików, wklej następujący kod, który wzorców obliczenia tangens hiperboliczny (zaimplementowana bez korzystania z biblioteki matematyczne ułatwia porównanie). Możesz także wprowadzić kod ręcznie, aby zgłaszać niektóre [Python funkcje edytowania](code-editing.md).

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
            assert -1 <= d <=1, " incorrect values"

    if __name__ == "__main__":
        print('Running benchmarks with COUNT = {}'.format(COUNT))
        test(sequence_tanh, 'sequence_tanh')

        test(lambda d: [tanh(x) for x in d], '[tanh(x) for x in d]')
    ```

1. Uruchom program używając **debugowania > Uruchom bez debugowania** (Ctrl + F5), aby wyświetlić wyniki. Można dostosować `COUNT` zmiennej do zmiany, jak długo wykonać testów porównawczych, aby uruchomić. Na potrzeby tego przewodnika ustaw wartość licznika każdego testu porównawczego trwa około dwóch sekund.

## <a name="create-the-core-c-project"></a>Tworzenie projektu C++ core

1. Kliknij prawym przyciskiem myszy rozwiązanie w Eksploratorze rozwiązań i wybierz **Dodaj > Nowy projekt...** . Rozwiązania Visual Studio może zawierać zarówno Python i C++ projektów ze sobą.

1. Wyszukaj frazę "C++", wybierz **pusty projekt**, określ nazwę (na przykład TanhBenchmark) i wybierz **OK**. Uwaga: Jeśli po zainstalowaniu **Python natywnych narzędzi** z programu Visual Studio 2017 r, można uruchomić z **Python rozszerzenie modułu** szablonu, który ma wiele opisany tutaj już w miejscu . W ramach tego przewodnika, począwszy od pusty projekt pokazano tworzenie modułu rozszerzenia krok po kroku.

1. Utwórz plik C++ w nowym projekcie, klikając prawym przyciskiem myszy **pliki źródłowe** węzła, następnie wybierz **Dodaj > Nowy element... "**, wybierz pozycję **plik C++**, nadaj mu nazwę (takich jak `module.cpp`) i wybierz **OK**. Ten krok jest niezbędny włączyć na stronach właściwości C++ w następnych krokach.

1. Kliknij prawym przyciskiem myszy nowy projekt i wybierz **właściwości**, następnie w górnej części **strony właściwości** okno dialogowe zostanie wyświetlone, ustaw **konfiguracji** do **wszystkie Konfiguracje**.

1. Ustaw określone właściwości, zgodnie z poniższym opisem, a następnie wybierz **OK**.

    | Tab | Właściwość | Wartość | 
    | --- | --- | --- |
    | Ogólne | Ogólne > nazwa docelowa | Ustaw to pole dokładnie odpowiadać nazwie modułu jako języka Python, widzi on. |
    | | Ogólne > celem rozszerzenia | .pyd |
    | | Domyślne ustawienia projektu > typ konfiguracji | Dynamiczna Biblioteka (dll) |
    | C/C++ > Ogólne | Dodatkowe katalogi dołączenia | Dodaj Python `include` folder na potrzeby instalacji, na przykład`c:\Python36\include` |     
    | C/C++ > preprocesora | Definicje preprocesora | Dodaj `Py_LIMITED_API;` na początku ciąg, który ogranicza niektórych funkcji, można wywołać w języku Python i sprawia, że kod przenośną między różnymi wersjami programu Python. |
    | C/C++ > Generowanie kodu | Biblioteka środowiska uruchomieniowego | Biblioteki DLL wielowątkowych (/ MD) (zobacz poniżej ostrzeżenia) |
    | Konsolidator > Ogólne | Katalogi bibliotek dodatkowe | Dodaj Python `libs` folder zawierający `.lib` pliki jako odpowiednią dla tej instalacji, na przykład `c:\Python36\libs`. (Pamiętaj wskazywał `libs` folder zawierający `.lib` pliki, i *nie* `Lib` folder zawierający `.py` pliki.) | 

    > [!Tip]
    > Jeśli nie widzisz karcie C/C++, jest on, ponieważ projekt nie zawiera żadnych plików, które identyfikuje go jako pliki źródłowe C/C++. Ten stan może wystąpić w przypadku tworzenia pliku źródłowego bez `.c` lub `.cpp` rozszerzenia. Na przykład, jeśli przypadkowo wprowadzono `module.coo` zamiast `module.cpp` nowego elementu wcześniej w oknie dialogowym, następnie Visual Studio tworzy plik, ale nie ustawiono typ pliku "C / C + kodu," czyli co aktywuje kartę właściwości C/C++. Ten misidentification pozostaje wielkość liter, nawet jeśli zmienisz nazwę pliku z `.cpp`. Aby poprawnie zainstalować ten typ pliku, kliknij prawym przyciskiem myszy plik w Eksploratorze rozwiązań wybierz **właściwości**, a następnie ustaw **typ pliku** do **kodu C/C++**.

    > [!Warning]
    > Nie należy ustawiać **C/C++ > Generowanie kodu > Biblioteka środowiska uruchomieniowego** opcje "wielowątkowych debugowania biblioteki DLL (/ MDd)" nawet w przypadku konfiguracji debugowania. Wybierz "DLL wielowątkowych (/ MD)" środowiska wykonawczego ponieważ pliki binarne Python bez debugowania tworzonych z. W przypadku opcji/mdd, zostanie wyświetlony błąd *C1189: Py_LIMITED_API jest niezgodny z Py_DEBUG, Py_TRACE_REFS i Py_REF_DEBUG* podczas kompilowania konfiguracją debugowania biblioteki DLL. Ponadto jeśli usuniesz `Py_LIMITED_API` Aby uniknąć błędów kompilacji, Python ulega awarii podczas próby zaimportowania z modułu. (Awarię (crash) to następuje w wywołaniu DLL `PyModule_Create` zgodnie z opisem później, z komunikatu wyjściowego z *błąd krytyczny Python: PyThreadState_Get: nie bieżącego wątku*.)
    >
    > Opcja/mdd jest używana do kompilacji pliki binarne debugowania języka Python (na przykład python_d.exe), ale nadal wybierając ją z rozszerzeniem DLL powoduje błąd kompilacji z `Py_LIMITED_API`.
   
1. Kliknij prawym przyciskiem myszy projekt C++, a następnie wybierz **kompilacji** do testowania konfiguracji (Debug i Release). `.pyd` Pliki znajdują się w *rozwiązania* folder **debugowania** i **wersji**, nie folder projektu C++ samej siebie.

1. Dodaj następujący kod do projektów C++ elementu głównego `.cpp` pliku:

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

Aby C++ DLL do rozszerzenia dla języka Python, należy zmodyfikować wyeksportowanych metod wchodzić w interakcje z typów języka Python. Następnie należy dodać funkcję, która eksportuje modułu, wraz z definicjami metod modułu. Tło na to, co przedstawiono w tym miejscu, można znaleźć w temacie [Python/C API Reference Manual](https://docs.python.org/3/c-api/index.html) i szczególnie [obiektów modułu](https://docs.python.org/3/c-api/module.html) na python.org. (Pamiętaj, aby wybrać wersji języka Python z kontrolka listy rozwijanej w prawym górnym rogu).

1. W pliku C++ obejmują `Python.h` u góry:

    ```cpp
    #include <Python.h>
    ```

1. Modyfikowanie `tanh_impl` metody, aby zaakceptować i zwracanych typów Python:

    ```cpp
    PyObject* tanh_impl(PyObject *, PyObject* o) {
        double x = PyFloat_AsDouble(o);
        double tanh_x = sinh_impl(x) / cosh_impl(x);
        return PyFloat_FromDouble(tanh_x);
    }
    ```

1. Struktury, który definiuje sposób C++ `tanh` funkcja jest udostępniana Python:

    ```cpp
    static PyMethodDef superfastcode_methods[] = {
        // The first property is the name exposed to python, the second is the C++ function name        
        { "fast_tanh", (PyCFunction)tanh_impl, METH_O, nullptr },

        // Terminate the array with an object containing nulls.
        { nullptr, nullptr, 0, nullptr }
    };
    ```

1. Dodaj struktura, która definiuje modułu, jak widać przez kod języka Python. (Wpływu są wewnętrzne dla projektów C++, takie jak module.cpp, nazwy plików).

    ```cpp
    static PyModuleDef superfastcode_module = {
        PyModuleDef_HEAD_INIT,
        "superfastcode",                        // Module name as Python sees it
        "Provides some functions, but faster",  // Module description
        0,
        superfastcode_methods                   // Structure that defines the methods
    };
    ```

1. Dodaj metodę, która wywołuje Python ładuje moduł, który musi mieć nazwę `PyInit_<module-name>`, gdzie  *&lt;nazwa_modułu&gt;*  dokładnie odpowiada projektu C++ **ogólne > Nazwa docelowego** właściwości (to znaczy, że jest on zgodny nazwę pliku `.pyd` skompilowanego przez projekt).

    ```cpp
    PyMODINIT_FUNC PyInit_superfastcode() {    
        return PyModule_Create(&superfastcode_module);
    }
    ```

1. Tworzenie projektu C++ ponownie w celu zweryfikowania kodu.

## <a name="test-the-code-and-compare-the-results"></a>Testowanie kodu i porównywania wyników

Teraz, gdy masz DLL strukturze rozszerzenia języka Python, zapoznaj się z jego projektów języka Python, zaimportuj moduł, a jego metody.

### <a name="make-the-dll-available-to-python"></a>Udostępnia biblioteki DLL języka Python

Istnieją dwa sposoby, aby udostępnić biblioteki DLL języka Python.

Można najpierw Dodaj odwołanie projektu języka Python do projektów C++, pod warunkiem, że są one w tym samym rozwiązaniu Visual Studio:

1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **odwołania** węzła w projekcie języka Python i wybierz **Dodaj odwołanie**. W wyświetlonym oknie dialogowym wybierz **projekty** wybierz opcję **superfastcode** projektu (lub korzystania z dowolnym wybraną nazwę), a następnie **OK**.

Po drugie można zainstalować moduł globalnego środowiska Python, udostępnianie innych projektów języka Python. Wykonywanie operacji tak zazwyczaj wymaga, aby odświeżyć bazy danych uzupełniania IntelliSense dla tego środowiska. Odświeżanie jest również podczas usuwania modułu ze środowiska.

1. Jeśli używasz programu Visual Studio 2017 r, uruchom Instalatora programu Visual Studio wybierz **Modyfikuj**, wybierz pozycję **pojedynczych składników > kompilatorów kompilacji narzędzia i środowisk uruchomieniowych > zestaw narzędzi w wersji 140 Visual C++ 2015.3**. Ten krok jest niezbędny, ponieważ języka Python (dla systemu Windows) jest skompilowanej za pomocą programu Visual Studio 2015 (wersja 14.0) i oczekuje, że te narzędzia są dostępne podczas kompilowania rozszerzeń za pomocą metody opisanej w tym miejscu.

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

1. `setup.py` Kod nakazuje Python do tworzenia rozszerzenia przy użyciu zestawu narzędzi Visual Studio 2015 C++, gdy jest używany z wiersza polecenia. Otwórz wiersz polecenia z podwyższonym poziomem uprawnień, przejdź do folderu zawierającego projektu C++ (i `setup.py`), a następnie wprowadź następujące polecenie:

    ```
    pip install .
    ```

### <a name="call-the-dll-from-python"></a>Wywołanie biblioteki DLL w języku Python

Po wykonaniu dowolnej z metod powyżej można teraz wywołać `fast_tanh` funkcji i porównać jego wydajność, aby implementacji Python:

1. Dodaj następujące wiersze w Twojej `.py` pliku do wywołania `fast_tanh` metody wyeksportowane z biblioteki DLL i wyświetlić dane wyjściowe. W przypadku wpisania `from s` instrukcji ręcznie, zobaczysz `superfastcode` znaleziona na liście uzupełniania i po wpisaniu `import` `fast_tanh` metody zostanie wyświetlone.

    ```python
    from superfastcode import fast_tanh    
    test(lambda d: [fast_tanh(x) for x in d], '[fast_tanh(x) for x in d]')
    ```

1. Uruchom Python program i zobacz, procedura C++ szybciej niż implementacji Python uruchamia 5 do 20 razy. Ponownie, spróbuj zwiększyć `COUNT` zmiennej, dzięki czemu większa różnice. Ponadto należy pamiętać, że kompilacji wydania modułu C++ uruchamia szybciej niż kompilację debugowania, ponieważ Kompilacja debugowania jest mniejsza zoptymalizowanych pod kątem i zawiera różne sprawdzanie błędów. Swobodnie przełączać się między te konfiguracje do porównania.

## <a name="debug-the-c-code"></a>Debugowanie kodu C++

Program Visual Studio obsługuje debugowania kodu Python i C++ razem.

1. Kliknij prawym przyciskiem myszy projekt języka Python w Eksploratorze rozwiązań, wybierz **właściwości**, wybierz pozycję **debugowania** , a następnie wybierz **Debuguj > Włącz debugowanie kodu natywnego** opcji.

    > [!Tip]
    > Gdy włączone jest debugowanie kodu natywnego, w oknie danych wyjściowych Python może zniknąć natychmiast po zakończeniu program bez umożliwiając zwykle Wstrzymaj "Naciśnij dowolny klawisz, aby kontynuować...". Aby wymusić przerwie, Dodaj `-i` opcji w celu **Uruchom > argumenty Interpreter** na **debugowania** karcie, gdy włączone jest debugowanie kodu natywnego. Ten argument umieszcza interpreter języka Python w trybie interakcyjnym, po zakończeniu kodu, w którym czeka na naciśnij klawisz Enter, aby zakończyć Ctrl + Z. (, Jeśli nie stanowi modyfikowanie kodu języka Python, możesz dodać `import os` i `os.system("pause")` instrukcje w końcu program. Ten kod duplikatów oryginalnego wiersza Wstrzymaj).

1. Wybierz **Plik > Zapisz** można zapisać zmian właściwości.

1. Ustaw dla konfiguracji kompilacji do debugowania na pasku narzędzi programu Visual Studio. 

    ![Ustawienie konfiguracji kompilacji debugowania](media/cpp-set-debug.png)

1. Ponieważ kod zwykle trwa dłużej, w debugerze, można zmienić `COUNT` zmiennej w Twojej `.py` pliku około 5 razy mniejsza wartość (na przykład zmienić go z `500000` do `100000`).

1. W kodzie C++ Ustaw punkt przerwania w pierwszym wierszu `tanh_impl` metody, a następnie uruchomienia debugera (F5 lub **Debuguj > Rozpocznij debugowanie**). Debuger zatrzymywana, gdy kod jest wywoływana. Jeśli nie zostaje trafiony punkt przerwania, sprawdź, czy konfiguracja jest ustawiona na debugowanie i zapisaniu projektu (który nie jest wykonywane automatycznie podczas uruchamiania debugera).

    ![Zatrzymywanie w punkcie przerwania w kodzie C++](media/cpp-debugging.png)

1. W tym momencie można wykonywać krokowo kodu C++, Sprawdź zmienne i tak dalej. Te funkcje są wyszczególnione w [debugowanie C++ i Python razem](debugging-mixed-mode.md).

## <a name="alternative-approaches"></a>Alternatywnych metod 

Istnieją różne sposoby tworzenia rozszerzenia języka Python, zgodnie z opisem w poniższej tabeli. Pierwszy wpis języka CPython jest, co zostało omówione w tym temacie już.

| Podejście | Zbioru | Przedstawiciel użytkowników | Pro(s) | CON(s) |
| --- | --- | --- | --- | --- |
| Moduły rozszerzenia C/C++ dla języka CPython | 1991 | Standardowa biblioteka | [Szczegółową dokumentację i samouczki](https://docs.python.org/3/c-api/). Pełną kontrolę. | Kompilacja, przenośność, zarządzanie odwołania. Wysoka C wiedzy. |
| SWIG | 1996 | [crfsuite](http://www.chokkan.org/software/crfsuite/) | Generowanie jednocześnie powiązania dla wielu języków. | Nadmierne obciążenie w przypadku języka Python tylko docelowy. |
| ctypes | 2003 | [oscrypto](https://github.com/wbond/oscrypto) | Nie kompilacji szeroki dostępności. | Uzyskiwanie dostępu do i mutacja struktury C skomplikowane i błąd podatnych na błędy. |
| Cython | 2007 | [gevent](http://www.gevent.org/), [kivy](https://kivy.org/) | Notacji języka Python. Wysoce dojrzała. Wysoka wydajność. | Kompilacja, nowej składni i łańcuch narzędzi. |
| cffi | 2013 | [Kryptografia](https://cryptography.io/en/latest/), [pypy](http://pypy.org/) | Łatwa integracja, PyPy zgodności. | Nowy, mniej dojrzała. |
