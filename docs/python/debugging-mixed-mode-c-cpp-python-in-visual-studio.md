---
title: Tryb mieszany debugowania dla języka Python
description: Jak można jednocześnie debugować C++ i języku Python w programie Visual Studio, w tym przechodzenie między środowiskami, wyświetlanie wartości i obliczaniu wyrażeń.
ms.custom: ''
ms.date: 01/16/2018
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
ms.openlocfilehash: 40ab75cfd35f3d748d5e000ff1a45d2999fc649e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="debugging-python-and-c-together"></a>Debugowanie razem Python i C++

Najbardziej regularne debugery Python obsługuje debugowania tylko kodu języka Python. W praktyce jednak Python umożliwia w połączeniu z C lub C++ w scenariuszach wymagających wysokiej wydajności lub możliwości bezpośrednie wywoływanie interfejsów API platformy. (Zobacz [Tworzenie rozszerzenia C++ dla języka Python](working-with-c-cpp-python-in-visual-studio.md) przewodnik.)

Program Visual Studio udostępnia zintegrowane, jednocześnie dla języka Python i natywnego C/C++, debugowanie w trybie mieszanym, pod warunkiem, że wybrano **Python natywnych narzędzi** opcji dla obciążenia Python Programowanie w Visual Studio Instalator.

> [!Note]
> Debugowanie w trybie mieszanym nie jest dostępna z narzędziami języka Python dla programu Visual Studio 1.x w Visual Studio 2015 lub starszym.

Funkcje debugowania w trybie mieszanym zawierają następujące informacje, jak opisano w tym artykule:

- Stosy wywołań połączone
- Krok między Python i kod natywny
- Punkty przerwania w obu typów kodu
- Zobacz Python reprezentacje obiektów ramek natywnych i na odwrót
- Debugowanie w kontekście projektu języka Python lub projektu C++

![Debugowanie w trybie mieszanym](media/mixed-mode-debugging.png)

