---
title: Publikowanie aplikacji w języku Python w usłudze Azure App Service
description: Jak opublikować aplikację sieci web Python bezpośrednio w usłudze Azure App Service w programie Visual Studio, w tym niezbędną treść w pliku web.config.
ms.date: 07/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: c42e87d6dcf4767621cafdb246294b8a45d0e4a7
ms.sourcegitcommit: 0cf1e63b6e0e6a0130668278489b21a6e5038084
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/02/2018
ms.locfileid: "39468673"
---
# <a name="publish-to-azure-app-service"></a>Publikowanie w usłudze Azure App Service

> [!Important]
> Wdrażanie aplikacji w języku Python w usłudze Azure App Service dla systemu Linux nie jest obecnie obsługiwane w programie Visual Studio. Firma Microsoft planuje wycofana języka Python w usłudze App Service na Windows. Aktualizacje zostaną opublikowane w tym artykule, jeśli jest dostępna. W międzyczasie można wdrożyć do usługi App Service w systemie Linux przy użyciu kontenerów. Aby uzyskać więcej informacji, zobacz [wdrażanie aplikacji sieci web języka Python w funkcji Web App for Containers](/azure/app-service/containers/quickstart-python).

Program Visual Studio oferuje możliwość publikowania aplikacji sieci web w języku Python bezpośrednio w usłudze Azure App Service. Publikowanie w usłudze Azure App Service oznacza kopiowanie wymaganych plików do serwera i konfigurowania odpowiednich *web.config* pliku, który powoduje, że serwer sieci web jak uruchomić aplikację.

Proces publikowania różni się od programu Visual Studio 2017 i Visual Studio 2015. W szczególności program Visual Studio 2015 automatyzuje niektóre kroki, w tym tworzenie *web.config*, ale taką automatyzację ogranicza długoterminowe elastyczność i kontrolę. Program Visual Studio 2017 wymaga dodatkowych ręcznych czynności, ale zapewnia dokładniejszą kontrolę nad środowiska Python. Obie opcje są opisane w tym miejscu.

