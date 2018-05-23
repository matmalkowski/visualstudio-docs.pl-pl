---
title: Odwołanie okno środowiska Python
description: Szczegółowe informacje na każdej z kart, które są wyświetlane w oknie środowiska Python w programie Visual Studio.
ms.date: 05/22/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: eaf64d0d7bde7b63359ba341a693a51051da6fc3
ms.sourcegitcommit: cc88ccc6aacebe497899fab05d243a65053e194c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2018
---
# <a name="python-environments-window-tabs-reference"></a>Odwołanie karty okno środowiska Python

Aby otworzyć **środowiska Python** okno:

- Wybierz **Widok > inne okna > środowiska Python** polecenia menu.
- Kliknij prawym przyciskiem myszy **środowiska Python** węzła projektu w Eksploratorze rozwiązań i wybierz **widok wszystkich środowisk języka Python**

Po rozwinięciu **środowiska Python** okna dostatecznie szerokie, te opcje są wyświetlane jako kart, które może się okazać bardziej wygodne do pracy z. Dla uzyskania przejrzystości kartach w tym artykule są wyświetlane w widoku rozszerzonego.

![Widok rozszerzony okno środowiska Python](media/environments-expanded-view.png)

## <a name="overview-tab"></a>Karta Przegląd

Zawiera podstawowe informacje i poleceń środowiska:

![Karta Przegląd środowiska Python](media/environments-overview-tab.png)

