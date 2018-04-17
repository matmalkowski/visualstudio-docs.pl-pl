---
title: Publikowanie aplikacji Python w usłudze Azure App Service
description: Jak opublikować aplikację sieci web języka Python bezpośrednio w usłudze Azure App Service w programie Visual Studio, w tym wymaganej zawartości w pliku web.config.
ms.custom: ''
ms.date: 09/27/2017
ms.technology:
- devlang-python
dev_langs:
- python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: f2aeaa9b9b7b0f6370ec7590bd2eb754b893aa2c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="publishing-to-azure-app-service"></a>Publikowanie w usłudze Azure App Service

Program Visual Studio oferuje możliwość publikowania aplikacji sieci web języka Python bezpośrednio w usłudze Azure App Service. Publikowanie w usłudze Azure App Service oznacza kopiowania plików na potrzeby serwera i konfigurując odpowiednie `web.config` pliku, który powoduje, że serwer sieci web jak uruchomić aplikację.

Proces publikowania różni się od programu Visual Studio 2017 i programu Visual Studio 2015. W szczególności programu Visual Studio 2015 automatyzuje, niektóre kroki, w tym tworzenie `web.config`, ale ta Automatyzacja ogranicza długoterminowej elastyczność i kontrolę. Visual Studio 2017 wymaga więcej czynności ręcznych, ale zapewnia dokładniejszą kontrolę nad środowiska Python. Obie te opcje są opisane poniżej.

