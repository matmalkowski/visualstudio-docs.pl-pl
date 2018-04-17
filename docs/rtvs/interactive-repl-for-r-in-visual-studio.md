---
title: Interaktywny REPL dla języka R
description: Jak używać interaktywne środowisko REPL dla inVisual Studio R, który jest zintegrowany z okna edytora.
ms.custom: ''
ms.date: 06/28/2017
ms.technology:
- devlang-r
dev_langs:
- R
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- data-science
ms.openlocfilehash: f40c5a7d00672422d861fad3caf16b0285949b6b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="working-with-the-r-interactive-window"></a>Praca z okno interaktywne R

R Tools dla programu Visual Studio (RTVS) oferuje interaktywnego okna R, znanej także jako **REPL** okna (odczytu oceny-drukowania-pętla), można wprowadzić kod języka R i od razu Zobacz wyniki. Wszystkie moduły, składni i zmienne, a także IntelliSense, jest dostępna w oknie interaktywnym.

Okno interaktywne również jest zintegrowany z regularnych okna edytora R. Wybierz kod i naciśnij klawisze Ctrl + Enter lub kliknij prawym przyciskiem myszy i wybierz **Execute w Interactive**, i jest on uruchamiany wiersz po wierszu w oknie interaktywnym tak, jakby został wpisany bezpośrednio. Gdy kursor znajduje się w jednym wierszu w oknie edytora, Ctrl + Enter wysyła go do okna interaktywnego, a następnie przesuwa kursor do następnego wiersza. W ten sposób można po prostu nacisnąć klawisze Ctrl + Enter, aby wykonywać krokowo kodu.

Aby skorzystać z tych funkcji, należy wykonać [wprowadzenie R](getting-started-with-r.md) wskazówki oraz sekcje w tym artykule. [Wstawki kodu](code-snippets-for-r.md) również działać w oknie interaktywnym, jak w oknach Edytora R.

## <a name="overview-of-the-interactive-window"></a>Omówienie okno interaktywne

Wpisz prawidłowy kod języka R i naciskając klawisz Enter na końcu wiersza uruchamia kod w tym wierszu:

```repl
> 3 + 3
[1] 6
```

Naciśnięcie klawisza Enter w dowolnym miejscu na jeden wiersz danych wejściowych działa także tego wiersza.

Wszystkie poprzednie dane wejściowe i wyjściowe w REPL jest tylko do odczytu i nie można zmienić. Można jednak wybrać i skopiować tekst z okna w dowolnym momencie, a także wkleić. Wklejony kod działa tak, jakby zostały wprowadzone wiersz po wierszu.

Oznacza to, gdy zacznij wpisywać ciąg instrukcji i naciśnij klawisz Enter, RTVS zna po instrukcji musi być kontynuowane i przejdzie do trybu wielowierszowego z + monitu po lewej i odpowiednie wcięcia. RTVS wykonuje ponadto nawiasy, nawiasy i nawiasy klamrowe:

![Wpis instrukcji wiele wierszy w oknie interaktywnym](media/repl-multiline-entry.png)

W tym trybie wielowierszowego klawisza Enter uruchamia blok kodu tylko wtedy, gdy znajduje się na końcu bloku, w przeciwnym razie go wstawia nowy wiersz. Jednak można nacisnąć klawisze Ctrl + Enter w dowolnym miejscu na natychmiastowe uruchomienie tego bloku kodu.

### <a name="toolbar-commands"></a>Polecenia paska narzędzi

Poniżej przedstawiono okno interaktywne z jego narzędzi:

![Okno interaktywne z paska narzędzi](media/repl-window.png)

Polecenia paska narzędzi są następujące, z których większość mają odpowiedniki klawiatury i są również dostępne na **narzędzia R > sesji** i **narzędzia R > katalog roboczy** menu (lub wspomnianego):