| Polecenie | Opis |
| --- | --- |
| Ustaw jako domyślny dla nowych projektów tego środowiska | Ustawia środowisko active, co może spowodować Visual Studio (wersja 2017 15.5 i starszych) może chwilę nie odpowiadać podczas ładuje IntelliSense bazy danych. Środowiska z wiele pakietów mogą być nieodpowiadająca przez dłuższy czas. |
| Odwiedź witrynę sieci Web dystrybutora | Otwiera w przeglądarce adres URL udostępniony przez dystrybucję oprogramowania Python. Python 3.x, na przykład przechodzi do python.org. |
| Otwórz okno interaktywne | Otwiera [okna interaktywnego (REPL)](python-interactive-repl-in-visual-studio.md) dla tego środowiska w programie Visual Studio stosowania [skrypty uruchamiania (patrz poniżej)](#startup-scripts). |
| Eksploruj interaktywne skryptów | Zobacz [skrypty uruchamiania](#startup-scripts). |
| Tryb interaktywny IPython | Jeśli wartość zostanie otwarte okno interaktywne z IPython domyślnie. Ten wbudowany włączone geograficzne oraz rozszerzona składnia IPython takich jak `name?` Aby wyświetlić Pomoc i `!command` powłoki poleceń. Ta opcja jest zalecana, gdy przy użyciu rozkładu Anaconda, ponieważ wymaga dodatkowych pakietów. Aby uzyskać więcej informacji, zobacz [przy użyciu IPython w oknie interaktywnym](interactive-repl-ipython.md). |
| Otwórz w programie PowerShell | Uruchamia interpretera w oknie poleceń programu PowerShell. |
| (Folder i program łącza) | Zapewniają szybki dostęp do folderu instalacji w środowisku, python.exe interpreter i pythonw.exe interpreter. Pierwszy otwiera w Eksploratorze Windows, tych dwóch Otwórz okno konsoli. |

### <a name="startup-scripts"></a>Skrypty uruchamiania

Interakcyjne systemu windows są wykorzystywane w zwykłych przepływu pracy, prawdopodobnie należy utworzyć funkcje pomocnicze, często używane. Może na przykład utworzyć funkcję, która otwiera DataFrame w programie Excel, a następnie zapisz ten kod jako skryptu uruchamiania tak, aby zawsze dostępne w oknie interaktywnym.

Skrypty uruchamiania zawierają kod, który okno interaktywne ładuje i uruchamia się automatycznie, w tym Importy, definicje funkcji i dosłownie inaczej. Te skrypty są przywoływane na dwa sposoby:

1. Po zainstalowaniu środowiska Visual Studio tworzy folder `Documents\Visual Studio 2017\Python Scripts\<environment>` gdzie &lt;środowiska&gt; jest zgodna z nazwą środowiska. Można łatwo przejść do folderu określonego środowiska o **Eksploruj interaktywne skrypty** polecenia. Po uruchomieniu okno interaktywne dla tego środowiska ładuje i działa niezależnie od `.py` znajdują się pliki w tym miejscu w kolejności alfabetycznej.

1. **Skryptów** kontroli w **Narzędzia > Opcje > Narzędzia Python Tools > interakcyjne Windows** kartę (zobacz [Opcje interakcyjne systemu windows](python-support-options-and-settings-in-visual-studio.md#interactive-windows-options)) należy podać dodatkowe folder służący do uruchamiania skryptów, które są załadowane, a następnie uruchomienie we wszystkich środowiskach. Jednak ta funkcja nie działa w chwili obecnej.

## <a name="configure-tab"></a>Karta Konfigurowanie

Jeśli jest dostępna, zawiera szczegółowe informacje, zgodnie z opisem w poniższej tabeli. Jeśli na tej karcie nie jest obecny, oznacza to, czy program Visual Studio automatycznie zarządza wszystkie szczegóły.

![Karta Konfigurowanie środowiska Python](media/environments-configure-tab.png)

| Pole | Opis |
| --- | --- |
| **Opis** | Nazwa umożliwiają środowiska. |
| **Ścieżka prefiksu** | Lokalizacja folderu podstawowego interpretera. Wypełnianie tej wartości, a następnie klikając polecenie **Autowykrywanie**, Visual Studio podejmuje próbę wypełnienia w pozostałych polach dla Ciebie. |
| **Ścieżka interpretera** | Ścieżka do pliku wykonywalnego interpreter często ścieżki prefiks następuje `python.exe` |
| **Okna interpretera** | Ścieżka do konsoli bez pliku wykonywalnego, często następuje ścieżki prefiks `pythonw.exe`. |
| **Ścieżka biblioteki**<br/>(jeśli jest dostępny) | Określa katalog główny biblioteki standardowe, ale tę wartość można zignorować, jeśli Visual Studio jest w stanie uzyskać dokładniejsze ścieżki od interpretera. |
| **Wersja językowa** | Wybrany z listy rozwijanej. |
| **Architektura** | Zwykle wykrywane i automatycznie wypełniane, w przeciwnym razie określa 32-bitowy lub 64-bitowej. |
| **Zmienna środowiskowa PATH** | Zmiennej środowiskowej, która używa interpretera można znaleźć ścieżki wyszukiwania. Visual Studio zmienia wartość zmiennej podczas uruchamiania Python, tak aby zawierała ścieżek wyszukiwania projektu. Zwykle ta właściwość powinna być równa `PYTHONPATH`, ale niektóre tłumaczy Użyj innej wartości. |

## <a name="packages-tab"></a>Karta pakietów

*Również z etykietą "pip" we wcześniejszych wersjach.*

Zarządza pakiety zainstalowane w środowisku przy użyciu narzędzia pip, co umożliwia również wyszukiwanie i instalowanie nowych (w tym wszelkie zależności). W Visual Studio 2017 wersji 15.7 lub nowszym **pakietów (Conda)** , który używa Menedżera pakietów conda zamiast tego zostanie wyświetlona karta. (Jeśli nie widzisz, że wybór, ustaw dla opcji **narzędzia** > **opcje** > **Python** > **eksperymentalne**   >  **Użyj Menedżera pakietów conda dostępne (zamiast pip)** i uruchom ponownie program Visual Studio.)

Pakiety, które są już zainstalowane są wyświetlane z formantami, aby zaktualizować (Strzałka w górę) i Odinstaluj (X koło) pakietu:

![Karta pakietów środowiska Python](media/environments-pip-tab-controls.png)

Wprowadzenie listę zainstalowanych pakietów, jak również pakiety, które mogą być instalowane z PyPI filtry terminu wyszukiwania.

![Karta pakietów środowiska Python z wyszukiwania na "num"](media/environments-pip-tab.png)

Jak widać na ilustracji powyżej, w wynikach wyszukiwania liczba pakietów, które pasują do szukanego terminu; Pierwsza pozycja na liście jednak to polecenie do uruchomienia `pip install <name>` bezpośrednio. Jeśli używasz **pakietów (Conda)** karcie, zamiast tego zobacz `conda install <name>`:

![Karta pakiety Conda przedstawiający conda polecenie instalacji](media/environments-conda-tab-install.png)

W obu przypadkach można dostosować instalację, dodając argumenty w polu wyszukiwania po nazwie pakietu. Po dołączeniu argumenty w wynikach wyszukiwania pokazuje `pip install` lub `conda install` następuje zawartość pola wyszukiwania:

![Przy użyciu argumentów na polecenia instalacji narzędzia pip i conda](media/environments-pip-tab-arguments.png)

Instalowanie pakietu tworzy oddzielne podfoldery w środowisku `Lib` folder w systemie plików. Na przykład, jeśli masz zainstalowany 3,6 Python w `c:\Python36`, pakiety są instalowane w `c:\Python36\Lib`; Jeśli masz zainstalowany w Anaconda3 `c:\Program Files\Anaconda3` , a następnie pakiety są instalowane w `c:\Program Files\Anaconda3\Lib`.

W tym ostatnim przypadku ponieważ środowisko znajduje się w obszarze chronionym systemu plików `c:\Program Files`, należy uruchomić program Visual Studio `pip install` z podniesionymi uprawnieniami, aby zezwolić na tworzenie podfolderów pakietu. Gdy wymagana jest podniesienia uprawnień, Visual Studio wyświetla monit "Aby zainstalować, zaktualizować lub usunąć pakiety dla tego środowiska może być wymagane uprawnienia administratora":

![Wiersz podniesienia uprawnień do instalacji pakietu aktualizacji](media/environments-pip-elevate.png)

**Podniesienie poziomu teraz** przyznaje uprawnienia administracyjne do narzędzia pip pojedyncza, podmiotu również do dowolnego systemu operacyjnego wyświetla monit o uprawnienia. Wybieranie **Kontynuuj bez uprawnień administratora** próby instalacji pakietu, ale narzędzie pip kończy się niepowodzeniem podczas próby utworzenia folderów z danych wyjściowych, takich jak "Błąd: nie można utworzyć" C:\Program Files\Anaconda3\Lib\site-packages\ PNG.PY': odmowa uprawnień. "

Wybieranie **zawsze podniesienia uprawnień podczas instalowania lub usuwania pakietów** zapobiega wyświetlaniu środowiska okna dialogowego. Aby ponownie wyświetlone okno dialogowe, przejdź do **Narzędzia > Opcje > Narzędzia Python Tools > Ogólne** i kliknij przycisk **zresetować wszystkie okna dialogowe trwale ukryty**.

W tym takie same opcje karcie, możesz również wybrać **pip są zawsze uruchamiane jako administrator** do pomijania okna dialogowego dla wszystkich środowisk. Zobacz [opcje — karta Ogólne](python-support-options-and-settings-in-visual-studio.md#general-options).

## <a name="intellisense-tab"></a>Karta IntelliSense

Wskazuje bieżący stan bazy danych uzupełniania IntelliSense:

![Karta IntelliSense środowiska Python](media/environments-intellisense-tab.png)

- W **programu Visual Studio 2017 wersji 15,5 cala** i wcześniej, IntelliSense zakończeń są zależne od bazy danych, która jest została skompilowana dla tej biblioteki. Tworzenie bazy danych jest realizowane w tle podczas biblioteki jest zainstalowany, ale może zająć trochę czasu i mogą być niekompletne podczas uruchamiania pisanie kodu.
- **Visual Studio 2017 wersji 15,6** i później używa szybszej metody, aby zapewnić zakończeń, które nie są zależne od bazy danych domyślnie. Z tego powodu etykietą karcie **IntelliSense [bazy danych wyłączone]**. Bazy danych można włączyć po usunięciu zaznaczenia opcji **narzędzia** > **opcje** > **Python**  >   **Eksperymentalne** > **użyć nowego stylu IntelliSense dla środowisk**.

Gdy program Visual Studio wykryje nowego środowiska (lub dodaj je), automatyczne rozpoczęcie do skompilowania bazy danych, analizując biblioteki plików źródłowych. Ten proces może potrwać od minutę na godzinę lub dłużej w zależności od tego, co jest zainstalowany. (Anaconda, na przykład zawiera wiele bibliotek i dopiero po pewnym czasie, aby skompilować bazy danych) Po wykonaniu tych czynności możesz uzyskać szczegółowe IntelliSense i nie trzeba ponownie Odśwież bazy danych (z **Odśwież DB** przycisk) aż do zainstalowania więcej bibliotek.

Biblioteki, dla których nie zostały skompilowane danych są oznaczone ikoną z **!**; Jeśli środowisko bazy danych nie jest zakończone, **!** jest także wyświetlany obok niej na liście głównego środowiska.

## <a name="see-also"></a>Zobacz także

- [Zarządzanie środowiska Python w programie Visual Studio](managing-python-environments-in-visual-studio.md)
- [Wybierz interpreter dla projektu](selecting-a-python-environment-for-a-project.md)
- [Używanie pliku requirements.txt dla zależności](managing-required-packages-with-requirements-txt.md)
- [Ścieżki wyszukiwania](search-paths.md)
