---
title: Zmienna Eksploratora dla R
description: Zmiennej Explorer w programie Visual Studio zawiera wszystkie zmienne w danym zakresie w bieżącej sesji R.
ms.date: 01/24/2018
ms.prod: visual-studio-dev15
ms.technology: vs-rtvs
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- data-science
ms.openlocfilehash: 467099581a746005ecbe686b5806943b3f16ac7e
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="variable-explorer"></a>Eksplorator zmiennej

**Explorer zmiennej** okna otwarte z **narzędzia R > systemu Windows > zmiennej Eksploratora** (lub Ctrl + 8 jeśli używano **narzędzia R > Ustawienia analizy danych**), zawiera wszystkie zmienne w danym zakresie w bieżącej sesji R. Przykładowo po otwarciu Eksploratora zmiennej i wprowadź następujące wiersze do [okna interaktywnego](interactive-repl-for-r-in-visual-studio.md):

```R
x <- 42
y <- 43
n <- c(1,2,3,5,8,13)
```

Okno Eksploratora zmiennej pojawia się w następujący sposób:

![Okno Eksploratora zmiennej w Visual Studio](media/variable-explorer-window.png)

Jeśli masz bardziej złożonych ramki danych R zdefiniowane w sesji, można przejść do danych. Na przykład po uruchomieniu `cars <- mtcars` rozwijając różnych węzłów w Eksploratorze zmiennej można nawigować zestawu danych:

![Rozwinięty widok Eksploratora zmiennej](media/variable-explorer-expanded-results.png)

Aby usunąć zmienne, kliknij prawym przyciskiem myszy i wybierz **usunąć**, lub wybierz zmienną i naciśnij klawisz Delete.

Możesz również wyszukać obserwacji w ramce danych przy użyciu Wyszukiwanie przyrostowe. Po pierwsze rozwiń węzły w ramce danych, który chcesz przeszukać, a następnie wprowadź terminy wyszukiwania w polu wyszukiwania.

## <a name="details-table-view"></a>Widok szczegółów (tabeli)

Ponieważ dane są często tabelarycznych, dowolny typ danych złożonych można wyświetlić jako osobnej tabeli wybierając ikonę lupy lub klikając prawym przyciskiem myszy i wybierając **Pokaż szczegóły**.

![Widok Eksploratora zmiennych w tabeli](media/variable-explorer-table-view.png)

Kliknięcie nagłówka kolumny dane są sortowane według kolumny (Przełączanie pomiędzy kolumny). Przytrzymując naciśnięty klawisz Shift i klikając dodatkowych kolumn dodaje te kolumny do również sortowania. Kliknięcie kolumny bez Shift zwraca do jednej kolumny sortowania.

Sekwencji, w którym klikając nagłówki kolumn określa kolejność, w którym odbywa się sortowania. Na przykład kliknięcie Shift **cyl** kolumny, a następnie klikając przycisk Shift **mpg** kolumny dwukrotnie sortuje listę rosnąca liczba cylindrów i malejącej milach na galon:

![Widok tabeli dane, sortowanie według dwóch kolumn.](media/variable-explorer-table-view-sorting.png)

Ponieważ Eksplorator zmiennej i widoki tabel znajdują się w oddzielnych okien programu Visual Studio, można rozmieścić je jednak side-by-side pracy, takich jak. Zobacz [dostosowywanie układów okien w programie Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md) ogólne instrukcje.

## <a name="open-in-excel-or-other-csv-capable-application"></a>Otwórz w programie Excel (lub inną aplikację z obsługą CSV)

Dla dalszego manipulacji i analizy często jest przydatne do wyeksportowania zmienne sesji do pliku CSV. Eksportowanie odbywa się z małych ikon programu Excel (![ikonę eksportowania Excel](media/variable-explorer-excel-icon.png)) obok każdego węzła w Eksploratorze zmiennej lub przez kliknięcie prawym przyciskiem myszy element i wybierając **otwartych w aplikacji CSV**. Wybierając ikonę zapisuje dane do pliku CSV w `%userprofile%\Documents\RTVS_CSV_Exports` folder, a następnie spowoduje uruchomienie tego pliku, które umożliwia otwarcie go w dowolnej aplikacji skojarzonej z `.csv` rozszerzenia.

## <a name="scopes"></a>Zakresy

Domyślnie do globalnego zakresu zostanie otwarty Eksplorator zmiennej. Możesz przełączyć się do zakresu pakiet, wybierając pakiet z listy rozwijanej w górnej części okna.

![Zmienna explorer przedstawiający zakres pakietu](media/variable-explorer-package-scopes.png)

Można również przełączyć się do zakresu funkcji po zatrzymaniu w punkcie przerwania w debugerze (należy pamiętać, że Eksplorator zmiennej nie automatycznie przełącza do zakresu funkcji debugowanego kodu):

![Zmienna Explorer przedstawiający ramki danych podczas debugowania](media/variable-explorer-as-locals-window.png)

Zmienna Explorer automatycznie zmieni zakresem funkcji krokowo kodu w debugerze, takie jak wyświetlanie zmiennych lokalnych w funkcji.

## <a name="importing-data-into-variable-explorer"></a>Importowanie danych do zmiennej Explorer

Dwa polecenia na pasku narzędzi Eksplorator zmiennych, które są również dostępne za pośrednictwem **narzędzia R > danych** menu importu zewnętrznych CSV zestawów danych do sesji R: **zaimportować zestaw danych do sesji R z adresu URL sieci Web** i **zaimportować zestaw danych do R sesji z pliku tekstowego**. 

Po wyłaniają plik CSV do zaimportowania, Visual Studio Wyświetla **zaimportować zestawu danych** okna dialogowego, w którym zostały opcji, aby kontrolować sposób analizowania tego pliku danych (oznacza to, co to jest separator pola i sposób obsługi cudzysłowów). Można również wyświetlić podgląd ramki importowanych danych i oryginalny plik danych:

![Importowanie zestawu danych w oknie dialogowym](media/variable-explorer-import-dataset-dialog.png)
