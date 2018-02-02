---
title: "Wprowadzenie do języka R w programie Visual Studio | Dokumentacja firmy Microsoft"
description: "Wskazówki dotyczące użycia języka R w programie Visual Studio, w tym tworzenia projektu, okno interaktywne kodu, edytowanie i debugowanie."
ms.custom: 
ms.date: 06/29/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
ms.topic: get-started-article
caps.latest.revision: 
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- data-science
ms.openlocfilehash: cf8df86322e10054dee5dbcee95839506f690306
ms.sourcegitcommit: ba29e4d37db92ec784d4acf9c6e120cf0ea677e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2018
---
# <a name="getting-started-with-r-tools-for-visual-studio"></a>Pierwsze kroki z narzędziami R dla programu Visual Studio

Po utworzeniu R narzędzi dla programu Visual Studio (RTVS) zainstalowany (zobacz [instalacji](installing-r-tools-for-visual-studio.md)), możesz szybko uzyskać smak doświadczenia, które zapewniają te narzędzia. 

## <a name="create-an-r-project"></a>Tworzenie projektu R

1. Uruchom program Visual Studio.
1. Wybierz **Plik > Nowy > Projekt...** (Ctrl+Shift+N)
1. Wybierz "Projekt R" w ramach **Szablony > R**, nadaj projektu, nazwy i lokalizacji, a wybierz **OK**:

   ![Okno dialogowe Nowy projekt dla języka R w programie Visual Studio (RTVS w VS2017)](media/getting-started-01-new-project.png)

