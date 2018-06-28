---
title: Rozszerzenie CookieCutter dla języka Python
description: Program Visual Studio obsługuje graficznego rozszerzenia Cookiecutter wykrywanie szablonów dla kodu języka Python i tworzenie projektów z tych szablonów.
ms.date: 06/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: a4cee1acbeeafb1360912f1f7342310a51ad54ff
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2018
ms.locfileid: "37058467"
---
# <a name="using-the-cookiecutter-extension"></a>Używanie rozszerzenia Cookiecutter

[Cookiecutter](https://cookiecutter.readthedocs.io/en/latest/) zawiera graficzny interfejs użytkownika do odnalezienia szablony, wprowadź opcje szablonu oraz tworzenie projektów i pliki. Wchodzi w skład programu Visual Studio 2017 r, a można zainstalować oddzielnie we wcześniejszych wersjach programu Visual Studio.

Cookiecutter wymaga Python 3.3 lub nowszych (32-bitowy lub 64-bitowych) lub Anaconda 3 4.2 i nowsze (32-bitowy lub 64-bitowe). Jeśli nie jest dostępny odpowiedni interpreter języka Python, Visual Studio, wyświetlane jest ostrzeżenie. Po zainstalowaniu interpreter języka Python, Visual Studio jest uruchomiona, kliknij przycisk Strona główna na pasku narzędzi Cookiecutter, aby wykryć interpretera nowo zainstalowany. (Zobacz [środowiska Python](managing-python-environments-in-visual-studio.md) więcej informacji o środowiskach ogólnie.)

Po zakończeniu instalacji wybierz **Widok > Cookiecutter Explorer** aby otworzyć okno:

![Okno główne Cookiecutter](media/cookiecutter-overview.png)

## <a name="cookiecutter-workflow"></a>Cookiecutter przepływu pracy

Praca z Cookiecutter jest proces przeglądania i wybrać szablon, klonowanie go na komputerze lokalnym, ustawianie opcji, a następnie tworzenia kodu na podstawie tego szablonu, zgodnie z opisem w poniższych sekcjach.

### <a name="browsing-templates"></a>Przeglądanie szablonów

Strona główna Cookiecutter zostanie wyświetlona lista szablonów do wyboru, zorganizowane w następujących grup:

| Grupa | Opis |
| --- | --- |
| Zainstalowany | Szablony, które zostały zainstalowane na komputerze lokalnym. W przypadku szablonu online repozytorium jest automatycznie sklonować do podfolderu `~/.cookiecutters`. Można usunąć wybranego szablonu zainstalowanych przez naciśnięcie przycisku **Del**. |
| Zalecane | Szablony są ładowane z zalecanych źródła danych. Źródło domyślnego jest wyselekcjonowanych przez firmę Microsoft. Zobacz [opcje Cookiecutter](#cookiecutter-options) poniżej szczegółowe informacje na temat dostosowywania kanału informacyjnego. |
| GitHub | Wyniki wyszukiwania GitHub cookiecutter — słowo kluczowe. Wyniki z serwisu GitHub wróć podzielony na strony, jeśli będą dostępne, wyniki **obciążenia więcej** pojawia się na końcu listy. |
| Niestandardowe | Lokalizacja niestandardowa została wprowadzona w polu wyszukiwania, wydaje się w tej grupie. Możesz wpisz pełną ścieżkę do repozytorium GitHub lub pełną ścieżkę do folderu na dysku lokalnym. |

### <a name="cloning"></a>Klonowania

Po wybraniu szablonu, a następnie **dalej**, Cookiecutter tworzy kopię lokalnych do pracy z.

W przypadku wybrania szablonu z **zalecane** lub **GitHub** grup, lub wprowadź niestandardowy adres URL w polu wyszukiwania i wybrać ten szablon, jej sklonować i zainstalowania na komputerze lokalnym. Jeśli ten szablon został zainstalowany w poprzedniej sesji programu Visual Studio, jest automatycznie usuwana, i został sklonowany najnowszej wersji.

W przypadku wybrania szablonu z **zainstalowana** grupy, lub wprowadź ścieżkę folderu niestandardowego w polu wyszukiwania i wybrać ten szablon programu Visual Studio ładuje szablon bez klonowania.

> [!Important]
> Szablony Cookiecutter są klonowane w jednym folderze `~/.cookiecutters`. Po nazwie repozytorium git, która nie obejmuje nazwę użytkownika usługi GitHub nosi nazwę każdego podfolderu. Konflikty mogą wystąpić, jeśli klonowanie różnych szablonów o takiej samej nazwie, które pochodzą z różnych autorów. W takim przypadku Cookiecutter zapobiega zastępowaniu istniejącego szablonu z innego szablonu o takiej samej nazwie. Aby zainstalować ten szablon, należy najpierw usunąć istniejący.

### <a name="setting-template-options"></a>Ustawianie opcji szablonu

Po zainstalowaniu szablonu w lokalnie Cookiecutter Wyświetla Strona opcji, w którym można określić miejsce Cookiecutter generuje pliki oraz inne opcje:

![Strona opcji Cookiecutter](media/cookiecutter-template-options.png)

Każdy szablon Cookiecutter definiuje swój własny zestaw opcji i określa wartość domyślną dla każdego z nich (wyświetlane jako sugerowane tekst w polu każdego wpisu). Wartość domyślna może być fragment kodu, często w przypadku, gdy jest wartość dynamiczną, która używa innych opcji. 

Istnieje możliwość dostosowania wartości domyślne dla określonych opcji z pliku konfiguracji użytkownika. Gdy rozszerzenia Cookiecutter wykryje plik konfiguracji użytkownika, zastępuje wartości domyślne szablonu z wartościami domyślnymi konfiguracji użytkownika. To zachowanie jest omówiona w [konfiguracji użytkownika](https://cookiecutter.readthedocs.io/en/latest/advanced/user_config.html) części dokumentacji Cookiecutter.

Jeśli szablon służy do określonych zadań programu Visual Studio do uruchomienia po generowania kodu, dodatkowe **uruchamiania dodatkowych zadań po zakończeniu** jest wyświetlana opcja umożliwiająca zrezygnować z tych zadań. Najczęściej zadań jest Otwórz przeglądarkę sieci web, otwórz pliki w edytorze, zainstaluj zależności i tak dalej.

### <a name="create"></a>Create

Po ustawieniu opcji wybierz **Utwórz** do generowania kodu (pojawi się ostrzeżenie, jeśli folder wyjściowy nie jest pusta). Jeśli znasz wynik szablonu i nie stanowi zastąpienie plików, można zignorować to ostrzeżenie. W przeciwnym razie wybierz **anulować**Określ pusty folder, a następnie ręcznie skopiuj utworzonych plików do folderu wyjściowego niepusty.

Po pomyślnym utworzeniu pliki Cookiecutter udostępnia opcję, aby otworzyć plik w **Eksploratora rozwiązań**:

![Polecenie Eksploratora rozwiązań przedstawiający Cookiecutter](media/cookiecutter-files-created.png)

## <a name="cookiecutter-options"></a>Opcje Cookiecutter

Cookiecutter opcje są dostępne za pośrednictwem **Narzędzia > Opcje > Cookiecutter**:

![Opcje Cookiecutter](media/cookiecutter-tools-options.png)

| Opcja | Opis |
| --- | --- |
| Zalecane adres URL źródła | Lokalizacja szablonów zalecane źródła danych. Może być adresem URL lub ścieżkę do pliku lokalnego. Adres URL pozostaw puste, aby używał domyślnego Microsoft wyselekcjonowanych źródła danych. Źródło zawiera listę proste lokalizacje szablonów, rozdzielone newlines. Poproś o wprowadzenie zmian do wyselekcjonowanych źródła, upewnij się żądanie ściągnięcia przed [źródła w serwisie GitHub](https://github.com/Microsoft/PTVS/blob/master/Python/Product/Cookiecutter/CookiecutterFeed.txt). |
| Pokaż Pomoc | Określa widoczność paska informacji pomocy w górnej części okna Cookiecutter. |

## <a name="optimizing-cookiecutter-templates-for-visual-studio"></a>Optymalizacja Cookiecutter szablony programu Visual Studio

Aby uzyskać podstawowe informacje dotyczące tworzenia szablonu Cookiecutter, zobacz [dokumentacji Cookiecutter](https://cookiecutter.readthedocs.io/en/latest/first_steps.html). Rozszerzenie Cookiecutter dla programu Visual Studio obsługuje szablony utworzone dla Cookiecutter w wersji 1.4.

Odwzorowanie domyślne zmiennych szablonu jest zależna od typu danych (ciągu lub listy):

- Ciąg: Etykieta w nazwie zmiennej, pole tekstowe do wprowadzania wartości i znak wodny przedstawiający wartość domyślna. Etykietki narzędzia w polu tekstowym wyświetlana jest wartość domyślna.
- Lista: Etykieta w nazwie zmiennej, pole kombi wyboru wartość. Etykietki narzędzia w polu kombi zawiera wartość domyślną.

Można zwiększyć na tym renderowania, określając dodatkowe metadane w Twojej `cookiecutter.json` pliku, który jest specyficzne dla programu Visual Studio (i zostanie zignorowane przez Cookiecutter interfejsu wiersza polecenia). Wszystkie właściwości są opcjonalne:

| Właściwość | Opis |
| --- | --- |
| Etykieta | Określa, jakie pojawia się powyżej edytor dla zmiennej, a nie nazwę zmiennej. |
| Opis | Określa etykietkę narzędzia, która pojawia się w formancie edycji, a wartość domyślna dla tej zmiennej. |
| Adres URL | Zmienia etykietę hiperłącza, z etykietka narzędzia, która zawiera adres URL. Kliknięcie hiperłącza otwiera przeglądarkę domyślną użytkownika do tego adresu URL. |
| Selektor | Umożliwia dostosowanie edytora dla zmiennej. Obecnie obsługiwane są następujące selektorów:<ul><li>`string`: Pole tekstowe standard, domyślny dla ciągów.</li><li>`list`: Pole kombi standard, domyślnie dla listy.</li><li>`yesno`: Pole kombi wybranie `y` i `n`, dla ciągów.</li><li>`odbcConnection`: Pole tekstowe z przycisk "...", który wyświetla okno dialogowe połączenia bazy danych.</li></ul> |

Przykład:

```json
{
    "site_name": "web-app",
    "python_version": ["3.5.2", "2.7.12"],
    "use_azure": "y",

    "_visual_studio": {
        "site_name": {
            "label": "Site name",
            "description": "E.g. <site-name>.azurewebsites.net (can only contain alphanumeric characters and `-`)"
        },
        "python_version": {
            "label": "Python version",
            "description": "The version of Python to run the site on"
        },
        "use_azure" : {
            "label": "Use Azure",
            "description": "Include Azure deployment files",
            "selector": "yesno",
            "url": "https://azure.microsoft.com"
        }
    }
}
```

### <a name="running-visual-studio-tasks"></a>Uruchamianie zadań programu Visual Studio

Cookiecutter ma funkcję *Post-Generate przechwytuje* umożliwiająca do uruchomienia dowolnego kodu Python po wygenerowaniu plików. Mimo że jest to elastyczny, nie zezwalał na łatwy dostęp do programu Visual Studio.

Na przykład możesz otworzyć plik w edytorze programu Visual Studio lub w jego przeglądarki sieci web, wyzwalacza lub interfejsu użytkownika programu Visual Studio, które monituje użytkownika, aby utworzyć środowisko wirtualne i zainstalować wymagań dotyczących pakietu.

Aby zezwolić na te scenariusze, Visual Studio szuka rozszerzonej metadanych w `cookiecutter.json` opisujący polecenia do uruchomienia po otwarciu plików wygenerowanych w Eksploratorze rozwiązań lub pliki są dodawane do istniejącego projektu. (Ponownie, użytkownik może zrezygnować z uruchomionych zadań czyszcząc **uruchamiania dodatkowych zadań po zakończeniu** w opcjach szablonu.)

Przykład:

```json
"_visual_studio_post_cmds": [
    {
        "name": "File.OpenFile",
        "args": "{{cookiecutter._output_folder_path}}\\readme.txt"
    },
    {
        "name": "Cookiecutter.ExternalWebBrowser",
        "args": "https://docs.microsoft.com"
    },
    {
        "name": "Python.InstallProjectRequirements",
        "args": "{{cookiecutter._output_folder_path}}\\dev-requirements.txt"
    }
]
```

Polecenia są określane przez nazwę i powinna być używana niezlokalizowana nazwa (angielski) do pracy w zlokalizowanych spowoduje zainstalowanie programu Visual Studio. Można przetestować i odnajdywanie nazw poleceń w oknie wiersza polecenia programu Visual Studio.

Jeśli chcesz przekazać jeden argument, należy określić go jako ciąg podobnie jak w poprzednim przykładzie.

Jeśli nie ma potrzeby przekazywania argumentu, pozostaw pusty ciąg lub pominąć go w formacie JSON:

```json
"_visual_studio_post_cmds": [
    {
        "name": "View.WebBrowser"
    }
]
```

Użyj tablicy dla wielu argumentów. Przełączniki podzielić przełącznika i jej wartość na oddzielne argumenty i używać prawidłowego zamykający. Na przykład:

```json
"_visual_studio_post_cmds": [
    {
        "name": "File.OpenFile",
        "args": [
            "{{cookiecutter._output_folder_path}}\\read me.txt",
            "/e:",
            "Source Code (text) Editor"
        ]
    }
]
```

Argumenty mogą odwoływać się do innych zmiennych Cookiecutter. W przykładach powyżej wewnętrznej `_output_folder_path` zmienna jest używana do utworzenia ścieżka bezwzględna do wygenerowanych plików.

Należy pamiętać, że `Python.InstallProjectRequirements` polecenia działa tylko wtedy, gdy trwa dodawanie plików do istniejącego projektu. To ograniczenie istnieje, ponieważ polecenie jest przetwarzany przez projekt języka Python w Eksploratorze rozwiązań i nie żadnego projektu do odbierania wiadomości w Eksploratorze rozwiązań — widok folderu. Mamy nadzieję usunąć win ograniczenia przyszłych wydaniach (i zapewnia lepszą obsługę widok folderu ogólnie).

## <a name="troubleshooting"></a>Rozwiązywanie problemów

### <a name="error-loading-template"></a>Błąd podczas ładowania szablonu

Niektóre szablony mogą być używane typy nieprawidłowe dane, takie jak wartość logiczna, w ich `cookiecutter.json`. Raport takich wystąpień autorowi szablonu, wybierając **problemów** łącze w okienku informacji szablonu.

### <a name="hook-script-failed"></a>Utworzenie punktu zaczepienia skryptu nie powiodło się

Niektóre szablony może używać po generowania skryptów, które nie są zgodne z Cookiecutter interfejsu użytkownika. Na przykład skrypty zapytania dla danych wejściowych użytkownika nie powiedzie się ze względu na Brak konsoli terminala.

### <a name="hook-script-not-supported-on-windows"></a>Utworzenie punktu zaczepienia skrypt nie jest obsługiwany w systemie Windows

Jeśli skrypt post jest `.sh`, a następnie mogą nie być skojarzone z aplikacją na komputerze z systemem Windows. Może pojawić się okno dialogowe systemu Windows monitem można odnaleźć zgodnej aplikacji w Sklepie Windows.

### <a name="templates-with-known-issues"></a>Szablony z znane problemy

Błędy w klonowania:

- **wildfish/cookiecutter-django-crud** (nieprawidłowy znak `|` w podfolderze o nazwie)
- **cookiecutter pyvanguard** (nieprawidłowy znak `|` w podfolderze o nazwie)

Błędy ładowania:

- **chrisdev/wagtail-cookiecutter-foundation** (używany typ boolean cookiecutter.json)
- **quintoandar/cookiecutter-android** (nie w folderze szablonów)

Uruchom błędów:

- **iknite/cookiecutter-ansible-role** (post haku skrypt wymaga danych wejściowych konsoli)
- **benregn/cookiecutter-django-ansible** (błąd Jinja)

Używa bash (nie krytyczny):

- **openstack-dev/cookiecutter**
