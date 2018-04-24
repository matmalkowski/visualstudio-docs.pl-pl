---
title: Szablony aplikacji sieci Web dla języka Python
description: Przegląd szablonów programu Visual Studio dla aplikacji sieci web napisanych w języku Python za pomocą struktury Bottle, Flask i Django, łącznie z konfiguracji debugowania i publikowania w usłudze Azure App Service.
ms.date: 07/13/2017
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 0abb3752972e90347de2f296c11c86d8335fbb9a
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="python-web-application-project-templates"></a>Szablony projektów aplikacji sieci web języka Python

Python w programie Visual Studio obsługują tworzenie projektów sieci web Bottle, Flask i Django oraz struktur za pomocą szablonów projektu i uruchamiania debugowania, które mogą być skonfigurowane do obsługi różnych platform. Można również używać ogólnych **projektu sieci Web** szablonu dla innych platform, takich jak ostrosłupa.

Visual Studio nie ma struktury samodzielnie. Struktury należy zainstalować oddzielnie prawym przyciskiem myszy projekt i wybierając **Python > Instalacja/aktualizacja framework...** .

Uruchomienia projektu utworzonych na podstawie szablonu (jak uzyskać dostęp za pomocą **Plik > Nowy > Projekt...** ) uruchamia serwer sieci web z losowo wybranym port lokalny, otwiera domyślną przeglądarkę podczas debugowania i umożliwia bezpośrednie publikowanie do systemu Microsoft Azure.

![Nowe szablony projektów sieci web](media/template-web-new-project.png)

