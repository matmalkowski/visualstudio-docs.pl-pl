---
title: Szablony aplikacji sieci Web dla języka Python
description: Przegląd szablonów programu Visual Studio dla aplikacji sieci web napisanych w języku Python za pomocą struktury Bottle, Flask i Django, łącznie z konfiguracji debugowania i publikowania w usłudze Azure App Service.
ms.date: 05/18/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: f975b726b8be76af1e3daeff59a06a18988644ab
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34752043"
---
# <a name="python-web-application-project-templates"></a>Szablony projektów aplikacji sieci web języka Python

Python w programie Visual Studio obsługują tworzenie projektów sieci web Bottle, Flask i Django oraz struktur za pomocą szablonów projektu i uruchamiania debugowania, które mogą być skonfigurowane do obsługi różnych platform. Te szablony obejmują `requirements.txt` Aby zadeklarować wymagane zależności. Podczas tworzenia projektu z jednego z tych szablonów, Visual Studio monit o zainstalowanie tych pakietów (zobacz [instalowanie wymagania dotyczące projektu](#installing-project-requirements) dalszej części tego artykułu).

Umożliwia także szablon ogólny "Projektu sieci Web" dla innych platform, takich jak ostrosłupa. W takim przypadku struktur nie są zainstalowane na podstawie tego szablonu. Zamiast tego należy zainstalować wymaganych pakietów do środowiska używasz projektu (zobacz [środowiska Python zarządzanie](managing-python-environments-in-visual-studio.md)).

## <a name="using-a-project-template"></a>Za pomocą szablonu projektu

Tworzenie projektu z szablonu przy użyciu **pliku** > **nowy** > **projektu**. Aby wyświetlić szablony projektów sieci web, wybierz **Python** > **Web** po lewej stronie okna dialogowego. Następnie wybierz szablon wybranych przez użytkownika, zapewniając nazwy projektu i rozwiązania, skonfigurować katalog rozwiązania i repozytorium Git i wybierz **OK**.

![Okno dialogowe nowego projektu aplikacji sieci web](media/projects-new-project-dialog-web.png)

Szablon ogólny "Projektu sieci Web" wspomniano wcześniej, zawiera tylko pusty projekt programu Visual Studio z żadnego kodu i żadnych założeń niż trwa projektów języka Python. Aby uzyskać szczegółowe informacje w szablonie "Usługi w chmurze Azure", zobacz [projekty usługi w chmurze Azure dla języka Python](python-azure-cloud-service-project-template.md).python-azure-cloud-service-project-template.md

Wszystkie inne szablony są oparte na platformy sieci web Bottle, Flask i Django i dzielą się na trzy główne grupy, zgodnie z opisem w poniższych sekcjach. Aplikacje utworzone przy użyciu jednej z tych szablonów zawiera kod wystarczające do uruchomienia i debugowania aplikacji lokalnie. Każda z nich są także niezbędne [obiektu aplikacji WSGI](http://www.python.org/dev/peps/pep-3333/) (python.org) do [wdrożyć w usłudze Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md).

### <a name="blank-group"></a>Puste grupy

Wszystkie szablony "Puste (RAM) projektu sieci Web" Tworzenie projektu z więcej lub mniej minimalnego schematyczny kod i zależności niezbędne zadeklarowany w `requirements.txt` pliku.

| Szablon | Opis |
| --- | --- |
| Projekt sieci Web Bottle puste | Generuje minimalnego aplikacji w `app.py` ze stroną główną dla `/` i `/hello/<name>` strona, która zwraca `<name>` przy użyciu wbudowanego bardzo krótki szablonu strony. |
| Puste Django Web Project | Generuje projekt Django o strukturze core Django lokacji, ale nie ma aplikacji Django. Aby uzyskać więcej informacji, zobacz [szablony Django](python-django-web-application-project-template.md) i [Learning Django w kroku 1](learn-django-in-visual-studio-step-01-project-and-solution.md). |
| Projekt sieci Web platformy Flask puste | Generuje minimalnego aplikacja z jednym "Witaj świecie!" dla strony `/`. Ta aplikacja jest podobny do następującego szczegółowy opis kroków, w wyniku [Szybki Start: program Visual Studio umożliwia tworzenie pierwszej aplikacji sieci web platformy Python](../ide/quickstart-python.md?context=visualstudio/python/default). Zobacz też [Learning Flask krok 1](learn-flask-visual-studio-step-01-project-solution.md).

### <a name="web-group"></a>Grupa aplikacji sieci Web

Wszystkie szablony "Projekt sieci Web (RAM)" utworzyć początkową aplikację sieci web z identyczne projektowania niezależnie od wybranego framework. Aplikacja ma Narzędzia główne, strony o i skontaktuj się z pomocą, wraz z paska nawigacji i elastycznego projektu za pomocą początkowego. Każdej aplikacji jest odpowiednio skonfigurowany do serwera plików statycznych (CSS, JavaScript i czcionki) i korzysta z mechanizmu szablonu strony odpowiednie dla struktury.

| Szablon | Opis |
| --- | --- |
| Projekt sieci Web bottle | Generuje pliki statyczne, dla których są zawarte w aplikacji `static` folderu i obsługiwane za pośrednictwem kodu w `app.py`. Routing dla poszczególnych stron znajduje się w `routes.py`i `views` folder zawiera szablony stron.|
| Projekt sieci Web Django | Generuje projekt Django i aplikacja Django z trzech stron, obsługę uwierzytelniania i bazy danych SQLite (ale żadnych modeli danych). Aby uzyskać więcej informacji, zobacz [szablony Django](python-django-web-application-project-template.md) i [Learning Django w kroku 4](learn-django-in-visual-studio-step-04-full-django-project-template.md). |
| Projekt sieci Web platformy flask | Generuje pliki statyczne, dla których są zawarte w aplikacji `static` folderu. Kod w `views.py` obsługuje routing z szablonami strony przy użyciu aparatu Jinja zawartych w `templates` folderu. `runserver.py` Plik zawiera kod uruchomienia. Zobacz [Learning Flask krok 4](learn-flask-visual-studio-step-04-full-flask-project-template.md). |
| Projekt sieci Web platformy flask/Jade | Generuje tej samej aplikacji jako z szablonu "Projekt sieci Web platformy Flask", ale dla aparatu tworzenia szablonów Jinja przy użyciu Jade rozszerzenia. |

### <a name="polls-group"></a>Grupy sond

Szablony "Sond (RAM) projektu sieci Web" utworzyć początkową aplikację sieci web za pomocą którego użytkownicy mogą głosowania na pytania ankiety różnych. Każda aplikacja oparta na strukturze szablonów projektu "Web". Aby zarządzać ankiety i odpowiedzi użytkownika przy użyciu bazy danych. Aplikacje obejmują modeli danych oraz specjalne aplikacji strony (/ inicjatora) która ładuje sond z `samples.json` pliku.

| Szablon | Opis |
| --- | --- |
| Projekt sieci Web Bottle sond | Generuje aplikację, która może działać względem bazy danych w pamięci, bazy danych MongoDB lub magazynu tabel Azure, która jest konfigurowana przy użyciu `REPOSITORY_NAME` zmiennej środowiskowej. Modeli danych i kod magazynu danych są zawarte w `models` folderu i `settings.py` plik zawiera kod, aby określić, w którym magazyn danych jest używany. |
| Projekt sieci Web Django sond | Generuje projekt Django oraz aplikacji Django z trzech stron i bazy danych SQLite. Zawiera dostosowania interfejsu administracyjnego Django, aby umożliwić uwierzytelniony administratorowi tworzenie i zarządzanie nimi sond. Aby uzyskać więcej informacji, zobacz [szablony Django](python-django-web-application-project-template.md) i [Learning Django w kroku 6](learn-django-in-visual-studio-step-06-polls-django-web-project-template.md). |
| Projekt sieci Web platformy Flask sond | Generuje aplikację, która może działać względem bazy danych w pamięci, bazy danych MongoDB lub magazynu tabel Azure, która jest konfigurowana przy użyciu `REPOSITORY_NAME` zmiennej środowiskowej. Modeli danych i kod magazynu danych są zawarte w `models` folderu i `settings.py` plik zawiera kod, aby określić, w którym magazyn danych jest używany. Aplikacja korzysta z aparatu Jinja dla szablonów strony. Zobacz [Learning Flask krok 5](learn-flask-visual-studio-step-05-polls-flask-web-project-template.md). |
| Projekt sieci Web platformy Flask/Jade sond | Generuje tej samej aplikacji jako z szablonu "Projektu sieci Web platformy Flask sond", ale dla aparatu tworzenia szablonów Jinja przy użyciu Jade rozszerzenia. |

## <a name="installing-project-requirements"></a>Instalowanie wymagania dotyczące projektu

Podczas tworzenia projektu za pomocą szablonu określonej struktury, ułatwiające instalowanie wymaganych pakietów przy użyciu narzędzia pip zostanie wyświetlone okno dialogowe. Zalecamy również przy użyciu [środowiska wirtualnego](selecting-a-python-environment-for-a-project.md#using-virtual-environments) dla projektów sieci web tak, aby prawidłowe zależności są uwzględniane podczas publikowania witryny sieci web:

![Okno dialogowe, który instaluje wymagane pakiety szablonu projektu](media/template-web-requirements-txt-wizard.png)

Jeśli używasz kontroli źródła, zwykle pominięto folderu środowiska wirtualnego następnie zgodnie z tym środowisku można utworzyć ponownie za pomocą tylko `requirements.txt`. Najlepszym sposobem, aby wykluczyć folder jest najpierw wybrać **będzie zainstalować je samodzielnie** w powyższym wierszu polecenia przed utworzeniem środowiska wirtualnego Wyłącz automatycznego zatwierdzania. Aby uzyskać więcej informacji, zobacz [samouczek dotyczący uczenia Django - kroki 1 i 2 i 1-3](learn-django-in-visual-studio-step-01-project-and-solution.md#step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository) i [samouczek dotyczący uczenia Flask - kroki 1 i 2 i 1-3](learn-flask-visual-studio-step-01-project-solution.md#step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository)

W przypadku wdrażania w usłudze Microsoft Azure App Service, wybierz wersję języka Python jako [lokacji rozszerzenia](https://aka.ms/PythonOnAppService) i ręcznie zainstalować pakiety. Ponadto ponieważ usługa aplikacji Azure ma **nie** automatycznie zainstalować pakiety z `requirements.txt` po wdrożeniu w programie Visual Studio, wykonaj szczegółów konfiguracji [aka.ms/PythonOnAppService](https://aka.ms/PythonOnAppService).

Usługi w chmurze Microsoft Azure *jest* obsługuje `requirements.txt` pliku. Zobacz [projekty usługi w chmurze Azure](python-azure-cloud-service-project-template.md) szczegółowe informacje.

## <a name="debugging"></a>Debugowanie

Po rozpoczęciu debugowania projektu sieci web programu Visual Studio rozpoczyna się serwera sieci web lokalnych losowych portu i otwiera przeglądarkę domyślną, aby ten adres i port. Aby określić dodatkowe opcje, kliknij prawym przyciskiem myszy projekt, wybierz **właściwości**i wybierz **uruchamiania Web** karty:

![Właściwości sieci Web uruchamiania dla szablonu ogólnego sieci web](media/template-web-launcher-properties.png)

W **debugowania** grupy:

- **Ścieżki wyszukiwania**, **argumenty skryptu**, **argumenty Interpreter**, i **ścieżki Interpreter**: te opcje są takie same jak w przypadku [normalne debugowanie](debugging-python-in-visual-studio.md)
- **Uruchamianie adresu URL**: Określa adres URL, która jest otwarta w przeglądarce. Domyślnie `localhost`.
- **Numer portu**: port do użycia, jeśli nie zostanie określona w adresie URL (Visual Studio: wybiera jeden domyślnie automatycznie). To ustawienie pozwala zastąpić domyślną wartość `SERVER_PORT` zmiennej środowiskowej, która jest używany przez Szablony do konfigurowania portu nasłuchuje serwer debugowania lokalnego.

Właściwości w **uruchamiania polecenia serwera** i **polecenia Debug serwera** grup (nie jest poniżej poziomu Pokaż w obrazie) określić, jak serwer sieci web jest uruchamiana. Ponieważ wiele platform wymaga użycia skryptu poza bieżącego projektu, w tym miejscu można skonfigurować skrypt i nazwę modułu uruchamiania można przekazać jako parametru.

- **Polecenie**: mogą być skryptami języka Python (`*.py` pliku), nazwa modułu (podobnie jak w `python.exe -m module_name`), lub pojedynczy wiersz kodu (podobnie jak w `python.exe -c "code"`). Wartość w polu listy rozwijanej wskazuje typy przeznaczony.
- **Argumenty**: argumenty są przekazywane w wierszu polecenia następujące polecenie.
- **Środowisko**: listę oddzielonych znakami nowego wiersza `NAME=VALUE` pary określania zmiennych środowiskowych. Te zmienne są ustawiane po wszystkie właściwości, które mogą być modyfikowane środowiska, takie jak port ścieżki numer i wyszukiwania i dlatego mogą zastąpić te wartości.

Dowolnej właściwości lub środowiska zmiennej projektu można określić ze składnią MSBuild, na przykład: `$(StartupFile) --port $(SERVER_PORT)`.
`$(StartupFile)` jest ścieżką względną do pliku uruchamiania i `{StartupModule}` jest importowane nazwę pliku uruchamiania. `$(SERVER_HOST)` i `$(SERVER_PORT)` są zmiennymi środowiskowymi normalne, które są ustawiane przez **adres URL do uruchomienia** i **numer portu** właściwości, automatycznie lub przez **środowiska** właściwości.

> [!Note]
> Wartości w **uruchamiania polecenia serwera** są używane z **debugowania > Uruchamianie serwera** polecenia lub Ctrl-F5; wartości w **polecenia Debug serwera** grupy są używane z **Debuguj > Rozpocznij debugowanie serwera** polecenia lub F5.

### <a name="sample-bottle-configuration"></a>Przykładowa konfiguracja Bottle

**Projektu sieci Web Bottle** szablon zawiera schematyczny kod, który obsługuje niezbędną konfigurację. Zaimportowane bottle aplikacji nie może zawierać ten kod, jednak w takim przypadku następujące ustawienia uruchamiania aplikacji przy użyciu zainstalowana `bottle` modułu:

- **Uruchom polecenie serwera** grupy:
  - **Polecenie**: `bottle` (modułu)
  - **Argumenty**: `--bind=%SERVER_HOST%:%SERVER_PORT% {StartupModule}:app`

- **Debugowanie polecenia Server** grupy:
  - **Polecenie**: `bottle` (modułu)
  - **Argumenty** `--debug --bind=%SERVER_HOST%:%SERVER_PORT% {StartupModule}:app`

`--reload` Opcja nie jest zalecana w przypadku używania programu Visual Studio dla debugowania.

### <a name="sample-pyramid-configuration"></a>Przykładowa konfiguracja ostrosłupowy

Aplikacje ostrosłupa obecnie najlepiej są tworzone przy użyciu `pcreate` narzędzia wiersza polecenia. Po utworzeniu aplikacji, można go zaimportować przy użyciu [z istniejących Python code](managing-python-projects-in-visual-studio.md#creating-a-project-from-existing-files) szablonu. Po wykonaniu tej czynności, wybierz **ogólnego projektu sieci Web** dostosowywania do konfigurowania opcji. Te ustawienia założono, że ostrosłupa jest zainstalowany w środowisku wirtualnym na `..\env`.

- **Debugowanie** grupy:
  - **Port serwera**: 6543 (lub niezależnie od jest skonfigurowana w pliku ini)

- **Uruchom polecenie serwera** grupy:
  - Polecenie: `..\env\scripts\pserve-script.py` (skrypt)
  - Argumenty: `Production.ini`

- **Debugowanie polecenia Server** grupy:
  - Polecenie: `..\env\scripts\pserve-script.py` (skrypt)
  - Argumenty: `Development.ini`

> [!Tip]
> Prawdopodobnie należy skonfigurować **katalog roboczy** właściwości projektu, ponieważ aplikacje ostrosłupa zazwyczaj są to jeden folder poniżej katalogu głównego projektu.

### <a name="other-configurations"></a>Inne konfiguracje

Jeśli masz ustawienia dla innej platformy, który chcesz udostępnić, lub jeśli chcesz zażądać ustawienia dla innej platformy, otwórz [problem w usłudze GitHub](https://github.com/Microsoft/PTVS/issues).

## <a name="convert-a-project-to-azure-cloud-service"></a>Konwertowanie projektu usługi w chmurze Azure

**Konwertuj na projekt usługi w chmurze Microsoft Azure** polecenie (obraz poniżej) dodaje projektu usługi w chmurze do rozwiązania. Ten projekt zawiera ustawienia wdrażania i konfiguracji dla maszyn wirtualnych i usług, które mają być użyte. Użyj **publikowania** na projekt w chmurze do wdrożenia usługi w chmurze; **publikowania** polecenia w projekcie języka Python nadal wdraża do witryn sieci Web. Aby uzyskać więcej informacji, zobacz [projektów usług w chmurze Azure](python-azure-cloud-service-project-template.md).

![Konwertuj na projekt usługi chmury Microsoft Azure — polecenie](media/template-web-convert-menu.png)

## <a name="see-also"></a>Zobacz także

- [Dokumentacja szablonów elementu języka Python](python-item-templates.md)
- [Publikowanie w usłudze Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)
