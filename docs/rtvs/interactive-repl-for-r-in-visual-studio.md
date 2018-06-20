---
title: Interaktywny REPL dla języka R
description: Jak używać interaktywne środowisko REPL dla inVisual Studio R, który jest zintegrowany z okna edytora.
ms.date: 06/28/2017
ms.prod: visual-studio-dev15
ms.technology: vs-rtvs
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- data-science
ms.openlocfilehash: a9e475e108fee9134699b0ee80e59fbf3f5eea32
ms.sourcegitcommit: f685fa5e2df9dc307bf1230dd9dc3288aaa408b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2018
ms.locfileid: "36238442"
---
# <a name="work-with-the-r-interactive-window"></a>Praca z okno interaktywne R

R Tools dla programu Visual Studio (RTVS) oferuje interaktywnego okna R, znanej także jako **REPL** okna (odczytu oceny-drukowania-pętla), można wprowadzić kod języka R i od razu Zobacz wyniki. Wszystkie moduły, składni i zmienne, a także IntelliSense, jest dostępna w oknie interaktywnym.

Okno interaktywne również jest zintegrowany z regularnych okna edytora R. Możesz wybrać kod i naciśnij klawisz **Ctrl**+**Enter**, lub kliknij prawym przyciskiem myszy i wybierz polecenie **Execute w Interactive**, i jest on uruchamiany wiersz po wierszu w trybie interaktywnym okna tak, jakby został wpisany bezpośrednio. Gdy kursor znajduje się w jednym wierszu w oknie edytora **Ctrl**+**Enter** wysyła tego wiersza do okna interaktywnego, a następnie przesuwa kursor do następnego wiersza. W ten sposób można nacisnąć **Ctrl**+**Enter** wielokrotnie do kroku za pomocą kodu.

Aby skorzystać z tych funkcji, należy wykonać [wprowadzenie R](getting-started-with-r.md) wskazówki oraz sekcje w tym artykule. [Wstawki kodu](code-snippets-for-r.md) również działać w oknie interaktywnym, jak w oknach Edytora R.

## <a name="overview-of-the-interactive-window"></a>Omówienie okno interaktywne

Wpisz prawidłowy kod języka R i naciskając klawisz **Enter** na końcu wiersza uruchamia kod w tym wierszu:

```repl
> 3 + 3
[1] 6
```

Naciśnięcie przycisku **Enter** dowolne miejsce na jeden wiersz danych wejściowych działa także tego wiersza.

Wszystkie poprzednie dane wejściowe i wyjściowe w REPL jest tylko do odczytu i nie można zmienić. Można jednak wybrać i skopiować tekst z okna w dowolnym momencie, a także wkleić. Wklejony kod działa tak, jakby zostały wprowadzone wiersz po wierszu.

Oznacza to, po rozpoczęciu wprowadzania instrukcji i naciśnij klawisz **Enter**, RTVS wie, gdy instrukcja musi być kontynuowana i przejdzie do trybu wielowierszowego z + monitu po lewej i odpowiednie wcięcia. RTVS wykonuje ponadto nawiasy, nawiasy i nawiasy klamrowe:

![Wpis instrukcji wiele wierszy w oknie interaktywnym](media/repl-multiline-entry.png)

W tym trybie wielowierszowego **Enter** klucza uruchamia blok kodu, tylko jeśli umieszczona na końcu bloku, w przeciwnym razie Wstawia nowy wiersz. Jednak możesz nacisnąć przycisk **Ctrl**+**Enter** na dowolnej pozycji do uruchomienia kodu natychmiast zablokować.

### <a name="toolbar-commands"></a>Polecenia paska narzędzi

Poniżej przedstawiono okno interaktywne z jego narzędzi:

![Okno interaktywne z paska narzędzi](media/repl-window.png)

Polecenia paska narzędzi są następujące, z których większość mają odpowiedniki klawiatury i są również dostępne na **narzędzia R** > **sesji** i **narzędzia R**  >  **Katalog roboczy** menu (lub wspomnianego):