Szablony każdego Bottle, Flask i Django obejmują lokacji starter z niektórymi stron i plików statycznych. Ten kod jest wystarczające do uruchomienia, a serwer lokalnie (której niektóre ustawienia muszą pochodzić ze środowiska) debugowania i wdrażania do systemu Microsoft Azure (gdy [aplikacji WSGI](http://www.python.org/dev/peps/pep-3333/) obiekt musi zostać zapewniony).

Podczas tworzenia projektu za pomocą szablonu określonej struktury, ułatwiające instalowanie wymaganych pakietów przy użyciu narzędzia pip zostanie wyświetlone okno dialogowe. Zalecamy również przy użyciu [środowiska wirtualnego](selecting-a-python-environment-for-a-project.md#using-virtual-environments) dla projektów sieci web tak, aby prawidłowe zależności są uwzględniane podczas publikowania witryny sieci web:

![Okno dialogowe, który instaluje wymagane pakiety szablonu projektu](media/template-web-requirements-txt-wizard.png)

W przypadku wdrażania w usłudze Microsoft Azure App Service, wybierz wersję języka Python jako [lokacji rozszerzenia](https://aka.ms/PythonOnAppService) i ręcznie zainstalować pakiety. Ponadto ponieważ usługa aplikacji Azure ma **nie** automatycznie zainstalować pakiety z `requirements.txt` po wdrożeniu w programie Visual Studio, wykonaj szczegółów konfiguracji [aka.ms/PythonOnAppService](https://aka.ms/PythonOnAppService).

Usługi w chmurze Microsoft Azure *jest* obsługuje `requirements.txt` pliku. [Projekty usługi chmury Azure](python-azure-cloud-service-project-template.md) szczegółowe informacje.

## <a name="debugging"></a>Debugowanie

Po rozpoczęciu debugowania projektu sieci web programu Visual Studio uruchamia serwer sieci web lokalnie i otwiera domyślnej przeglądarki do tego adresu i portu. Aby określić dodatkowe opcje, kliknij prawym przyciskiem myszy projekt, wybierz **właściwości**i wybierz **uruchamiania Web** karty:

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
> Prawdopodobnie należy skonfigurować **katalog roboczy** właściwości projektu, ponieważ aplikacje ostrosłupa są zwykle jednego katalogu poziomu głębiej niż do górnej części drzewa źródła.

### <a name="other-configurations"></a>Inne konfiguracje

Jeśli masz ustawienia dla innej platformy, który chcesz udostępnić, lub jeśli chcesz zażądać ustawienia dla innej platformy, otwórz [problem w usłudze GitHub](https://github.com/Microsoft/PTVS/issues).

## <a name="publishing-to-azure-app-service"></a>Publikowanie w usłudze Azure App Service

Istnieją dwa podstawowe sposoby publikowania w usłudze Azure App Service. Po pierwsze, wdrożenia z kontroli źródła może służyć w taki sam sposób jak w przypadku innych języków zgodnie z opisem w [dokumentacji platformy Azure](http://azure.microsoft.com/en-us/documentation/articles/web-sites-publish-source-control/). Aby opublikować bezpośrednio z programu Visual Studio, kliknij prawym przyciskiem myszy projekt i wybierz **publikowania**:

![Publikowanie polecenia w menu kontekstowym projektu](media/template-web-publish-command.png)

Po wybraniu polecenia, Kreator przeprowadzi Cię przez proces tworzenia witryny sieci web lub importowanie publikowania plików i publikowanie na serwerze zdalnym zmodyfikować ustawień, wyświetlanie podglądu.

Podczas tworzenia witryny w usłudze aplikacji, musisz zainstalować Python i wszelkie pakiety, które zależy od lokacji. Należy najpierw opublikować witrynę sieci, ale nie będą uruchamiane, dopóki nie skonfigurowano Python.

Aby zainstalować Python w usłudze aplikacji, zaleca się używanie [lokacji rozszerzenia](http://www.siteextensions.net/packages?q=Tags%3A%22python%22) (siteextensions.net). Te rozszerzenia są kopie [wydania oficjalne](https://www.python.org) języka Python, zoptymalizowany i pakietach dla usługi Azure App Service.

Rozszerzenie lokacji można wdrożyć za pomocą [portalu Azure](https://portal.azure.com/). Wybierz **narzędzi programistycznych > rozszerzenia** bloku aplikacji usługi, wybierz **Dodaj**i przewiń listę, aby znaleźć elementy języka Python:

![Dodaj rozszerzenie lokacji w portalu Azure](media/template-web-site-extensions.png)

Jeśli używasz JSON szablony wdrażania można określić rozszerzenia lokacji jako zasób witryny:

```json
{
    "resources": [
    {
        "apiVersion": "2015-08-01",
        "name": "[parameters('siteName')]",
        "type": "Microsoft.Web/sites",
        ...
    },
    "resources": [
    {
        "apiVersion": "2015-08-01",
        "name": "python352x64",
        "type": "siteextensions",
        "properties": { },
        "dependsOn": [
            "[resourceId('Microsoft.Web/sites', parameters('siteName'))]"
        ]
    },
    ...
}
```

Ponadto możesz zalogować się za pośrednictwem [konsoli deweloperskiej](https://github.com/projectkudu/kudu/wiki/Kudu-console) i instalowanie rozszerzenia lokacji z tego miejsca.

Po zainstalowaniu rozszerzenia lokacji i wykonywania pip bezpośrednio przy użyciu konsoli programowanie jest obecnie, zalecanym sposobem instalowania pakietów. Przy użyciu pełną ścieżkę do języka Python jest ważna, lub może wykonywać niewłaściwy i nie jest zazwyczaj konieczne do użycia w środowisku wirtualnym. Na przykład:

```command
c:\Python35\python.exe -m pip install -r D:\home\site\wwwroot\requirements.txt

c:\Python27\python.exe -m pip install -r D:\home\site\wwwroot\requirements.txt
```

Po wdrożeniu usługi Azure App Service, lokalizacji uruchomiono za Microsoft IIS. Aby włączyć lokację do pracy z programem IIS, należy dodać co najmniej `web.config` pliku. Prawym przyciskiem myszy projekt i wybierając są dostępne dla niektórych typowych celów wdrożenia dostępne szablony **Dodaj > Nowy element...**  (zobacz poniżej okna dialogowego), a te konfiguracje można łatwo zmodyfikować do innych celów. Zobacz [odwołanie do konfiguracji usług IIS](https://www.iis.net/configreference) informacji o ustawieniach konfiguracji dostępności.

![Szablony elementów Azure](media/template-web-azure-items.png)

Dostępne elementy obejmują:

- Azure w pliku web.config (FastCGI): dodaje `web.config` po zapewnia aplikacji w pliku [WSGI](https://wsgi.readthedocs.io/en/latest/) obiektu do obsługi połączeń przychodzących.
- Azure w pliku web.config (HttpPlatformHandler): dodaje `web.config` gdy aplikacja nasłuchuje na gniazda dla połączeń przychodzących w pliku.
- Azure statyczne pliki web.config: Jeśli masz w powyższych `web.config` pliki, Dodaj plik do podkatalogu, aby wykluczyć go z obsługiwanych przez aplikację.
- Azure zdalnego debugowania pliku web.config: dodaje pliki niezbędne do zdalnego debugowania przez protokół WebSockets.
- Pliki obsługi roli sieci Web: zawiera domyślne skryptów wdrażania do role sieci web usługi w chmurze.
- Pliki obsługi roli procesu roboczego: zawiera skrypty wdrażania, a następnie uruchom domyślne role proces roboczy usługi w chmurze.

Jeśli dodasz debugowanie `web.config` szablonu do projektu i będzie używany, zdalnego debugowania języka Python, należy opublikować witrynę w konfiguracji "Debug". To ustawienie jest oddzielony od bieżącej konfiguracji aktywne rozwiązanie i zawsze domyślnie "Wersja". Aby go zmienić, otwórz **ustawienia** karcie i użyj **konfiguracji** pola kombi w Kreatorze publikowania (zobacz [dokumentacji platformy Azure](https://azure.microsoft.com/develop/python/) Aby uzyskać więcej informacji na temat tworzenia i Wdrażanie aplikacji sieci Web platformy Azure):

![Zmienianie konfiguracji publikowania](media/template-web-publish-config.png)

**Konwertuj na projekt usługi w chmurze Microsoft Azure** polecenie (obraz poniżej) dodaje projektu usługi w chmurze do rozwiązania. Ten projekt zawiera ustawienia wdrażania i konfiguracji dla maszyn wirtualnych i usług, które mają być użyte. Użyj **publikowania** na projekt w chmurze do wdrożenia usługi w chmurze; **publikowania** polecenia w projekcie języka Python nadal wdraża do witryn sieci Web. Zobacz [projektów usług w chmurze Azure](python-azure-cloud-service-project-template.md) więcej szczegółów.

![Konwertuj na projekt usługi chmury Microsoft Azure — polecenie](media/template-web-convert-menu.png)