|   |   |
|---|---|
| ![Ikona aparatu film wideo](../install/media/video-icon.png "obejrzeć film wideo") | Aby obejrzeć wprowadzenie do tworzenia, testowania i debugowania modułów macierzystych C z programem Visual Studio, zobacz [nowości: Tworzenie modułów macierzystych](https://youtu.be/D9RlT06a1EI) (witrynie youtube.com, 9 m 09s). Wideo ma zastosowanie do programu Visual Studio 2015 i 2017 r. |

## <a name="enable-mixed-mode-debugging-in-a-python-project"></a>Włącz debugowanie w trybie mieszanym w projekcie języka Python

1. Kliknij prawym przyciskiem myszy projekt języka Python w Eksploratorze rozwiązań, wybierz **właściwości**, wybierz pozycję **debugowania** , a następnie wybierz **Włącz debugowanie kodu natywnego**. Ta opcja umożliwia włączenie trybu mieszanego dla sesji debugowania wszystkie.

    ![Włączanie debugowania kodu natywnego](media/mixed-mode-debugging-enable-native.png)

    > [!Tip]
    > Gdy włączone jest debugowanie kodu natywnego, w oknie danych wyjściowych Python może zniknąć natychmiast po zakończeniu program bez umożliwiając zwykle Wstrzymaj "Naciśnij dowolny klawisz, aby kontynuować...". Aby wymusić przerwie, Dodaj `-i` opcji w celu **Uruchom > argumenty Interpreter** na **debugowania** karcie, gdy włączone jest debugowanie kodu natywnego. Ten argument umieszcza interpreter języka Python w trybie interakcyjnym, po zakończeniu kodu, w którym czeka na naciśnij klawisz Enter, aby zakończyć Ctrl + Z.

1. Podczas dołączania do istniejącego procesu debugera trybu mieszanego (**Debuguj > dołączyć do procesu...** ), użyj **wybierz...**  przycisk, aby otworzyć **wybór typu kodu** okna dialogowego. Następnie ustaw **Debuguj te typy kodu** opcję i zaznacz oba **natywnego** i **Python** na liście:

    ![Wybieranie typów kodu macierzystego i języka Python](media/mixed-mode-debugging-code-type.png)

    Ustawienia typu kodu są trwałe, więc jeśli chcesz wyłączyć debugowanie w trybie mieszanym podczas dołączania do innego procesu później, wyczyść typ kodu języka Python.

    Można wybrać inne typy kodu, oprócz lub zamiast **natywnego**. Na przykład, jeśli zarządzanej aplikacji obsługuje języka CPython, z kolei używa modułów macierzystych rozszerzenia, i chcesz debugować wszystkie trzy, można sprawdzić **Python**, **natywnego**, i **zarządzane**razem ujednoliconym środowisku debugowania w tym stosy wywołań połączone, a następnie między wszystkie trzy środowisk uruchomieniowych.

1. Podczas uruchamiania debugowania w trybie mieszanym po raz pierwszy, może zostać wyświetlony **wymagane symbole Python** okna dialogowego (zobacz [symboli do debugowania w trybie mieszanym](debugging-symbols-for-mixed-mode-c-cpp-python.md)). Musisz zainstalować symbole tylko raz w każdym środowisku danego języka Python. Symbole są automatycznie dołączane po zainstalowaniu obsługi języka Python za pomocą Instalatora programu Visual Studio 2017 r.

1. Sprawdź kod źródłowy standard języka Python, osiągalny podczas debugowania, odwiedź [ https://www.python.org/downloads/source/ ](https://www.python.org/downloads/source/), pobierz odpowiednie dla posiadanej wersji archiwum i wyodrębnij go do folderu. Można następnie punktu programu Visual Studio do określonych plików w tym folderze, w dowolnym momencie go monit.

## <a name="enable-mixed-mode-debugging-in-a-cc-project"></a>Włącz debugowanie w trybie mieszanym w projekcie C/C++

Visual Studio 2017 (wersja 15.5 i nowsze) obsługuje debugowanie w trybie mieszanym z projektu C/C++ (na przykład, podczas gdy [osadzanie Python w innej aplikacji, zgodnie z opisem na python.org](https://docs.python.org/3/extending/embedding.html)). Aby włączyć debugowanie w trybie mieszanym, należy skonfigurować projekt C/C++ do uruchomienia Debuggera"Python lub natywne":

1. Kliknij prawym przyciskiem myszy projekt C/C++ w Eksploratorze rozwiązań i wybierz **właściwości**
1. Wybierz **debugowanie** , a następnie wybierz "Python lub natywne debugera" z **debugera, aby uruchomić**i wybierz **OK**.

    ![Wybieranie debugera Python lub natywne w projekcie C/C++](media/mixed-mode-debugging-select-cpp-debugger.png)

Za pomocą tej metody, należy pamiętać, że nie można debugować `py.exe` uruchamiania, ponieważ jego spowoduje utworzenie elementu podrzędnego `python.exe` debugera nie można dołączyć do procesu. Jeśli chcesz uruchomić `python.exe` bezpośrednio z argumentami, zmień **polecenia** opcję we właściwościach Python lub natywne debugowanie (wyświetlane na poprzedniej ilustracji), aby określić pełną ścieżkę do `python.exe`, następnie określ argumenty **Argumenty polecenia**.

### <a name="attaching-the-mixed-mode-debugger"></a>Dołączanie debugera trybu mieszanego

Wszystkie poprzednie wersje programu Visual Studio debugowanie w trybie mieszanym bezpośredniego można włączyć tylko wtedy, gdy uruchamianie projektu języka Python w programie Visual Studio, ponieważ jest używany przez debuger natywny projektów C/C++. Można jednak uruchomić debugera oddzielnie:

1. Uruchomienie bez debugowania projektu C++ (**debugowania > Uruchom bez debugowania** lub Ctrl + F5).
1. Wybierz **Debuguj > dołączyć do procesu...** . W oknie dialogowym, wybierz odpowiedni proces, a następnie użyj **wybierz...**  przycisk, aby otworzyć **wybór typu kodu** okna dialogowego, w którym można wybrać Python:

    ![Wybór języka Python jako typ debugowania podczas dołączanie debugera](media/mixed-mode-debugging-attach-type.png)

1. Wybierz **OK** celu zamknięcia tego okna dialogowego, następnie **Attach** można uruchomić debugera.
1. Może być konieczne wprowadzenie odpowiednich pauzę lub opóźnienia w aplikacji C++, aby upewnić się, że nie wymaga kod języka Python, który chcesz debugować przed prawdopodobieństwo można dołączyć debugera.

## <a name="mixed-mode-specific-features"></a>Funkcje specyficzne dla trybu mieszanego

- [Stos wywołań połączone](#combined-call-stack)
- [Wykonywanie krok po kroku, między Python i kod natywny](#stepping-between-python-and-native-code)
- [Wyświetl wartości PyObject w kodzie natywnym](#pyobject-values-view-in-native-code)
- [Wyświetl wartości macierzystych w kodzie języka Python](#native-values-view-in-python-code)

### <a name="combined-call-stack"></a>Stos wywołań połączone

Stos wywołań okna zawiera zarówno macierzystego i Python ramek stosu przeplatana z przejścia oznaczone między nimi:

![Stos wywołań połączone](media/mixed-mode-debugging-call-stack.png)

Przejścia są wyświetlane jako "[kod zewnętrzny]", bez określania kierunku przejścia, jeśli **Narzędzia > Opcje > debugowanie > Ogólne > Włącz opcję tylko mój kod** opcja jest ustawiona.

Dwukrotne kliknięcie żadnej ramce wywołanie powoduje active i otwiera kod źródłowy odpowiednie, jeśli to możliwe. Jeśli kod źródłowy jest niedostępny, ramki nadal jest aktywowane i mogą być kontrolowane zmiennych lokalnych.

### <a name="stepping-between-python-and-native-code"></a>Wykonywanie krok po kroku, między Python i kod natywny

Korzystając z Step Into (F11) lub polecenia Step Out (Shift + F11), debuger trybu mieszanego poprawnie obsługuje zmiany pomiędzy typami kodu. Na przykład gdy Python wywołuje metody typu, która jest zaimplementowana w języku C, wykonywanie krok po kroku na wywołanie metody zatrzymuje się na początku funkcji macierzystej implementacji metody. Podobnie, gdy kod natywny wywołuje niektórych funkcji interfejsu API języka Python, która powoduje wywoływany kod języka Python. Na przykład Wkraczanie do `PyObject_CallObject` na wartość funkcja, która została pierwotnie zdefiniowana w języku Python zatrzymuje się na początku funkcji języka Python. Wykonywanie krok po kroku w języku Python Native jest również obsługiwany w przypadku funkcje natywne wywołane z języka Python za pomocą [ctypes](http://docs.python.org/3/library/ctypes.html).

### <a name="pyobject-values-view-in-native-code"></a>Wyświetl wartości PyObject w kodzie natywnym

Gdy ramka natywna (C lub C++) jest aktywny, jego zmiennych lokalnych wyświetlane w oknie zmienne lokalne debugera. W modułów macierzystych rozszerzenia języka Python, wiele z tych zmiennych są typu `PyObject` (czyli element typedef dla `_object`), lub kilka innych podstawowych Python typów (patrz poniżej). W debugowanie w trybie mieszanym, te wartości przedstawia dodatkowe podrzędnym z etykietą "Python widok". Po rozwinięciu ten węzeł zawiera reprezentacja Python zmiennej, taki sam jak co zobaczysz Jeśli zmienna lokalna odwołuje się do tego samego obiektu był obecny w ramce Python. Element podrzędny tego węzła są edytowalne.

![Widok języka Python](media/mixed-mode-debugging-python-view.png)

Aby wyłączyć tę funkcję, kliknij prawym przyciskiem myszy w oknie zmienne lokalne i przełączania **Python > Pokaż węzłów widoku Python** opcji menu:

![Włączanie widoku języka Python](media/mixed-mode-debugging-enable-python-view.png)

C typy węzłów tego pokazu "[widok Python]" (jeśli jest włączona):

- `PyObject`
- `PyVarObject`
- `PyTypeObject`
- `PyByteArrayObject`
- `PyBytesObject`
- `PyTupleObject`
- `PyListObject`
- `PyDictObject`
- `PySetObject`
- `PyIntObject`
- `PyLongObject`
- `PyFloatObject`
- `PyStringObject`
- `PyUnicodeObject`

"[Widok Python]" nie jest automatycznie wyświetlane dla typów, które samodzielne utworzenie. Podczas tworzenia rozszerzeń dla języka Python 3.x, braku zazwyczaj nie stanowi to problemu ponieważ dowolnego obiektu ostatecznie ma `ob_base` pole jeden z typów powyżej, co powoduje, że "[Python widoku]".

Dla języka Python 2.x, jednak każdego typu obiektu zwykle deklaruje jej nagłówek jako kolekcja pola śródwierszowe, i istnieje skojarzenie między typami utworzone niestandardowe i `PyObject` na poziomie systemu typu w kodzie C/C++. Aby umożliwić węzłów "[widok Python]" dla takich typów niestandardowych, Edytuj `PythonDkm.natvis` w [katalog instalacji narzędzi Python tools](installing-python-support-in-visual-studio.md#install-locations)i dodać innego elementu w pliku XML dla struktury języka C lub C++ klasy.

Opcja alternatywne (i lepsze) jest wykonanie czynności opisanych [3123 program ten](http://www.python.org/dev/peps/pep-3123/) i Użyj jawnego `PyObject ob_base;` pola zamiast `PyObject_HEAD`, ale które mogą nie być możliwe ze względów zgodności z poprzednimi wersjami.

### <a name="native-values-view-in-python-code"></a>Wyświetl wartości macierzystych w kodzie języka Python

Podobnie jak w poprzedniej sekcji, można włączyć "[C++ widok]" natywnej wartości w oknie zmienne lokalne gdy ramka Python jest aktywny. Ta funkcja nie jest włączona domyślnie, możesz włączyć ją, klikając prawym przyciskiem myszy w oknie zmienne lokalne i przełączanie **Python > Pokaż węzłów widoku C++** opcji menu.

![Włączanie widoku C++](media/mixed-mode-debugging-enable-cpp-view.png)

Węzeł "[C++ widok]" zawiera reprezentację wewnętrzna struktura C/C++ dla wartości, takie same jak zobaczysz w ramka natywna. Na przykład zawiera wystąpienie `_longobject` (dla którego `PyLongObject` jest elementem typedef) dla długich liczb całkowitych Python który próbuje rozpoznać typy dla natywnego klas, które utworzone przez użytkownika samodzielnie. Element podrzędny tego węzła są edytowalne.

![Widok C++](media/mixed-mode-debugging-cpp-view.png)

Jeśli pole podrzędny obiekt jest typu `PyObject`, lub jednego z innych obsługiwanych typów, to jego "[widok Python]" reprezentacja węzła (Jeśli te oświadczenia są włączone), co umożliwia nawigowanie wykresów obiektów, których łącza nie są bezpośrednio widoczne dla Python.

W przeciwieństwie do węzłów "[widok Python]", korzystających z języka Python metadane obiektu można określić typu obiektu, nie istnieje mechanizm podobnie niezawodnej "[C++ widoku]". Ogólnie rzecz biorąc, określoną wartość Python (to znaczy `PyObject` odwołania) nie jest możliwe niezawodnie ustalić, które struktury C/C++ jest wspierającą. Debuger trybu mieszanego próbuje odgadnąć tego typu, analizując różnych pól typu obiektu (takich jak `PyTypeObject` odwołuje się jego `ob_type` pole) mają typy wskaźników funkcji. Jeśli jeden z tych wskaźników funkcji odwołuje się do funkcji, które mogą zostać rozwiązane, a ta funkcja ma `self` parametr typu określony więcej niż `PyObject*`, a następnie typu zakłada, że zapasowy typ. Na przykład jeśli `ob_type->tp_init` punktów danego obiektu w następujących funkcji:

```c
static int FobObject_init(FobObject* self, PyObject* args, PyObject* kwds) {
    return 0;
}
```

następnie debuger poprawnie można wywnioskować, że typ C obiektu jest `FobObject`. Jeśli nie można określić dokładniejsze typu z `tp_init`, powoduje przeniesienie do innych pól. Jeśli nie można wywnioskować typu za pomocą dowolnego z tych pól, węzeł "[C++ widok]" zawierał obiekt jako `PyObject` wystąpienia.

Aby zawsze uzyskać przydatne reprezentację niestandardowe typy utworzone, najlepiej zarejestrować co najmniej jedna funkcja specjalne podczas rejestrowania typu i użyj silnie typizowanego `self` parametru. Większość typów spełnienia tego wymagania naturalnie; Jeśli to nie jest przypadek, następnie `tp_init` jest zazwyczaj najodpowiedniejszym wpisu do użycia w tym celu. Implementacja fikcyjny `tp_init` dla typu, który znajduje się wyłącznie do włączenia typ debugera wnioskowania można tylko zwrócić zero natychmiast, jak w powyższym przykładowy kod.

## <a name="differences-from-standard-python-debugging"></a>Różnice z standardowe debugowania języka Python

Debuger trybu mieszanego różni się od [standardowe debugera Python](debugging-python-in-visual-studio.md) w tym wprowadza pewne dodatkowe funkcje, ale nie ma niektórych możliwości związanych z Python:

- Nieobsługiwane funkcje: warunkowych punktów przerwania, okna interaktywnego debugowania i zdalne debugowanie między platformami.
- Okno bezpośrednie: ale dostępne z ograniczonym podzbiorem jej funkcje, w tym wszystkie ograniczenia znajduje się w tym miejscu.
- Obsługiwane wersje Python: języka CPython 2.7 i 3.3 + tylko.
- Visual Studio Shell: Podczas korzystania z języka Python z programu Visual Studio Shell (na przykład, jeśli został zainstalowany przy użyciu zintegrowanego Instalatora), programu Visual Studio nie mógł otworzyć projektów C++ i edytowania plików języka C++, jest to edytor tekstu podstawowego. Jednak debugowanie C/C++ i debugowanie w trybie mieszanym są w pełni obsługiwane w powłoce z kodem źródłowym, Wkraczanie do kodu macierzystego i C++ wyrażenia w oknach debugera.
- Wyświetlanie i rozwijanie obiektów: gdy wyświetlanie Python obiektów w oknach zmienne lokalne i obejrzyj okna narzędzi debugera, debugera trybu mieszanego pokazuje tylko struktura obiektów. On automatycznie ocenę właściwości lub Pokaż obliczona atrybutów. Dla kolekcji, zawiera tylko elementy kolekcji wbudowanych typów (`tuple`, `list`, `dict`, `set`). Niestandardowe typy kolekcji są nie wizualizowane jako kolekcje, chyba że są one dziedziczone z pewien typ kolekcji wbudowanych.
- Szacowanie wyrażeń: patrz poniżej.

### <a name="expression-evaluation"></a>Szacowanie wyrażeń

Standardowa debugera Python umożliwia oceny dowolnego wyrażeń języka Python w obserwowane i bezpośredniego systemu windows podczas debugowanym procesie jest wstrzymana w dowolnym momencie w kodzie, dopóki nie zostanie zablokowany w operacji We/Wy lub inne podobne wywołanie systemowe. W debugowanie w trybie mieszanym, można oszacować wyrażenia dowolnego tylko wtedy, gdy zatrzymany w kodzie języka Python, po punkt przerwania lub przy przechodzeniu do kodu. Tylko w wątku, w którym wystąpiło punkt przerwania lub wykonywania krokowego operacji można oszacować wyrażenia.

Po zatrzymaniu w kodzie natywnym, lub w kodzie języka Python gdzie powyższe warunki nie są stosowane (na przykład po zakończeniu operacji poza krok lub w innym wątku), Obliczanie wyrażenia jest ograniczona do uzyskiwania dostępu do zmiennych lokalnych i globalnych aktualnie wybranego zakresu Ramka, uzyskiwanie dostępu do swoich pól i indeksowania kolekcji wbudowanych typów z literały. Na przykład obliczyć następującego wyrażenia może być w dowolnym kontekście (pod warunkiem, że wszystkie identyfikatory odwoływać się do istniejących zmiennych i pól odpowiednie typy):

```python
foo.bar[0].baz['key']
```

Debuger trybu mieszanego rozwiązuje również takich wyrażeń inaczej. Wszystkie operacje dostęp do elementu członkowskiego wyszukiwanie tylko pola, które są bezpośrednio część obiektu (np. wpis w jego `__dict__` lub `__slots__`, lub pole natywnego struktury, który jest dostępny dla języka Python za pomocą `tp_members`) i Ignoruj wszystkie `__getattr__`, `__getattribute__`lub logiki deskryptora. Podobnie, Ignoruj wszystkie operacje indeksowania `__getitem__`i uzyskać bezpośredni dostęp do struktur danych wewnętrznych kolekcji.

Dla spójności ten program rozpoznawania nazw jest używana do wszystkie wyrażenia, które pasują do ograniczeń dla oceny wyrażenia ograniczone, niezależnie od tego, czy są dozwolone dowolnego wyrażenia do bieżącego punkt zatrzymania. Aby wymusić prawidłowego semantykę języka Python podczas ewaluatora kompletne jest dostępny, ujmij wyrażenie w nawiasach:

```python
(foo.bar[0].baz['key'])
```