---
title: Dokumentacja okna środowiska Python
description: Szczegółowe informacje dotyczące każdej z kart, które są wyświetlane w oknie środowiska Python w programie Visual Studio.
ms.date: 05/25/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: d4adc1ac472bb05affa547d795690dc7143655fd
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "34572127"
---
# <a name="python-environments-window-tabs-reference"></a>Dokumentacja karty okna środowiska Python

Aby otworzyć **środowiska Python** okna:

- Wybierz **Widok > inne Windows > środowiska Python** polecenia menu.
- Kliknij prawym przyciskiem myszy **środowiska Python** węzeł projektu w Eksploratorze rozwiązań i wybierz pozycję **wyświetlanie wszystkich środowisk języka Python**

Po rozwinięciu **środowiska Python** dostatecznie szerokie okna, te opcje są wyświetlane jako kart, które może się okazać bardziej wygodne do pracy z. W celu uściślenia karty, w tym artykule są wyświetlane w widoku rozszerzonym.

![Widok rozszerzony okna środowiska Python](media/environments-expanded-view.png)

## <a name="overview-tab"></a>Karta Przegląd

Zawiera podstawowe informacje i poleceń dla środowiska:

![Karta Przegląd środowiska Python](media/environments-overview-tab.png)

| Polecenie | Opis |
| --- | --- |
| Należy to środowisko domyślne dla nowych projektów | Ustawia aktywnego środowiska może spowodować, że program Visual Studio (2017 w wersji 15.5 i starszych) krótko przestanie przestać odpowiadać podczas ładowania bazy danych IntelliSense. W środowiskach z wielu pakietów, może być nieodpowiadająca przez dłuższy czas. |
| Odwiedź witrynę sieci Web dystrybutora | Otworzy w przeglądarce adres URL podany przez funkcję dystrybucji języka Python. Python 3.x, na przykład, przechodzi do python.org. |
| Otwórz okno interaktywne | Otwiera [okna interaktywnego (REPL)](python-interactive-repl-in-visual-studio.md) dla tego środowiska w programie Visual Studio stosowania [skrypty uruchamiania (patrz poniżej)](#startup-scripts). |
| Eksploruj interaktywne skrypty | Zobacz [skrypty uruchamiania](#startup-scripts). |
| Użyj trybu interaktywnego IPython | Po ustawieniu spowoduje otwarcie okna interaktywnego z powłoką IPython domyślnie. Ten wbudowany włączone geograficzne oraz rozszerzonej składni IPython takich jak `name?` Aby wyświetlić Pomoc i `!command` dla poleceń powłoki. Ta opcja jest zalecana, gdy za pomocą dystrybucji pakietu Anaconda, ponieważ wymaga dodatkowych pakietów. Aby uzyskać więcej informacji, zobacz [przy użyciu IPython w oknie interaktywnym](interactive-repl-ipython.md). |
| Otwórz w programie PowerShell | Uruchamia interpreter w okno poleceń programu PowerShell. |
| (Folder i program łącza) | Zapewnia szybki dostęp do folderu instalacji środowiska, python.exe interpreter i interpretera pythonw.exe. Pierwszy otwiera w Eksploratorze Windows, w dwóch ostatnich przypadkach Otwórz okno konsoli. |

### <a name="startup-scripts"></a>Skrypty uruchamiania

W codziennym przepływie pracy, wykorzystywane są interaktywnych okien, prawdopodobnie należy opracować funkcji pomocnika, które regularnie używane. Może na przykład utworzyć funkcję, która otwiera ramkę danych w programie Excel, a następnie zapisz ten kod jako skrypt do uruchomienia, aby zawsze będzie ona dostępna w oknie interaktywnym.

Skrypty uruchamiania zawierają kod, który okno interaktywne ładuje i uruchamia się automatycznie, w tym importów, definicje funkcji i dosłownie czymkolwiek. Te skrypty są przywoływane na dwa sposoby:

1. Podczas instalowania środowiska Visual Studio tworzy folder `Documents\Visual Studio 2017\Python Scripts\<environment>` gdzie &lt;środowiska&gt; jest zgodna z nazwą środowiska. Łatwo można przejść do folderu określonego środowiska z **Eksploruj interaktywne skrypty** polecenia. Po uruchomieniu oknie interaktywnym dla danego środowiska, ładuje i uruchamia niezależnie od rodzaju `.py` pliki znajdują się w tym miejscu w kolejności alfabetycznej.

1. **Skrypty** w kontrolce **Narzędzia > Opcje > Python Tools > interaktywne Windows** kartę (zobacz [opcje interaktywnych okien](python-support-options-and-settings-in-visual-studio.md#interactive-windows-options)) należy podać dodatkowe folder skrypty uruchamiania, które są ładowane i uruchamiać we wszystkich środowiskach. Jednak ta funkcja nie działa w chwili obecnej.

## <a name="configure-tab"></a>Karta Konfigurowanie

Jeśli to możliwe, zawiera szczegółowe informacje, zgodnie z opisem w poniższej tabeli. Jeśli na tej karcie nie jest obecny, oznacza to, czy Visual Studio automatycznie zarządza wszystkie szczegółowe informacje.

![Karta Konfigurowanie środowiska Python](media/environments-configure-tab.png)

| Pole | Opis |
| --- | --- |
| **Opis** | Nazwa do nadania środowiska. |
| **Ścieżka prefiksu** | Lokalizacja folderu podstawowego interpretera. Wypełnianie tej wartości, a następnie klikając pozycję **Autowykrywanie**, Visual Studio polegające na próbie wypełnienia w pozostałych polach za Ciebie. |
| **Cesta k interpretu** | Ścieżka do pliku wykonywalnego interpretera często ścieżka prefiksu następuje `python.exe` |
| **Interpreter okna** | Ścieżka do konsoli bez pliku wykonywalnego, często następuje ścieżka prefiksu `pythonw.exe`. |
| **Ścieżka biblioteki**<br/>(jeśli jest dostępny) | Określa katalog główny biblioteki standardowej, ale ta wartość może być ignorowany, jeśli program Visual Studio jest w stanie poprosić bardziej precyzyjne ścieżka interpretera. |
| **Wersja językowa** | Wybranie z menu rozwijanego. |
| **Architektura** | Zwykle wykrywane i automatycznie wypełniane, w przeciwnym razie określa 32-bitową lub 64-bitowych. |
| **Zmiennej środowiskowej PATH** | Zmienna środowiskowa interpreter używane do wyszukiwania ścieżki wyszukiwania. Program Visual Studio zmienia wartość zmiennej, podczas uruchamiania Python tak, aby zawierała ścieżek wyszukiwania projektu. Zazwyczaj ta właściwość powinna być równa `PYTHONPATH`, ale niektóre interpretery użycie innej wartości. |

## <a name="packages-tab"></a>Karta pakietów

*We wcześniejszych wersjach, również oznaczone jako "pip".*

Zarządza pakiety zainstalowane w środowisku przy użyciu narzędzia pip, dzięki czemu możesz również wyszukać i zainstalować nowe (w tym wszystkie zależności). W programie Visual Studio 2017 wersji 15.7 lub nowszej **pakietów (Conda)** , który używa Menedżera pakietów conda zamiast tego zostanie wyświetlona karta. (Jeśli nie widzisz tego wyboru, należy ustawić opcję **narzędzia** > **opcje** > **Python** > **eksperymentalne**   >  **Użyj Menedżera pakietów conda dostępne (a nie pip)** i uruchom ponownie program Visual Studio.)

Pakiety, które są już zainstalowane są wyświetlane z kontrolkami, aby zaktualizować (Strzałka w górę) i Odinstaluj (X okrąg) pakietu:

![Karta pakietów środowiska Python](media/environments-pip-tab-controls.png)

Wprowadzenie filtry termin wyszukiwania listę zainstalowanych pakietów, a także pakietów, które mogą być instalowane z PyPI.

![Karta pakietów środowiska Python za pomocą wyszukiwania na "liczba"](media/environments-pip-tab.png)

Jak widać na ilustracji powyżej, w wynikach wyszukiwania wyświetlić liczbę pakietów, które pasują do szukanego terminu; pierwszy wpis na liście jest jednak polecenie do uruchomienia `pip install <name>` bezpośrednio. Jeśli używasz **pakietów (Conda)** kartę, zamiast tego zobacz `conda install <name>`:

![Karta pakiety Conda przedstawiający conda polecenie instalacji](media/environments-conda-tab-install.png)

W obu przypadkach można dostosować instalację, dodając argumentów w polu wyszukiwania, po nazwie pakietu. Po dołączeniu argumentów w wynikach wyszukiwania pokazuje `pip install` lub `conda install` następuje zawartość pola wyszukiwania:

![Na polecenia instalacji narzędzia pip i conda przy użyciu argumentów](media/environments-pip-tab-arguments.png)

Instalowanie pakietu tworzy oddzielne podfoldery w tym środowisku `Lib` folder w systemie plików. Na przykład, jeśli masz zainstalowane środowisko Python 3.6 w `c:\Python36`, pakiety są instalowane w `c:\Python36\Lib`; Jeśli masz zainstalowany w Anaconda3 `c:\Program Files\Anaconda3` , a następnie pakiety są instalowane w `c:\Program Files\Anaconda3\Lib`.

### <a name="granting-administrator-privileges-for-package-install"></a>Udzielanie uprawnień administratora dla pakietu instalacji

Podczas instalowania pakietów w środowisku, w którym znajduje się w obszaru chronionego systemu plików, takich jak `c:\Program Files\Anaconda3\Lib`, należy uruchomić program Visual Studio `pip install` podwyższonym poziomem uprawnień, aby zezwalała na utworzyć podfoldery, pakietu. Gdy wymagana jest podniesienie uprawnień, program Visual Studio wyświetla monit "Aby zainstalować, zaktualizować lub usunąć pakiety dla tego środowiska mogą być wymagane uprawnienia administratora":

![Monit o podniesienie uprawnień dla instalacji pakietu aktualizacji](media/environments-pip-elevate.png)

**Podnieś uprawnienia teraz** udziela uprawnień administracyjnych do narzędzia pip dla jednej operacji podmiotu również na dowolnym systemie operacyjnym, wyświetla monit o uprawnienia. Wybieranie **Kontynuuj bez uprawnień administratora** próby instalacji pakietu, ale narzędzie pip kończy się niepowodzeniem podczas próby takich jak tworzenie folderów z danymi wyjściowymi "Błąd: nie można utworzyć" C:\Program Files\Anaconda3\Lib\site-packages\ PNG.PY': odmowa uprawnień. "

Wybieranie **zawsze podniesienie poziomu podczas instalowania lub usuwania pakietów** zapobiega wyświetlaniu w środowisku okna dialogowego. Aby ponownie wyświetlone okno dialogowe, przejdź do **Narzędzia > Opcje > Python Tools > Ogólne** i wybierz przycisk, **zresetować wszystkie okna dialogowe trwale ukryty**.

W tym, że takie same opcje karty, możesz również wybrać **pip są zawsze uruchamiane jako administrator** do pomijania w oknie dialogowym dla wszystkich środowisk. Zobacz [opcje — karta Ogólne](python-support-options-and-settings-in-visual-studio.md#general-options).

### <a name="security-restrictions-with-older-versions-of-python"></a>Ograniczenia zabezpieczeń ze starszymi wersjami języka Python

Korzystając z języka Python 2.6, 3.1 i 3.2, Visual Studio wyświetla ostrzeżenie, "z powodu zabezpieczeń, które ograniczeń dotyczących instalowania z Internetu może nie działać w tej wersji języka Python":

![Komunikat dotyczący pip instalowanie ograniczenia przy użyciu starszej wersji języka Python](media/environments-old-version-restriction.png)

Przyczyna to ostrzeżenie jest to, że z tych starszych wersji języka Python, `pip install` nie zawiera obsługę dla zabezpieczeń TLS (Transport Layer) 1.2, który jest wymagany do pobierania pakietów ze źródła pakietu, pypi.org. Niestandardowe kompilacje języka Python może obsługiwać protokół TLS 1.2 w którym to przypadku `pip install` mogą działać.

Może być możliwe pobranie odpowiedniego `get-pip.py` pakietu z [bootstrap.pypa.io](https://bootstrap.pypa.io/), ręcznie Pobierz pakiet z [pypi.org](https://pypi.org/), a następnie zainstaluj pakiet z tej lokalnej kopii.

Zalecenia, jednak jest po prostu uaktualnić do środowisko Python 2.7 lub 3.3 +, w którym nie ma przypadków to ostrzeżenie.

## <a name="intellisense-tab"></a>Karta IntelliSense

Przedstawia bieżący stan bazy danych uzupełniania IntelliSense:

![Karta IntelliSense środowiska Python](media/environments-intellisense-tab.png)

- W **programu Visual Studio 2017 w wersji 15.5** i wcześniej, uzupełnianiu IntelliSense są zależne od bazy danych, która jest zostały skompilowane dla tej biblioteki. Tworzenia bazy danych jest wykonywane w tle, gdy biblioteka jest zainstalowany, ale może zająć trochę czasu i mogą być niekompletne po rozpoczęciu pisania kodu.
- **Visual Studio 2017 w wersji 15.6** później przy użyciu metody szybciej dostarcza uzupełnień, które nie zależą od bazy danych domyślnie. Z tego powodu karcie jest oznaczona etykietą **IntelliSense [baza danych wyłączone]**. Aby umożliwić bazy danych, usuwając zaznaczenie opcji **narzędzia** > **opcje** > **Python**  >   **Eksperymentalne** > **Użyj nowego stylu funkcji IntelliSense dla środowisk**.

Gdy program Visual Studio wykryje nowe środowisko (lub dodać jeden), automatycznie rozpoczyna do skompilowania bazy danych, analizując plików źródłowych w bibliotece. Ten proces może potrwać od chwilę na godzinę lub dłużej w zależności od tego, co jest zainstalowany. (Anaconda, na przykład jest dostarczany z wielu bibliotek i zajmuje trochę czasu, aby skompilować bazy danych) Po wykonaniu tych czynności, Uzyskaj szczegółowe IntelliSense i nie trzeba ponownie Odśwież bazy danych (przy użyciu **Odśwież DB** przycisk) aż do zainstalowania nad dodatkowymi bibliotekami.

Biblioteki, dla których jeszcze nie zostały skompilowane danych są oznaczone **!**; Jeśli bazy danych środowiska nie została ukończona, **!** również obok niego zostanie wyświetlony na liście głównego środowiska.

## <a name="see-also"></a>Zobacz także

- [Zarządzanie środowiskami Python w programie Visual Studio](managing-python-environments-in-visual-studio.md)
- [Wybierz interpreter dla projektu](selecting-a-python-environment-for-a-project.md)
- [Używanie pliku requirements.txt dla zależności](managing-required-packages-with-requirements-txt.md)
- [Ścieżki wyszukiwania](search-paths.md)
