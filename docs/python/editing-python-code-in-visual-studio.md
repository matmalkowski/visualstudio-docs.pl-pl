---
title: Edytowanie kodu języka Python
description: Python edycji w programie Visual Studio oferuje IntelliSense, fragmentów kodu i funkcje nawigacji obok formatowania, linting i refaktoryzacji.
ms.date: 05/07/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 90f73daad0c4ea9184337050d77a53b14e289614
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2018
ms.locfileid: "34449143"
---
# <a name="editing-python-code"></a>Edytowanie kodu języka Python

Deweloperzy poświęcać dużo czasu w edytorze kodu tak [Python obsługi w programie Visual Studio](installing-python-support-in-visual-studio.md) zapewnia funkcję ułatwiającą Twoją produktywność. Cechy IntelliSense wyróżnianie składni, automatycznego uzupełniania pomocy podpisu, zamienników metod, wyszukiwania i nawigacji.

Edytor jest także zintegrowane z okno interaktywne programu Visual Studio, co ułatwia wymienić kod między nimi. Zobacz [samouczek krok 3: Korzystanie z okna interaktywny REPL](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md) i [przy użyciu okna interaktywnego — Wyślij kod, aby polecenie interaktywne](python-interactive-repl-in-visual-studio.md#send-code-to-interactive-command) szczegółowe informacje.

|   |   |
|---|---|
| ![Ikona aparatu film wideo](../install/media/video-icon.png "obejrzeć film wideo") | [Obejrzyj film (Microsoft Virtual Academy)](https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Editing-Python-Code-r2iQH5LWE_4605918567) dla pokaz edytowanie kodu języka Python (2 m 30s).|

Dokumentacja ogólna edytowanie kodu w programie Visual Studio, aby zapoznać [funkcje edytora kodu](../ide/writing-code-in-the-code-and-text-editor.md). Zobacz też [konspekt w Visual Studio](../ide/outlining.md), który pomaga pozostać koncentruje się na poszczególnych sekcji kodu.

Można również użyć przeglądarki obiektów Visual Studio (**Widok > inne okna > przeglądarki obiektów** lub Ctrl + W, J) do sprawdzania Python klas zdefiniowanych w każdym module i funkcji zdefiniowanych w tych klas.

## <a name="intellisense"></a>IntelliSense

Udostępnia IntelliSense [zakończeń](#completions), [pomocy podpisu](#signature-help), [szybka podpowiedź](#quick-info), i [kolorowanie](#code-coloring). Visual Studio 2017 wersji 15.7 lub nowszym obsługuje również [wpisz wskazówek](#type-hints).

Aby zwiększyć wydajność, IntelliSense w **programu Visual Studio 2017 wersji 15,5 cala** i wcześniej zależy od ukończenia bazy danych, generowany dla każdego środowiska Python w projekcie. Bazy danych może być konieczne odświeżenie Jeśli dodać, usunąć lub zaktualizować pakiety. Stan bazy danych jest wyświetlany w **środowiska Python** okno (element równorzędny Solution Explorer) na **IntelliSense** kartę (zobacz [odwołania okno środowiska](python-environments-window-tab-reference.md#intellisense-tab)).

**Visual Studio 2017 wersji 15,6** i później używa różne sposoby, aby zapewnić zakończeń IntelliSense, które nie są zależne od bazy danych.

### <a name="completions"></a>Zakończeń

Zakończeń są wyświetlane jako instrukcji, identyfikatorów i słów, które mogą być odpowiednio wprowadzone w bieżącej lokalizacji w edytorze. Co to jest wyświetlane na liście jest oparta na kontekście i jest filtrowana na pominięcie nieprawidłowe lub rozpraszać opcje. Zakończeń często są wyzwalane przez wpisanie różnych instrukcje (takie jak `import`) i operatory (w tym okresie), ale można je pojawiać się w dowolnym momencie, wpisując polecenie Ctrl-J, miejsca.

![Element członkowski uzupełniania](media/code-editing-completions-simple.png)

Po otwarciu listy uzupełniania można wyszukać uzupełnianie przy użyciu klawiszy strzałek myszy lub kontynuując do typu. Podczas wpisywania więcej liter listy dalsze są filtrowane do wyświetlenia prawdopodobnie zakończeń. Można także użyć skróty takich jak:

- Wpisywanie liter, które nie są na początku nazwy, takich jak analizy, aby znaleźć "argparse"
- Wpisywanie tylko litery, które są w chwili rozpoczęcia słów, takich jak "abc", aby znaleźć "AbstractBaseClass" lub "lotniczego", aby znaleźć "as_integer_ratio"
- Pomijanie litery, takich jak b64, aby znaleźć "base64"

Kilka przykładów:

![Element członkowski uzupełnianie za pomocą filtrowania](media/code-editing-completion-filtering.png)

Członek zakończeń pojawiają się automatycznie po wpisaniu okres po wartości oraz atrybutów potencjalnych typy i metody lub zmienne. Jeśli zmienna może być więcej niż jednego typu, lista zawiera wszystkie możliwości ze wszystkich typów, z dodatkowych informacji o tym, typy, które obsługują każdego ukończenia. W przypadku, gdy zakończeniu jest obsługiwana przez wszystkie możliwe typy, jest wyświetlany bez adnotacji.

![Element członkowski wykonania wielu typów](media/code-editing-completion-types.png)

Domyślnie nie są pokazywane elementy członkowskie "dunder" (członkowie otwierające i zamykające podkreślenia podwójny). Ogólnie rzecz biorąc takie elementy członkowskie nie powinien być dostępny bezpośrednio. Jeśli potrzebujesz jednej jednak wpisanie wiodące podkreślenie podwójne dodaje te zakończeń do listy:

![Uzupełnianie prywatnego elementu członkowskiego](media/code-editing-completion-dunder.png)

`import` i `from ... import` instrukcje wyświetlić listę modułów, które można importować. Z `from ... import`, lista zawiera elementy członkowskie, które mogą zostać zaimportowane z określonego modułu.

![Ukończenia importowania](media/code-editing-completion-import.png)

`raise` i `except` instrukcje wyświetlania listy klas, które mogą być typy błędów. Listy nie może zawierać wszystkie wyjątki zdefiniowane przez użytkownika, ale pomaga szybko odnaleźć odpowiednie wyjątki wbudowany:

![Ukończenia wyjątków](media/code-editing-completion-exception.png)

Wpisanie uruchamia dekoratora i przedstawia potencjalne elementów decorator. Wiele z tych elementów nie są możliwe do użycia jako elementów decorator; Sprawdź dokumentację biblioteki, aby określić, który ma zostać użyty.

![Dekoratora zakończenia](media/code-editing-completion-decorator.png)

> [!Tip]
> Można skonfigurować zachowanie zakończeń za pośrednictwem **Narzędzia > Opcje > Edytor tekstu > Python > Zaawansowane "**. Wśród nich **na ciąg wyszukiwania na podstawie listy filtrów**: stosuje filtrowanie sugestii ukończenia podczas wpisywania (domyślny jest zaznaczone), i **zakończenia elementu członkowskiego Wyświetla przecięcie składników** zawiera tylko zakończeń, które są obsługiwane przez wszystkie możliwe typy (Domyślnie zaznaczenie jest usunięte). Zobacz [opcji - wyników zakończenia](python-support-options-and-settings-in-visual-studio.md#completion-results).

### <a name="type-hints"></a>Wskazówki dotyczące typu

*Visual Studio 2017 wersji 15.7 i nowszych.*

"Typ wskazówki" w języku Python 3.5 + ([484 program ten](https://www.python.org/dev/peps/pep-0484/) (python.org) jest składnia adnotacja dla funkcji i klasy, które wskazują typy argumentów, zwracać wartości i atrybuty klasy. IntelliSense wyświetla typ wskazówek po umieszczeniu na wywołania funkcji, argumentów i zmiennych, które mają te adnotacji.

W poniższym przykładzie `Vector` klasy jest zadeklarowany jako `List[float]`i `scale` funkcja zawiera wskazówki typu dla jego argumentów i wartości zwracanej. Kursora myszy nad wywołanie tej funkcji zawiera wskazówki dotyczące typu:

![Ustawiając kursor nad wywołanie funkcji, aby wyświetlić wskazówki typu](media/code-editing-type-hints1.png)

W poniższym przykładzie widać, jak adnotacji atrybutów `Employee` klasy są wyświetlane w menu podręcznym uzupełniania IntelliSense dla atrybutu:

![Wskazówki typu przedstawiający uzupełniania IntelliSense](media/code-editing-type-hints2.png)

Warto także sprawdzić poprawności typu wskazówek w projekcie, ponieważ błędy normalnie nie będą wyświetlane do czasu wykonywania. W tym celu programu Visual Studio integruje branży standardowe narzędzie MyPy za pomocą polecenia menu kontekstowe **Python > Uruchom Mypy** w **Eksploratora rozwiązań**:

![Uruchom polecenie z menu kontekstowego MyPy w Eksploratorze rozwiązań](media/code-editing-type-hints-run-mypy.png)

Uruchomiony wiersz polecenia do zainstalowania pakietu mypy, jeśli potrzebne. Visual Studio następnie uruchamia mypy można sprawdzić poprawności typu wskazówek w każdym pliku Python w projekcie. Błędy są wyświetlane w programie Visual Studio **listy błędów** okna. Zaznaczenie elementu w oknie powoduje przejście do odpowiedniej linii w kodzie.

Jako prosty przykład definicji następujących funkcji zawiera wskazówki typu w celu wskazania, że `input` argument jest typu `str`, podczas gdy wywołanie tej funkcji podejmuje próbę przekazania całkowitą:

```python
def commas_to_colons(input: str):
    items = input.split(',')
    items = [x.strip() for x in items]
    return ':'.join(items)

commas_to_colons(1)
```

Przy użyciu **Uruchom Mypy** polecenia dla tego kodu generuje następujący błąd:

![Przykład wynik sprawdzania poprawności typu wskazówek mypy](media/code-editing-type-hints-validation-error.png)

> [!Tip]
> W przypadku wersji środowiska Python przed 3.5, Visual Studio wyświetla również typ wskazówek, zapewniających za pośrednictwem *stub pliki* (`.pyi`). Pliki szczątkowe można używać zawsze, gdy nie chcesz dołączyć wskazówki typu bezpośrednio w kodzie, lub gdy chcesz utworzyć typu wskazówek dotyczących serwerów biblioteki, która nie używa ich bezpośrednio. Aby uzyskać więcej informacji, zobacz [tworzenia klas zastępczych dla modułów środowiska Python](https://github.com/python/mypy/wiki/Creating-Stubs-For-Python-Modules) w witrynie wiki mypy projektu.
>
> W chwili obecnej Visual Studio nie obsługuje typu wskazówek w komentarzach.

### <a name="signature-help"></a>Podpis pomocy

Podczas pisania kodu, który wywołuje funkcję, podpisu pomoc jest wyświetlany, gdy typ otwarcia `(` i wyświetla informacje o dostępnej dokumentacji i parametru. Można również wyświetlić ją z klawiszy Ctrl + Shift + spacja wewnątrz wywołania funkcji. Informacje wyświetlane jest zależna od ciągów dokumentacji w kodzie źródłowym funkcji, ale zawiera wartości domyślne.

![Podpis pomocy](media/code-editing-signature-help.png)

> [!Tip]
> Aby wyłączyć pomocy podpisu, przejdź do **Narzędzia > Opcje > Edytor tekstu > Python > Ogólne** i wyczyść **uzupełniania > informacje o parametrach**.

### <a name="quick-info"></a>Szybkie informacje

Kursor myszy nad identyfikator wyświetlana etykietka narzędzia Szybkie informacje. W zależności od identyfikatora szybkie informacje mogą być wyświetlane potencjalnych wartości lub typów, dowolnej dostępnej dokumentacji zwracać typy i lokalizacje definicji:

![Szybkie informacje](media/code-editing-quick-info.png)

### <a name="code-coloring"></a>Kolorowanie

Kolorowanie używa informacji z analizy kodu do zmiennych kolorów, instrukcje i inne części kodu. Na przykład zmienne, które odwołują się do klasy lub moduły mogą być wyświetlane w kolorze innego niż funkcji lub inne wartości, a w innym kolorze niż zmiennych lokalnych i globalnych są wyświetlane nazwy parametrów. (Domyślnie funkcje nie są wyświetlane wytłuszczonym drukiem):

![Kolorowanie](media/code-editing-code-coloring.png)

Aby dostosować kolory, przejdź do **Narzędzia > Opcje > środowiska > czcionki i kolory** i modyfikowanie wpisów Python w **wyświetlania elementów** listy:

![Opcje czcionek i kolorów](media/code-editing-customize-colors.png)

> [!Tip]
> Aby wyłączyć kolorowania kodu, przejdź do **Narzędzia > Opcje > Edytor tekstu > Python > Zaawansowane** i wyczyść **różne opcje > Kolor nazw oparty na typie**. Zobacz [opcji - różne opcje](python-support-options-and-settings-in-visual-studio.md#miscellaneous-options).

## <a name="code-snippets"></a>Fragmenty kodu

Wstawki kodu są fragmenty kodu, który można wstawiać do plików, wpisując skrót i naciśnięcie klawisza Tab lub przy użyciu **Edytuj > IntelliSense > Wstaw fragment kodu** i **z funkcji Otocz przez** poleceń, Wybieranie **Python**, a następnie wybierając żądane fragment kodu.

Na przykład `class` jest skrót dla fragmentu kodu, która wstawia definicji klasy. Zobacz fragment znajdują się na liście automatycznego uzupełniania po wpisaniu `class`:

![Fragment kodu dotyczący skrótów — klasa](media/code-editing-code-snippet-class.png)

Naciśnięcie klawisza Tab generuje rest klasy. Mogą być następnie typu na liście nazwy i typy podstawowe przechodzenia między wyróżnione pola z kartą, naciśnij klawisz Enter, aby rozpocząć, wpisując treści.

![Najważniejsze funkcje w obszarach fragment kodu zakończenia](media/code-editing-code-snippets.png)

### <a name="menu-commands"></a>Polecenia menu

Jeśli używasz **Edytuj > IntelliSense > Wstaw fragment kodu** polecenia menu, musisz najpierw wybierz pozycję "Python", a następnie wybierz fragment:

![Wybieranie fragment kodu za pomocą polecenia wstawiania wstawki kodu programu](media/code-editing-code-snippet-insert.png)

**Edytuj > IntelliSense > z funkcji Otocz przez** polecenia, podobnie, umieszcza bieżące zaznaczenie w edytorze tekstu w wybranym elemencie strukturalnych. Na przykład załóżmy, że ma nieco kodu podobne do poniższych:

```python
sum = 0
for x in range(1, 100):
    sum = sum + x
```

Wybierając ten kod i wybierając pozycję **z funkcji Otocz przez** polecenie wyświetla listę dostępnych fragmentów. Wybieranie `def` w miejscach listy wybranego kodu w ramach definicji funkcji, a można za pomocą klawisza Tab do przechodzenia między nazwą funkcji wyróżnione i argumenty:

![Dla wstawki kodu za pomocą polecenia z funkcji Otocz przez](media/code-editing-code-snippet-surround-with.png)

### <a name="examine-available-snippets"></a>Przejrzyj dostępne wstawki kodu programu

Zostanie wyświetlony fragmenty kodu dostępnych w Menedżerze fragmentów kodu otworzyć za pomocą **Narzędzia > Menedżerze fragmentów kodu** polecenia menu i wybierając **Python** jako język:

![Menedżer wstawek kodu](media/code-editing-code-snippets-manager.png)

Aby utworzyć własną fragmentów, zobacz [wskazówki: tworzenie wstawek kodu](../ide/walkthrough-creating-a-code-snippet.md).

Jeśli piszesz fragment kodu dużą, którą chcesz udostępnić, możesz zająć się on wysłany w gist i [Daj nam znać](https://github.com/Microsoft/PTVS/issues). Firma Microsoft może istnieć możliwość uwzględniania go w przyszłej wersji programu Visual Studio.

## <a name="navigating-your-code"></a>Nawigowanie po kodzie

Obsługa języka Python w programie Visual Studio zapewnia kilka oznacza szybką nawigację w kodzie, w tym bibliotek, które źródła kod jest dostępny: [pasek nawigacyjny](#navigation-bar), [przejdź do definicji](#go-to-definition), [Przejdź do](#navigate-to), i [Znajdź wszystkie odwołania](#find-all-references). Można również użyć programu Visual Studio [przeglądarki obiektów](../ide/viewing-the-structure-of-code.md#BKMK_ObjectBrowser).

### <a name="navigation-bar"></a>Pasek nawigacyjny

Na pasku nawigacyjnym jest wyświetlany w górnej części każdego okna edytora i zawiera listę dwupoziomowej definicji. Po lewej stronie rozwiń zawiera klasę najwyższego poziomu i definicje funkcji w bieżącym pliku; Prawy listy rozwijanej zostanie wyświetlona lista definicji w zakresie wyświetlane po lewej stronie. Jak przenoszenia w edytorze listy aktualizacji, aby wyświetlić bieżący kontekst i można również wybrać wpis z tych list można przejść bezpośrednio do w.

![Pasek nawigacyjny](media/code-editing-navigation-bar.png)

> [!Tip]
> Aby ukryć pasek nawigacyjny, przejdź do **Narzędzia > Opcje > Edytor tekstu > Python > Ogólne** i wyczyść **Ustawienia > pasek nawigacyjny**.

### <a name="go-to-definition"></a>Przejdź do definicji

**Przejdź do definicji** szybko przechodzi z użycia dla identyfikatora (np. nazwę funkcji, klasy lub zmienna), do kodu źródłowego których jest zdefiniowana. Można go wywołać prawym przyciskiem myszy identyfikator i wybierając **przejdź do definicji** lub umieszczając karetki w identyfikatorze i naciskając klawisz F12. Działa ona za pośrednictwem kod i zewnętrznej biblioteki pod warunkiem, że kod źródłowy jest dostępny. Jeśli kod źródłowy biblioteki nie jest dostępna, **przejdź do definicji** przechodzi do odpowiedniego `import` instrukcji odwołania do modułu lub wyświetlania wystąpił błąd.

![Przejdź do definicji](media/code-editing-go-to-definition.png)

### <a name="navigate-to"></a>Przejdź do

**Edytuj > Przejdź do...**  polecenie (Ctrl przecinkami) Wyświetla pole wyszukiwania w edytorze, na którym wpisz dowolny ciąg i wyświetlić możliwe dopasowania w kodzie, który definiuje funkcję, klasa lub zmienną zawierającą ten ciąg. Ta funkcja udostępnia podobną funkcję jak **przejdź do definicji** , ale bez konieczności zlokalizować Użyj identyfikatora.

Dwukrotnie dowolną nazwę, lub wybierając z klawiszy strzałek i wprowadź, przechodzi do definicji tego identyfikatora.

![Przejdź do](media/code-editing-navigate-to.png)

### <a name="find-all-references"></a>Znajdź wszystkie odwołania

**Znajdź wszystkie odwołania** jest pomocny sposób odnajdowania, gdzie jest zarówno z dowolnym danym identyfikatorem zdefiniowany i używany, oraz importowania przypisania. Można go wywołać prawym przyciskiem myszy identyfikator i wybierając **Znajdź wszystkie odwołania**, lub umieszczając karetki w identyfikatorze i naciskając klawisz Shift + F12. Dwukrotne kliknięcie elementu na liście przechodzi do jego lokalizacji.

![Znajdź wszystkie odwołania wyników](media/code-editing-find-all-references.png)

## <a name="see-also"></a>Zobacz także

- [Formatowanie](formatting-python-code.md)
- [Refaktoryzacja](refactoring-python-code.md)
- [Zaznaczanie błędów](linting-python-code.md)