---
title: Przejdź do kodu w programie Visual Studio
ms.date: 09/26/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code editor, navigation
- code editor, go to
- code editor, go to definition
- code editor, go to line
- code editor, peek definition
- code editor, navigation bar
- go to definition
- peek definition
- go to line
- go to
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9293565b4a238b1486f491c5a343d83364fba088
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2018
ms.locfileid: "34448613"
---
# <a name="navigate-code"></a>Przejdź do kodu

Program Visual Studio oferuje wiele sposobów, aby przejść do kodu w edytorze. W tym temacie przedstawiono różne sposoby, można przejść kodu i linki do tematów, które wchodzą w bardziej szczegółowo.

## <a name="navigate-backward-and-navigate-forward-commands"></a>Przejdź wstecz i przejdź do przodu poleceń

Można użyć **Przejdź wstecz** (**Ctrl**+**-**) i **przejdź do przodu** ( **CTRL**+**Shift**+**-**) na pasku narzędzi, aby przenieść punkt wstawiania do poprzedniej lokalizacji lub aby powrócić do bardziej ostatnie lokalizacji z poprzedniej lokalizacji. Tych przycisków zachować 20 ostatnich lokalizacji punktu wstawiania. Te polecenia są również dostępne na **widoku** menu, w obszarze **Przejdź wstecz** i **przejdź do przodu**.

![Przyciski nawigacji do przodu i Wstecz](../ide/media/vs2017_nav_buttons.png)

## <a name="navigation-bar"></a>Pasek nawigacyjny

Można użyć **pasek nawigacyjny** (pola listy rozwijanej w górnej części okna kodu) aby nawigować do kodu w codebase. Można wybrać typ lub element członkowski, aby przejść bezpośrednio do niego. Na pasku nawigacyjnym zostanie wyświetlone podczas edytowania kodu w języku Visual Basic, C# lub bazy kodu C++. W klasie częściowej elementów członkowskich zdefiniowanych poza bieżący plik kodu mogą być wyłączone (pojawią się one w kolorze szarym).

 ![Pasek nawigacyjny kodu](../ide/media/vside_navigation_bar.png)

Można nawigować list rozwijanych w następujący sposób:

- Aby przejść do innego projektu, do którego należy bieżący plik, należy wybrać w lewej listy rozwijanej.

- Aby przejść do klasy lub typu, wybierz go w środku listy rozwijanej.

- Aby przejść bezpośrednio do procedury lub innego członka klasy, wybierz go w prawo listy rozwijanej.

- Aby przenieść fokus z okna Kod na pasku nawigacyjnym, naciśnij kombinację klawiszy skrótów **Ctrl**+**F2**.

- Aby przesunąć pole pola na pasku nawigacyjnym, naciśnij klawisz **kartę** klucza.

- Aby wybrać element paska nawigacji, który ma fokus i wrócić do okna kodu, naciśnij klawisz **Enter** klucza.

- Aby przywrócić fokusu na pasku nawigacyjnym kodu bez zaznaczania czegokolwiek, naciśnij klawisz **Esc** klucza.

Aby ukryć pasek nawigacyjny, zmień **pasek nawigacyjny** opcji **edytora tekstów wszystkie języki** ustawienia (**narzędzia** > **opcje**  >  **Edytor tekstu** > **wszystkie języki**), lub zmienić ustawienia dla poszczególnych języków.

## <a name="find-all-references"></a>Znajdź wszystkie odwołania

Znajduje wszystkie odwołania do wybranego elementu w rozwiązaniu. Możesz użyć tego sprawdź efekty uboczne o dużych refaktoryzacji lub Sprawdź kod "martwy". Naciśnij klawisz **F8** do przechodzenia między wyników. Aby uzyskać więcej informacji, zobacz [Znajdowanie odwołań w kodzie](finding-references.md).

Dane wejściowe        | Funkcja
------------ | ---
**Keyboard** | Umieść kursor tekstu gdzieś w nazwie typu, a następnie naciśnij klawisz **Shift**+**F12**
**Myszy**    | Wybierz **Znajdź wszystkie odwołania** z menu kontekstowego

## <a name="reference-highlighting"></a>Podświetlanie odwołań

Po kliknięciu symbol w kodzie źródłowym wszystkich wystąpień tego symbolu są wyróżniane w dokumencie. Wyróżnione symboli może zawierać deklaracje i odwołań i wiele innych symboli, która **Znajdź wszystkie odwołania** zwróci. Obejmują one nazwy klas, obiektów, zmienne, metod i właściwości. Kod Visual Basic słowa kluczowe dla wielu struktury sterujące są wyróżnione. Aby przejść do następnej lub poprzedniej symbol wyróżnione, naciśnij **Ctrl**+**Shift**+**Strzałka w dół** lub **Ctrl** + **Shift**+**Strzałka w górę**. Można zmienić kolory wyróżnienia **narzędzia** > **opcje** > **środowiska** > **czcionek i Kolory** > **wyróżnione odwołanie**.

## <a name="go-to-commands"></a>Przejdź do poleceń

Przejdź do ma następujące polecenia, które są dostępne w **Edytuj** menu w obszarze **przejdź do**:

- **Przejdź do wiersza** (**Ctrl**+**G**): Przenieś do określonego numeru wiersza w aktywnym dokumencie.

- **Przejdź do wszystkich** (**Ctrl**+**T** lub **Ctrl**+**,**): Przejdź do określonego wiersza typu plik, składnika lub symbol.

- **Przejdź do pliku** (**Ctrl**+**1**, **Ctrl**+**F**): Przenieś do określonego pliku w rozwiązanie.

