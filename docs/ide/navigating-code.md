---
title: Nawigowanie po kodzie | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 09/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
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
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 7b81517d8d8e0cc6dd1386525f7a2129ed18851c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="navigating-code"></a>Nawigowanie po kodzie  
Program Visual Studio oferuje wiele sposobów, aby przejść do kodu w edytorze. W tym temacie przedstawiono różne sposoby, można przejść kodu i linki do tematów, które wchodzą w bardziej szczegółowo.  

## <a name="navigate-backward-and-navigate-forward-commands"></a>Przejdź wstecz i przejdź do przodu poleceń  
Można użyć **Przejdź wstecz** (**Ctrl + -**) i **przejdź do przodu** (**klawisze Ctrl + Shift + -**) przycisków na pasku narzędzi, aby przenieść punkt wstawiania do poprzedniej lokalizacji lub zwróć się do nowych lokalizacji z poprzedniej lokalizacji. Tych przycisków zachować 20 ostatnich lokalizacji punktu wstawiania. Te polecenia są również dostępne na **widoku** menu, w obszarze **Przejdź wstecz** i **przejdź do przodu**.  

![Przyciski nawigacji do przodu i Wstecz](../ide/media/vs2017_nav_buttons.png)  

## <a name="navigation-bar"></a>Pasek nawigacyjny
Można użyć **pasek nawigacyjny** (pola listy rozwijanej w górnej części okna kodu) aby nawigować do kodu w codebase. Można wybrać typ lub element członkowski, aby przejść bezpośrednio do niego. Na pasku nawigacyjnym zostanie wyświetlone podczas edytowania kodu w języku Visual Basic, C# lub bazy kodu C++. W klasie częściowej elementów członkowskich zdefiniowanych poza bieżący plik kodu mogą być wyłączone (pojawią się one w kolorze szarym).  

 ![Pasek nawigacyjny kodu](../ide/media/vside_navigation_bar.png)

Można nawigować list rozwijanych w następujący sposób:  

-   Aby przejść do innego projektu, do którego należy bieżący plik, należy wybrać w lewej listy rozwijanej.

-   Aby przejść do klasy lub typu, wybierz go w środku listy rozwijanej.  

-   Aby przejść bezpośrednio do procedury lub innego członka klasy, wybierz go w prawo listy rozwijanej.  

-   Aby przenieść fokus z okna Kod na pasku nawigacyjnym, naciśnij kombinację klawiszy skrótów **Ctrl + F2**.  

-   Aby przesunąć pole pola na pasku nawigacyjnym, naciśnij klawisz **kartę** klucza.  

-   Aby wybrać element paska nawigacji, który ma fokus i wrócić do okna kodu, naciśnij klawisz **Enter** klucza.  

-   Aby przywrócić fokusu na pasku nawigacyjnym kodu bez zaznaczania czegokolwiek, naciśnij klawisz **Esc** klucza.  

Aby ukryć pasek nawigacyjny, zmień **pasek nawigacyjny** opcję w ustawieniach edytora tekstów wszystkie języki (**narzędzia**, **opcje**, **Edytor tekstu**, **Wszystkie języki**), lub zmienić ustawienia dla poszczególnych języków.  

## <a name="find-all-references"></a>Znajdź wszystkie odwołania  
Znajduje wszystkie odwołania do wybranego elementu w rozwiązaniu. Możesz użyć tego sprawdź efekty uboczne o dużych refaktoryzacji lub Sprawdź kod "martwy". Naciśnij klawisz **F8** do przechodzenia między wyników. Aby uzyskać więcej informacji, zobacz [Znajdowanie odwołań w kodzie](finding-references.md).  

Dane wejściowe        | Funkcja 
------------ | ---
**Klawiatury** | Umieść kursor tekstu gdzieś w nazwie typu, a następnie naciśnij klawisz **Shift + F12**  
**Myszy**    | Wybierz **Znajdź wszystkie odwołania** z menu kontekstowego  

## <a name="reference-highlighting"></a>Podświetlanie odwołań
Po kliknięciu symbol w kodzie źródłowym wszystkich wystąpień tego symbolu są wyróżniane w dokumencie. Wyróżnione symboli może zawierać deklaracje i odwołań i wiele innych symboli, która **Znajdź wszystkie odwołania** zwróci. Obejmują one nazwy klas, obiektów, zmienne, metod i właściwości. Kod Visual Basic słowa kluczowe dla wielu struktury sterujące są wyróżnione. Aby przejść do następnej lub poprzedniej symbol wyróżnione, naciśnij **klawisze Ctrl + Shift + Strzałka w dół** lub **klawisze Ctrl + Shift + Strzałka w górę**. Można zmienić kolory wyróżnienia **narzędzia**, **opcje**, **środowiska**, **czcionki i kolory**, **wyróżnione Odwołanie.**  

## <a name="go-to-commands"></a>Przejdź do poleceń  
Przejdź do ma następujące polecenia, które są dostępne w **Edytuj** menu w obszarze **przejdź do**:  

- **Przejdź do wiersza** (**Ctrl + G**): Przenieś do określonego numeru wiersza w aktywnym dokumencie.  

- **Przejdź do wszystkich** (**klawisze Ctrl + T** lub **Ctrl +,**): Przejdź do określonego wiersza, typu, pliku, elementu członkowskiego lub symbol.  

- **Przejdź do pliku** (**Ctrl + 1**, **Ctrl + F**): Przenieś do określonego pliku w rozwiązaniu.  

- **Przejdź do typu** (**Ctrl + 1**, **klawisze Ctrl + T**): Przenieś do określonego typu w rozwiązaniu.  

