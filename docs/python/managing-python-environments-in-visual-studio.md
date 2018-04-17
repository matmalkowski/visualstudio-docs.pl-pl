---
title: Jak zarządzać środowiska Python i tłumaczy
description: Jak używać okno środowiska Python w Visual Studio, aby zarządzać globalne i środowisk wirtualnych, konfigurowanie niestandardowych środowisk, instalowania tłumaczy Python, instalowanie pakietów, ustawianie ścieżki wyszukiwania i zarządzania środowiskami dla projektów programu Visual Studio.
ms.custom: ''
ms.date: 03/21/2018
ms.technology:
- devlang-python
ms.devlang: python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 1bff11b34f6f9a6a469230f30c636e65ab143e30
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="managing-python-environments-in-visual-studio"></a>Zarządzanie środowiska Python w programie Visual Studio

Python *środowiska* jest kontekst, w którym można uruchomić kod języka Python i zawiera globalny, wirtualne i środowisk conda. Środowisko składa się z tłumacza, biblioteki (zazwyczaj Python standardowa biblioteka) i zestaw zainstalowanych pakietów. Te składniki wspólnie określają, które konstrukcji języka i składni są prawidłowe, jakiego systemu operacyjnego funkcje są dostępne, a które pakietów, należy użyć.

W programie Visual Studio w systemie Windows [środowiska Python](#managing-python-environments-in-visual-studio) okno, zgodnie z opisem w tym artykule jest gdzie zarządzać tych środowisk i wybierz jedno jako domyślne dla nowych projektów. Dla żadnego danego projektu można również wybierz określone środowisko, zamiast Użyj wartości domyślnej.

**Uwaga**: Jeśli jesteś nowym użytkownikiem Python w programie Visual Studio, zobacz następujące artykuły w tle konieczne:

- [Praca z języka Python w programie Visual Studio](overview-of-python-tools-for-visual-studio.md)
- [Instalowanie obsługi języka Python w programie Visual Studio](installing-python-support-in-visual-studio.md)

Również uwaga nie może zarządzać środowiska Python kodu, który jest otwierane tylko w folderze przy użyciu **Plik > Otwórz > folderu** polecenia. Zamiast tego [utworzenia projektu języka Python z istniejącego kodu](quickstart-01-python-in-visual-studio-project-from-existing-code.md) korzystać z funkcji środowiska Visual Studio.

Jeśli chcesz zainstalować pakiety w środowisku, można skorzystać z [kartę pakiety](python-environments-window-tab-reference.md#packages-tab).

## <a name="types-of-environments"></a>Typy środowisk

### <a name="global-environments"></a>Globalne środowisk

Każdej instalacji języka Python (na przykład, Python 2.7, 3,6 Python, Anaconda 4.4.0 itp., zobacz [zaznaczenie i instalowanie tłumaczy Python](installing-python-interpreters.md)) zachowuje własną globalnego środowiska. Każde środowisko składa się z określonym interpreter języka Python, jego biblioteki standardowej i zestaw wstępnie zainstalowane pakiety. Instalowanie pakietu do globalnego środowiska udostępnia je do wszystkich projektów przy użyciu tego środowiska. Jeśli środowisko znajduje się w obszarze ochrona systemu plików (w ramach `c:\program files`, na przykład), a następnie instalowanie pakietów wymaga uprawnień administratora.

Globalne środowiska są dostępne dla wszystkich projektów na komputerze. W programie Visual Studio wybierz opcję jedną globalnego środowiska jako domyślny, który jest używany we wszystkich projektach, jeśli nie możesz wybrać inną nazwę dla projektu. Aby uzyskać więcej informacji, zobacz [wybierając środowisko dla projektu](selecting-a-python-environment-for-a-project.md).

### <a name="virtual-environments"></a>Środowiska wirtualne

Pakiety zainstalowane w środowisku globalne nie są dostępne dla wszystkich projektów, które używają tego środowiska, gdy dwa projekty wymagają niezgodnych pakietów lub różne wersje tego samego pakietu może wystąpić konflikty. Środowiska wirtualne uniknąć takie konflikty przy użyciu interpreter i standardowej biblioteki z globalnego środowiska, ale obsługa własnych magazynów pakietu w folderach izolowanego.

W programie Visual Studio można utworzyć środowisko wirtualne dla konkretnego projektu, który jest przechowywany w podfolderze w projekcie. Program Visual Studio udostępnia polecenie, aby wygenerować `requirements.txt` plików ze środowiska wirtualnego, dzięki czemu można łatwo odtworzyć w środowisku na innych komputerach. Aby uzyskać więcej informacji, zobacz [za pomocą środowisk wirtualnych](selecting-a-python-environment-for-a-project.md#using-virtual-environments).

### <a name="conda-environments"></a>Conda środowisk

Środowisko conda jest utworzony przy użyciu `conda` narzędzia. Środowisk Conda zwykle są przechowywane w `envs` folderu w ramach instalacji Anaconda, a w związku z tym act środowisk podobnie do globalnego. Na przykład instalowanie nowego pakietu do środowiska conda udostępnia tego pakietu do wszystkich projektów przy użyciu tego środowiska.

Visual Studio, obecnie automatycznie wykrywa środowisk conda, ale możesz wskazać Visual Studio go ręcznie. Zobacz [ręczne identyfikowanie istniejącego środowiska](#manually-identifying-an-existing-environment).

## <a name="the-python-environments-window"></a>Okno środowiska Python

Środowiska, w których zna Visual Studio są wyświetlane w **środowiska Python** okna. Aby otworzyć okno, użyj jednej z następujących metod:

- Wybierz **Widok > inne okna > środowiska Python** polecenia menu.
- Kliknij prawym przyciskiem myszy **środowiska Python** węzła projektu w Eksploratorze rozwiązań i wybierz **widok wszystkich środowisk języka Python**:

    ![Widok wszystkich środowisk polecenia w Eksploratorze rozwiązań](media/environments-view-all.png)

W obu przypadkach **środowiska Python** okno jako element równorzędny karty do Eksploratora rozwiązań:

![Okno środowiska Python](media/environments-default-view.png)

Powyższy obraz pokazuje, że program Visual Studio wykrył dwóch instalacji języka Python 3,6 (32-bitowy) wraz z Anaconda 5.0.0.

Domyślne środowisko pogrubioną czcionką jest (w tym przypadku część instalacji Anaconda), 3,6 Python, używający dla wszystkich nowych projektów programu Visual Studio. Polecenia w dolnej części okna dotyczą wybranego 3,6 Python interpreter, które jako użytkownik widzi jest instalacji określonych w `C:\Python36-32`. Jeśli nie widzisz środowisku spodziewasz się, zobacz [ręczne identyfikowanie istniejącego środowiska](#manually-identifying-an-existing-environment).

Po prawej stronie każdego środowiska wymienionych jest formant, który powoduje otwarcie okna interaktywnego dla tego środowiska. Inny formant może pojawić się odświeża IntelliSense bazy danych dla tego środowiska (zobacz [odwołania okno środowiska](python-environments-window-tab-reference.md#intellisense-tab) szczegółowe informacje o bazie danych).

Poniżej listy środowisk jest selektora listy rozwijanej dla **omówienie**, **pakiety**, i **IntelliSense** opcje opisane w [środowiska Python okno karty](python-environments-window-tab-reference.md). Ponadto po rozwinięciu **środowiska Python** okna dostatecznie szerokie, te opcje są wyświetlane jako kart, które może się okazać bardziej wygodne do pracy z:

![Widok rozszerzony okno środowiska Python](media/environments-expanded-view.png)

> [!Note]
> Mimo że program Visual Studio szanuje opcję pakiety w przypadku lokacji systemu, nie udostępnia sposób, aby zmienić go z poziomu programu Visual Studio.

|   |   |
|---|---|
| ![Ikona aparatu film wideo](../install/media/video-icon.png "obejrzeć film wideo") | [Obejrzyj film (Microsoft Virtual Academy)](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=qrDmN4LWE_8305918567) na środowiska Python w programie Visual Studio (2 m 35s).|

### <a name="what-if-no-environments-appear"></a>Co zrobić, jeśli są widoczne nie środowiska?

Są wyświetlane nie środowisk, oznacza, że nie można wykryć wszystkie instalacje Python w standardowe lokalizacje programu Visual Studio. Na przykład użytkownik może mają zainstalowaną 2017 usługi Visual Studio, ale wyczyszczone wszystkie opcje interpreter w opcjach Instalatora dla obciążenia Python. Podobnie, został zainstalowany program Visual Studio 2015 lub starszym, ale nie został zainstalowany interpreter ręcznie (zobacz [tłumaczy instalowanie Python](installing-python-interpreters.md)).

Jeśli znasz interpreter języka Python jest zainstalowana na komputerze, ale Visual Studio (dowolna wersja) nie wykryje go, a następnie użyj **+ niestandardowy...**  polecenie, aby ręcznie określić jego lokalizacji. Zobacz następną sekcję [ręczne identyfikowanie istniejącego środowiska](#manually-identifying-an-existing-environment).

> [!Tip]
> Visual Studio wykrywa aktualizacje do istniejących interpretera, takich jak uaktualnianie Python 2.7.11 do 2.7.14 przy użyciu instalatorów od python.org. W procesie instalacji środowiska starsze zniknie z **środowiska Python** listy aktualizacji pojawia się w jego miejscu.
>
> Jednak jeśli ręcznie przenieść interpreter i jego środowiska przy użyciu systemu plików programu Visual Studio będą wiedzieć, nowej lokalizacji. Aby uzyskać więcej informacji, zobacz [przenoszenie interpreter](installing-python-interpreters.md#moving-an-interpreter).

## <a name="manually-identifying-an-existing-environment"></a>Ręczne identyfikowanie istniejącego środowiska

Aby zidentyfikować środowisku, w którym jest zainstalowany w lokalizacji niestandardowej, również w środowiskach conda, wykonaj następujące kroki:

1. Wybierz **+ niestandardowy...**  w **środowiska Python** okna, które umożliwia otwarcie **Konfiguruj** karty:

    ![Domyślny widok dla nowego środowiska niestandardowych](media/environments-custom-1.png)

1. Wprowadź nazwę dla środowiska w **opis** pola.

1. Wpisz lub Przeglądaj (przy użyciu **... ***) do ścieżki interpreter w **ścieżki prefiks** pola.

1. Jeśli program Visual Studio wykryje interpreter języka Python w tej lokalizacji (takie jak ścieżka dla środowiska conda), umożliwia **Autowykrywanie** polecenia. Wybieranie **Autowykrywanie* zakończeniu pozostałe pola. Można również ręcznie wykonać tych pól.

    ![Włączanie polecenia Autowykrywanie](media/environments-custom-2.png)

    ![Uzupełnianie pola środowiska po użyciu Autowykrywanie](media/environments-custom-3.png)

1. Gdy pola zawierają wartości, które mają, wybierz **Zastosuj** Aby zapisać konfigurację. Można teraz używać środowiska jak każdy inny w programie Visual Studio.

1. Jeśli trzeba usunąć ręcznie zidentyfikowanych środowiska, wybierz **Usuń** na **Konfiguruj** kartę. Automatycznie wykrytej środowisk nie zawierają tej opcji. Aby uzyskać więcej informacji, zobacz [kartę Konfiguracja](python-environments-window-tab-reference.md#configure-tab).

## <a name="see-also"></a>Zobacz także

- [Instalowanie tłumaczy Python](installing-python-interpreters.md)
- [Wybierz interpreter dla projektu](selecting-a-python-environment-for-a-project.md)
- [Używanie pliku requirements.txt dla zależności](managing-required-packages-with-requirements-txt.md)
- [Ścieżki wyszukiwania](search-paths.md)
- [Odwołanie do okna środowiska Python](python-environments-window-tab-reference.md)