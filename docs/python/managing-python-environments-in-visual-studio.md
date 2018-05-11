---
title: Zarządzanie środowiska Python i tłumaczy
description: Użyj okno środowiska Python, aby zarządzać globalnych, wirtualne i środowisk conda, zainstalować tłumaczy Python i pakietów i przypisywanie środowisk do projektów programu Visual Studio.
ms.date: 05/07/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 1ba3902fde77e297148c2006f89dd61bca1e902b
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2018
---
# <a name="how-to-create-and-manage-python-environments-in-visual-studio"></a>Jak utworzyć i zarządzać środowiska Python w programie Visual Studio

Python *środowiska* jest kontekst, w którym można uruchomić kod języka Python i zawiera globalny, wirtualne i środowisk conda. Środowisko składa się z tłumacza, biblioteki (zazwyczaj Python standardowa biblioteka) i zestaw zainstalowanych pakietów. Te składniki wspólnie określają, które konstrukcji języka i składni są prawidłowe, jakiego systemu operacyjnego funkcje są dostępne, a które pakietów, należy użyć.

W programie Visual Studio w systemie Windows [okno środowiska Python](#the-python-environments-window) okno, zgodnie z opisem w tym artykule jest gdzie zarządzać tych środowisk i wybierz jedno jako domyślne dla nowych projektów. Dla żadnego danego projektu można również wybierz określone środowisko, zamiast Użyj wartości domyślnej.

**Uwaga**: Jeśli jesteś nowym użytkownikiem Python w programie Visual Studio, zobacz następujące artykuły w tle konieczne:

- [Praca z języka Python w programie Visual Studio](overview-of-python-tools-for-visual-studio.md)
- [Instalowanie obsługi języka Python w programie Visual Studio](installing-python-support-in-visual-studio.md)

Ponadto Uwaga nie może zarządzać środowiska Python kodu, który jest otwierać tylko w folderze przy użyciu **pliku** > **Otwórz** > **folderu** polecenie. Zamiast tego [utworzenia projektu języka Python z istniejącego kodu](quickstart-01-python-in-visual-studio-project-from-existing-code.md) korzystać z funkcji środowiska Visual Studio.

Jeśli chcesz zainstalować pakiety w środowisku, można skorzystać z [kartę pakiety](python-environments-window-tab-reference.md#packages-tab).

## <a name="types-of-environments"></a>Typy środowisk

### <a name="global-environments"></a>Globalne środowisk

Każdej instalacji języka Python (na przykład, Python 2.7, 3,6 Python, Anaconda 4.4.0 itp., zobacz [zaznaczenie i instalowanie tłumaczy Python](installing-python-interpreters.md)) zachowuje własną globalnego środowiska. Każde środowisko składa się z określonym interpreter języka Python, jego biblioteki standardowej i zestaw wstępnie zainstalowane pakiety. Instalowanie pakietu do globalnego środowiska udostępnia je do wszystkich projektów przy użyciu tego środowiska. Jeśli środowisko znajduje się w obszarze ochrona systemu plików (w ramach `c:\program files`, na przykład), a następnie instalowanie pakietów wymaga uprawnień administratora.

Globalne środowiska są dostępne dla wszystkich projektów na komputerze. W programie Visual Studio wybierz opcję jedną globalnego środowiska jako domyślny, który jest używany we wszystkich projektach, jeśli nie możesz wybrać inną nazwę dla projektu. Aby uzyskać więcej informacji, zobacz [wybierając środowisko dla projektu](selecting-a-python-environment-for-a-project.md).

### <a name="virtual-environments"></a>Środowiska wirtualne

Pakiety zainstalowane w środowisku globalne nie są dostępne dla wszystkich projektów, które używają tego środowiska, gdy dwa projekty wymagają niezgodnych pakietów lub różne wersje tego samego pakietu może wystąpić konflikty. Środowiska wirtualne uniknąć takie konflikty przy użyciu interpreter i standardowej biblioteki z globalnego środowiska, ale obsługa własnych magazynów pakietu w folderach izolowanego.

W programie Visual Studio można utworzyć środowisko wirtualne dla konkretnego projektu, który jest przechowywany w podfolderze w projekcie. Program Visual Studio udostępnia polecenie, aby wygenerować `requirements.txt` plików ze środowiska wirtualnego, dzięki czemu można łatwo odtworzyć w środowisku na innych komputerach. Aby uzyskać więcej informacji, zobacz [za pomocą środowisk wirtualnych](selecting-a-python-environment-for-a-project.md#using-virtual-environments).

### <a name="conda-environments"></a>Conda środowisk

Środowisko conda jest utworzony przy użyciu `conda` narzędzia, lub za pomocą zintegrowanego conda zarządzania w programie Visual Studio 2017 wersji 15.7 lub nowszej. (Wymaga Anaconda lub Miniconda; Anaconda jest dostępna za pośrednictwem Instalator programu Visual Studio, zobacz [instalacji — Visual Studio 2017](installing-python-support-in-visual-studio.md#visual-studio-2017).)

> [!Note]
> Aby uzyskać najlepsze wyniki w środowiskach conda, użyj conda 4.4.8 lub nowszym (conda wersje różnią się od wersji Anaconda). Instalowanie Anaconda 5.1 Instalatora programu Visual Studio 2017 r.

Aby wyświetlić wersji conda, gdzie są przechowywane środowisk conda, oraz inne informacje, uruchom `conda info` Anaconda z wiersza polecenia (czyli wiersz polecenia gdzie Anaconda znajduje się w ścieżce):

```bash
conda info
```
Możesz conda środowiska foldery są wyświetlane w następujący sposób:

```output
       envs directories : c:\anaconda3\envs
                          C:\Users\user\AppData\Local\conda\conda\envs
                          C:\Users\user\.conda\envs
```

Ponieważ środowisk conda nie są przechowywane z projektem, działają podobnie do globalnego środowisk. Na przykład instalowanie nowego pakietu do środowiska conda udostępnia tego pakietu do wszystkich projektów przy użyciu tego środowiska.

Dla programu Visual Studio 2017 wersji 15.6 lub starszej, można użyć środowiska conda wskazując je ręcznie, zgodnie z opisem w [ręcznie Zidentyfikuj istniejącego środowiska](#manually-identify-an-existing-environment).

Visual Studio 2017 wersji 15.7 i nowszych automatycznie wykrywa środowisk conda i wyświetla je w **środowiska Python** okna zgodnie z opisem w następnej sekcji.

## <a name="the-python-environments-window"></a>Okno środowiska Python

Środowiska, w których zna Visual Studio są wyświetlane w **środowiska Python** okna. Aby otworzyć okno, użyj jednej z następujących metod:

- Wybierz **widoku** > **inne okna** > **środowiska Python** polecenia menu.
- Kliknij prawym przyciskiem myszy **środowiska Python** węzła projektu w Eksploratorze rozwiązań i wybierz **widok wszystkich środowisk języka Python**:

    ![Widok wszystkich środowisk polecenia w Eksploratorze rozwiązań](media/environments-view-all.png)

W obu przypadkach **środowiska Python** okno jako element równorzędny karty do Eksploratora rozwiązań:

![Okno środowiska Python](media/environments-default-view.png)

Domyślne środowisko pogrubioną czcionką jest 3,6 Python, używający dla wszystkich nowych projektów programu Visual Studio. Środowisku wymienionych dowolnego typu, może służyć jako domyślny.

Polecenia w dolnej części okna dotyczą interpretera wybrane, jak widać to instalacja określonych w `C:\Python36-32` (część instalacji Anaconda jest pogrubiony domyślnego środowiska). Jeśli nie widzisz środowisku spodziewasz się, zobacz [ręcznie Zidentyfikuj istniejącego środowiska](#manually-identify-an-existing-environment).

Po prawej stronie każdego środowiska wymienionych jest formant, który powoduje otwarcie okna interaktywnego dla tego środowiska. (W programie Visual Studio 2017 w 15,5 cala i starszych inny formant się, że odświeża IntelliSense bazy danych dla tego środowiska. Zobacz [odwołania okno środowiska](python-environments-window-tab-reference.md#intellisense-tab) szczegółowe informacje o bazie danych).

Poniżej listy środowisk jest selektora listy rozwijanej dla **omówienie**, **pakiety**, i **IntelliSense** opcje opisane w [środowiska Python okno karty](python-environments-window-tab-reference.md). Ponadto po rozwinięciu **środowiska Python** okna dostatecznie szerokie, te opcje są wyświetlane jako kart, które może się okazać bardziej wygodne do pracy z:

![Widok rozszerzony okno środowiska Python](media/environments-expanded-view.png)

Na powyższej ilustracji widać pełną listę środowisk na tym komputerze określonego, wraz z dodatkowych poleceń, aby utworzyć środowiska.

> [!Note]
> Mimo że program Visual Studio szanuje opcję pakiety w przypadku lokacji systemu, nie udostępnia sposób, aby zmienić go z poziomu programu Visual Studio.

|   |   |
|---|---|
| ![Ikona aparatu film wideo](../install/media/video-icon.png "obejrzeć film wideo") | [Obejrzyj film (Microsoft Virtual Academy)](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=qrDmN4LWE_8305918567) na środowiska Python w programie Visual Studio (2 m 35s).|

### <a name="what-if-no-environments-appear"></a>Co zrobić, jeśli są widoczne nie środowiska?

Są wyświetlane nie środowisk, oznacza, że nie można wykryć wszystkie instalacje Python w standardowe lokalizacje programu Visual Studio. Na przykład użytkownik może mają zainstalowaną 2017 usługi Visual Studio, ale wyczyszczone wszystkie opcje interpreter w opcjach Instalatora dla obciążenia Python. Podobnie, został zainstalowany program Visual Studio 2015 lub starszym, ale nie został zainstalowany interpreter ręcznie (zobacz [tłumaczy instalowanie Python](installing-python-interpreters.md)).

Jeśli znasz interpreter języka Python jest zainstalowana na komputerze, ale Visual Studio (dowolna wersja) nie wykryje go, a następnie użyj **+ niestandardowy...**  polecenie, aby ręcznie określić jego lokalizacji. Zobacz następną sekcję [ręcznie Zidentyfikuj istniejącego środowiska](#manually-identify-an-existing-environment).

> [!Tip]
> Visual Studio wykrywa aktualizacje do istniejących interpretera, takich jak uaktualnianie Python 2.7.11 do 2.7.14 przy użyciu instalatorów od python.org. W procesie instalacji środowiska starsze zniknie z **środowiska Python** listy aktualizacji pojawia się w jego miejscu.
>
> Jednak jeśli ręcznie przenieść interpreter i jego środowiska przy użyciu systemu plików programu Visual Studio będą wiedzieć, nowej lokalizacji. Aby uzyskać więcej informacji, zobacz [przenoszenie interpreter](installing-python-interpreters.md#moving-an-interpreter).

< name = "ręcznie identyfikowanie — moduł istniejących środowiska ></a>

## <a name="manually-identify-an-existing-environment"></a>Ręcznie Zidentyfikuj istniejącego środowiska

Wykonaj następujące kroki, aby zidentyfikować środowisku, w którym jest zainstalowany w lokalizacji niestandardowej (również w środowiskach conda w Visual Studio 2017 wersji 15.6 i starszych):

1. Wybierz **+ niestandardowe** w **środowiska Python** okna, które umożliwia otwarcie **Konfiguruj** karty:

    ![Domyślny widok dla nowego środowiska niestandardowych](media/environments-custom-1.png)

1. Wprowadź nazwę dla środowiska w **opis** pola.

1. Wpisz lub Przeglądaj (przy użyciu **... ***) do ścieżki interpreter w **ścieżki prefiks** pola.

1. Jeśli program Visual Studio wykryje interpreter języka Python w tej lokalizacji (takie jak ścieżka dla środowiska conda), umożliwia **Autowykrywanie** polecenia. Wybieranie **Autowykrywanie* zakończeniu pozostałe pola. Można również ręcznie wykonać tych pól.

    ![Włączanie polecenia Autowykrywanie](media/environments-custom-2.png)

    ![Uzupełnianie pola środowiska po użyciu Autowykrywanie](media/environments-custom-3.png)

1. Gdy pola zawierają wartości, które mają, wybierz **Zastosuj** Aby zapisać konfigurację. Można teraz używać środowiska jak każdy inny w programie Visual Studio.

1. Jeśli trzeba usunąć ręcznie zidentyfikowanych środowiska, wybierz **Usuń** na **Konfiguruj** kartę. Automatycznie wykrytej środowisk nie zawierają tej opcji. Aby uzyskać więcej informacji, zobacz [kartę Konfiguracja](python-environments-window-tab-reference.md#configure-tab).

## <a name="create-a-conda-environment"></a>Utwórz środowisko conda

*Visual Studio 2017 wersji 15.7 i nowszych.*

1. Wybierz **+ Utwórz środowisko conda** w **środowiska Python** okna, które umożliwia otwarcie **Tworzenie nowego środowiska conda** karty:

    ![Utwórz kartę dla nowego środowiska conda](media/environments-conda-1.png)

1. Wprowadź nazwę dla środowiska w **nazwa** Wybierz podstawowy interpreter języka Python w **Python** pola i wybierz pozycję **Utwórz**.

1. **Dane wyjściowe** okna pokazywania postępu dla nowego środowiska z kilku instrukcjami interfejsu wiersza polecenia po zakończeniu tworzenia:

    ![Pomyślnym utworzeniu środowiska conda](media/environments-conda-2.png)

1. W programie Visual Studio może aktywować środowisku conda dla projektu, tak jak inne środowisko zgodnie z opisem na [wybierając środowisko dla projektu](selecting-a-python-environment-for-a-project.md).

1. Aby zainstalować pakiety w środowisku, należy użyć [kartę pakiety](python-environments-window-tab-reference.md#packages-tab).

## <a name="see-also"></a>Zobacz także

- [Instalowanie tłumaczy Python](installing-python-interpreters.md)
- [Wybierz interpreter dla projektu](selecting-a-python-environment-for-a-project.md)
- [Używanie pliku requirements.txt dla zależności](managing-required-packages-with-requirements-txt.md)
- [Ścieżki wyszukiwania](search-paths.md)
- [Odwołanie do okna środowiska Python](python-environments-window-tab-reference.md)