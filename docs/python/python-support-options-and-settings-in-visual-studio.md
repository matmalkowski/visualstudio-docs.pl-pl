---
title: "Opcje i ustawienia dla języka Python w programie Visual Studio | Dokumentacja firmy Microsoft"
description: "Odwołanie do różnych ustawień w programie Visual Studio, które odnoszą się do kodu Python i projektów."
ms.custom: 
ms.date: 01/04/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Python_Tools
- VS.ToolsOptionsPages.Python_Tools.General
- VS.ToolsOptionsPages.Python_Tools.Debugging
- VS.ToolsOptionsPages.Python_Tools.Diagnostics
- VS.ToolsOptionsPages.Python_Tools.Interactive_Windows
- VS.ToolsOptionsPages.Text_Editor.Python.Advanced
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 31d46778cd764ee841662ed6581b6b06ee66919c
ms.sourcegitcommit: ba29e4d37db92ec784d4acf9c6e120cf0ea677e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2018
---
# <a name="options-for-python-in-visual-studio"></a>Opcje dla języka Python w programie Visual Studio

Aby wyświetlić opcje języka Python, użyj **Narzędzia > Opcje** menu poleceń, upewnij się, że **Pokaż wszystkie ustawienia** jest zaznaczone, a następnie przejdź do **narzędzi Python Tools**:

![Okno dialogowe z opcje języka Python, karta Ogólne](media/options-general.png)

Dostępne są również dodatkowe opcje specyficzne dla języka Python na **Edytor tekstu > Python > Zaawansowane** kartę.

