---
title: "Debugowanie w trybie mieszanym dla języka Python w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 07/12/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: de429d6ffd934b44a15aa8b407243f8ccf0e2149
ms.sourcegitcommit: f36eb7f989efbdbed0d0a087afea8ffe27d8ca15
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2017
---
# <a name="debugging-python-and-c-together"></a>Debugowanie razem Python i C++

Najbardziej regularne debugery Python obsługuje debugowania tylko kodu języka Python. W praktyce, Python jest jednak używany w połączeniu z C lub C++ którym wymagany jest wysoka wydajność lub wprowadzić możliwość bezpośrednie wywoływanie interfejsów API platformy (zobacz [Tworzenie rozszerzenia C++ dla języka Python](cpp-and-python.md) przykład. Po załadowaniu projektu języka Python, program Visual Studio udostępnia zintegrowane, jednoczesnych trybu mieszanego możliwość krok między Python i kodu natywnego, punkty przerwania w obu typów kodu i możliwość debugowania dla języka Python i natywnego C/C++, z stosy wywołań połączone, Zobacz Python reprezentacje obiektów ramek natywnych i na odwrót:

![Debugowanie w trybie mieszanym](media/mixed-mode-debugging.png) 

Aby obejrzeć wprowadzenie do tworzenia, testowania i debugowania modułów macierzystych C z programem Visual Studio, zobacz [nowości: Tworzenie modułów macierzystych](https://youtu.be/D9RlT06a1EI) (witrynie youtube.com, 9m9s). Wideo ma zastosowanie do programu Visual Studio 2015 i 2017 r.

> [!VIDEO https://www.youtube.com/embed/D9RlT06a1EI]

> [!Note]
> Debugowanie w trybie mieszanym nie jest dostępna z narzędziami języka Python dla programu Visual Studio 1.x.

## <a name="enabling-mixed-mode-debugging"></a>Włączanie debugowania w trybie mieszanym

1. Kliknij prawym przyciskiem myszy projekt w Eksploratorze rozwiązań wybierz **właściwości**, wybierz pozycję **debugowania** karcie, a następnie włącz opcję **Włącz debugowanie kodu natywnego**. Ta opcja umożliwia włączenie trybu mieszanego dla sesji debugowania wszystkie.

    ![Włączanie debugowania kodu natywnego](media/mixed-mode-debugging-enable-native.png)

    > [!Tip]    
    > Gdy włączone jest debugowanie kodu natywnego, w oknie danych wyjściowych Python może zniknąć natychmiast po zakończeniu program bez umożliwiając zwykle Wstrzymaj "Naciśnij dowolny klawisz, aby kontynuować...". Aby wymusić przerwie, Dodaj `-i` opcji w celu **Uruchom > argumenty Interpreter** na **debugowania** karcie, gdy włączone jest debugowanie kodu natywnego. Ten argument umieszcza interpreter języka Python w trybie interakcyjnym, po zakończeniu kodu, w którym czeka na naciśnij klawisz Enter, aby zakończyć Ctrl + Z.

1. Podczas dołączania do istniejącego procesu debugera trybu mieszanego (**Debuguj > dołączyć do procesu...** ), wybierz pozycję **wybierz...**  przycisk, aby otworzyć **wybór typu kodu** okno dialogowe, zestaw **Debuguj te typy kodu** i wybrać zarówno **natywnego** i  **Python** na liście:

    ![Wybieranie typów kodu macierzystego i języka Python](media/mixed-mode-debugging-code-type.png)

    Ustawienia typu kodu są trwałe, więc jeśli chcesz wyłączyć debugowanie w trybie mieszanym podczas dołączania do innego procesu później, powtórz te kroki i wyczyść typ kodu języka Python.

    Można wybrać inne typy kodu, oprócz lub zamiast **natywnego**. Na przykład, jeśli zarządzanej aplikacji obsługuje języka CPython, z kolei używa modułów macierzystych rozszerzenia, i chcesz debugować wszystkie trzy, można sprawdzić **Python**, **natywnego**i kod zarządzany ** do ujednoliconego w tym obsługi debugowania łączyć stosy wywołań i przechodzenie między wszystkie trzy środowisk uruchomieniowych.

1. Podczas uruchamiania debugowania w trybie mieszanym po raz pierwszy, może zostać wyświetlony **wymagane symbole Python** okna dialogowego. Zobacz [symboli do debugowania w trybie mieszanym](debugging-symbols-for-mixed-mode.md) szczegółowe informacje. Musisz zainstalować symbole tylko raz w każdym środowisku danego języka Python. Należy pamiętać, że po zainstalowaniu obsługi języka Python za pomocą Instalatora programu Visual Studio 2017 symbole są dołączane automatycznie.

1. Można również trzeba przygotować się kodu źródłowego języka Python. Dla języka Python standardowy, kod źródłowy jest uzyskiwany z [https://www.python.org/downloads/source/](https://www.python.org/downloads/source/). Pobierz odpowiednią dla danej wersji archiwum i wyodrębnij go do folderu. Można następnie punktu programu Visual Studio do określonych plików w tym folderze, w dowolnym momencie go monit.

> [!Note]
> Trybu mieszanego debugowania zgodnie z opisem w tym miejscu jest włączona tylko wtedy, gdy projekt Python załadowanych do programu Visual Studio. Tego projektu określa tryb debugowania programu Visual Studio, czyli, co sprawia, że opcja trybu mieszanego dostępne. Jeśli jednak masz załadować projekt C++ (jak w przypadku podczas [osadzanie Python w innej aplikacji, zgodnie z opisem na python.org](https://docs.python.org/3/extending/embedding.html), a następnie debuger natywny C++, która nie obsługuje debugowanie w trybie mieszanym korzysta z programu Visual Studio.
>
> W takim przypadku Uruchom bez debugowania projektu C++ (**debugowania > uruchomienie bez debugowania** lub Ctrl + F5), a następnie użyć **debugowania > dołączyć do procesu...** . W oknie dialogowym, wybierz odpowiedni proces, a następnie użyj **wybierz...**  przycisk, aby otworzyć **wybór typu kodu** okna dialogowego, w którym można wybrać Python, jak pokazano poniżej. Wybierz **OK** celu zamknięcia tego okna dialogowego, następnie **Attach** można uruchomić debugera. Należy pamiętać, że może być konieczne wprowadzenie odpowiednich pauzę lub opóźnienia w aplikacji C++, aby upewnić się, że nie wymaga Python chcesz debugować przed można uruchomić debugera.
>
> ![Wybór języka Python jako typ debugowania podczas dołączanie debugera](media/mixed-mode-debugging-attach-type.png)

## <a name="mixed-mode-specific-features"></a>Funkcje specyficzne dla trybu mieszanego

- [Stos wywołań połączone](#combined-call-stack)
- [Wykonywanie krok po kroku, między Python i kod natywny](#stepping-between-python-and-native-code)
- [Wyświetl wartości PyObject w kodzie natywnym](#pyobject-values-view-in-native-code)
- [Wyświetl wartości macierzystych w kodzie języka Python](#native-values-view-in-python-code)

### <a name="combined-call-stack"></a>Stos wywołań połączone

Stos wywołań okna zawiera zarówno macierzystego i Python ramek stosu przeplatana z przejścia oznaczone między nimi:

![Stos wywołań połączone](media/mixed-mode-debugging-call-stack.png)

> [!Note]
> Przejścia są wyświetlane jako "[kod zewnętrzny]", bez określania kierunku przejścia, jeśli **Narzędzia > Opcje > debugowanie > Ogólne > Włącz opcję tylko mój kod** opcja jest ustawiona.

Dwukrotne kliknięcie żadnej ramce wywołanie powoduje active i otwiera kod źródłowy odpowiednie, jeśli to możliwe. Jeśli kod źródłowy jest niedostępny, ramki nadal jest aktywowane i mogą być kontrolowane zmiennych lokalnych.

### <a name="stepping-between-python-and-native-code"></a>Wykonywanie krok po kroku, między Python i kod natywny

Korzystając z Step Into (F11) lub polecenia Step Out (Shift + F11), debuger trybu mieszanego poprawnie obsługuje zmiany pomiędzy typami kodu. Na przykład gdy Python wywołuje metody typu, która jest zaimplementowana w języku C, wykonywanie krok po kroku na wywołanie metody zatrzymuje się na początku funkcji macierzystej implementacji metody. Podobnie, gdy kod natywny wywołuje niektórych funkcji interfejsu API języka Python, która powoduje wywoływany kod języka Python. Na przykład Wkraczanie do `PyObject_CallObject` na wartość funkcja, która została pierwotnie zdefiniowana w języku Python zatrzymuje się na początku funkcji języka Python. Wykonywanie krok po kroku w języku Python Native jest również obsługiwany w przypadku funkcje natywne wywołane z języka Python za pomocą [ctypes](http://docs.python.org/3/library/ctypes.html).

### <a name="pyobject-values-view-in-native-code"></a>Wyświetl wartości PyObject w kodzie natywnym

Gdy ramka natywna (C lub C++) jest aktywny, jego zmiennych lokalnych wyświetlane w oknie zmienne lokalne debugera. W modułów macierzystych rozszerzenia języka Python, wiele z tych zmiennych są typu `PyObject` (czyli element typedef dla `_object`), lub kilka innych podstawowych Python typów (patrz poniżej). W debugowanie w trybie mieszanym, te wartości przedstawia dodatkowe podrzędnym z etykietą "Python widok". Po rozwinięciu ten węzeł zawiera reprezentacja Python zmiennej, taki sam jak co zobaczysz Jeśli zmienna lokalna odwołuje się do tego samego obiektu był obecny w ramce Python. Element podrzędny tego węzła są edytowalne.

![Widok języka Python](media/mixed-mode-debugging-python-view.png)

Aby wyłączyć tę funkcję, kliknij prawym przyciskiem myszy w oknie zmienne lokalne i przełączania **Python > Pokaż węzłów widoku Python** opcji menu:

![Włączanie widoku języka Python](media/mixed-mode-debugging-enable-python-view.png)

C typy węzłów tego pokazu "[widok Python]" (jeśli jest włączona):

- `PyObject `
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

Dla języka Python 2.x, jednak każdego typu obiektu zwykle deklaruje jej nagłówek jako kolekcja pola śródwierszowe, i istnieje skojarzenie między typami utworzone niestandardowe i `PyObject` na poziomie systemu typu w kodzie C/C++. Aby umożliwić węzłów "[widok Python]" dla takich typów niestandardowych, Edytuj `PythonDkm.natvis` w [katalog instalacji narzędzi Python tools](installation.md#install-locations)i dodać innego elementu w pliku XML dla struktury języka C lub C++ klasy.

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

Debuger trybu mieszanego różni się od [standardowe debugera Python](debugging.md) w tym wprowadza pewne dodatkowe funkcje, ale nie ma niektórych możliwości związanych z Python:

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