| Przycisk | Polecenie | Kombinacja klawiszy | Opis | 
| --- | --- | --- | --- |
| ![Przycisk resetowania](media/repl-toolbar-01-reset.png) | Resetowanie | **CTRL**+**Shift**+**F10** | Resetuje sesji okna interaktywnego, czyszcząc wszystkie zmienne i historii. |
| ![Przycisk Wyczyść](media/repl-toolbar-02-clear.png) | Wyczyść | **CTRL**+**L** | Czyści wyświetlanego w oknie interaktywnym; nie ma wpływu na zmienne sesji lub z historii. |
| ![Przyciski historii](media/repl-toolbar-03-history.png) | Poprzednie polecenie historii<br/>Następne polecenie historii | **Zapasowej**, **w dół**<br/>**ALT**+**się**, **Alt**+**w dół** | Przewija historii, z pewnymi rodzajami zachowań dla bloków kodu wiele wierszy. Zobacz [historii](#history). |
| ![Przycisk obszaru roboczego obciążenia](media/repl-toolbar-04-load-workspace.png) | Obszar roboczy obciążenia | n/d | Ładuje poprzedniej zapisane obszaru roboczego (zobacz [obszarów roboczych i sesje](#workspaces-and-sessions). |
| ![Obszar roboczy przycisk Zapisz jako](media/repl-toolbar-05-save-workspace-as.png)| Zapisz obszar roboczy jako | n/d | Zapisuje bieżący stan sesji jako obszaru roboczego (zobacz [obszarów roboczych i sesje](#workspaces-and-sessions). |
| ![Przycisk skryptu źródło R](media/repl-toolbar-06-source-r-script.png) | Skrypt źródła R | **CTRL**+**Shift**+**S** | Wywołania `source` z aktualnie aktywnego skryptu języka R w edytorze programu Visual Studio, która uruchamia kod.  Ten przycisk jest wyświetlany tylko wtedy, gdy plik R jest otwarty w edytorze programu Visual Studio. | 
| ![Skrypt źródła R z przyciskiem echo](media/repl-toolbar-07-source-r-script-with-echo.png) | Skrypt źródła R Echo | **CTRL**+**Shift**+**wprowadź** | Jednak sam, jak skrypt języka R źródła Wyświetla zawartość skryptu w oknie interaktywnym. |
| ![Przerwanie przycisk R](media/repl-toolbar-08-interrupt-r.png)| Przerwania R | **ESC** | Zatrzymuje wszystkie uruchamianie kodu w oknie interaktywnym, takich jak `while` pętli zrzut ekranu przedstawia na początku tej sekcji. |
| ![Dołącz debuger przycisku](media/repl-toolbar-09b-attach-debugger.png)| Dołączanie debugera | n/d | Również dostępne za pomocą **debugowania** > **dołączyć do interaktywnego R** polecenia. | 
| ![Ustaw katalog roboczy do lokalizacji pliku źródłowego](media/repl-toolbar-10-set-working-directory-source.png)| Ustawianie pracy katalog do lokalizacji plików źródłowych | **CTRL**+**Shift**+**E** | Ustawia katalog roboczy najbardziej ostatnio pochodzenia pliku załadowane do okna interaktywnego (przy użyciu `source`). Zobacz [katalog roboczy](#working-directory). |
| ![Ustaw katalog roboczy na przycisk lokalizacji projektu](media/repl-toolbar-11-set-working-directory-to-project.png) | Ustawianie pracy katalogu do lokalizacji projektu | **CTRL**+**Shift**+**P** | Ustawia katalog roboczy na katalog główny aktualnie załadowanego projektu w programie Visual Studio. Zobacz [katalog roboczy](#working-directory). |
| (Pole tekstowe) | Wybierz pracy katalogu | n/d | Bezpośrednie pole wejściowe dla katalogu roboczego. Zobacz [katalog roboczy](#working-directory). |

## <a name="workspaces-and-sessions"></a>Obszary robocze i sesji

Wykonywanie kodu w oknie interaktywnym tworzy się kontekstu w bieżącej sesji. Kontekst składa się ze zmiennych globalnych, definicje funkcji, biblioteka obciążeń i tak dalej. Ten kontekst jest nazywane ogólnie *obszaru roboczego*, i można zapisywać i załadować obszarów roboczych w dowolnym momencie. 

Wybieranie **Zapisz obszar roboczy jako** przycisku lub przy użyciu **narzędzia R** > **sesji** > **Zapisz obszar roboczy jako**polecenie wyświetla monit o lokalizację i nazwę pliku (rozszerzenie domyślne *. RData*).

Aby zapisać obszaru roboczego przy użyciu określonej nazwy pliku (wartość domyślna to *. RData*), kliknij na **Zapisz obszar roboczy** przycisk REPL:

Aby ponownie załadować uprzednio zapisanego obszaru roboczego, wybierz **obciążenia roboczego** przycisk lub użyj **narzędzia R** > **sesji** > **obciążenia Obszar roboczy** i przejdź do pliku.

**Zresetować** przycisk lub **narzędzia R** > **sesji** > **zresetować** czyści kontekstu sesji. Jeśli korzystasz z sesji zdalnej, zresetowanie spowoduje również usunięcie profilu użytkownika na komputerze zdalnym, aby wyczyścić poza przechowywane wszystkie pliki. (Zobacz [obszarów roboczych](r-workspaces-in-visual-studio.md#directories-on-local-and-remote-computers).)

## <a name="working-directory"></a>Katalog roboczy

Deweloperzy często chcesz zmienić ich katalog roboczy, podczas gdy w sesji interaktywnej. Różne polecenia dostępne na pasku narzędzi **narzędzia R** > **katalog roboczy** menu i menu kontekstowego projektu można łatwo ustawić katalogu roboczego do lokalizacji pliku źródłowego , lokalizacji lub projektu lub dowolnego dowolnego miejsca. Dzięki temu pomaga uniknąć wpisywania pełnych nazw ścieżek lub długie nazwy ścieżek względnych podczas odwoływania się do plików.

## <a name="history"></a>Historia

Każdy wiersz wprowadzone w oknie interaktywnym zawiera wiersze wysyłane z edytora, zostaną zachowane w historii REPL. Następnie można przejść za pomocą historii z Up i klawiszy strzałek, ponieważ prawdopodobnie przyzwyczajony do w wierszu polecenia.

Jeden różnica polega na tym, że jeśli zacznij pisać w bieżącym wierszu i naciśnij klawisz, że bieżący wiersz jest zachowane w historii nawet za pośrednictwem można nie tego wiersza jeszcze uruchomione.

Historia w oknie interaktywnym działa inteligentnie instrukcji innych bloku kodu, które obejmuje wierszy. Gdy okrągło historii w górę i Strzałka w dół, bloki kodu wielowierszowego pobierania jako całą jednostkę i wyświetlane jako bieżącego wpisu. W tym momencie klawiszy strzałek przejdź za pośrednictwem tego bloku kodu wiersz po wierszu, aż do osiągnięcia górny lub dolny. W górnej części bloku kodu strzałki w górę pobiera poprzedni element w historii; w wierszu dolnej strzałkę w dół pobiera następny element.

To zachowanie bierze pod uwagę w przypadku typowej uruchomienie ostatniego elementu w historii kodu za pomocą strzałki w górę i **Enter** klawiszy kombinacja, umożliwiając naturalnie do edycji bloku kodu wiele wierszy, naciskając klawisz Strzałka w górę do Przejdź do niego.

Aby uniknąć Przechodzenie do bloków kodu wiele wierszy, użyj przycisków paska narzędzi lub **Alt**+**się** i **Alt**-**wdół**, oraz wszystkie takie bloki są traktowane jako jeden wiersz.

Najprostszym sposobem, aby skorzystać z funkcji historii jest spróbuj je samodzielnie w oknie interaktywnym. Poniższy kod zapewnia kilka odpowiedniego wiersza jednym i wielu deklaracji. Za pomocą kopiowania i wklejania każda instrukcja oddzielnie, jednak, aby utworzyć odpowiednie historii. (Można również Wklej kod w osobnym pliku kodu i wysłać wiersze do interaktywnego okna z **Ctrl**+**Enter**.)

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