> [!Note]
> Aby uzyskać podstawowe informacje dotyczące zmian między wersjami programu Visual Studio 2015 i Visual Studio 2017, zobacz w blogu, [Opublikuj na platformie Azure w programie Visual Studio 2017](https://blogs.msdn.microsoft.com/pythonengineering/2016/12/12/publish-to-azure-in-vs-2017/).

## <a name="prerequisites"></a>Wymagania wstępne

W ramach tego przewodnika należy projektu aplikacji sieci web, oparte na platformy Bottle, Flask i Django. Jeśli jeszcze nie masz projektu, aby ponowić proces publikowania, Utwórz projekt prosty test w następujący sposób:

1. W programie Visual Studio, wybierz **pliku** > **New** > **projektu**, wyszukaj "Bottle", wybierz **projektu sieci Web Bottle**, określ nazwę i ścieżkę do projektu, kliknij przycisk **OK**. (Szablon Bottle jest uwzględniany z pakietem roboczym programowania Python; zobacz [instalacji](installing-python-support-in-visual-studio.md).)

1. Postępuj zgodnie z monitami, aby zainstalować pakiety zewnętrzne, wybierając **zainstalować w środowisku wirtualnym** i preferowaną podstawowy interpreter dla środowiska wirtualnego. Ten wybór wersji języka Python zainstalowane w usłudze App Service jest zazwyczaj odpowiada.

1. Projekt testowy lokalnie, naciskając klawisz **F5** lub wybierając **debugowania** > **Rozpocznij debugowanie**.

## <a name="create-an-azure-app-service"></a>Tworzenie usługi Azure App Service

Publikowanie na platformie Azure wymaga docelowej usługi App Service. W tym celu można utworzyć usługi App Service przy użyciu subskrypcji platformy Azure, możesz też tymczasową witrynę.

Jeśli nie masz jeszcze subskrypcji, skorzystaj z [bezpłatne konto Azure pełnej](https://azure.microsoft.com/free/), co obejmuje istnieją małe wymogi dotyczące środków na korzystanie z usług platformy Azure. Należy również rozważyć skorzystania [Visual Studio Dev Essentials](https://azure.microsoft.com/pricing/member-offers/vs-dev-essentials/), które zapewnia 25 USD środków co miesiąc przez cały rok.

> [!Tip]
> Mimo że Azure poprosi o podanie karty kredytowej zweryfikować swoje konto, karta nie jest rozliczane. Można również ustawić [limit wydatków](/azure/billing/billing-spending-limit) równa z bezpłatnych środków, aby zagwarantować, że występują nie dodatkowych opłat. Ponadto platforma Azure oferuje bezpłatne usługi App Service za warstwę planu, która doskonale nadaje się dla aplikacji prosty test, zgodnie z opisem w następnej sekcji.

### <a name="use-a-subscription"></a>Użyj subskrypcji

Z aktywną subskrypcją platformy Azure Utwórz usługę App Service przy użyciu pusta aplikacja internetowa w następujący sposób:

1. Zaloguj się na [portal.azure.com](https://portal.azure.com).
1. Wybierz **+ nowy**, a następnie wybierz **sieci Web i mobilność** następuje **aplikacji sieci Web**.
1. Określ nazwę dla aplikacji sieci web, pozostaw **grupy zasobów** do **Utwórz nowy**i wybierz polecenie **Windows** jako system operacyjny.
1. Wybierz **plan App service/lokalizacja**, wybierz opcję **Utwórz nową**i określ nazwę i lokalizację. Następnie wybierz pozycję **warstwa cenowa**, przewiń w dół i wybierz **bezpłatna F1** planowanie, naciśnij klawisz **wybierz**, a następnie **OK** i następnie **Tworzenie**.
1. (Opcjonalnie) Po utworzeniu usługi App Service, przejdź do niego, wybierz **Pobierz profil publikowania**, a następnie zapisz plik lokalnie.

### <a name="use-a-temporary-app-service"></a>Użyj tymczasowych usługi App Service

Tworzenie tymczasowego usługi App Service bez subskrypcji platformy Azure w następujący sposób:

1. Otwórz przeglądarkę, aby [try.azurewebsites.net](https://try.azurewebsites.net).
1. Wybierz **aplikacji sieci Web** typ aplikacji, następnie wybierz **dalej**.
1. Wybierz **pusta witryna**, a następnie **Utwórz**.
1. Zaloguj się przy użyciu społecznościowych logowania wybranego i po pewnym czasie lokacja jest gotowa na wyświetlany adres URL.
1. Wybierz **Pobierz profil publikowania** i Zapisz *.publishsettings* pliku, który można użyć później.

## <a name="configure-python-on-azure-app-service"></a>Konfigurowanie języka Python w usłudze Azure App Service

Po utworzeniu usługi App Service z pustym uruchamiania aplikacji sieci Web (lub w ramach subskrypcji w bezpłatnej lokacji), zainstaluj wybranej wersji języka Python, zgodnie z opisem [zarządzanie z językiem Python w usłudze Azure App Service](managing-python-on-azure-app-service.md). Publikowanie z programu Visual Studio 2017, zarejestruj się w dokładnej ścieżki do interpretera języka Python zainstalowane z rozszerzeniem lokacji zgodnie z opisem w tym artykule.

Jeśli to konieczne, możesz także zainstalować `bottle` pakietu przy użyciu procesu w tych instrukcjach, ponieważ ten pakiet jest zainstalowany jako część druga kroki opisane w tym przewodniku.

## <a name="publish-to-app-service---visual-studio-2017"></a>Publikowanie w usłudze App Service — program Visual Studio 2017

Publikowanie w usłudze Azure App Service z programu Visual Studio 2017 kopiuje tylko pliki w projekcie do serwera. Jest to konieczne, w związku z tym, aby utworzyć pliki niezbędne do skonfigurowania środowiska serwera.

1. W programie Visual Studio **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt i wybierz **Dodaj** > **nowy element**. W wyświetlonym oknie dialogowym wybierz **web.config Pro Azure (Fastcgi)** szablonu, a następnie wybierz **OK**. Spowoduje to utworzenie *web.config* pliku w katalogu głównym projektu.

1. Modyfikowanie `PythonHandler` wpis *web.config* tak, aby ścieżka odpowiada instalację języka Python na serwerze (zobacz [dokumentacja konfiguracji usług IIS](https://www.iis.net/configreference) (iis.net) dla szczegółowymi informacjami na temat). Na przykład w przypadku języka Python 3.6.1 x64 wpis powinna wyglądać następująco:

    ```xml
    <system.webServer>
      <handlers>
        <add name="PythonHandler" path="*" verb="*" modules="FastCgiModule"
            scriptProcessor="D:\home\Python361x64\python.exe|D:\home\Python361x64\wfastcgi.py"
            resourceType="Unspecified" requireAccess="Script"/>
      </handlers>
    </system.webServer>
    ```

1. Ustaw `WSGI_HANDLER` wpisu w *web.config* odpowiednio dla struktury korzystasz:

    - **Bottle**: Dodawanie nawiasów po `app.wsgi_app` jak pokazano poniżej. Jest to konieczne, ponieważ ten obiekt jest funkcją (zobacz *app.py*) zamiast zmiennej:

        ```xml
        <!-- Bottle apps only -->
        <add key="WSGI_HANDLER" value="app.wsgi_app()"/>
        ```

    - **Flask**: zmiana `WSGI_HANDLER` wartość `<project_name>.app` gdzie `<project_name>` jest zgodna z nazwą projektu. Możesz znaleźć dokładny identyfikator, analizując `from <project_name> import app` instrukcji w *runserver.py*. Na przykład jeśli projekt ma nazwę "FlaskAzurePublishExample", wpis wyglądałby następująco:

        ```xml
        <!-- Flask apps only: change the project name to match your app -->
        <add key="WSGI_HANDLER" value="FlaskAzurePublishExample.app"/>
        ```

    - **Django**: dwie zmiany są potrzebne do *web.config* dla projektów Django. Najpierw należy zmienić `WSGI_HANDLER` wartość `django.core.wsgi.get_wsgi_application()` (obiekt jest w *wsgi.py* plików):

        ```xml
        <!-- Django apps only -->
        <add key="WSGI_HANDLER" value="django.core.wsgi.get_wsgi_application()"/>
        ```

        Po drugie, Dodaj następujący wpis poniżej dla `WSGI_HANDLER`, zastępując `DjangoAzurePublishExample` o nazwie projektu:

        ```xml
        <add key="DJANGO_SETTINGS_MODULE" value="DjangoAzurePublishExample.settings" />
        ```

1. **Tylko aplikacje Django**: Projekt w Django *settings.py* plików, Dodawanie domeny do adresu URL witryny `ALLOWED_HOSTS` jak pokazano poniżej, zastępując "vspython-test-02.azurewebsites .net" adres URL, oczywiście:

    ```python
    # Change the URL to your specific site
    ALLOWED_HOSTS = ['vspython-test-02.azurewebsites.net']
    ```

    Błąd podczas dodawania adresu URL do wyników tablicy w błędzie **DisallowedHost na / nieprawidłowy nagłówek HTTP_HOST: "\<adres URL witryny\>". Może być konieczne dodanie "\<adres URL witryny\>" do ALLOWED_HOSTS.**

    Należy pamiętać, że gdy tablica jest pusta, Django automatycznie umożliwia nazwy "Host_lokalny", ale dodanie adresu URL produkcji powoduje usunięcie tej możliwości. Aby z tego powodu należy zachować oddzielne deweloperskich i produkcyjnych kopii *settings.py*, lub użyj zmiennych środowiskowych, aby kontrolować wartości w czasie wykonywania.

1. W **Eksploratora rozwiązań**, rozwiń folder o nazwie taka sama jak projekt, kliknij prawym przyciskiem myszy **statyczne** folderu, wybierz **Dodaj** > **nowy element** , wybierz opcję **Azure statycznych plików web.config** szablonu, a następnie wybierz **OK**. Ta akcja powoduje utworzenie innego *web.config* w *statyczne* folder, który wyłącza Python przetwarzania dla tego folderu. Ta konfiguracja wysyła żądania dotyczące plików statycznych do domyślnego serwera sieci web, a nie przy użyciu aplikacji języka Python.

1. Następnie zapisać projekt, w programie Visual Studio **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt i wybierz **Publikuj**.

    ![Polecenia menu kontekstowego projektu publikowania](media/template-web-publish-command.png)

1. W **Publikuj** kartę, która pojawia się, zaznaczyć miejscem docelowym publikowania:

    1. Subskrypcja platformy Azure: Wybierz **Microsoft Azure App Service**, następnie **wybierz istniejącą** następuje **Publikuj**. Zostanie wyświetlone okno dialogowe, w którym można wybrać odpowiednią subskrypcję i usługi app service. Jeśli nie pojawia się usługa App Service, należy użyć pobrany profil publikowania, zgodnie z poniższym opisem dla tymczasowych usługi App Service.

       ![Publikowanie do usługi Azure kroku 1, Visual Studio 2017, w przypadku istniejących subskrypcji](media/tutorials-common-publish-1a-2017.png)

    2. Jeśli korzystania tymczasowe usługi App Service na try.azurewebsites.net lub w przeciwnym razie należy użyć profilu publikowania, wybierz **\>** formantu, aby znaleźć **Importuj profil**, wybierz tę opcję, następnie Wybierz **Publikuj**. Powoduje wyświetlenie monitu o podanie lokalizacji *.publishsettings* wcześniej pobrany plik.

    ![Publikowanie do usługi Azure kroku 1, Visual Studio 2017 tymczasową aplikację usługi](media/tutorials-common-publish-1b-2017.png)

1. Visual Studio Wyświetla stan publikowania w **działania publikowania internetowego** okna i **Publikuj** okna. Po zakończeniu publikowania w domyślnej przeglądarce otworzy się adres URL witryny. Adres URL jest również wyświetlany na **Publikuj** okna.

1. Po otwarciu przeglądarki może zostać wyświetlony komunikat, **nie można wyświetlić strony, ponieważ wystąpił błąd wewnętrzny serwera.** Ten komunikat oznacza, że środowiska Python na serwerze nie jest w pełni skonfigurowany, w którym to przypadku wykonaj następujące czynności:

    1. Zapoznaj się ponownie do [zarządzanie z językiem Python w usłudze Azure App Service](managing-python-on-azure-app-service.md), upewniając się, że masz odpowiednią języka Python zainstalowane rozszerzenie witryny.

    2. Dokładnie sprawdź ścieżkę do interpretera języka Python w swojej *web.config* pliku. Ścieżka musi dokładnie odpowiadać lokalizacji instalacji rozszerzenia wybranej witryny.

    3. Uaktualnij wszystkie pakiety wymienione w swojej aplikacji za pomocą konsoli Kudu *requirements.txt* pliku: Przejdź do tego samego folderu języka Python, który jest używany w *web.config*, takich jak  */home/python361x64*, i uruchom następujące polecenie, zgodnie z opisem w [konsoli Kudu](managing-python-on-azure-app-service.md#azure-app-service-kudu-console) sekcji:

    ```command
    python -m pip install --upgrade -r /home/site/wwwroot/requirements.txt
    ```

    Jeśli widzisz błędy uprawnień podczas uruchamiania tego polecenia, sprawdź, czy używasz polecenia w folderze rozszerzenia witryny i *nie* w folderze instalacji języka Python domyślnej usługi App Service. Ponieważ nie można modyfikować tych środowisk domyślne, bez obaw próby zainstalowania pakietów zakończy się niepowodzeniem.

    4. Dla danych wyjściowych szczegółowy komunikat o błędzie, należy dodać następujący wiersz do *web.config* w ramach `<system.webServer>` węzła, który umożliwia bardziej szczegółowe dane wyjściowe błędu:

    ```xml
    <httpErrors errorMode="Detailed"></httpErrors>
    ```

    5. Spróbuj ponownie uruchomić usługi App Service po zainstalowaniu nowych pakietów. Ponowne uruchomienie komputera nie jest konieczne w przypadku zmiany *web.config*, jak usługa App Service, automatyczne ponowne uruchomienie zawsze, gdy *web.config* zmiany.

    > [!Tip]
    > Jeśli wprowadzisz zmiany do swojej aplikacji *requirements.txt* pliku, pamiętaj ponownie użyć konsoli Kudu, aby zainstalować wszystkie pakiety, które są teraz wymienione w tym pliku.

1. Po skonfigurowaniu w pełni środowisko serwera, Odśwież stronę w przeglądarce i aplikacji sieci web powinna zostać wyświetlona.

    ![Wyniki publikowania aplikacji Bottle, Flask i Django w usłudze App Service](media/azure-publish-results.png)

## <a name="publish-to-app-service---visual-studio-2015"></a>Publikowanie w usłudze App Service — program Visual Studio 2015

> [!Note]
> Krótki film tego procesu można znaleźć na [samouczek Visual Studio języka Python: tworzenie witryny sieci Web](https://www.youtube.com/watch?v=FJx5mutt1uk&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=6) (witrynie youtube.com, 3m10s).

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt i wybierz **Publikuj**.

1. W **Publikuj** okno dialogowe, wybierz opcję **Microsoft Azure App Service**:

  ![Publikowanie do usługi Azure, krok 1](media/tutorials-common-publish-1.png)

1. Wybieranie klasy docelowej:

    - Jeśli masz subskrypcję platformy Azure, wybierz **Microsoft Azure App Service** jako miejscem docelowym publikowania, następnie w oknie dialogowym poniżej wybierz istniejącej usługi App Service lub **New** Aby utworzyć nową.
    - Jeśli używasz tymczasową witrynę z try.azurewebsites.net wybierz **importu** jako miejscem docelowym publikowania, następnie Przeglądaj w poszukiwaniu *.publishsettings* plik pobrany z witryny i wybierz **OK** .

1. Szczegóły usługi App Service są wyświetlane w **Publikuj** okna dialogowego **połączenia** poniższej karcie.

  ![Publikowanie do usługi Azure, krok 2](media/tutorials-common-publish-2.png)

1. Wybierz **dalej** zgodnie z potrzebami, aby przejrzeć dodatkowe ustawienia. Jeśli planujesz [zdalne debugowanie kodu w języku Python na platformie Azure](debugging-remote-python-code-on-azure.md), należy ustawić **konfiguracji** do **debugowania**

1. Wybierz **publikowania**. Gdy aplikacja jest wdrażana na platformie Azure, domyślnej przeglądarki otwiera się w danej lokacji.

W ramach tego procesu Visual Studio wykona następujące czynności:

- Tworzenie *web.config* pliku na serwerze, który zawiera odpowiednie wskaźniki do aplikacji `wsgi_app` działać, a w usłudze App Service domyślnie języka Python 3.4 interpretera.
- Wyłącz przetwarzanie plików w projekcie *statyczne* folder (reguł dla tego znajdują się w *web.config*).
- Opublikuj w środowisku wirtualnym na serwerze.
- Dodaj *web.debug.config* plików i ptvsd narzędzia, aby umożliwić debugowanie zdalne debugowanie.

Jak wspomniano wcześniej, te kroki automatyczne uprościć proces publikowania, ale utrudnić do kontrolowania środowiska Python. Na przykład *web.config* pliku jest tworzony tylko na serwerze, ale nie są dodawane do projektu. Proces publikowania również trwa dłużej, ponieważ ona jest kopiowanie środowiska zupełnie wirtualnego z komputera dewelopera zamiast polegania na konfigurację serwera.

Po pewnym czasie może chcesz zachować swoje własne *web.config* pliku i użyć *requirements.txt* bezpośrednio utrzymanie pakiety na serwerze. Za pomocą *requirements.txt*, w szczególności gwarantuje, że zawsze być zgodna swoje środowiska deweloperskie i serwera.

## <a name="remote-debugging-on-azure-app-service"></a>Zdalne debugowanie w usłudze Azure App Service

Po opublikowaniu **debugowania** konfiguracji z programu Visual Studio 2015, proces automatycznie tworzy *web.debug.config* plików i dodaje *ptvsd* folder zawierający niezbędne narzędzia do debugowania.

Za pomocą programu Visual Studio 2017 zamiast tego dodać te składniki bezpośrednio do projektu. Kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań**, wybierz opcję **Dodaj** > **nowy element**i wybierz **Azure debugowanie zdalne web.config** szablonu. Debugowanie *web.debug.config* pliku i *ptvsd* folderu narzędzia są wyświetlane w projekcie.

Wdrożenie tych plików na serwerze (automatycznie przy użyciu programu Visual Studio 2015; następnie opublikować za pomocą programu Visual Studio 2017), możesz wykonać instrukcje dotyczące [zdalne debugowanie platformy Azure](debugging-remote-python-code-on-azure.md).