1. Po utworzeniu projektu Zobacz się następujące systemu windows:

    - Po prawej stronie jest Visual Studio Eksploratorze rozwiązań, której występuje projektu w nadrzędnym *rozwiązania*. (Rozwiązania może zawierać dowolną liczbę projektów o różnych typach; zobacz [projekty](r-projects-in-visual-studio.md) szczegółowe informacje.
    - W lewej górnej części jest nowy plik R (`script.R`) funkcje służące do edytowania kodu źródłowego z wszystkimi programu Visual Studio do edytowania.
    - W lewym dolnym rogu jest **R interakcyjne** okna, w którym możesz interaktywnie opracowanie i przetestowanie kodu.

> [!Note]
> Można użyć **R interakcyjne** okna bez żadnych projektów otwarte, a nawet po załadowaniu projekt innego typu. Po prostu wybierz **narzędzia R > Windows > R interakcyjne** w dowolnym momencie.

## <a name="explore-the-interactive-window-and-intellisense"></a>Eksploruj okna interaktywnego i IntelliSense

1. Test, który działa okno interaktywne, wpisując w `3 + 4` , a następnie wprowadź można przejrzeć wyniki:

    ![Okno interaktywne R w Visual Studio 2017 (VS2017)](media/getting-started-02-interactive1.png)

1. Wprowadź coś bardziej skomplikowane nieco, `ds <- c(1.5, 6.7, 8.9) * 1:12`, a następnie wprowadź `ds` można przejrzeć wyniki:

    ![Dodatkowe interakcyjne przykład R w programie Visual Studio](media/getting-started-03-interactive2.png)

1. Wpisz w `mean(ds)` , ale należy zauważyć, że jak najszybciej po wpisaniu `m` lub `me`, Visual Studio IntelliSense udostępnia opcje automatycznego uzupełniania. Po wybraniu zakończenia, który ma na liście, naciśnij klawisz Tab, aby wstawić Możesz zmienić wybór z klawiszy strzałek lub myszy.

    ![Znajdujące się po wprowadzeniu kodu IntelliSense](media/getting-started-04-intellisense1.png)

1. Po zakończeniu `mean`, wpisz nawias otwierający `(` i zwróć uwagę, jak IntelliSense umożliwia pomocy wbudowanej funkcji:

    ![Wyświetlanie pomocy dla funkcji IntelliSense](media/getting-started-05-intellisense2.png)

1. Zakończenie wiersza `mean(ds)` i naciśnij klawisz Enter, aby zobaczyć wynik (`[1] 39.51667`).

1. Okno interaktywne jest zintegrowany z pomocy, więc wprowadzania `?mean` Wyświetla Pomoc dla tej funkcji w **pomocy R** okna w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [pomoc w R narzędzi dla programu Visual Studio](getting-started-help.md).

    ![Okno Pomoc R w programie Visual Studio](media/getting-started-06-help.png)

1. Niektóre polecenia, takie jak `plot(1:100)`, Otwórz nowe okno w programie Visual Studio, gdy nie można wyświetlić dane wyjściowe bezpośrednio w oknie interaktywnym:

    ![Wyświetlanie wykresu w programie Visual Studio](media/getting-started-07-plot-window.png)

Okno interaktywne umożliwia również przejrzeć historię, obciążenia i Zapisz obszarów roboczych dołączyć do debugera i interakcję z plikami kodu źródłowego zamiast kopiowania i wklejania. Zobacz [Praca z okno interaktywne R](interactive-repl-for-r-in-visual-studio.md) szczegółowe informacje.

## <a name="experience-code-editing-features"></a>Funkcje edycji kodu obsługi

Praca krótko z okno interaktywne przedstawiono podstawowe funkcje edycji takie jak IntelliSense, które również działają w edytorze kodu. Po wprowadzeniu tego samego kodu jako przed Zobacz tego samego autouzupełniania i monity IntelliSense, ale nie dane wyjściowe.

Pisanie kodu w `.R` plików pozwala zobaczyć cały kod jednocześnie i ułatwia zmiany małe, a następnie szybko sprawdzić działanie uruchamiając kod w oknie interaktywnym. Może także zawierać dowolną liczbę plików w projekcie. Jeśli kod jest w pliku, można również uruchomić go krok w debugerze (omówione w dalszej części tego artykułu). Funkcje te są przydatne informacje o jest tworzenie algorytmów obliczeniową i pisanie kodu do manipulowania co najmniej jeden zestaw danych, szczególnie w przypadku, gdy chcesz sprawdzić wszystkie wyniki pośrednie.

Na przykład poniższe kroki tworzenia trochę kodu do eksplorowania [centralnej Newtona Limit](https://en.wikipedia.org/wiki/Central_limit_theorem) (Wikipedia). (Ten przykład jest dostosowany z *R Cookbook* przez Teetor Pawła.)

1. W `script.R` edytor, wprowadź następujący kod:

    ```R
    mu <- 50
    stddev <- 1
    N <- 10000
    pop <- rnorm(N, mean = mu, sd = stddev)
    plot(density(pop), main = "Population Density", xlab = "X", ylab = "")
    ```

1. Aby szybko wyświetlić wyniki, wybierz cały kod (Ctrl + A), a następnie naciśnij klawisze Ctrl + Enter lub kliknij prawym przyciskiem myszy i wybierz polecenie **wykonaj w programie Interactive**. Zaznaczony kod uruchamiany w okno interaktywne tak, jakby został wpisany bezpośrednio, przedstawiający wynik w oknie kreślenia:

    ![Wyświetlanie wykresu w programie Visual Studio](media/getting-started-08-plot1.png)

1. Dla jednowierszowego naciśnij klawisze Ctrl + Enter w dowolnym momencie uruchomić tego wiersza w oknie interaktywnym.

> [!Tip]
> Wzorzec wprowadzanie zmian i naciśnięcie klawiszy Ctrl + Enter (lub zaznaczanie wszystkiego o Ctrl + A i naciskając klawisz Ctrl + Enter) Dowiedz się, aby szybko uruchomić kod. W ten sposób jest bardziej wydajne niż przy użyciu myszy dla tej samej operacji.
> 
> Można ponadto przeciągnij i upuść okna kreślenia poza ramki Visual Studio i umieść go w przy każdym innym na ekranie. Następnie można zmienić rozmiar okna kreślenia wymiary i zapisz go do obrazu lub pliku PDF.

1. Dodaj kilka wierszy kodu do uwzględnienia drugi wykres więcej:

    ```R
    n <- 30
    samp.means <- rnorm(N, mean = mu, sd = stddev / sqrt(n))
    lines(density(samp.means))
    ```

1. Naciśnij klawisze Ctrl + A i Ctrl + Enter ponownie do uruchomienia kodu, który wygenerował następujące wyniki:

    ![Zaktualizowano podwójną kreślenia w programie Visual Studio](media/getting-started-09-plot2.png)

1. Problem jest pierwszy wykres określa skali pionowej, więc wykreślenia drugiego (z `lines`) nie pasuje. Aby rozwiązać ten problem, należy ustawić `ylim` parametru `plot` wywołań, ale nie tak, aby prawidłowo musimy dodać kod do obliczenia maksymalnej wartości pionowej. Ten wiersz po wierszu w oknie interaktywnym jest niewygodne ponieważ musimy rozmieszczanie kod, aby użyć `samp.means` przed wywołaniem `plot`. W pliku kodu, jednak firma Microsoft może łatwo wprowadzać odpowiednie zmiany:

    ```R
    mu <- 50
    stddev <- 1
    N <- 10000
    pop <- rnorm(N, mean = mu, sd = stddev)

    n <- 30
    samp.means <- rnorm(N, mean = mu, sd = stddev / sqrt(n))
    max.samp.means <- max(density(samp.means)$y)

    plot(density(pop), main = "Population Density",
        ylim = c(0, max.samp.means),
        xlab = "X", ylab = "")
    lines(density(samp.means))
    ```

1. CTRL + A i Ctrl + Enter ponownie sprawdzić działanie:

    ![Zaktualizowano podwójne kreślenia w programie Visual Studio poprawnie skalowania](media/getting-started-10-plot3.png)

Istnieje więcej, które można wykonać w edytorze. Aby uzyskać więcej informacji, zobacz [edytowanie kodu](editing-r-code-in-visual-studio.md), [IntelliSense](r-intellisense.md), i [wstawki kodu](code-snippets-for-r.md).

## <a name="debugging-your-code"></a>Debugowanie kodu

Jednym z kluczowych możliwości programu Visual Studio jest jego debugowania interfejsu użytkownika. RTVS jest oparty na tym silne foundation i dodaje innowacyjnych interfejsu użytkownika, takich jak [Explorer zmiennej i podglądu tabeli danych](variable-explorer.md). W tym miejscu wystarczy Spójrzmy pierwszy na debugowanie.

1. Aby rozpocząć, Resetuj bieżący obszar roboczy, aby wyczyścić wszystkie jego wykonaniu wykonanej do tej pory przy użyciu **narzędzia R > sesji > Resetuj** polecenia menu. Domyślnie wszystkie czynności wykonywane w oknie interaktywnym przypadającą na bieżącej sesji, który następnie jest już używana przez debuger. Resetowanie sesji, pewność, że sesja debugowania rozpoczyna się od żadne istniejące dane. **Zresetować** polecenia, jednak nie ma wpływu na Twoje `script.R` źródła pliku, ponieważ ma czy zarządzane i zapisany poza obszar roboczy.

1. Z `script.R` plik utworzony w poprzedniej sekcji, ustaw punkt przerwania w wierszu, który rozpoczyna się od `pop <-` wprowadzania karetkę na tej linii, a następnie naciskając klawisz F9 lub wybierając **Debuguj > Przełącz punkt przerwania** menu polecenie. Po prostu kliknij w lewym marginesie (lub odstępu) dla tego wiersza, w którym pojawi się czerwone punktu przerwania kropki (.):

    ![Ustawienia punktu przerwania w edytorze](media/getting-started-11-debug1.png)

1. Uruchom debuger kodu z `script.R` wybierając **plik źródłowy uruchamiania** przycisk na pasku narzędzi, wybranie **debugowania > plik źródłowy uruchamiania** elementów menu lub naciskając klawisz F5. Visual Studio wprowadzi trybu debugowania i uruchamiania kodu. Przestaje, jednak na wiersz, w którym można ustawić punktu przerwania:

    ![Zatrzymywanie na punkt przerwania w debugerze programu Visual Studio](media/getting-started-12-debug2.png)

1. Podczas debugowania, Visual Studio umożliwia krokowo kodu wiersz po wierszu. Możesz również wkroczyć do funkcji, Przekrocz nad nimi lub wychodzenia z nich do wywoływania kontekstu. Funkcje te, wraz z innymi, można znaleźć w **debugowania** menu, w menu kontekstowym kliknij prawym przyciskiem myszy w edytorze i narzędzi debugowania:

    ![Debugowania narzędzi w programie Visual Studio](media/getting-started-13-debug3.png)

1. Po zatrzymaniu w punkcie przerwania, można sprawdzić wartości zmiennych. Zlokalizuj **automatycznych** okna w Visual Studio i wybierz kartę wzdłuż dolnej części o nazwie **zmiennych lokalnych**. **Zmiennych lokalnych** oknie zmienne lokalne są wyświetlane w bieżącym punkcie w programie. Jeśli użytkownik jest zatrzymana na wcześniej ustawić punkt przerwania, zobaczysz, że `pop` zmienna nie jest jeszcze zdefiniowana. Teraz używać **Debuguj > Step Over** polecenia (F10) i zostanie wyświetlony wartość `pop` są wyświetlane:

    ![Okno zmiennych lokalnych w programie Visual Studio](media/getting-started-14-debug4.png)

1. Aby zbadać zmiennych w innych zakresach, w tym zakresie globalnym i zakresy pakietu, należy użyć [Explorer zmiennej](variable-explorer.md). Eksplorator zmiennej oferuje również możliwość, aby przełączyć do widoku tabelarycznego z kolumnami można sortować i do eksportowania danych do pliku CSV.

    ![Rozwinięty widok Eksploratora zmiennej](media/variable-explorer-expanded-results.png)

1. Można kontynuować krokowe wykonywanie programu wiersz po wierszu, lub wybierz opcję **Kontynuuj** (F5), aby uruchomić go do wykonania (lub następnego punktu przerwania).

Aby przejść głębiej, zobacz [debugowanie](debugging-r-in-visual-studio.md) i [Explorer zmiennej](variable-explorer.md).

## <a name="next-steps"></a>Następne kroki

W tym przewodniku samouczka podstawy projektów języka R, przy użyciu okna interaktywnego, code, edytowanie i debugowanie w programie Visual Studio. Aby kontynuować, eksploracji więcej możliwości, zobacz następujące artykuły, a także wyświetlany w spisie treści artykułów:

- [Przykładowych projektach](getting-started-samples.md)
- [Edytowanie kodu](editing-r-code-in-visual-studio.md)
- [Debugowanie](debugging-r-in-visual-studio.md)
- [Obszary robocze](r-workspaces-in-visual-studio.md)
- [Wizualizowanie danych](visualizing-data-with-r-in-visual-studio.md)