| Przycisk | Polecenie | Kombinacja klawiszy | Opis | 
| --- | --- | --- | --- |
| ![Przycisk resetowania](media/repl-toolbar-01-reset.png) | Resetowanie | Ctrl+Shift+F10 | Resetuje sesji okna interaktywnego, czyszcząc wszystkie zmienne i historii. |
| ![Przycisk Wyczyść](media/repl-toolbar-02-clear.png) | Wyczyść | Ctrl+L | Czyści wyświetlanego w oknie interaktywnym; nie ma wpływu na zmienne sesji lub z historii. |
| ![Przyciski historii](media/repl-toolbar-03-history.png) | Poprzednie polecenie historii<br/>Następne polecenie historii | W górę, dół<br/>Alt + Strzałka w górę, dół Alt | Przewija historii, z pewnymi rodzajami zachowań dla bloków kodu wiele wierszy. Zobacz [historii](#history). |
| ![Przycisk obszaru roboczego obciążenia](media/repl-toolbar-04-load-workspace.png) | Obszar roboczy obciążenia | n/d | Ładuje poprzedniej zapisane obszaru roboczego (zobacz [obszarów roboczych i sesje](#workspaces-and-sessions). |
| ![Obszar roboczy przycisk Zapisz jako](media/repl-toolbar-05-save-workspace-as.png)| Zapisz obszar roboczy jako | n/d | Zapisuje bieżący stan sesji jako obszaru roboczego (zobacz [obszarów roboczych i sesje](#workspaces-and-sessions). |
| ![Przycisk skryptu źródło R](media/repl-toolbar-06-source-r-script.png) | Skrypt źródła R | Ctrl+Shift+S | Wywołania `source` z aktualnie aktywnego skryptu języka R w edytorze programu Visual Studio, która uruchamia kod.  Ten przycisk jest wyświetlany tylko wtedy, gdy plik R jest otwarty w edytorze programu Visual Studio. | 
| ![Skrypt źródła R z przyciskiem echo](media/repl-toolbar-07-source-r-script-with-echo.png) | Skrypt źródła R Echo | Ctrl+Shift+Enter | Jednak sam, jak skrypt języka R źródła Wyświetla zawartość skryptu w oknie interaktywnym. | 
| ![Przerwanie przycisk R](media/repl-toolbar-08-interrupt-r.png)| Przerwania R | Esc | Zatrzymuje wszystkie uruchamianie kodu w oknie interaktywnym, takich jak `while` pętli zrzut ekranu przedstawia na początku tej sekcji. |
| ![Dołącz debuger przycisku](media/repl-toolbar-09b-attach-debugger.png)| Dołączanie debugera | n/d | Również dostępne za pomocą **Debuguj > dołączyć do interaktywnego R** polecenia. | 
| ![Ustaw katalog roboczy do lokalizacji pliku źródłowego](media/repl-toolbar-10-set-working-directory-source.png)| Ustawianie pracy katalog do lokalizacji plików źródłowych | Ctrl+Shift+E | Ustawia katalog roboczy najbardziej ostatnio pochodzenia pliku załadowane do okna interaktywnego (przy użyciu `source`). Zobacz [katalog roboczy](#working-directory). |
| ![Ustaw katalog roboczy na przycisk lokalizacji projektu](media/repl-toolbar-11-set-working-directory-to-project.png) | Ustawianie pracy katalogu do lokalizacji projektu | Ctrl+Shift+P | Ustawia katalog roboczy na katalog główny aktualnie załadowanego projektu w programie Visual Studio. Zobacz [katalog roboczy](#working-directory). |
| (Pole tekstowe) | Wybierz pracy katalogu | n/d | Bezpośrednie pole wejściowe dla katalogu roboczego. Zobacz [katalog roboczy](#working-directory). |

## <a name="workspaces-and-sessions"></a>Obszary robocze i sesji

Wykonywanie kodu w oknie interaktywnym tworzy się kontekstu w bieżącej sesji. Kontekst składa się ze zmiennych globalnych, definicje funkcji, biblioteka obciążeń i tak dalej. Ten kontekst jest nazywane ogólnie *obszaru roboczego*, i można zapisywać i załadować obszarów roboczych w dowolnym momencie. 

Wybieranie **Zapisz obszar roboczy jako** przycisku lub przy użyciu **narzędzia R > sesji > Zapisz obszar roboczy jako...**  polecenie wyświetla monit o lokalizację i nazwę pliku (rozszerzenie domyślne `.RData`).

Aby zapisać obszaru roboczego przy użyciu określonej nazwy pliku (wartość domyślna to `.RData`), kliknij przycisk Zapisz obszar roboczy w REPL:

Aby ponownie załadować uprzednio zapisanego obszaru roboczego, wybierz **obciążenia roboczego** przycisk lub użyj **narzędzia R > sesji > obciążenia roboczego...**  i przejdź do pliku.

**Zresetować** przycisk lub **narzędzia R > sesji > Resetuj** czyści kontekstu sesji. Jeśli korzystasz z sesji zdalnej, zresetowanie spowoduje również usunięcie profilu użytkownika na komputerze zdalnym, aby wyczyścić poza przechowywane wszystkie pliki. (Zobacz [obszarów roboczych](r-workspaces-in-visual-studio.md#directories-on-local-and-remote-computers).)

## <a name="working-directory"></a>Katalog roboczy

Deweloperzy często chcesz zmienić ich katalog roboczy, podczas gdy w sesji interaktywnej. Różne polecenia dostępne na pasku narzędzi **narzędzia R > katalog roboczy** menu i menu kontekstowego projektu pozwala łatwo ustawić katalogu roboczego lokalizację pliku źródłowego, lokalizacji lub projektu lub innych dowolne lokalizacji. Dzięki temu pomaga uniknąć wpisywania pełnych nazw ścieżek lub długie nazwy ścieżek względnych podczas odwoływania się do plików.

## <a name="history"></a>Historia

Każdy wiersz wprowadzone w oknie interaktywnym zawiera wiersze wysyłane z edytora, zostaną zachowane w historii REPL. Następnie można przejść za pomocą historii z Up i klawiszy strzałek, ponieważ prawdopodobnie przyzwyczajony do w wierszu polecenia.

Jeden różnica polega na tym, że jeśli zacznij pisać w bieżącym wierszu i naciśnij klawisz, że bieżący wiersz jest zachowane w historii nawet za pośrednictwem można nie tego wiersza jeszcze uruchomione.

Historia w oknie interaktywnym działa inteligentnie instrukcji innych bloku kodu, które obejmuje wierszy. Gdy okrągło historii w górę i Strzałka w dół, bloki kodu wielowierszowego pobierania jako całą jednostkę i wyświetlane jako bieżącego wpisu. W tym momencie klawiszy strzałek przejdź za pośrednictwem tego bloku kodu wiersz po wierszu, aż do osiągnięcia górny lub dolny. W górnej części bloku kodu strzałki w górę pobiera poprzedni element w historii; w wierszu dolnej strzałkę w dół pobiera następny element.

To zachowanie bierze pod uwagę w przypadku typowych uruchomienie ostatniego elementu w historii kodu za pomocą Up strzałkę i wprowadź klawiszy kombinacja, umożliwiając naturalnie do edycji bloku kodu wiele wierszy, naciskając klawisz Strzałka w górę aby przejść do niego.

Aby uniknąć Przechodzenie do bloków kodu wiele wierszy, korzystając z paska narzędzi przycisków lub Alt + Strzałka w górę i Alt-Strzałka w dół, a wszystkie takie bloki są traktowane jako jeden wiersz.

Najprostszym sposobem, aby skorzystać z funkcji historii jest spróbuj je samodzielnie w oknie interaktywnym. Poniższy kod zapewnia kilka odpowiedniego wiersza jednym i wielu deklaracji. Za pomocą kopiowania i wklejania każda instrukcja oddzielnie, jednak, aby utworzyć odpowiednie historii. (Można również Wklej kod w osobnym pliku kodu i wysłać wiersze do interaktywnego okna z klawiszy Ctrl + Enter.)

```R
3 + 3

4 + 4

5 + 5

add <- function (x, y) {
  return (x + y)
}

sub <- function (x, y) {
  return (x - y)
}
```