> [!Note]
> **Eksperymentalne** grupy zawiera opcje dla funkcji, które są nadal w fazie projektowania i nie opisano w tym miejscu. Są one często omówione w ogłoszenia na [engineering Python na blogu Microsoft](https://blogs.msdn.microsoft.com/pythonengineering/).

## <a name="general-options"></a>Opcje ogólne

| Opcja | Domyślny | Opis |
| --- | --- | --- |
| Pokaż okno danych wyjściowych podczas tworzenia środowisk wirtualnych| On | Usuń zaznaczenie, aby zapobiec wyświetlaniu w oknie danych wyjściowych. |
| Pokaż okno dane wyjściowe podczas instalowania lub usuwania pakietów | On |  Usuń zaznaczenie, aby zapobiec wyświetlaniu w oknie danych wyjściowych. |
| Zawsze uruchamiaj pip jako administrator | Off | Zawsze eksponuje `pip install` operacje dla wszystkich środowisk. Podczas instalowania pakietów, Visual Studio monituje o uprawnienia administratora, jeśli środowisko znajduje się w obszarze chronionym systemu plików takich jak `c:\Program Files`. W tym wierszu, możesz zawsze podniesienia uprawnień `pip install` tylko ten jeden środowiska. Zobacz [środowiska Python — karta pip](managing-python-environments-in-visual-studio.md#pip-tab). |
| Automatyczne generowanie ukończenia DB przy pierwszym użyciu | On | Aby uzyskać [zakończeń IntelliSense](editing-python-code-in-visual-studio.md#intellisense) do pracy w bibliotece, Visual Studio należy wygenerować ukończenia bazy danych dla tej biblioteki. Tworzenie bazy danych jest realizowane w tle biblioteki jest zainstalowany, ale nie może być ukończone po rozpoczęciu pisania kodu. W przypadku wybrania tej opcji programu Visual Studio priorytetem ukończenia bazy danych biblioteki podczas pisania kodu, który korzysta z niego. |
| Ignoruj zmienne PYTHONPATH systemowe | On | PYTHONPATH jest domyślnie ignorowana, ponieważ program Visual Studio oferuje bardziej bezpośrednie sposób określ ścieżki wyszukiwania w środowiskach i projektów. Zobacz [środowiska Python - ścieżki wyszukiwania](managing-python-environments-in-visual-studio.md#search-paths) szczegółowe informacje. |
| Ścieżki wyszukiwania aktualizacji podczas dodawania plików połączonych | On | Gdy ustawiona, dodając [połączony plik](managing-python-projects-in-visual-studio.md#linked-files) z projektem aktualizacje [ścieżki wyszukiwania](managing-python-environments-in-visual-studio.md#search-paths) tak, aby IntelliSense mogą zawierać zawartość folderu połączony plik w jego ukończenia bazy danych. Usuń zaznaczenie tej opcji, aby wykluczyć takiej zawartości z bazy danych ukończenia. |
| Ostrzegaj, gdy zaimportowane się, że nie można odnaleźć modułu | On | Wyczyść tę opcję, aby pominąć ostrzeżenia, gdy wiesz, zaimportowanego modułu nie jest obecnie dostępna, ale w przeciwnym razie nie ma wpływu na kod operacji. |
| Wcięcie niespójne raportu jako | Ostrzeżenia | Ponieważ interpreter języka Python silnie zależny od prawidłowego wcięcia w celu ustalenia zakresu, Visual Studio domyślnie wystawia ostrzeżenia po wykryciu niespójne wcięcia, które mogą wskazywać błędów kodu. Ustaw *błędy* się jeszcze bardziej strict, co powoduje, że program zakończyć pracę w takich przypadkach. Aby całkowicie wyłączyć to zachowanie, wybierz *nie*. |
| Sprawdź, czy ankiety/wiadomości | Raz w tygodniu | Ustawia częstotliwość jaką zezwolisz na używanie programu Visual Studio można Otwórz okno zawierające strony sieci web z powiązanych Python ankiet i wiadomości, jeśli jest dostępna. Opcje są *nigdy*, *raz dziennie*, *raz w tygodniu*, i *raz w miesiącu*. |
| Resetuj wszystkie okna dialogowe trwale ukryty (przycisk) | n/d | Różne okna dialogowe udostępniają opcje, takie jak **nie pokazuj tego ponownie**. Ten przycisk służy do wyczyścić te opcje i spowodować okien dialogowych się ponownie. |

![Okno dialogowe z opcje języka Python, karta Ogólne](media/options-general.png)

## <a name="debugging-options"></a>Opcje debugowania

| Opcja | Domyślny | Opis |
| --- | --- | --- |
| Przed uruchomieniem, gdy istnieją błędy | On | Gdy są ustawione, wyświetli monit o potwierdzenie uruchomienia kodu, który zawiera błędy. Usuń zaznaczenie tej opcji, aby wyłączyć ostrzeżenia. |
| Oczekiwanie na dane wejściowe, gdy proces kończy się nienormalnie<br/><br/>Oczekiwanie na dane wejściowe, gdy proces kończy się zwykle | Na (dla obu) | Uruchamia program Python uruchomiony z programu Visual Studio w osobnym oknie konsoli. Domyślnie okno oczekuje na naciśnięcie klawisza przed jego zamknięciem, niezależnie od tego, jak wyjście z programu. Aby usunąć ten monit i zamknąć okno automatycznie, wyczyść jednego lub obu tych opcji. |
| TEE dane wyjściowe programu do okna wyjściowego debugowania | On | Wyświetla dane wyjściowe programu w oknie konsoli oddzielne i w oknie programu Visual Studio danych wyjściowych. Usuń zaznaczenie tej opcji, aby wyświetlić dane wyjściowe tylko w oknie konsoli oddzielne. |
| Podziel na SystemExit wyjątku z kodem zakończenia o wartości zero | Off | Jeśli ustawiona, zatrzyma debugera na ten wyjątek. Jeśli jest wyczyszczone, debuger kończy działanie bez podziału. |
| Włącz debugowanie standardowa biblioteka języka Python | Off | Umożliwia Wkrocz do biblioteki standardowej kodu źródłowego podczas debugowania, ale wydłuża czas potrzebny do debugera rozpocząć.|

![Okno dialogowe, debugowanie kartę Opcje języka Python](media/options-debugging.png)

## <a name="diagnostics-options"></a>Opcje diagnostyki

| Opcja | Domyślny | Opis |
| --- | --- | --- |
| Obejmują analizy dzienników | On | Zawiera szczegółowe dzienniki odnoszących się do analizy zainstalowanego środowiska Python, podczas zapisywania do pliku diagnostyki lub skopiować je do Schowka za pomocą przycisków. Ta opcja może znacznie zwiększyć rozmiar wygenerowanego pliku, ale często jest wymagany do diagnozowania problemów IntelliSense. |
| Zapisz diagnostyki w pliku (przycisk) | n/d | Monit o podanie nazwy pliku, a następnie zapisuje dziennik do pliku tekstowego. |
| Diagnostyka kopiowania do Schowka (przycisk) | n/d | Umieszczenie całego dziennika w Schowku; Ta operacja może potrwać pewien czas zależnie od rozmiaru dziennika. |

![Okno dialogowe, karta Diagnostyka opcje języka Python](media/options-diagnostics.png)

## <a name="interactive-windows-options"></a>Interaktywne opcje systemu Windows

| Opcja | Domyślny | Opis |
| --- | --- | --- |
| Skrypty | n/d | Określa ogólne folder uruchamiania skryptów do zastosowania do interaktywnego systemu windows dla wszystkich środowisk. Zobacz [skrypty uruchamiania](managing-python-environments-in-visual-studio.md#startup-scripts). Należy jednak pamiętać, że ta funkcja nie działa obecnie. |
| Strzałki w górę lub w dół przejdź historii | On | Używa klawiszy strzałek w celu nawigowania w historii w oknie interaktywnym. Wyczyścić to ustawienie, aby przejść w danych wyjściowych okno interaktywne zamiast za pomocą klawiszy strzałek. |
| Tryb uzupełniania | Tylko obliczać wyrażeń bez wywołania funkcji | Proces określania dostępne elementy członkowskie na wyrażeniu w oknie interaktywnym może wymagać oceny bieżącego wyrażenia niedokończone może powodować efekty uboczne lub funkcji jest wywołana wiele razy. Ustawieniem domyślnym *tylko obliczać wyrażeń bez wywołania funkcji* wyklucza wyrażeń, które są wyświetlane do wywoływania funkcji, ale ocenia inne wyrażenia. Na przykład ocenia `a.b` , ale nie `a().b`.  *Nigdy nie obliczać wyrażeń* uniemożliwia wszystkie efekty uboczne, za pomocą tylko normalne aparacie IntelliSense dla sugestie. *Ocena wszystkie wyrażenia* ocenia pełne wyrażenie uzyskanie sugestii, niezależnie od tego, efekty uboczne. |
| Ukryj podpowiedzi analizy statycznej | Off | Gdy opcja wyświetla tylko sugestii, które są uzyskiwane przez obliczenie wyrażenia. Jeśli w połączeniu z tryb uzupełniania *nigdy nie obliczać wyrażeń*, nie przydatne zakończeń są wyświetlane w oknie interaktywnym. |

![Okno dialogowe, karta interaktywnego okna Opcje języka Python](media/options-interactive-windows.png)

## <a name="advanced-python-editor-options"></a>Zaawansowane opcje edytora języka Python

### <a name="completion-results"></a>Wyników zakończenia

| Opcja | Domyślny | Opis |
| --- | --- | --- |
| Zakończenie elementu członkowskiego Wyświetla przecięcia elementów członkowskich | Off | Gdy są ustawione, pokazuje tylko zakończeń, które są obsługiwane przez wszystkie możliwe typy. |
| Lista filtrów oparte na ciąg wyszukiwania | On | Stosuje filtrowanie sugestii ukończenia podczas wpisywania (domyślny jest zaznaczone). |
| Automatycznie wyświetlaj zakończeń dla wszystkich identyfikatorów | On | Usuń zaznaczenie tej opcji, aby wyłączyć zakończeń w edytorze i interaktywne systemu windows. |

### <a name="selection-in-completion-list"></a>Wybór na liście uzupełniania

| Opcja | Domyślny | Opis |
| --- | --- | --- |
| Zatwierdzane przez wpisanie następujących znaków | {}[]().,:;+-*/%&&#124;^~=<>#@\ | Te znaki wykonaj zazwyczaj identyfikator, który może wybrać z listy uzupełniania tak jest wygodne zatwierdzić zakończenia po prostu, wpisując znak. Można usunąć lub Dodaj do listy zgodnie z potrzebami określonych znaków.  |
| Wprowadź zakończenia bieżącego zatwierdzeń | On | Po ustawieniu klawisza Enter wybiera i dotyczy obecnie wybranego zakończenia zgodnie z powyższym znaków (ale oczywiście nie znak Enter, więc nie można go bezpośrednio przejść do tej listy!). |
| Dodaj nowy wiersz po naciśnięciu klawisza enter na końcu wpisaniu całego słowa | Off | Domyślnie po wpisaniu całe wyrazy, która jest wyświetlana w menu podręcznym uzupełniania i naciśnij klawisz Enter, zatwierdzeniu tego ukończenia. Przez ustawienie dla tej opcji, efektywnie zatwierdzeniu zakończeń po zakończeniu wpisywania identyfikatora, tak aby Enter Wstawia nowy wiersz. |

### <a name="miscellaneous-options"></a>Inne opcje

| Opcja | Domyślny | Opis |
| --- | --- | --- |
| Trybu zwijania przy otwieraniu plików | On | Podczas otwierania pliku kodu Python automatycznie włączyć funkcję Visual Studio zwijania w edytorze. |
| Wklej usunięte monitów REPL | On | Usuwa >>> i... z wklejony tekst, umożliwiając łatwy transfer kod z okna interaktywnego do edytora. Usuń zaznaczenie tej opcji, jeśli chcesz zachować te znaki podczas wklejania z innych źródeł. |
| Na podstawie typów nazwy kolorów | On | Umożliwia kolorowania w kodzie języka Python. |

![Python Edytor okno dialogowe Opcje, karta Zaawansowane](media/options-editor-advanced.png)