> [!Note]
> Dalsze informacje o zmianach między Visual Studio 2015 i Visual Studio 2017, można znaleźć w blogu, [publikowania na platformie Azure w programie Visual Studio 2017](https://blogs.msdn.microsoft.com/pythonengineering/2016/12/12/publish-to-azure-in-vs-2017/).

## <a name="prerequisites"></a>Wymagania wstępne

W ramach tego przewodnika należy projektu aplikacji sieci web oparta na platformach Bottle, Flask i Django. Jeśli nie masz jeszcze projektu, aby ponowić proces publikowania Utwórz projekt testowy proste w następujący sposób:

1. W programie Visual Studio, wybierz **Plik > Nowy > Projekt**, wyszukaj "Bottle", wybierz **projektu sieci Web Bottle**, określ, jak i nazwę i ścieżkę do projektu, kliknij przycisk **OK**. (Szablon Bottle jest dołączana do obciążenia programowania Python; zobacz [instalacji](installing-python-support-in-visual-studio.md).)

1. Postępuj zgodnie z monitami, aby zainstalować pakiety zewnętrzne, wybierając **zainstalować w środowisku wirtualnym** i preferowany podstawowy interpreter środowiska wirtualnego. Zazwyczaj odpowiada ten wybór z wersją programu Python zainstalowanym usługi aplikacji.

1. Testowanie projektu lokalnie naciśnięcie klawisza F5 lub wybierając **Debuguj > Rozpocznij debugowanie**.

## <a name="create-an-azure-app-service"></a>Tworzenie usługi aplikacji Azure

Publikowanie na platformie Azure wymaga docelowej usługi aplikacji. W tym celu można utworzyć usługę aplikacji przy użyciu subskrypcji platformy Azure lub za pośrednictwem tymczasowego witryny.

Jeśli nie masz już subskrypcję, Rozpocznij od [bezpłatne konto Azure pełnej](https://azure.microsoft.com/free/), w tym atrakcyjnych środki na korzystanie z usług Azure. Należy również rozważyć skorzystania [podstawowe informacje dotyczące programu Visual Studio Dev](https://azure.microsoft.com/pricing/member-offers/vs-dev-essentials/), które zapewnia środki 25 co miesiąc przez cały rok.

> [!Tip]
> Mimo że Azure wprowadza się karty kredytowej, aby zweryfikować swoje konto, nie jest pobierana karty. Można również ustawić [limit wydatków](/azure/billing/billing-spending-limit) równa z bezpłatnych środków w celu zagwarantowania, że występuje nie dodatkowych opłat. Ponadto platforma Azure udostępnia bezpłatnej usługi aplikacji warstwy planu, który jest odpowiedni dla aplikacji prosty test zgodnie z opisem w następnej sekcji.

### <a name="using-a-subscription"></a>Przy użyciu subskrypcji

Z aktywną subskrypcją platformy Azure utworzenie aplikacji usługi z pustą aplikację sieci Web w następujący sposób:

1. Zaloguj się na stronie [portal.azure.com](https://portal.azure.com).
1. Wybierz **+ nowy**, a następnie wybierz pozycję **sieci Web i mobilność** następuje **aplikacji sieci Web**.
1. Określ nazwę dla aplikacji sieci web, pozostaw **grupy zasobów** do "Utwórz nowy" i wybierz polecenie **Windows** jako systemu operacyjnego.
1. Wybierz **lokalizacja planu usługi aplikacji**, wybierz pozycję **Utwórz nowy**i określ nazwę i lokalizację. Następnie wybierz **warstwa cenowa**, przewiń w dół i wybierz **F1 bezpłatna** planowanie, naciśnij klawisz **wybierz**, a następnie **OK** , a następnie **Utworzyć**.
1. (Opcjonalnie) Po utworzeniu usługi App Service, przejdź do niego, wybierz **profilu publikowania Get**i Zapisz plik lokalnie.

### <a name="using-a-temporary-app-service"></a>Przy użyciu tymczasowego usługi aplikacji

Tworzenie tymczasowych usługi aplikacji bez konieczności subskrypcji platformy Azure w następujący sposób:

1. Otwórz przeglądarkę, aby [try.azurewebsites.net](https://try.azurewebsites.net).
1. Wybierz **aplikacji sieci Web** typu aplikacji, następnie wybierz **dalej**.
1. Wybierz **pusta witryna**, a następnie **Utwórz**.
1. Zaloguj się przy użyciu społecznościowych logowania wybranych przez użytkownika, a po pewnym czasie jest gotowy na wyświetlany adres URL witryny.
1. Wybierz **Pobierz profil publikowania** i Zapisz `.publishsettings` pliku, który można użyć później.

## <a name="configure-python-on-azure-app-service"></a>Konfigurowanie języka Python w usłudze aplikacji Azure

Po utworzeniu aplikacji usługi z pustą uruchomieniu aplikacji sieci Web (lub w ramach subskrypcji w witrynie wolnego), zainstaluj wybranej wersji języka Python, zgodnie z opisem [Zarządzanie Python w usłudze Azure App Service](managing-python-on-azure-app-service.md). Publikowanie z programu Visual Studio 2017 r, zarejestruj się w dokładnej ścieżki interpreter języka Python zainstalowane z rozszerzeniem lokacji zgodnie z opisem w tym artykule.

W razie potrzeby można również zainstalować `bottle` pakietu przy użyciu procesu w tych instrukcjach, ponieważ ten pakiet jest zainstalowany jako część innych kroków w tym przewodniku.

## <a name="publish-to-app-service---visual-studio-2017"></a>Publikowanie do usługi App Service — Visual Studio 2017 r.

Publikowanie do usługi Azure App Service z kopii programu Visual Studio 2017 tylko pliki w projekcie do serwera. Jest to konieczne, w związku z tym można utworzyć pliki niezbędne do skonfigurowania środowiska serwera.

1. W programie Visual Studio **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt i wybierz **Dodaj > Nowy element...* . W oknie dialogowym wybierając szablon "Azure" web.config"(Fast CGI) i wybierz OK. Spowoduje to utworzenie `web.config` pliku w katalogu głównym projektu.

1. Modyfikowanie `PythonHandler` wpis w `web.config` , aby ścieżka instalacji języka Python na serwerze. Na przykład dla języka Python 3.6.1 x64 wpis powinna wyglądać następująco:

    ```xml
    <system.webServer>
      <handlers>
        <add name="PythonHandler" path="*" verb="*" modules="FastCgiModule"
            scriptProcessor="D:\home\Python361x64\python.exe|D:\home\Python361x64\wfastcgi.py"
            resourceType="Unspecified" requireAccess="Script"/>
      </handlers>
    </system.webServer>
    ```

1. Ustaw `WSGI_HANDLER` wpis w `web.config` odpowiednio dla struktury używasz:

    - **Bottle**: Dodaj nawiasy po `app.wsgi_app` jak pokazano poniżej. Jest to konieczne, ponieważ ten obiekt jest funkcją (zobacz `app.py`) zamiast zmiennej:

        ```xml
        <!-- Bottle apps only -->
        <add key="WSGI_HANDLER" value="app.wsgi_app()"/>
        ```

    - **Flask**: zmiana `WSGI_HANDLER` do wartości `<project_name>.app` gdzie `<project_name>` jest zgodna z nazwą projektu. Dokładnego identyfikatora można znaleźć, sprawdzając `from <project_name> import app` instrukcji w `runserver.py`. Na przykład jeśli projekt ma nazwę "FlaskAzurePublishExample", wpis będzie wyglądać następująco:

        ```xml
        <!-- Flask apps only: change the project name to match your app -->
        <add key="WSGI_HANDLER" value="FlaskAzurePublishExample.app"/>
        ```

    - **Django**: dwie zmiany są potrzebne do `web.config` dla aplikacji Django. Najpierw należy zmienić `WSGI_HANDLER` do wartości `django.core.wsgi.get_wsgi_application()` (obiekt jest w `wsgi.py` pliku):

        ```xml
        <!-- Django apps only -->
        <add key="WSGI_HANDLER" value="django.core.wsgi.get_wsgi_application()"/>
        ```

        Po drugie, Dodaj następujący wpis poniżej dla `WSGI_HANDLER`, zastępując `DjangoAzurePublishExample` o nazwie projektu:

        ```xml
        <add key="DJANGO_SETTINGS_MODULE" value="DjangoAzurePublishExample.settings" />
        ```

1. **Tylko aplikacje Django**: W folderze, który jest zgodna z nazwą projektu, otwórz `settings.py` i Dodaj domenę adres URL witryny do `ALLOWED_HOSTS` jak pokazano poniżej, zastępując "vspython-test-02.azurewebsites .net" adres URL oczywiście:

    ```python
    # Change the URL to your specific site
    ALLOWED_HOSTS = ['vspython-test-02.azurewebsites.net']
    ```

    Błąd podczas dodawania adresu URL do tablicy spowoduje błąd "DisallowedHost w lub nieprawidłowy nagłówek HTTP_HOST:"\<adres URL witryny\>". Może być konieczne dodanie "\<adres URL witryny\>" do ALLOWED_HOSTS. "

1. W **Eksploratora rozwiązań**, rozwiń folder o nazwie takiej jak projektu, kliknij prawym przyciskiem myszy `static` folderu, wybierz opcję **Dodaj > Nowy element...** , wybierz szablon "Azure statycznych plików web.config" i wybierz **OK**. Ta akcja tworzy innego `web.config` w `static` folderu, które wyłączają Python przetwarzania dla tego folderu. Ta konfiguracja wysyła żądań dotyczących plików statycznych do domyślnego serwera sieci web, a nie za pomocą aplikacji Python.

1. Następnie zapisać projekt, w programie Visual Studio **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt i wybierz **publikowania**.

1. W **publikowania** karty zostanie wyświetlone, wybierz cel publikowania:

    a. Subskrypcji platformy Azure: Wybierz **Microsoft Azure App Service**, następnie **wybierz istniejącą** następuje **publikowania**. Zostanie wyświetlone okno dialogowe, w którym można wybrać odpowiednią subskrypcję i usłudze aplikacji. Jeśli nie ma usługi App Service, użyj pobrany profil publikowania, zgodnie z poniższym opisem dla tymczasowych usługi aplikacji.

    ![Publikowanie do usługi Azure kroku 1, Visual Studio 2017 r, istniejące subskrypcje](media/tutorials-common-publish-1a-2017.png)

    b. Jeśli używany tymczasowego usługi aplikacji na try.azurewebsites.net lub w przeciwnym razie należy użyć profilu publikowania, wybierz **>** formantu, aby znaleźć **Importowanie profilu**, wybierz tę opcję, następnie Wybierz **publikowania**. Powoduje wyświetlenie monitu o lokalizacji `.publishsettings` wcześniej pobrany plik.

    ![Publikowanie do usługi Azure kroku 1, Visual Studio 2017 r, tymczasowy aplikacji usługi](media/tutorials-common-publish-1b-2017.png)

1. Visual Studio Wyświetla stan publikowania w okna "Działania usługi sieci Web publikowanie" i publikacji. Po zakończeniu publikowania w domyślnej przeglądarce otworzy adres URL witryny. Adres URL jest także wyświetlany w oknie publikowania.

1. Po otwarciu przeglądarki może zostać wyświetlony komunikat, "nie można wyświetlić strony, ponieważ wystąpił wewnętrzny błąd serwera." Ten komunikat oznacza, że środowiska Python, na serwerze nie jest całkowicie skonfigurowany, w którym to przypadku należy wykonać poniższe kroki:

    a. Odwołuje się ponownie do [Zarządzanie Python w usłudze Azure App Service](managing-python-on-azure-app-service.md), upewniając się, że masz odpowiednie Python lokacji zainstalowane rozszerzenia.

    b. Sprawdź ścieżkę do interpreter języka Python w Twojej `web.config` pliku. Ścieżka musi dokładnie odpowiadać rozszerzenia lokacji wybranej lokalizacji instalacji.

    c. Uaktualnij wszystkie pakiety wymienione w Twojej aplikacji za pomocą konsoli Kudu `requirements.txt` plik: Przejdź do tego samego folderu języka Python, który jest używany w `web.config`, takich jak `/home/python361x64`, i uruchom następujące polecenie, zgodnie z opisem w [Kudu konsoli](managing-python-on-azure-app-service.md#azure-app-service-kudu-console)sekcji:

    ```command
    python -m pip install --upgrade -r /home/site/wwwroot/requirements.txt
    ```

    Jeśli występuje błąd uprawnień podczas uruchamiania tego polecenia, sprawdź, czy używasz polecenia w folderze rozszerzenia lokacji i *nie* w folderze instalacji języka Python domyślne usługi aplikacji. Ponieważ nie można modyfikować tych środowisk domyślne, pewnością próby zainstalowania pakietów nie powiedzie się.

    d. Aby uzyskać szczegółowe informacje o błędzie wyniki, Dodaj następujący wiersz do `web.config` w `<system.webServer>` węzła, który zawiera bardziej szczegółowe dane wyjściowe błędów:

    ```xml
    <httpErrors errorMode="Detailed"></httpErrors>
    ```

    e. Spróbuj ponownie uruchomić usługę aplikacji po zainstalowaniu nowych pakietów. Ponowne uruchomienie komputera nie jest konieczne w przypadku zmiany `web.config`, tak jak w przypadku usługi aplikacji — automatyczne ponowne uruchomienie po każdej zmianie `web.config` zmiany.

    > [!Tip] 
    > Jeśli wprowadzisz zmiany do swojej aplikacji `requirements.txt` plików, należy ponownie zainstalować wszystkie pakiety, które są teraz wymienione w tym pliku przy użyciu konsoli Kudu. 

1. Po skonfigurowaniu pełni środowiska serwera, Odśwież stronę w przeglądarce i powinna zostać wyświetlona aplikacja sieci web.

    ![Wyniki publikowania aplikacji Bottle, Flask i Django w usłudze App Service](media/azure-publish-results.png)

## <a name="publishing-to-app-service---visual-studio-2015"></a>Publikowanie w usłudze App Service — Visual Studio 2015

> [!Note] 
> Krótki film tego procesu można znaleźć w [Visual Studio Python samouczek: tworzenie witryny sieci Web](https://www.youtube.com/watch?v=FJx5mutt1uk&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=6) (witrynie youtube.com, 3m10s).

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt wybierz **publikowania**.

1. W **publikowania** okno dialogowe, wybierz opcję **Microsoft Azure App Service**:

  ![Publikowanie do usługi Azure, krok 1](media/tutorials-common-publish-1.png)

1. Wybierz element docelowy:

    - Jeśli masz subskrypcję platformy Azure, wybierz **Microsoft Azure App Service** jako miejsce docelowe publikowania, następnie w oknie dialogowym następujące wybierz istniejącą usługę aplikacji lub **nowy** Aby utworzyć nowy.
    - Jeśli używasz tymczasowego witryny z try.azurewebsites.net wybierz **importu** jako miejsce docelowe publikowania, następnie przejdź do `.publishsettings` plik pobrany z witryny i wybierz **OK**.

1. Szczegóły usługi aplikacji są wyświetlane w **publikowania** okna dialogowego **połączenia** poniższej karcie.

  ![Publikowanie do usługi Azure, krok 2](media/tutorials-common-publish-2.png)

1. Wybierz **Dalej >** zgodnie z potrzebami, aby przejrzeć dodatkowe ustawienia. Jeśli planujesz [zdalne debugowanie kodu Python na platformie Azure](debugging-remote-python-code-on-azure.md), należy ustawić **konfiguracji** do **debugowania**

1. Wybierz **publikowania**. Po wdrożeniu aplikacji na platformie Azure domyślnej przeglądarki zostanie otwarty w tej witrynie. 

W ramach tego procesu Visual Studio wykonuje następujące czynności:

- Utwórz `web.config` plików na serwerze, który zawiera odpowiednie wskaźniki w aplikacji `wsgi_app` funkcji i aplikacji usługi domyślne języka Python 3.4 interpreter.
- Wyłącz przetwarzanie plików do projektu `static` folder (są to zasady `web.config`).
- Opublikuj w środowisku wirtualnym na serwerze.
- Dodaj `web.debug.config` plików i ptvsd narzędzia, aby włączyć debugowanie zdalnego debugowania.

Jak wspomniano wcześniej, te kroki automatyczne uprościć proces publikowania, ale utrudnić do kontrolowania środowiska Python. Na przykład `web.config` plik jest tworzone tylko na serwerze, ale nie zostały dodane do projektu. Proces publikowania również trwa dłużej, ponieważ jego jest kopiowanie całego wirtualnego środowiska na komputerze projektowym zamiast polegania na konfigurację serwera.

Po pewnym czasie można zachować swoje własne `web.config` pliku i użyć `requirements.txt` do obsługi pakietów na serwerze bezpośrednio. Przy użyciu `requirements.txt`, w szczególności gwarantuje, zgodnych zawsze środowiska programowania i serwera.

## <a name="remote-debugging-on-azure-app-service"></a>Debugowanie zdalne w usłudze Azure App Service

Podczas publikowania konfiguracji debugowania z programu Visual Studio 2015, proces automatycznie tworzy `web.debug.config` plików i dodaje `ptvsd` folderu zawierającego niezbędne debugowania narzędzi.

Z programu Visual Studio 2017 r możesz zamiast tego dodać te składniki bezpośrednio do projektu. Kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań**, wybierz pozycję **Dodaj > Nowy element...** i wybierz szablon "Azure zdalnego debugowania pliku web.config". Debugowanie `web.debug.config` pliku i `ptvsd` folderu narzędzia są wyświetlane w projekcie.

Gdy pliki te zostały wdrożone na serwerze (automatycznie z programem Visual Studio 2015; na następnego opublikować z programu Visual Studio 2017 r), można postępuj zgodnie z instrukcjami dotyczącymi [Azure zdalne debugowanie](debugging-remote-python-code-on-azure.md).