- **Przejdź do typu** (**Ctrl**+**1**, **Ctrl**+**T**): Przenieś do określonego typu w rozwiązanie.

- **Przejdź do elementu członkowskiego** (**Ctrl**+**1**, **Ctrl**+**M**): Przenieś do określonego elementu członkowskiego w rozwiązanie.

- **Przejdź do symbolu** (**Ctrl**+**1**, **Ctrl**+**S**): Przenieś do określony symbol w rozwiązanie.

Zobacz więcej informacji na temat tych poleceń w [znaleźć za pomocą polecenia przejdź do kodu](../ide/go-to.md) tematu.

## <a name="go-to-definition"></a>Przejdź do definicji

Przejdź do definicji przejście do definicji wybranego elementu. Aby uzyskać więcej informacji, zobacz [przejdź do definicji i definicji wglądu](../ide/go-to-and-peek-definition.md).

Dane wejściowe        | Funkcja
------------ | ---
**Keyboard** | Umieść kursor tekstu gdzieś w nazwie typu, a następnie naciśnij klawisz **F12**
**Myszy**    | Kliknij prawym przyciskiem myszy na nazwie typu i wybierz **przejdź do definicji** lub naciśnij klawisz **Ctrl** i kliknij na nazwie typu (nowe dla programu Visual Studio 2017 wersji 15.4)

## <a name="peek-definition"></a>Definicji wglądu

Podgląd wyświetla definicji definicji elementu wybranego w oknie bez konieczności opuszczania bieżącej lokalizacji w edytorze kodu. Aby uzyskać więcej informacji, zobacz [porady: wyświetlanie i edytowanie kodu za pomocą definicji wglądu](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md) i [przejdź do definicji i definicji wglądu](../ide/go-to-and-peek-definition.md).

Dane wejściowe        | Funkcja
------------ | ---
**Keyboard** | Umieść kursor tekstu gdzieś w nazwie typu, a następnie naciśnij klawisz **Alt**+**F12**
**Myszy**    | Kliknij prawym przyciskiem myszy na nazwie typu i wybierz **definicji wglądu** lub naciśnij klawisz **Ctrl** i kliknij na nazwie typu (Jeśli masz **Otwórz definicję w widoku peek** zaznaczoną opcją)

## <a name="go-to-implementation"></a>Przejdź do implementacji

Przy użyciu przejdź do implementacji, można przejść z klasy podstawowej lub wpisz, aby ich implementacji. Jeśli istnieje wiele implementacji, zobaczysz je na liście **wyniki Znajdź Symbol** okno:

Dane wejściowe        | Funkcja
------------ | ---
**Keyboard** | Umieść kursor tekstu gdzieś w nazwie typu, a następnie naciśnij klawisz **Ctrl**+**F12**
**Myszy**    | Kliknij prawym przyciskiem myszy na nazwie typu i wybierz **przejdź do implementacji**

## <a name="call-hierarchy"></a>Hierarchia wywołań

Możesz wyświetlić wywołania do i z metody w [okno hierarchii wywołań](../ide/reference/call-hierarchy.md):

Dane wejściowe        | Funkcja
------------ | ---
**Keyboard** | Umieść kursor tekstu gdzieś w nazwie typu, a następnie naciśnij klawisz **Ctrl**+**K**, **Ctrl**+**T**
**Myszy**    | Kliknij prawym przyciskiem myszy na nazwę elementu członkowskiego i wybierz **Widok hierarchii wywołań**

## <a name="next-method-and-previous-method-commands-visual-basic"></a>Next — metoda i poprzednich — metoda polecenia (Visual Basic)

W plikach kodu języka Visual Basic należy używać tych poleceń, aby przenieść punkt wstawiania do różnych metod. Wybierz **Edytuj** > **Next — metoda** lub **Edytuj** > **Poprzednia metoda**.

## <a name="structure-visualizer"></a>Struktura wizualizatora

Funkcja wizualizatora struktury w kodzie edytor *struktury zasady* -pionowa kreska-kreska wierszy, które wskazują pasujących nawiasów klamrowych w baza kodu. Dzięki temu go lepiej widoczne, gdzie rozpocząć bloków logicznych i na końcu.

![Struktura wizualizatora](../ide/media/vside_structure_visualizer.png)

Aby wyłączyć wierszy przewodnik struktury, przejdź do **narzędzia** > **opcje** > **Edytor tekstu** > **Ogólne** i wyczyść **Pokaż linie przewodnik struktury** pole.

## <a name="enhanced-scroll-bar"></a>Pasek przewijania rozszerzone

Pasek przewijania rozszerzone w oknie Kod służy do pobrania z lotu ptaka kodu. W trybie mapy widać podglądy kodu podczas przenoszenia kursora na pasku przewijania w górę i w dół. Aby uzyskać więcej informacji, zobacz [porady: śledzenie kodu dostosowując pasek przewijania](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md).

## <a name="codelens-information"></a>Informacje wskaźników CodeLens

Można znaleźć informacje dotyczące określonego kodu, zmiany i kto przygotował tych zmian, odwołuje się do usterki, elementów roboczych, przeglądy kodu i jednostki stan testu, korzystając z funkcji CodeLens w edytorze kodu. CodeLens działa jak ekran projekcyjny wskazuje pozycję, korzystając z programu Visual Studio Enterprise z Team Foundation Server. Zobacz [znajdowanie zmian w kodzie i innych elementów historii](../ide/find-code-changes-and-other-history-with-codelens.md).

## <a name="see-also"></a>Zobacz także

- [Funkcje Edytor kodu](../ide/writing-code-in-the-code-and-text-editor.md)
- [Wyświetlanie hierarchii wywołań](../ide/reference/call-hierarchy.md)
