---
title: "Instalowanie tłumaczy Python i bibliotek w usłudze Azure App Service | Dokumentacja firmy Microsoft"
description: "Jak zainstalować interpreter języka Python i bibliotek w usłudze Azure App Service i konfigurowanie aplikacji sieci web, aby poprawnie odwoływać się do tego interpreter."
ms.custom: 
ms.date: 09/13/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: 
ms.topic: article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: bc9317615edbf49e35aa0ac3d2ff079beab20df5
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="managing-python-on-azure-app-service"></a>Zarządzanie Python w usłudze aplikacji Azure

[Usługa aplikacji Azure](https://azure.microsoft.com/services/app-service/) jest ofertę platformy jako usługa dla aplikacji sieci web, czy są one witryn dostępne za pośrednictwem przeglądarki, interfejsów API REST używany przez własnych klientów lub przetwarzania wyzwolenia zdarzenia. Usługa aplikacji w pełni obsługuje Hermetyzowanie przy użyciu języka Python do wdrożenia aplikacji.

Można dostosowywać obsługi języka Python w usłudze Azure App Service jest dostępna jako zestaw usług aplikacji *lokacji rozszerzenia* czy każdy zawierać określonej wersji środowiska uruchomieniowego języka Python. Następnie można zainstalować wszystkie odpowiednie pakiety bezpośrednio do tego środowiska, zgodnie z opisem w tym temacie. Dostosowując środowiska w samej usługi aplikacji, nie należy do obsługi pakietów w projektach aplikacji sieci web lub przekaż je z kodu aplikacji.

> [!Tip]
> Chociaż usługi aplikacji — domyślnie ma Python 2.7 i języka Python 3.4 zainstalowane w głównym folderów na serwerze, nie można dostosować lub instalowania pakietów w tych środowiskach ani powinien zależeć od ich obecności. Należy zamiast tego polegać na rozszerzeniu lokacji, którą kontrolujesz, zgodnie z opisem w tym temacie.

> [!Important]
> Procesach opisanych w tym miejscu są może ulec zmianie, a szczególnie w celu poprawy jakości. Zmiany są ogłaszane na [Python Engineering na blogu Microsoft](https://blogs.msdn.microsoft.com/pythonengineering/).

## <a name="choosing-a-python-version-through-the-azure-portal"></a>Wybieranie wersji języka Python, za pośrednictwem portalu Azure

1. Utwórz usługę aplikacji dla aplikacji sieci web w portalu Azure.
1. Na stronie usługi App Service, przewiń do **narzędzi programistycznych** zaznacz **rozszerzenia**, a następnie wybierz pozycję **+ Dodaj**.
1. Przewiń w dół do rozszerzenia plików, które zawiera wersję środowiska Python ma na liście:

    ![Rozszerzenia języka Python przedstawiający portal Azure](media/python-on-azure-extensions.png)

    > [!Tip]
    > Jeśli konieczne starszej wersji środowiska Python i nie jest widoczny na liście rozszerzeń witryny, można nadal zainstalować go za pomocą Menedżera zasobów Azure zgodnie z opisem w następnej sekcji.

1. Zaznacz rozszerzenie, zaakceptuj postanowienia prawne, a następnie wybierz **OK**.
1. Po zakończeniu instalacji w portalu pojawi się powiadomienie.

## <a name="choosing-a-python-version-through-the-azure-resource-manager"></a>Wybieranie wersji języka Python za pomocą usługi Azure Resource Manager

Jeśli wdrażasz App Service przy użyciu szablonu usługi Azure Resource Manager, należy dodać rozszerzenie lokacji jako zasób. Rozszerzenie jest wyświetlany jako zagnieżdżonych zasobów z typem `siteextensions` i nazwy na podstawie [siteextensions.net](https://www.siteextensions.net/packages?q=Tags%3A%22python%22).

Na przykład po dodawania odwołania do `python361x64` (Python 3.6.1 x 64), Twój szablon może wyglądać następująco (niektóre właściwości pominięcia):

```json
"resources": [
  {
    "apiVersion": "2015-08-01",
    "name": "[parameters('siteName')]",
    "type": "Microsoft.Web/sites",

    // ...

    "resources": [
      {
        "apiVersion": "2015-08-01",
        "name": "python361x64",
        "type": "siteextensions",
        "properties": { },
        "dependsOn": [
          "[resourceId('Microsoft.Web/sites', parameters('siteName'))]"
        ]
      },
      // ...
    ]
  }
```

## <a name="setting-webconfig-to-point-to-the-python-interpreter"></a>Ustawienia pliku web.config, aby wskazywał interpreter języka Python

Po zainstalowaniu rozszerzenia lokacji (za pośrednictwem portalu lub szablonu usługi Azure Resource Manager), następnie wskaż aplikacji `web.config` pliku interpreter języka Python. `web.config` Pliku powoduje, że serwer sieci web IIS (7 +) uruchomioną w usłudze aplikacji o jak powinna obsługiwać żądań Python za pośrednictwem FastCGI lub HttpPlatform.

Rozpocznij od znajdowanie pełną ścieżkę do rozszerzenia lokacji `python.exe`, Utwórz i zmodyfikuj odpowiednie `web.config` pliku.

### <a name="finding-the-path-to-pythonexe"></a>Znajdowanie ścieżkę do python.exe

Rozszerzenie lokacji Python jest zainstalowany na serwerze, w obszarze `d:\home` w folderze właściwe dla wersji języka Python i architektura (z wyjątkiem kilku starszych wersji). Na przykład Python 3.6.1 x64 jest zainstalowany w `d:\home\python361x64`. Pełna ścieżka do interpreter języka Python jest następnie `d:\home\python361x64\python.exe`.

Aby wyświetlić określoną ścieżkę w usłudze App Service, wybierz **rozszerzenia** na stronie usługi aplikacji, następnie wybierz rozszerzenie na liście.

![Lista rozszerzeń w usłudze Azure App Service](media/python-on-azure-extension-list.png)

Ta akcja powoduje otwarcie strony opis rozszerzenia zawierający ścieżkę:

![Szczegóły rozszerzenia w usłudze Azure App Service](media/python-on-azure-extension-detail.png)

Jeśli masz problem z wyświetlaniem ścieżka rozszerzenia można znaleźć je ręcznie przy użyciu konsoli:

1. Na stronie usługi aplikacji, wybierz **narzędzi programistycznych > konsoli**.
1. Wprowadź polecenie `ls ../home` lub `dir ..\home` można znaleźć folderów rozszerzenia najwyższego poziomu, takich jak `Python361x64`.
1. Wprowadź polecenie, takie jak `ls ../home/python361x64` lub `dir ..\home\python361x64` upewnić się, że zawiera `python.exe` i inne pliki interpreter.

### <a name="configuring-the-fastcgi-handler"></a>Konfigurowanie obsługi FastCGI

FastCGI jest interfejs, który działa na poziomie żądania. Usługi IIS odbiera połączenia przychodzące i przekazuje każdego żądania do aplikacji WSGI uruchomione w jednym lub większą trwałość Python procesów. [Pakietu wfastcgi](https://pypi.io/project/wfastcgi) jest wstępnie zainstalowana i skonfigurowana z każdego rozszerzenia lokacji Python, więc możesz go łatwo uaktywnić przez kod w tym `web.config` co przedstawiono poniżej dla aplikacji sieci web, w ramach struktury Bottle, takich jak. Należy pamiętać, że pełne ścieżki do `python.exe` i `wfastcgi.py` są umieszczane w `PythonHandler` klucza:

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <appSettings>
    <add key="PYTHONPATH" value="D:\home\site\wwwroot"/>
    <!-- The handler here is specific to Bottle; other frameworks vary. -->
    <add key="WSGI_HANDLER" value="app.wsgi_app()"/>
    <add key="WSGI_LOG" value="D:\home\LogFiles\wfastcgi.log"/>
  </appSettings>
  <system.webServer>
    <handlers>
      <add name="PythonHandler" path="*" verb="*" modules="FastCgiModule"
           scriptProcessor="D:\home\Python361x64\python.exe|D:\home\Python361x64\wfastcgi.py"
           resourceType="Unspecified" requireAccess="Script"/>
    </handlers>
  </system.webServer>
</configuration>
```

`<appSettings>` Zdefiniowanych w tym miejscu są dostępne dla aplikacji jako zmienne środowiskowe:

- Wartość `PYTHONPATH` może zostać rozszerzona za darmo, ale musi zawierać katalogu głównego aplikacji.
- `WSGI_HANDLER`musi wskazywać do aplikacji WSGI importowane z aplikacji.
- `WSGI_LOG`jest opcjonalne, ale zalecane do debugowania swojej aplikacji. 

Zobacz [publikowania na platformie Azure](publishing-python-web-applications-to-azure-from-visual-studio.md) dodatkowe szczegóły dotyczące `web.config` aplikacji sieci web zawartość Bottle, Flask i Django.

### <a name="configuring-the-httpplatform-handler"></a>Konfigurowanie obsługi HttpPlatform

Moduł HttpPlatform przekazuje połączenia gniazda bezpośrednio do autonomicznego procesu Python. Tego przekazywanego umożliwia uruchamianie dowolnego serwera sieci web, ale wymaga uruchomienia skrypt, który uruchamia serwer sieci web lokalnego. Określ skrypt w `<httpPlatform>` elementu `web.config`, gdzie `processPath` atrybutu punktów rozszerzenia lokacji interpreter języka Python oraz `arguments` atrybutu punktów skrypt i argumenty, aby zapewnić:

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.webServer>
    <handlers>
      <add name="PythonHandler" path="*" verb="*" modules="httpPlatformHandler" resourceType="Unspecified"/>
    </handlers>
    <httpPlatform processPath="D:\home\Python361x64\python.exe"
                  arguments="D:\home\site\wwwroot\runserver.py --port %HTTP_PLATFORM_PORT%"
                  stdoutLogEnabled="true"
                  stdoutLogFile="D:\home\LogFiles\python.log"
                  startupTimeLimit="60"
                  processesPerApplication="16">
      <environmentVariables>
        <environmentVariable name="SERVER_PORT" value="%HTTP_PLATFORM_PORT%" />
      </environmentVariables>
    </httpPlatform>
  </system.webServer>
</configuration>
```

`HTTP_PLATFORM_PORT` Zmiennej środowiskowej pokazane zawiera port serwera lokalnego powinien nasłuchiwać połączeń z localhost. W tym przykładzie przedstawiono również sposób tworzenia innej zmiennej środowiskowej, w razie potrzeby można w takim przypadku `SERVER_PORT`.

## <a name="installing-packages"></a>Instalowanie pakietów

Interpreter języka Python zainstalowane za pomocą rozszerzenia lokacji jest tylko jeden fragment środowiska Python. Prawdopodobnie należy zainstalować różne pakiety w tym środowisku również.

Aby zainstalować pakiety bezpośrednio w środowisku serwera, użyj jednej z następujących metod:

| Metody | Użycie |
| --- | --- |
| [Konsola Kudu usługi aplikacji Azure](#azure-app-service-kudu-console) | Instaluje interaktywne pakietów. Pakiety muszą być czysty Python lub należy opublikować koła. |
| [Program kudu interfejsu API REST](#kudu-rest-api) | Może służyć do automatyzowania instalacji pakietu aktualizacji.  Pakiety muszą być czysty Python lub należy opublikować koła. |
| Pakietu z aplikacją | Zainstaluj pakiety bezpośrednio do projektu, a następnie wdrożenia ich do usługi App Service tak, jakby były częścią aplikacji. W zależności od tego, jak wiele zależności są i jak często należy zaktualizować, ta metoda może być Najprostszym sposobem uzyskać przechodzi do wdrożenia pracy. Można wskazać, że biblioteki musi odpowiadać wersji języka Python na serwerze, w przeciwnym razie Zobacz zasłoniętej błędy po wdrożeniu. Inaczej mówiąc, ponieważ wersji języka Python w usłudze App Service, rozszerzenia lokacji są dokładnie takie same jak te wersje wydanej w dniu python.org, można łatwo uzyskać zgodnej wersji dla rozwoju lokalnych. |
| Środowiska wirtualne | Nieobsługiwane. Zamiast tego należy użyć, tworzenie pakietów i ustawić `PYTHONPATH` zmiennej środowiskowej, aby wskazać lokalizację pakietów. |

### <a name="azure-app-service-kudu-console"></a>Konsola Kudu usługi aplikacji Azure

[Konsoli Kudu](https://github.com/projectkudu/kudu/wiki/Kudu-console) umożliwia bezpośrednie, z podwyższonym poziomem uprawnień dostępu do wiersza polecenia do serwera usługi aplikacji i systemu plików. To jest zarówno przydatnym narzędziem debugowania i umożliwia operacji interfejsu wiersza polecenia, takich jak instalowanie pakietów.

1. Otwórz program Kudu ze strony usługi aplikacji w portalu Azure, wybierając **narzędzi programistycznych > Zaawansowane narzędzia**, wybierając **Przejdź**. Ta akcja powoduje przejście do adresu URL, który jest taki sam jak podstawowy aplikacji adres URL Twojej usługi z wyjątkiem z `.scm` wstawiony. Na przykład, jeśli podstawowy adres URL jest `https://vspython-test.azurewebsites.net/` Kudu jest na `https://vspython-test.scm.azurewebsites.net/` (które można dodać do zakładek):

    ![Konsoli Kudu dla usługi Azure App Service](media/python-on-azure-console01.png)

1. Wybierz **konsoli debugowania > CMD** aby otworzyć konsolę, w którym można nawigować do instalacji języka Python i zobacz, co biblioteki są już istnieje.

1. Do zainstalowania jednego pakietu:

    a. Przejdź do folderu instalacji języka Python, w którym chcesz zainstalować pakiet, takich jak `d:\home\python361x64`.

    b. Użyj `python.exe -m pip install <package_name>` do zainstalowania pakietu.

    ![Przykład instalowania bottle za pośrednictwem konsoli Kudu dla usługi Azure App Service](media/python-on-azure-console02.png)

1. Jeśli została wdrożona `requirements.txt` dla aplikacji do serwera, zainstalować te wymagania w następujący sposób:

    a. Przejdź do folderu instalacji języka Python, w którym chcesz zainstalować pakiet, takich jak `d:\home\python361x64`.

    b. Uruchom polecenie `python.exe -m pip install --upgrade -r d:\home\site\wwwroot\requirements.txt`.

    Przy użyciu `requirements.txt` jest zalecane, ponieważ jest łatwy do odtworzenia pakietu dokładną wartość lokalnie i na serwerze. Pamiętaj tylko odwiedzić konsoli po wdrożeniu zmiany wprowadzone w `requirements.txt` i ponownie uruchom polecenie.

> [!Note]
> Nie żadnego kompilatora C z usługi aplikacji, więc musisz zainstalować kółka pod kątem ewentualnych pakietów z modułów macierzystych rozszerzenia. Wiele pakietów popularnych podać własne koła. W przypadku pakietów, które nie należy używać `pip wheel <package_name>` na komputerze lokalnym programowanie i przekazywania następnie kółka do swojej witryny. Na przykład zobacz [zarządzania wymagane pakiety](managing-python-environments-in-visual-studio.md#managing-required-packages-requirementstxt).

### <a name="kudu-rest-api"></a>Program kudu interfejsu API REST

Zamiast używać konsoli Kudu za pośrednictwem portalu Azure, możesz uruchamiać polecenia zdalnie za pomocą interfejsu API REST Kudu publikując polecenie `https://yoursite.scm.azurewebsites.net/api/command`. Na przykład, aby zainstalować `bottle` pakietu, post następujący ciąg JSON do `/api/command`:

```json
{
    "command": 'python.exe -m pip install bottle',
    "dir": '\home\python361x64'
}
```

Aby uzyskać informacje o poleceniach oraz uwierzytelniania, zobacz [dokumentacji Kudu](https://github.com/projectkudu/kudu/wiki/REST-API).

Możesz też sprawdzić za pomocą poświadczeń `az webapp deployment list-publishing-profiles` polecenia za pomocą wiersza polecenia platformy Azure (zobacz [wdrożenia aplikacji sieci Web az](/cli/azure/webapp/deployment?view=azure-cli-latest#az_webapp_deployment_list_publishing_profiles)). Biblioteka pomocnika do ogłaszania Kudu poleceń jest dostępna na [GitHub](https://github.com/lmazuel/azure-webapp-publish/blob/master/azure_webapp_publish/kudu.py#L42).
