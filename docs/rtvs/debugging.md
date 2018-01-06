---
title: "Debugowanie za pomocą narzędzia R dla programu Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 06/29/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload: data-science
ms.openlocfilehash: aca1fc0200e57867418c2a4c5ca7a718afdbc469
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="debugging-r-in-visual-studio"></a>R debugowania w programie Visual Studio

R narzędzi dla programu Visual Studio (RTVS) integruje się z pełne środowisko debugowania programu Visual Studio (zobacz [debugowania w programie Visual Studio](../debugger/debugging-in-visual-studio.md). Ta obsługa obejmuje punkty przerwania, dołączanie do uruchomionego procesu, kontroli i oglądaniu zmiennych i sprawdzanie stosu wywołań. W tym temacie opisuje następnie te aspekty debugowania, które są unikatowe dla języków R i RTVS.

Uruchamianie debugera dla pliku startowym R w projekcie R jest taka sama jak w przypadku innych typów projektów: Użyj **debugowania > Rozpocznij debugowanie**, klawisz F5 lub **plik źródłowy uruchamiania** na pasku narzędzi debugowania: 

![Przycisk start debugera dla języka R](media/debugger-start-button.png)

Aby zmienić plik uruchamiania, kliknij prawym przyciskiem myszy plik w Eksploratorze rozwiązań i wybierz **ustawić jako uruchamiania skryptu języka R**.

We wszystkich przypadkach, uruchamianie debugera "sources" pliku w oknie interaktywnym, co oznacza załadowanie go i uruchamianie tak jak pokazano w danych wyjściowych okno interaktywne:

```output
> rtvs::debug_source("c:/proj/rproject1/rproject1/script.R")
Sourcing: c:\proj\rproject1\rproject1\script.R
Sourcing: c:\proj\rproject1\rproject1\Settings.R
```

Zwróć uwagę, że `rtvs::debug_source` funkcja służy do źródła skryptu. Ta funkcja jest wymagana, ponieważ RTVS musi zmodyfikować kod w ramach przygotowania do debugowania. Jeśli przy użyciu dowolnego polecenia źródeł RTVS i Debuger jest dołączony, Visual Studio automatycznie używa `rtvs::debug_source`.

Można też ręcznie uruchomić debugera z okno interaktywne bezpośrednio za pomocą **narzędzia R > sesji > dołączyć debuger** polecenia **debugowania > dołączyć do interaktywnego R** polecenia lub  **Dołącz debuger** polecenia na pasku narzędzi okna interaktywnego. Po wykonaniu czynności odpowiada Twoje pliki źródłowe, które chcesz debugować. Jeśli chcesz ręcznie pliki źródłowe upewnij się, że używasz `rtvs::debug_source` i nie regularne `source` polecenia w języku R.

To połączenie między debugera i okno interaktywne ułatwia wykonywanie czynności, takich jak telefonicznej (i debugowanie) funkcji z wartościami innym parametrem. Na przykład załóżmy, że masz następująca funkcja pochodzenia pliku (znaczenie, gdy jest on ładowany do sesji):

```R
add <- function(x, y) {
    return(x + y)
}
```

A następnie ustaw punkt przerwania na `return` instrukcji. Teraz, w oknie interaktywnego wprowadzania `add(4,5)` zatrzyma debugera na punkt przerwania.


## <a name="environment-browser-in-the-interactive-window"></a>Przeglądarka środowiska w oknie interaktywnym

Gdy użytkownik jest zatrzymana w debugerze, również w przypadku został zatrzymany w wierszu przeglądarka środowiska [okna interaktywnego](interactive-repl.md). Monit jest wyświetlany jako `Browse[n]>` gdzie n jest liczbą.

W przeglądarce środowiska obsługuje wiele poleceń specjalne:

| Polecenie | Opis |
| --- | --- |
| n | Następny: uruchamia następnej instrukcji w kodzie pliku (taki sam jak Przekrocz). |
| s | Wkrocz do: uruchamia następnej instrukcji w pliku kodu krokowe wykonywanie w zakresie funkcji, jeśli następna instrukcja znajduje się wywołanie funkcji. |
| F | Zakończ: uruchamia końca bieżącego zakresu funkcji i zwraca do wywołującego (tak samo, jak krok out). |
| Pobi c | Kontynuuj: uruchamia program do następnego punktu przerwania. |
| Q | Zamyka: kończy się sesja debugowania. |
| gdzie | Pokaż stos: Wyświetla okna interaktywnego stosu wywołań. |
| Pomoc | Pokaż Pomoc: Wyświetla dostępne polecenia w oknie interaktywnym. |
| &lt;wyrażenie&gt; | obliczenia wyrażenia w *wyrażenie*. |

![Przeglądarka środowiska w oknie interaktywnym](media/debugger-environment-browser.png)
