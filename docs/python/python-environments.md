---
title: "Środowiska Python w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/09/2018
ms.reviewer: 
ms.suite: 
ms.technology: devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "11"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 54c25180e0133ec407099cf4bb0f58f2279279d4
ms.sourcegitcommit: 11740fed01cc602252ef698aaa11c07987b00570
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2018
---
# <a name="python-environments"></a>Środowiska Python

Python *środowiska* kontekst, w którym można uruchomić kod języka Python. Środowisko składa się z tłumacza, biblioteki (zazwyczaj Python standardowa biblioteka) i zestaw zainstalowanych pakietów. Te składniki wspólnie określają, które konstrukcji języka i składni są prawidłowe, jakiego systemu operacyjnego funkcje są dostępne, a które pakietów, należy użyć.

W programie Visual Studio, zarządzanie wszystkimi środowisk przy użyciu [okno środowiska Python](#managing-python-environments-in-visual-studio) zgodnie z opisem w tym artykule. Danego projektu, wybrano środowisko do użycia na potrzeby uruchamiania kodu, debugowanie, sprawdzanie składni, wyświetlanie zakończeń import i element członkowski, a wszelkie inne zadania, które są specyficzne dla interpretera i zainstalowane biblioteki. Visual Studio zachowuje również bazy danych dla poszczególnych środowisk udostępniający automatycznego uzupełniania po wprowadzeniu kodu IntelliSense.

Środowiska wirtualne programu Visual Studio również zapewnia obsługę `requirements.txt` plików i ścieżek wyszukiwania.

**Uwaga**: Jeśli jesteś nowym użytkownikiem Python w programie Visual Studio, zobacz następujące artykuły w tle konieczne:

- [Praca z języka Python w programie Visual Studio](python-in-visual-studio.md)
- [Instalowanie obsługi języka Python w programie Visual Studio](installation.md)

## <a name="global-and-virtual-environments"></a>Globalne i wirtualnych środowisk

Istnieją dwa typy środowiska Python: globalna i wirtualnych.

**Globalne środowisk**: instalacji każdego języka Python (na przykład, Python 2.7, 3,6 Python i Anaconda 4.4.0, zobacz [zaznaczenie i instalowanie tłumaczy Python](#selecting-and-installing-python-interpreters) przechowuje własnego środowiska. Każde środowisko składa się z określonym interpreter języka Python, jego biblioteki standardowej i zestaw wstępnie zainstalowane pakiety. Instalowanie pakietu do globalnego środowiska udostępnia je do wszystkich projektów przy użyciu tego środowiska. Jeśli środowisko znajduje się w obszarze ochrona systemu plików (w ramach `c:\program files`, na przykład), a następnie instalowanie pakietów wymaga uprawnień administratora.

Globalne środowiska są dostępne dla wszystkich projektów na komputerze. W programie Visual Studio wybierz opcję jedną globalnego środowiska jako domyślny, który jest używany we wszystkich projektach, jeśli nie możesz wybrać inną nazwę dla projektu. Aby uzyskać więcej informacji, zobacz [wybierając środowisko dla projektu](#selecting-an-environment-for-a-project).

**Środowiska wirtualne**: ponieważ pakiety zainstalowane w środowisku globalne nie są dostępne dla wszystkich projektów, które używają tego środowiska, mogą wystąpić konflikty, gdy dwa projekty wymagają niezgodnych pakietów lub różne wersje tego samego pakietu. Środowiska wirtualne uniknąć takie konflikty przy użyciu interpreter i standardowej biblioteki z globalnego środowiska, ale obsługa własnych magazynów pakietu w folderach izolowanego.

W programie Visual Studio, można utworzyć środowisko wirtualne dla konkretnego projektu, który jest przechowywany w podfolderze w projekcie (zobacz [tworzenia środowisk wirtualnych](#creating-virtual-environments). Plik projektu identyfikuje również środowiska wirtualnego. Visual Studio rejestruje także wszelkie pakiety, które zainstalować do tego środowiska wirtualnego w projekcie `requirements.txt` pliku. Jeśli następnie udostępnić projektu i innymi deweloperami otwórz go na komputerach, program Visual Studio udostępnia opcję, aby ponownie utworzyć środowisko wirtualne.

### <a name="selecting-and-installing-python-interpreters"></a>Wybieranie i instalowanie tłumaczy Python

Domyślnie instalowanie Python obciążenia Programowanie w Visual Studio 2017 instaluje Python 3 (64-bitowe). Opcjonalnie można zainstalować 32-bitowe i 64-bitowe wersje Python 2, Python 3, Anaconda 2 i Anaconda 3, zgodnie z opisem w [instalacji](installation.md). Można też ręcznie zainstalują dowolną z tłumaczy wymienione w poniższej tabeli.

Dla programu Visual Studio 2015 i starszych należy ręcznie zainstalować jedną tłumaczy.

Visual Studio (wszystkie wersje) automatycznie tworzy środowisko dla każdego zainstalowana interpreter języka Python, sprawdzając rejestru (następujące [514 program ten - Python rejestracji w rejestrze systemu Windows](https://www.python.org/dev/peps/pep-0514/)). Jeśli program Visual Studio nie wykrywa zainstalowane środowisko, zobacz [tworzenia środowiska dla istniejących interpreter](#creating-an-environment-for-an-existing-interpreter).

| Interpreter | Opis |
| --- | --- |
| [Języka CPython](https://www.python.org/) | "Natywny" i najbardziej często używanych interpretera dostępne w wersjach 32-bitowych i 64-bitowych (32-bitowy zalecane). Zawiera najnowsze funkcje językowe, maksymalną zgodność pakiet języka Python, pełną obsługę debugowania i współdziałanie z [IPython](http://ipython.org/). Zobacz też: [użyć Python 2 lub Python 3?](http://wiki.python.org/moin/Python2orPython3). Należy pamiętać, że Visual Studio 2015 i starsze nie obsługują 3,6 Python i zapewnić błąd "Nieobsługiwana wersja języka python 3,6". Użyj języka Python w wersji 3.5 lub starszej zamiast tego. |
| [IronPython](https://github.com/IronLanguages/ironpython2) | .NET stosowania Python, dostępne w wersjach 32-bitowych i 64-bitowych, podając podstawowe interop /F #/ Visual C dostęp do interfejsów API architektury .NET, Python standardowe debugowania (ale nie C++ debugowanie w trybie mieszanym) oraz mieszany IronPython / C# debugowania. IronPython, jednak nie obsługuje środowisk wirtualnych. |
| [Anaconda](https://www.continuum.io) | Danych otwartych nauki platformy obsługiwane przez Python i zawiera najnowszą wersję języka CPython i większość pakietów trudne do zainstalowania. Firma Microsoft zaleca, jeśli nie zdecydujesz inaczej. |
| [PyPy](http://www.pypy.org/) | Implementacja JIT śledzenie wysokiej wydajności, języka Python, który ułatwia programy długotrwałe i sytuacji możesz określić wydajności problemów, ale nie można znaleźć inne rozwiązania. Działa z programem Visual Studio, ale z ograniczoną obsługę zaawansowanych funkcji debugowania. |
| [Jython](http://www.jython.org/) | Implementacja Python na maszynie wirtualnej Java (JVM). Podobny do IronPython, kodu uruchamianego w Jython mogą prowadzić interakcję z klas Java i bibliotek, ale może nie móc korzystać z wielu bibliotek przeznaczonych do języka CPython. Działa z programem Visual Studio, ale z ograniczoną obsługę zaawansowanych funkcji debugowania. |

Deweloperzy, które chcą udostępniać nowych metod wykrywania dla środowiska Python, zobacz [wykrywania środowiska PTVS](https://github.com/Microsoft/PTVS/wiki/Extensibility-Environments) (witryną github.com).

## <a name="managing-python-environments-in-visual-studio"></a>Zarządzanie środowiska Python w programie Visual Studio

Aby otworzyć okno środowiska Python, wybierz **Widok > inne okna > środowiska Python** polecenie menu, kliknij prawym przyciskiem myszy **środowiska Python** węzła projektu w Eksploratorze rozwiązań i Wybierz **widok wszystkich środowisk języka Python**:

    ![View All Environments command in Solution Explorer](media/environments-view-all.png)

W obu przypadkach jako element równorzędny karty do Eksploratora rozwiązań zostanie wyświetlone okno środowiska Python.

![Okno środowiska Python](media/environments-default-view.png)

W powyższym przykładzie zainstalowania języka Python 3.4 (32-bitowe języka CPython) wraz z 32-bitowe i 64-bitowych wersji IronPython 2.7. Domyślne środowisko pogrubioną czcionką jest języka Python 3.4, który jest używany dla wszystkich nowych projektów. Jeśli nie widać żadnych środowisk na liście, oznacza to, zostały zainstalowane narzędzia Python Tools for Visual Studio w programie Visual Studio 2015 lub starszym, ale nie zostały zainstalowane interpreter języka Python (zobacz [Zaznaczanie i instalowanie tłumaczy Python](#selecting-and-installing-python-interpreters) powyżej). **+ Niestandardowy...**  polecenie pozwala [utworzyć środowisko dla istniejących interpreter](#create-an-environment-for-an-existing-interpreter).

Po prawej stronie każdego środowiska wymienionych jest formant, który powoduje otwarcie okna interaktywnego dla tego środowiska. Inny formant może pojawić się odświeża IntelliSense bazy danych dla tego środowiska.

Poniżej listy środowisk jest selektora listy rozwijanej dla **omówienie**, **pakiety**, i **IntelliSense** opcje w dalszej części tej sekcji. Po rozwinięciu **środowiska Python** okna dostatecznie szerokie, te opcje są wyświetlane jako kart, które może się okazać bardziej wygodne do pracy z:

![Widok rozszerzony okno środowiska Python](media/environments-expanded-view.png)

> [!Note]
> Mimo że program Visual Studio szanuje opcję pakiety w przypadku lokacji systemu, nie udostępnia sposób, aby zmienić go z poziomu programu Visual Studio.

Wprowadzenie wideo do zarządzania środowiska w programie Visual Studio, zobacz [Zarządzanie środowiska Python](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=qrDmN4LWE_8305918567) (Microsoft Virtual Academy, 2m35s).

> [!VIDEO https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Managing-Python-Environments-qrDmN4LWE_8305918567]

### <a name="creating-an-environment-for-an-existing-interpreter"></a>Tworzenie środowiska dla istniejących interpretera

Jeśli program Visual Studio nie zlokalizować interpreter (na przykład jeśli jest zainstalowana w lokalizacji niestandardowej), można utworzyć i środowisku co następuje:

1. Wybierz **+ niestandardowy...**  w [okno środowiska Python](#managing-python-environments-in-visual-studio), co powoduje utworzenie nowego środowiska i otwiera [ **Konfiguruj** kartę](#configure-tab) opisane poniżej.)

    ![Domyślny widok dla nowego środowiska niestandardowych](media/environments-custom-1.png)

1. Wprowadź nazwę dla środowiska w **opis** pola.
1. Wprowadź lub wyszukaj ścieżkę interpreter w **ścieżki prefiks** pola.
1. Wybierz **Autowykrywanie** mają Visual Studio, wypełnij pozostałe pola lub zakończyć je ręcznie.
1. Wybierz **Zastosuj** można zapisać środowiska.
1. Jeśli musisz usunąć środowisko, wybierz **Usuń** na **Konfiguruj** kartę. Automatycznie wykrytej środowisk nie zawierają tej opcji. Zobacz następną sekcję, aby uzyskać więcej informacji.

### <a name="moving-an-existing-interpreter"></a>Przenoszenie istniejących interpretera

Jeśli przenosisz tłumacza istniejącej do nowej lokalizacji w systemie plików, Visual Studio nie automatycznie wykrywa zmiany i należy ręcznie zaktualizować jego środowiska:

- Jeśli pierwotnie utworzono środowisko dla tego interpreter, należy edytować tego środowiska, aby wskazywał nową lokalizację.

- Jeśli środowisko zostało pierwotnie wykrywane automatycznie, został zainstalowany na komputerze, program Instalator distinct, który utworzył wpisy rejestru, które sprawdza, czy program Visual Studio. W tym przypadku najpierw przywrócić interpreter języka Python do jej oryginalnej lokalizacji. Następnie odinstaluj go za pomocą Instalatora, który usuwa wpisy rejestru. Następnie ponownie zainstalować interpreter w wybranej lokalizacji. Uruchom ponownie program Visual Studio i powinien Autowykrywanie nowej lokalizacji. Daje to pewność, czy inne efekty uboczne Instalatora zostały zastosowane poprawnie.

### <a name="overview-tab"></a>Karta Przegląd

Zawiera podstawowe informacje i poleceń środowiska:

![Karta Przegląd środowiska Python](media/environments-overview-tab.png)

| Polecenie | Opis |
| --- | --- |
| Ustaw jako domyślny dla nowych projektów tego środowiska | Ustawia środowisko active, co może spowodować Visual Studio może chwilę nie odpowiadać podczas ładuje IntelliSense bazy danych. Środowiska z wiele pakietów mogą być nieodpowiadająca przez dłuższy czas. |
| Odwiedź witrynę sieci Web dystrybutora | Otwiera w przeglądarce adres URL udostępniony przez dystrybucję oprogramowania Python. Python 3.x, na przykład przechodzi do python.org. |
| Otwórz okno interaktywne | Otwiera [okna interaktywnego (REPL)](interactive-repl.md) dla tego środowiska w programie Visual Studio stosowania [skrypty uruchamiania (patrz poniżej)](#startup-scripts). |
| Eksploruj interaktywne skryptów | Zobacz [skrypty uruchamiania](#startup-scripts). |
| Tryb interaktywny IPython | Jeśli wartość zostanie otwarte okno interaktywne z IPython domyślnie. Ten wbudowany włączone geograficzne oraz rozszerzona składnia IPython takich jak `name?` Aby wyświetlić Pomoc i `!command` powłoki poleceń. Ta opcja jest zalecana, gdy przy użyciu rozkładu Anaconda, ponieważ wymaga dodatkowych pakietów. Aby uzyskać więcej informacji, zobacz [przy użyciu IPython w oknie interaktywnym](interactive-repl-ipython.md). |
| Otwórz w programie PowerShell | Uruchamia interpretera w oknie poleceń programu PowerShell. |
| (Łącza folder) | Zapewniają szybki dostęp do folderu instalacji w środowisku, python.exe interpreter i pythonw.exe interpreter. Pierwszy otwiera w Eksploratorze Windows, tych dwóch Otwórz okno konsoli. |

#### <a name="startup-scripts"></a>Skrypty uruchamiania

Interakcyjne systemu windows są wykorzystywane w zwykłych przepływu pracy, prawdopodobnie należy utworzyć funkcje pomocnicze, często używane. Może na przykład utworzyć funkcję, która otwiera DataFrame w programie Excel, a następnie zapisz ten kod jako skryptu uruchamiania tak, aby zawsze dostępne w oknie interaktywnym.

Skrypty uruchamiania zawierają kod, który okno interaktywne ładuje i uruchamia się automatycznie, w tym Importy, definicje funkcji i dosłownie inaczej. Te skrypty są przywoływane na dwa sposoby:

1. Po zainstalowaniu środowiska Visual Studio tworzy folder `Documents\Visual Studio 2017\Python Scripts\<environment>` gdzie &lt;środowiska & gt "jest zgodna z nazwą środowiska. Można łatwo przejść do folderu określonego środowiska o **Eksploruj interaktywne skrypty** polecenia. Po uruchomieniu okno interaktywne dla tego środowiska ładuje i działa niezależnie od `.py` znajdują się pliki w tym miejscu w kolejności alfabetycznej.

1. **Skryptów** kontroli w **Narzędzia > Opcje > Narzędzia Python Tools > interakcyjne Windows** kartę (zobacz [Opcje interakcyjne systemu windows](options.md#interactive-windows-options)) należy podać dodatkowe folder służący do uruchamiania skryptów, które są załadowane, a następnie uruchomienie we wszystkich środowiskach. Jednak ta funkcja nie działa w chwili obecnej.

### <a name="configure-tab"></a>Karta Konfigurowanie

Jeśli wyświetlane, zawiera szczegółowe informacje, zgodnie z opisem w poniższej tabeli. Jeśli na tej karcie nie jest obecny, oznacza to, czy program Visual Studio automatycznie zarządza wszystkie szczegóły.

![Karta Konfigurowanie środowiska Python](media/environments-configure-tab.png)

| Pole | Opis |
| --- | --- |
| **Opis** | Nazwa umożliwiają środowiska. |
| **Ścieżka prefiksu** | Lokalizacja folderu podstawowego interpretera. Wypełnianie tej wartości, a następnie klikając polecenie **Autowykrywanie**, Visual Studio podejmuje próbę wypełnienia w pozostałych polach dla Ciebie. |
| **Ścieżka interpretera** | Ścieżka do pliku wykonywalnego interpreter często ścieżki prefiks następuje`python.exe` |
| **Okna interpretera** | Ścieżka do konsoli bez pliku wykonywalnego, często następuje ścieżki prefiks `pythonw.exe`. |
| **Ścieżka biblioteki** | Określa katalog główny biblioteki standardowe, ale tę wartość można zignorować, jeśli Visual Studio jest w stanie uzyskać dokładniejsze ścieżki od interpretera. |
| **Wersja językowa** | Wybrany z listy rozwijanej. |
| **Architektura** | Zwykle wykrywane i automatycznie wypełniane, w przeciwnym razie określa 32-bitowy lub 64-bitowej. |
| **Zmienna środowiskowa PATH** | Zmiennej środowiskowej, która używa interpretera można znaleźć ścieżki wyszukiwania. Visual Studio zmienia wartość zmiennej podczas uruchamiania Python, tak aby zawierała ścieżek wyszukiwania projektu. Zwykle ta właściwość powinna być równa `PYTHONPATH`, ale niektóre tłumaczy Użyj innej wartości. |

### <a name="pip-tab"></a>Karta PIP

Zarządza pakiety zainstalowane w środowisku, co umożliwia również wyszukiwanie i instalowanie nowych (w tym wszelkie zależności). Wyszukiwanie filtry obecnie zainstalowanych pakietów i [PyPI](https://pypi.python.org). Można również bezpośrednio wprowadzić dowolne `pip install` polecenie w polu wyszukiwania, takie jak tym flagi `--user` lub `--no-deps`.

![Karta pip środowiska Python](media/environments-pip-tab.png)

Instalowanie pakietu tworzy oddzielne podfoldery w środowisku `Lib` folder w systemie plików. Na przykład, jeśli masz zainstalowany 3,6 Python w `c:\Python36`, pakiety są instalowane w `c:\Python36\Lib`; Jeśli masz zainstalowany w Anaconda3 `c:\Program Files\Anaconda3` , a następnie pakiety są instalowane w `c:\Program Files\Anaconda3\Lib`.

W tym ostatnim przypadku ponieważ środowisko znajduje się w obszarze chronionym systemu plików `c:\Program Files`, należy uruchomić program Visual Studio `pip install` z podniesionymi uprawnieniami, aby zezwolić na tworzenie podfolderów pakietu. Gdy wymagana jest podniesienia uprawnień, Visual Studio wyświetla monit "Aby zainstalować, zaktualizować lub usunąć pakiety dla tego środowiska może być wymagane uprawnienia administratora":

![Wiersz podniesienia uprawnień do instalacji pakietu aktualizacji](media/environments-pip-elevate.png)

**Podniesienie poziomu teraz** przyznaje uprawnienia administracyjne do narzędzia pip pojedyncza, podmiotu również do dowolnego systemu operacyjnego wyświetla monit o uprawnienia. Wybieranie **Kontynuuj bez uprawnień administratora** próby instalacji pakietu, ale narzędzie pip kończy się niepowodzeniem podczas próby utworzenia folderów z danych wyjściowych, takich jak "Błąd: nie można utworzyć" C:\Program Files\Anaconda3\Lib\site-packages\ PNG.PY': odmowa uprawnień. "

Wybieranie **zawsze podniesienia uprawnień podczas instalowania lub usuwania pakietów** zapobiega wyświetlaniu środowiska okna dialogowego. Aby ponownie wyświetlone okno dialogowe, przejdź do **Narzędzia > Opcje > Narzędzia Python Tools > Ogólne** i kliknij przycisk **zresetować wszystkie okna dialogowe trwale ukryty**.

W tym takie same opcje karcie, możesz również wybrać **pip są zawsze uruchamiane jako administrator** do pomijania okna dialogowego dla wszystkich środowisk. Zobacz [opcje — karta Ogólne](options.md#general-options).

### <a name="intellisense-tab"></a>Karta IntelliSense

Wskazuje bieżący stan bazy danych uzupełniania IntelliSense:

![Karta IntelliSense środowiska Python](media/environments-intellisense-tab.png)

Baza danych zawiera metadanych dla biblioteki wszystkie środowiska i przyspiesza IntelliSense i zmniejsza zużycie pamięci. Gdy program Visual Studio wykryje nowego środowiska (lub dodaj je), automatyczne rozpoczęcie do skompilowania bazy danych, analizując biblioteki plików źródłowych. Ten proces może potrwać od minutę na godzinę lub dłużej w zależności od tego, co jest zainstalowany. (Anaconda, na przykład zawiera wiele bibliotek i dopiero po pewnym czasie, aby skompilować bazy danych) Po wykonaniu tych czynności możesz uzyskać szczegółowe IntelliSense i nie trzeba ponownie Odśwież bazy danych (z **Odśwież DB** przycisk) aż do zainstalowania więcej bibliotek.

Biblioteki, dla których nie zostały skompilowane danych są oznaczone ikoną z **!**; Jeśli środowisko bazy danych nie jest zakończone, **!** jest także wyświetlany obok niej na liście głównego środowiska.

## <a name="selecting-an-environment-for-a-project"></a>Wybierając środowisko dla projektu

Środowisk specyficznego dla projektu upewnij się, czy projekt jest zawsze uruchamiany w środowisku ignorowanie domyślnego środowiska globalnego. Na przykład jeśli globalne domyślnego środowiska jest języka CPython, ale projekt wymaga IronPython i niektórych bibliotek, które nie są zainstalowane w globalnej środowiska, następnie środowisku specyficznego dla projektu jest konieczne.

Projekt środowiska są wyświetlane w Eksploratorze rozwiązań w węźle środowiska Python. Bold wpis jest aktywna i Visual Studio korzysta z niego do debugowania, importowanie i zakończeń — członek, sprawdzanie składni i innych zadań, które wymagają środowiska:

![Projekt środowiskach, wyświetlany w Eksploratorze rozwiązań](media/environments-project.png)

Aby aktywować innego środowiska dla projektu, kliknij prawym przyciskiem myszy tego środowiska i wybierz **aktywacji środowiska**.

Wszelkie globalne środowiska może zostać dodana jako środowisku projektu, klikając prawym przyciskiem myszy **środowiska Python** i wybierając **środowiska Python Dodaj lub Usuń...** . Na wyświetlonej liście można wybrać, lub Anuluj wybór tych środowisk, w których są dostępne w projekcie.

![Okno dialogowe Dodawanie/usuwanie środowiska Python](media/environments-add-remove.png)

W Eksploratorze rozwiązań można również rozwinąć środowiska, aby wyświetlić jego zainstalowanych pakietów (te mogą być importowane i używane w kodzie, gdy środowisko jest aktywny):

![Pakiety języka Python dla środowiska w Eksploratorze rozwiązań](media/environments-installed-packages.png)

Aby zainstalować nowe pakiety, kliknij prawym przyciskiem myszy środowisko, wybierz **zainstaluj pakiet języka Python...** i wprowadź nazwę żądanego pakietu. Pakiety (i zależności) zostaną pobrane z [indeksu pakietów języka Python (PyPI)](https://pypi.python.org/pypi), gdzie można także przeszukać dostępnych pakietów. Pasek stanu programu Visual Studio i dane wyjściowe okna przedstawia informacje o instalacji. Aby odinstalować pakiet, kliknij prawym przyciskiem wybierz **Usuń**.

> [!Note]
> Obsługa zarządzania pakiet języka Python jest obecnie opracowywane przez zespół deweloperów języka Python core. Wyświetlane wpisy nie zawsze są dokładne i instalowaniem i odinstalowywaniem nie może być niezawodne lub są dostępne. Visual Studio korzysta z Menedżera pakietów pip, jeśli jest dostępny i pobiera i instaluje je w razie potrzeby. Program Visual Studio umożliwia także easy_install Menedżera pakietów. Wyświetlana jest również pakiety zainstalowane przy użyciu narzędzia pip lub easy_install z wiersza polecenia.

> [!Tip]
> Typowe sytuacji, gdy pip nie można zainstalować pakietu to pakietu zawierającego kod źródłowy dla natywnych składników w `*.pyd` plików. Bez wymagana wersja programu Visual Studio pip nie można skompilować tych składników. Komunikat o błędzie wyświetlany w tej sytuacji `error: Unable to find vcvarsall.bat`. `easy_install`często jest w stanie pobrać wstępnie skompilowanych plików binarnych, możesz również pobrać odpowiedni kompilatora dla starszych wersji języka Python z [http://aka.ms/VCPython27](http://aka.ms/VCPython27). Aby uzyskać więcej informacji, zobacz [jak rozwiązać problemy z "nie można odnaleźć vcvarsallbat"](https://blogs.msdn.microsoft.com/pythonengineering/2016/04/11/unable-to-find-vcvarsall-bat/) na Python tools blogu zespołu.

## <a name="creating-virtual-environments"></a>Tworzenie środowisk wirtualnych

1. Kliknij prawym przyciskiem myszy **środowiska Python** w Eksploratorze rozwiązań i wybierz **Dodawanie środowiska wirtualnego...** , co spowoduje uruchomienie następujących czynności:

    ![Tworzenie środowiska wirtualnego](media/environments-add-virtual-1.png)

1. Określ nazwę, aby utworzyć środowisko wirtualne w ścieżce projektu lub pełną ścieżkę do utworzenia go w innym miejscu. (Aby zapewnić maksymalne zgodność przy użyciu innych narzędzi, użyć tylko liter i cyfr w nazwie).

1. Wybierz jako podstawowy interpreter środowisku globalne, a następnie kliknij przycisk **Utwórz**. Jeśli `pip` i `virtualenv` lub `venv` pakiety nie są dostępne, pobierania i instalowania.

    Jeśli ścieżka prowadzi do istniejącego środowiska wirtualnego, wykryto interpreter podstawowy i przycisk Utwórz zmienia się na **Dodaj**:

    ![Dodawanie istniejącego środowiska wirtualnego](media/environments-add-virtual-2.png)

Istniejącego środowiska wirtualnego można również dodać, klikając prawym przyciskiem myszy **środowiska Python** w Eksploratorze rozwiązań i wybierając **Dodawanie istniejącego środowiska wirtualnego...** . Visual Studio automatycznie wykrywa interpreter podstawowy przy użyciu `orig-prefix.txt` plików w środowisku `lib` katalogu.

Gdy środowisko wirtualne zostanie dodany do projektu, zostanie wyświetlony w **środowiska Python** okna, możesz to zrobić podobnie jak inne środowiska i można zarządzać jej pakietów. Prawym przyciskiem myszy i wybierając **Usuń** Usuwa odwołanie do środowiska albo usuwa środowiska i wszystkie jego pliki na dysku (ale nie interpreter podstawowy).

Należy pamiętać, że wadą do środowisk wirtualnych jest że ustalony plikowym i w związku z tym nie można łatwo można udostępnione lub do innych komputerów programowanie. Na szczęście, można użyć `requirements.txt` plików zgodnie z opisem w następnej sekcji, aby umożliwić adresatów projektu, aby łatwo przywrócić środowiska.

## <a name="managing-required-packages-requirementstxt"></a>Zarządzanie wymaganych pakietów (requirements.txt)

Współużytkuje projektem, przy użyciu systemu kompilacji, czy jest planowane [opublikowania go w usłudze Microsoft Azure](template-azure-cloud-service.md), należy określić pakiety zewnętrzne, które wymaga projektu. Zalecanym rozwiązaniem jest użycie [pliku requirements.txt](http://pip.readthedocs.org/en/latest/user_guide.html#requirements-files) (readthedocs.org) zawierający listę poleceń dla narzędzia pip, który instaluje wymagane wersje pakietów zależnych.

Z technicznego punktu widzenia nazwy pliku może służyć do śledzenia wymagania (przy użyciu `-r <full path to file>` podczas instalowania pakietu), ale Visual Studio zapewnia obsługę określonych `requirements.txt`:

- Jeśli został załadowany projekt, który zawiera `requirements.txt` i chcesz, aby zainstalować te pakiety wymienione w tym pliku, rozwiń węzeł **środowiska Python** w węźle **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy a następnie wybierz węzeł środowiska **Zainstaluj z pliku requirements.txt**:

    ![Zainstaluj z pliku requirements.txt](media/environments-requirements-txt-install.png)

- Jeśli masz już wszystkie niezbędne pakiety zainstalowane w projekcie, należy kliknąć prawym przyciskiem myszy środowisko, w Eksploratorze rozwiązań i wybrać **Generuj plik requirements.txt** można utworzyć niezbędnego pliku. Jeśli plik już istnieje, zostanie wyświetlony monit o jak go zaktualizować:

    ![Opcje pliku requirements.txt aktualizacji](media/environments-requirements-txt-replace.png)

  - **Zastąp cały plik** usuwa wszystkie elementy, komentarze i opcje, które istnieją.
  - **Odśwież istniejących** wykrywa wymagań dotyczących pakietu i aktualizuje specyfikatory wersji, aby dopasować aktualnie zainstalowaną wersję.
  - **Aktualizowanie i dodawanie wpisów** odświeża wszelkie wymagania, które zostały znalezione i dodaje wszystkie inne pakiety na końcu pliku.

Ponieważ `requirements.txt` pliki mają zawiesza wymagania dotyczące projektu, wszystkie zainstalowane pakiety są zapisywane z użyciem wersji dokładne. Użycie wersji dokładne gwarantuje, że można łatwo odtworzyć środowiska na innym komputerze. Pakiety są dołączane, nawet jeśli zostały one zainstalowane z zakresem wersji, jako zależność inny pakiet, lub z Instalatorem niż pip.

Jeśli `requirements.txt` plik istnieje podczas dodawania nowego środowiska wirtualnego **Dodawanie środowiska wirtualnego** Wyświetla okno dialogowe opcję pakiety są instalowane automatycznie, dzięki czemu można łatwo odtworzyć w środowisku na innym komputerze:

![Tworzenie środowiska wirtualnego z pliku requirements.txt](media/environments-requirements-txt.png)

Jeśli nie można zainstalować pakietu przez narzędzie pip, ale pojawia się `requirements.txt` niepowodzenia instalacji całego pliku. W takim przypadku ręcznie edytować plik, aby wykluczyć ten pakiet lub użyć [opcje przez narzędzie pip](http://pip.readthedocs.org/en/latest/reference/pip_install.html#requirements-file-format) do odwoływania się do zainstalowania wersji pakietu. Na przykład użytkownik może chcieć użyć [ `pip wheel` ](http://pip.readthedocs.org/en/latest/reference/pip_wheel.html) skompilować zależności, a następnie dodaj `--find-links <path>` opcji do Twojej `requirements.txt`:

```output
C:\Project>pip wheel azure
Downloading/unpacking azure
    Running setup.py (path:C:\Project\env\build\azure\setup.py) egg_info for package azure

Building wheels for collected packages: azure
    Running setup.py bdist_wheel for azure
    Destination directory: c:\project\wheelhouse
Successfully built azure
Cleaning up...

C:\Project>type requirements.txt
--find-links wheelhouse
--no-index
azure==0.8.0

C:\Project>pip install -r requirements.txt -v
Downloading/unpacking azure==0.8.0 (from -r requirements.txt (line 3))
    Local files found: C:/Project/wheelhouse/azure-0.8.0-py3-none-any.whl
Installing collected packages: azure
Successfully installed azure
Cleaning up...
    Removing temporary dir C:\Project\env\build...
```

## <a name="search-paths"></a>Ścieżki wyszukiwania

Typowy Usage Python `PYTHONPATH` zmiennej środowiskowej (lub `IRONPYTHONPATH`, itd.) zapewnia domyślnej ścieżki wyszukiwania plików modułu. Oznacza to, że jeśli używasz `from <name> import...` lub `import <name>` instrukcji, Python wyszukuje następujące lokalizacje w kolejności zgodnej nazwie:

1. Wbudowane moduły języka Python.
1. Folder zawierający kod języka Python, który jest uruchomiony.
1. "Moduł ścieżki wyszukiwania" jako zdefiniowanej przez zmienną środowiskową zastosowania. (Zobacz [ścieżki wyszukiwania modułu](https://docs.python.org/2/tutorial/modules.html#the-module-search-path) i [zmiennych środowiskowych](https://docs.python.org/2/using/cmdline.html#envvar-PYTHONPATH) w podstawowej dokumentacji języka Python.)

Visual Studio ignoruje zmiennej środowiskowej ścieżki wyszukiwania, jednak nawet wtedy, gdy zmienna jest ustawiana dla całego systemu. Jest on ignorowany, w rzeczywistości, dokładnie *ponieważ* ustawiono dla całego systemu i w związku z tym zgłasza niektóre kwestie, które nie mogą być odbierane automatycznie: moduły do którego istnieje odwołanie, przeznaczone dla języka Python 2.7 lub Python 3.3? Są one będą zastąpienie modułów standardowa biblioteka? Zna dewelopera tego zachowania, czy jest próba złośliwego przejęcie kontroli?

Program Visual Studio udostępnia w związku z tym określenie ścieżki wyszukiwania bezpośrednio w środowiskach i projektów. Kod, który uruchamiania lub debugowania w programie Visual Studio odbiera ścieżki wyszukiwania w wartości `PYTHONPATH` (i inne zmienne równoważne). Dodając ścieżki wyszukiwania, Visual Studio przeprowadzający bibliotek w tych lokalizacjach i kompilacje baz danych IntelliSense dla nich (utworzenie bazy danych może zająć trochę czasu w zależności od liczby bibliotek).

Aby dodać ścieżkę wyszukiwania, kliknij prawym przyciskiem myszy **ścieżki wyszukiwania** elementu w Eksploratorze rozwiązań wybierz **Dodaj Folder do ścieżki wyszukiwania...** i wybierz folder do dołączenia. Ta ścieżka jest używana w każdym środowisku skojarzony z projektem. (Mogą zostać wyświetlone błędy Jeśli środowisko jest oparta na Python 3 i użytkownik podejmie próbę dodania ścieżki wyszukiwania w modułach Python 2.7.)

Pliki z `.zip` lub `.egg` rozszerzenia również mogą być dodawane jako ścieżki wyszukiwania, wybierając **dodać archiwum Zip do ścieżki wyszukiwania...** . Podobnie jak w przypadku folderów, zawartość te pliki są skanowane i udostępnione IntelliSense.

Jeśli zawartość nie należy zmieniać często są regularnie przy użyciu tej samej ścieżki wyszukiwania, może być bardziej wydajne, aby zainstalować go do folderu pakietów lokacji. Ścieżki wyszukiwania następnie są analizowane i przechowywane w bazie danych IntelliSense, jest zawsze być skojarzony z danego środowiska i nie wymaga ścieżkę wyszukiwania do dodania do każdego projektu.