- **Przejdź do elementu członkowskiego** (**Ctrl + 1**, **Ctrl + M**): Przenieś do określonego elementu członkowskiego w rozwiązaniu.  

- **Przejdź do symbolu** (**Ctrl + 1**, **Ctrl + S**): Przenieś do symbolu określona w rozwiązaniu.  

Zobacz więcej informacji na temat tych poleceń w [znaleźć za pomocą polecenia przejdź do kodu](../ide/go-to.md) tematu.  

## <a name="go-to-definition"></a>Przejdź do definicji  
Przejdź do definicji przejście do definicji wybranego elementu. Aby uzyskać więcej informacji, zobacz [definicji wglądu i przejdź do definicji](../ide/go-to-and-peek-definition.md).  

Dane wejściowe        | Funkcja 
------------ | ---
**Klawiatury** | Umieść kursor tekstu gdzieś w nazwie typu, a następnie naciśnij klawisz **F12**
**Myszy**    | Kliknij prawym przyciskiem myszy na nazwie typu i wybierz **przejdź do definicji** lub naciśnij klawisz **Ctrl** i kliknij na nazwie typu (nowe dla programu Visual Studio 2017 wersji 15.4)  

## <a name="peek-definition"></a>Definicji wglądu  
Podgląd wyświetla definicji definicji elementu wybranego w oknie bez konieczności opuszczania bieżącej lokalizacji w edytorze kodu. Aby uzyskać więcej informacji, zobacz [porady: wyświetlanie i Edycja kodu za pomocą definicji wglądu](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md) i [definicji wglądu i przejdź do definicji](../ide/go-to-and-peek-definition.md).  

Dane wejściowe        | Funkcja 
------------ | ---
**Klawiatury** | Umieść kursor tekstu gdzieś w nazwie typu, a następnie naciśnij klawisz **Alt + F12**
**Myszy**    | Kliknij prawym przyciskiem myszy na nazwie typu i wybierz **definicji wglądu** lub naciśnij klawisz **Ctrl** i kliknij na nazwie typu (Jeśli masz **Otwórz definicję w widoku peek** zaznaczoną opcją)  

## <a name="go-to-implementation"></a>Przejdź do implementacji  
Przy użyciu przejdź do implementacji, można przejść z klasy podstawowej lub wpisz, aby ich implementacji. Jeśli istnieje wiele implementacji, zobaczysz je na liście **wyniki Znajdź Symbol** okno:  

Dane wejściowe        | Funkcja 
------------ | ---
**Klawiatury** | Umieść kursor tekstu gdzieś w nazwie typu, a następnie naciśnij klawisz **Ctrl + F12**
**Myszy**    | Kliknij prawym przyciskiem myszy na nazwie typu i wybierz **przejdź do implementacji**  

## <a name="call-hierarchy"></a>Hierarchia wywołań  
Hierarchia wywołań przedstawia wywołania do metody w oknie hierarchii wywołań:  

Dane wejściowe        | Funkcja 
------------ | ---
**Klawiatury** | Umieść kursor tekstu gdzieś w nazwie typu, a następnie naciśnij klawisz **Ctrl + K**, **klawisze Ctrl + T**  
**Myszy**    | Kliknij prawym przyciskiem myszy na nazwę elementu członkowskiego i wybierz **Widok hierarchii wywołań**  

## <a name="next-method-and-previous-method-commands-visual-basic"></a>Next — metoda i poprzednich — metoda polecenia (Visual Basic)  
W plikach kodu języka Visual Basic należy używać tych poleceń, aby przenieść punkt wstawiania do różnych metod. Wybierz **Edytuj**, **Next — metoda** lub **Edytuj**, **Poprzednia metoda**.  

## <a name="structure-visualizer"></a>Struktura wizualizatora  
Funkcja wizualizatora struktury w kodzie edytor *struktury zasady* -pionowa kreska-kreska wierszy, które wskazują pasujących nawiasów klamrowych w baza kodu. Dzięki temu go lepiej widoczne, gdzie rozpocząć bloków logicznych i na końcu.  

![Struktura wizualizatora](../ide/media/vside_structure_visualizer.png)  

Aby wyłączyć wierszy przewodnik struktury, przejdź do **narzędzia**, **opcje**, **Edytor tekstu**, **ogólne** i wyczyść **Pokaż Struktura zasady** pole.  

## <a name="enhanced-scroll-bar"></a>Pasek przewijania rozszerzone
Pasek przewijania rozszerzone w oknie Kod służy do pobrania z lotu ptaka kodu. W trybie mapy widać podglądy kodu podczas przenoszenia kursora na pasku przewijania w górę i w dół. Aby uzyskać więcej informacji, zobacz [porady: Śledź kodu dostosowując pasek przewijania](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md).  

## <a name="codelens-information"></a>Informacje wskaźników CodeLens
Można znaleźć informacje dotyczące określonego kodu, zmiany i kto przygotował tych zmian, odwołuje się do usterki, elementów roboczych, przeglądy kodu i jednostki stan testu, korzystając z funkcji CodeLens w edytorze kodu. CodeLens działa jak ekran projekcyjny wskazuje pozycję, korzystając z programu Visual Studio Enterprise z Team Foundation Server. Zobacz [znajdowanie zmian w kodzie i innych elementów historii](../ide/find-code-changes-and-other-history-with-codelens.md).  

## <a name="see-also"></a>Zobacz też  
[Pisanie kodu w edytorze kodu i tekstu](../ide/writing-code-in-the-code-and-text-editor.md) 
