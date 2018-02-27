---
title: "Edytowanie kodu języka Python w programie Visual Studio | Dokumentacja firmy Microsoft"
description: "Python edycji w programie Visual Studio oferuje IntelliSense, fragmentów kodu i funkcje nawigacji obok formatowania, linting i refaktoryzacji."
ms.custom: 
ms.date: 02/15/2018
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
ms.openlocfilehash: e1e592d6fdb8fd7deb1e702513a932297a60e6ac
ms.sourcegitcommit: c0a2385a16cc4f47d2e1ff23d35c4da40f5605e0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="editing-python-code"></a>Edytowanie kodu języka Python

Deweloperzy poświęcać dużo czasu w edytorze kodu tak [Python obsługi w programie Visual Studio](installing-python-support-in-visual-studio.md) zapewnia funkcję ułatwiającą Twoją produktywność. Cechy IntelliSense wyróżnianie składni, automatycznego uzupełniania pomocy podpisu, zamienników metod, wyszukiwania i nawigacji.

Edytor jest także zintegrowane z okno interaktywne programu Visual Studio, co ułatwia wymienić kod między nimi. Zobacz [samouczek krok 3: Korzystanie z okna interaktywny REPL](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md) i [przy użyciu okna interaktywnego — Wyślij kod, aby polecenie interaktywne](python-interactive-repl-in-visual-studio.md#send-code-to-interactive-command) szczegółowe informacje.

|   |   |
|---|---|
| ![Ikona aparatu film wideo](../install/media/video-icon.png "obejrzeć film wideo") | [Obejrzyj film (Microsoft Virtual Academy)](https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Editing-Python-Code-r2iQH5LWE_4605918567) dla pokaz edytowanie kodu języka Python (2 m 30s).|

Dokumentacja ogólna edytowanie kodu w programie Visual Studio, aby zapoznać [pisanie kodu w edytorze kodu i tekstu](../ide/writing-code-in-the-code-and-text-editor.md). Zobacz też [konspekt w Visual Studio](../ide/outlining.md), który pomaga pozostać koncentruje się na poszczególnych sekcji kodu.

Można również użyć przeglądarki obiektów Visual Studio (**Widok > inne okna > przeglądarki obiektów** lub Ctrl + W, J) do sprawdzania Python klas zdefiniowanych w każdym module i funkcji zdefiniowanych w tych klas.

## <a name="intellisense"></a>IntelliSense

Udostępnia IntelliSense [zakończeń](#completions), [pomocy podpisu](#signature-help), [szybka podpowiedź](#quick-info), i [kolorowanie](#code-coloring). Aby zwiększyć wydajność, IntelliSense zależy od ukończenia bazy danych, generowany dla każdego środowiska Python w projekcie. Bazy danych może być konieczne odświeżenie Jeśli dodać, usunąć lub zaktualizować pakiety. Stan bazy danych jest wyświetlany w **środowiska Python** okno (element równorzędny Solution Explorer) na **IntelliSense** kartę (zobacz [odwołania okno środowiska Python](python-environments-window-tab-reference.md#intellisense-tab)).

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

## <a name="code-snippets"></a>Wstawki kodu

Wstawki kodu są fragmenty kodu, który można wstawiać do plików, wpisując skrót i naciśnięcie klawisza Tab lub przy użyciu **Edytuj > IntelliSense > Wstaw fragment kodu** **z funkcji Otocz przez** poleceń. Na przykład wpisanie `class` po klucz generowane przez kartę rest klasy. Możesz wpisać zamiast nazwy i przechodzenia między wyróżnionych polach o karcie listy baz naciśnij klawisz Enter, aby rozpocząć, wpisując treści.

![Wstawki kodu](media/code-editing-code-snippets.png)

Zostanie wyświetlony fragmenty kodu dostępnych w Menedżerze fragmentów kodu (**Narzędzia > Menedżerze fragmentów kodu**), wybierając żądane **Python** jako język:

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