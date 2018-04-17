---
title: Projekty języka R
description: Jak utworzyć Menedżera R projekty w programie Visual Studio, w tym właściwości, polecenia projektu i szablony.
ms.custom: ''
ms.date: 06/29/2017
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
ms.openlocfilehash: 1c24677ca645484141973cea67bdb29aa11880be
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="creating-r-projects-in-visual-studio"></a>Tworzenie projektów języka R w programie Visual Studio

Projekt R ( `.rxproj` pliku) identyfikuje źródła i plikami zawartości skojarzonymi z projektu. Także zawiera informacje o kompilacji dla każdego pliku, przechowuje informacje o integracji z systemami kontroli źródła i pomaga organizować aplikacji na logiczne składniki. Informacje związane z obszaru roboczego takie jak lista zainstalowanych pakietów, jednak jest obsługiwane oddzielnie w obszar roboczy.

Projekty zawsze są zarządzane w programie Visual Studio *rozwiązania*, który może zawierać dowolną liczbę projektów, które mogą odwoływać się wzajemnie. Zobacz [pomocą wiele typów projektów programu Visual Studio](#use-multiple-project-types-in-visual-studio).

## <a name="creating-a-new-r-project"></a>Tworzenie nowego projektu R

1. Uruchom program Visual Studio.
1. Wybierz **Plik > Nowy > Projekt...** (Ctrl+Shift+N)
1. Wybierz "Projekt R" w ramach **Szablony > R**, nadaj projektu, nazwy i lokalizacji, a wybierz **OK**:

    ![Okno dialogowe Nowy projekt dla języka R w programie Visual Studio (RTVS w VS2017)](media/getting-started-01-new-project.png)

To polecenie tworzy projekt z pustą `script.R` plik otwarty w edytorze. Zwróć uwagę, również w **Eksploratora rozwiązań** istnieją dwa inne pliki w projekcie:

![Zawartość utworzone na podstawie szablonu projektu języka R](media/projects-template-results.png)

`.Rhistory` Rejestruje niezależnie od polecenia wprowadź do [R interakcyjne](interactive-repl-for-r-in-visual-studio.md) okna. Można otworzyć okna historii dedykowany z **narzędzia R > Windows > Historia** polecenia. To okno ma narzędzi przycisk kontekstu elementy menu i wyczyścić zawartość historii.

`rproject.rproj` Pliku zachowuje niektóre ustawienia specyficzne dla języka R projektu, które w przeciwnym razie nie są zarządzane przez program Visual Studio:

| Właściwość | Domyślny | Opis |
| --- | --- | --- |
| Wersja | 1.0 | Wersja narzędzia R dla programu Visual Studio, używany do tworzenia projektu. |
| RestoreWorkspace | Domyślny | Automatyczne ładowanie poprzedniej zmienne obszaru roboczego z `.RData` pliku w katalogu projektu. |
| SaveWorkspace | Domyślny | Zapisz bieżący obszar roboczy zmienne `.RData` pliku w katalogu projektu podczas zamykania projektu. |
| AlwaysSaveHistory | Domyślny | Zapisz bieżący historii okna interaktywnego `.RHistory` pliku w katalogu projektu podczas zamykania projektu. |
| EnableCodeIndexing | Tak | Określa, czy do uruchomienia zadania indeksowania w tle szybkość wyszukiwania kodu. |
| UseSpacesForTab | Tak | Określa, czy do wstawiania spacji (tak) lub znak tabulacji (nie) po naciśnięciu klawisza Tab w edytorze. |
| NumSpacesForTab | 2 | Liczba spacji do wstawienia w przypadku UseSpacesForTab tak. |
| Kodowanie | UTF-8 | Domyślne kodowanie używane do `.R` plików. |
| RnwWeave | Sweave | Pakiet do użycia podczas tkania pliku Rnw. |
| LaTeX | pdfLaTeX | Bibliotekę do użycia podczas konwertowania RMarkdwon na PDF. |

### <a name="converting-a-folder-of-files-to-an-r-project"></a>Konwertowanie folderu plików do projektu R

Jeśli masz istniejące foldery `.R` pliki, które mają być zarządzane w projekcie, wykonaj następujące czynności:

1. Utwórz nowy projekt w programie Visual Studio, jak w poprzedniej sekcji.
1. Skopiuj pliki w folderze projektu.
1. W Eksploratorze rozwiązań programu Visual Studio kliknij prawym przyciskiem myszy projekt, wybierz **Dodaj > Kończenie elementu**, a następnie przejdź do plików, które chcesz dodać. Te pliki są wyświetlane w drzewie z projektu po wybraniu **OK**.
1. Aby zorganizować kodu w podfolderach, kliknij prawym przyciskiem myszy projekt, wybierz **Dodaj > Nowy Folder** najpierw następnie skopiuj pliki do tego folderu i dodać tych istniejących elementów w kroku 3.

## <a name="project-properties"></a>Właściwości projektu

Otwieranie stron właściwości projektu, kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i wybierz **właściwości**, lub wybierz **projektu > właściwości (nazwa projektu)...*  elementu menu. W otwartym oknie Wyświetla właściwości projektu:

| Tab | Właściwość | Opis |
| --- | --- | --- |
| Uruchom | Uruchamianie pliku | Nazwę pliku, który jest uruchamiany z **plik źródłowy uruchamiania** polecenia, F5 **debugowania > Rozpocznij debugowanie**, lub **debugowania > Uruchom bez debugowania**. Prawym przyciskiem myszy plik w projekcie i wybierając **Ustaw jako skryptu uruchomieniowego R** także ustawia go jako plik uruchamiania. |
| | Resetowanie R interakcyjne przy uruchomieniu | Czyści wszystkie zmienne z obszaru roboczego okno interaktywne podczas uruchamiania projektu. Operacją gwarancje tak nie jest zawartość nie końcowej obszaru roboczego z poprzedniej działa. |
| | Ścieżka projektu zdalnego | Ścieżka do zdalnego obszaru roboczego. |
| | Transfer plików przy uruchomieniu | Wskazuje, czy projekt plików może ulec filtr w **plików do transferu**, mają być kopiowane do zdalnego obszaru roboczego przy każdym uruchomieniu. |
| | Plików do transferu | Nazwy plików i wskazujący określonych plików do skopiowania do zdalnego obszaru roboczego, jeśli symboli wieloznacznych **przesyłać pliki przy uruchomieniu** jest zaznaczone. |
| Ustawienia | (Plik Settings.R) | Ustawienia projektu R pochodzą z `Settings.R` lub `*.Settings.R` pliki, które znajdują się wewnątrz projektu. Jeśli plik ustawień, nie istnieje, możesz dodać zmienne, Zapisz strony i domyślnym `Settings.R` zostanie utworzony plik. Można również dodać do projektu przy użyciu pliku ustawień **pliku > Dodaj nowy element...*  polecenia menu. <br/> Ustawienia są przechowywane jako kod języka R i plik można ustalić źródło przed uruchomieniem inne moduły, w związku z tym wstępnego zapełniania środowiska ze wstępnie zdefiniowanymi ustawieniami. |

## <a name="r-specific-project-commands"></a>Polecenia specyficzne dla języka R projektu

Projektów programu Visual Studio obsługują pewną liczbę poleceń ogólne za pośrednictwem menu kliknij prawym przyciskiem myszy i **projektu** menu. Aby uzyskać więcej informacji o tych ogólnych możliwości, zobacz [rozwiązania i projekty w programie Visual Studio](../ide/solutions-and-projects-in-visual-studio.md). Należy pamiętać, mimo że 

R narzędzi dla programu Visual Studio (RTVS) dodaje własne polecenia menu kliknij prawym przyciskiem myszy dla projektu R i również pliki i foldery w projekcie.

| Polecenie | Opis |
| --- | --- |
| Ustaw katalog roboczy, w tym miejscu | Ustawia katalog roboczy okno interaktywne R do folderu projektu, który może być również używany na dowolnym podfolderze w projekcie. |
| Otwórz Folder zawierający | Zostanie otwarty Eksplorator Windows w lokalizacji wybranego pliku. | 
| Dodaj skrypt języka R | Tworzy i otwiera nową `.R` plik o nazwie domyślnej. Można również użyć **Dodaj > Nowy element...**  polecenie, aby utworzyć `.R` pliki oraz wiele innych typów plików. Zobacz [szablonów elementów specyficznych dla R](#r-specific-item-templates). |
| Dodaj R Markdown | Tworzy i otwiera nowy `.rmd` dokumentu z domyślną nazwą. Można również użyć **Dodaj > Nowy element...**  polecenie, aby utworzyć `.rmd` pliki oraz wiele innych typów plików. Zobacz [szablonów elementów specyficznych dla R](#r-specific-item-templates).  | 
| Publikowanie procedury składowane | Uruchamia proces publikowania żadnych procedur składowanych zawarte w skryptach R. Zobacz [procedur składowanych pracy z programem SQL Server](integrating-sql-server-with-r.md#working-with-sql-server-stored-procedures). | 

## <a name="r-specific-item-templates"></a>Szablony elementów specyficznych dla języka R

RTVS zawiera wiele szablonów dla określonych typów plików. Dostęp do szablonów prawym przyciskiem myszy projekt R i wybierając **Dodaj > Nowy element...** , wybierając **projektu > Dodaj nowy element...** , lub za pomocą **Plik > Nowy > pliku...**  i wybierając **R** kartę. Najlepszym sposobem, aby zapoznać się z szablonu jest utworzenie nowego projektu i Wstaw pliki każdego typu.

> [!Note]
> **Dodaj > Nowy element...**  polecenia również wyświetlić typów ogólnych plików, które nie są wymienione w tabeli; **Plik > Nowy > pliku...**  tych typów znajdują się w zamian na **ogólne** kartę.

| Typ pliku | Opis |
| --- | --- |
| Skrypt języka R | Plik tekstowy zawierający tych samych poleceń, które mogą być wprowadzane w wierszu polecenia języka R. |
| R Markdown | Plik zawierający [R Markdown](rmarkdown-with-r-in-visual-studio.md) dokumentu. |
| Ustawienia języka R | Plik, który przechowuje ustawienia aplikacji R. | 
| Dokumentacja języka R | Ogólny plik dokumentacji R zawierający tylko nazwę, alias i tytuł pola. |
| Dokumentacja języka R (funkcja) | Plik dokumentacji R zawierający wiele pól z komentarzami opisu funkcji. |
| Dokumentacja języka R (zestawu danych) | Plik dokumentacji R zawierający wiele pól z komentarzami opisu zestawu danych. |
| Zapytanie SQL | I puste `.sql` pliku. Zobacz [integracji programu SQL Server](integrating-sql-server-with-r.md). |
| Procedura składowana z języka R | Plik R z podrzędnych zapytanie SQL i podrzędnym przechowywany plik szablonu procedury. Zobacz [integracji programu SQL Server](integrating-sql-server-with-r.md). |

## <a name="use-multiple-project-types-in-visual-studio"></a>Używanie wielu typów projektu w programie Visual Studio

Rozwiązania Visual Studio zapewniają wygodne miejsce do zbierania i powiązane projekty w jednym miejscu logiczne. Rozwiązania zapewnić kodu uporządkowane i ułatwia współpracę w obrębie zespołów.

W poniższym przykładzie rozwiązanie zawiera projekt R modelu, który został utworzony przy użyciu R i usługi Azure Machine Learning, projekt Python/scikit — Dowiedz się projektu C++ zawierającego modułów znacznym pracy obliczeniowej, projekt SQL w celu zarządzania danymi i Python/Bottle projekt witryny sieci web, która publikuje wyniki:

![Visual Studio Solution Explorer przedstawiający wielu powiązanych projektów w rozwiązaniu](media/projects-polyglot.png)

Wyróżnione pogrubione projekt jest projektem "Autostart" dla rozwiązania; Aby go zmienić, kliknij prawym przyciskiem myszy inny projekt i wybierz **Ustaw jako projekt startowy**.

> [!Note]
> Obecnie nie ma żadnych jawnych R, aby C# / integracji języka C++ (jest dostępna dla języka Python, zobacz [Tworzenie rozszerzenia C++ dla języka Python](../python/working-with-c-cpp-python-in-visual-studio.md)).  Jednak są dostępne, które zapewniają C# i mostków C++ dla R. biblioteki

Aby uzyskać więcej informacji na temat zarządzania projektów i rozwiązań — ogólnie rzecz biorąc, zobacz [rozwiązania i projekty w programie Visual Studio](../ide/solutions-and-projects-in-visual-studio.md).
