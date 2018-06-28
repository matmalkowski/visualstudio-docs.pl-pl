---
title: Zdalne debugowanie ASP.NET na komputerze zdalnym usług IIS | Dokumentacja firmy Microsoft
ms.custom: remotedebugging
ms.date: 05/21/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 9cb339b5-3caf-4755-aad1-4a5da54b2a23
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 4a08c957e03dd2df80d9b3b770e569ba1e64104f
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2018
ms.locfileid: "37057895"
---
# <a name="remote-debug-aspnet-on-a-remote-iis-computer"></a>Zdalne debugowanie ASP.NET na komputerze zdalnym usług IIS
Do debugowania aplikacji ASP.NET, która została wdrożona do usług IIS, zainstalować i uruchomić narzędzia zdalnej na komputerze, których wdrożono aplikację, a następnie dołącz do uruchomionej aplikacji z programu Visual Studio.

![Składniki zdalnego debugera](../debugger/media/remote-debugger-aspnet.png "Remote_debugger_components")

W tym przewodniku opisano sposób konfigurowania i konfigurowania aplikacji programu Visual Studio 2017 ASP.NET MVC 4.5.2, wdrażanie usług IIS i uruchomić zdalnego debugera z programu Visual Studio.

> [!NOTE]
> Do zdalnego debugowania ASP.NET Core zamiast niego, zobacz [zdalnego debugowania ASP.NET Core na komputerze IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md). Dla usługi Azure App Service można łatwe wdrażanie i debugowanie na wstępnie skonfigurowane wystąpienia usług IIS przy użyciu [debugera migawki](../debugger/debug-live-azure-applications.md) (.NET 4.6.1 wymagane) lub [dołączanie debugera z Eksploratora serwera](../debugger/remote-debugging-azure.md).

Procedury te zostały przetestowane na tych konfiguracji serwera:
* Windows Server 2012 R2 i IIS 8 (dla systemu Windows Server 2008 R2 kroki serwera są różne)

## <a name="requirements"></a>Wymagania

Zdalny debuger jest obsługiwana w systemie Windows Server, począwszy od systemu Windows Server 2008 Service Pack 2. Aby uzyskać pełną listę wymagań, zobacz [wymagania](../debugger/remote-debugging.md#requirements_msvsmon).

> [!NOTE]
> Debugowanie między dwoma komputerami połączone za pośrednictwem serwera proxy nie jest obsługiwane. Debugowanie za pośrednictwem duże opóźnienie lub połączenie o niskiej przepustowości, takich jak Internet, połączenia telefonicznego lub przez Internet między krajów nie jest zalecana i może się nie powieść lub zbyt wolno.

## <a name="app-already-running-in-iis"></a>Aplikacja już uruchomione w usługach IIS?

Ten artykuł zawiera kroki na konfigurowaniu podstawowych konfiguracji usług IIS w systemie Windows server i wdrażania aplikacji w programie Visual Studio. Te kroki są dołączone do upewnij się, że serwer ma wymagane składniki zainstalowane, że aplikacja może działać prawidłowo, a można przystąpić do zdalnego debugowania.

* Jeśli aplikacja działa w usługach IIS i po prostu chcesz pobrać zdalnego debugera i Rozpocznij debugowanie, przejdź do [pobrać i zainstalować narzędzia zdalnego w systemie Windows Server](#BKMK_msvsmon).

* Jeśli potrzebujesz pomocy, aby upewnić się, że aplikacja jest skonfigurowany, wdrożona i działają poprawnie w usługach IIS tak, aby umożliwić debugowanie, wykonaj wszystkie kroki opisane w tym temacie.

## <a name="create-the-aspnet-452-application-on-the-visual-studio-computer"></a>Utwórz platformy ASP.NET 4.5.2 aplikacji na komputerze programu Visual Studio
  
1. Tworzenie nowej aplikacji MVC ASP.NET. (**Plik > Nowy > Projekt**, a następnie wybierz pozycję ** Visual C# > sieci Web > Aplikacja sieci Web ASP.NET. W **ASP.NET 4.5.2** sekcji szablonów, wybierz opcję **MVC**. Upewnij się, że **Włącz obsługę Docker** nie jest zaznaczone, a **uwierzytelniania** ustawiono **bez uwierzytelniania**. Nazwij projekt **MyASPApp**.)

2. Otwórz plik HomeController.cs i ustaw punkt przerwania `About()` metody.

## <a name="bkmk_configureIIS"></a> Instalowanie i konfigurowanie usług IIS w systemie Windows Server

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Zaktualizuj ustawienia zabezpieczeń przeglądarki w systemie Windows Server

Jeśli Konfiguracja zwiększonych zabezpieczeń jest włączona w programie Internet Explorer (jest ona włączona domyślnie), następnie należy dodać niektóre domeny jako zaufane witryny, aby możliwe było pobrać niektórych składników serwera sieci web. Dodaj zaufanych witryn, przechodząc do **Opcje internetowe > Zabezpieczenia > Zaufane witryny > witryny**. Dodaj następujące domeny.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- Program IIS.NET

Podczas pobierania oprogramowania może otrzymywać żądania udzielenia uprawnienie do ładowania różnych skrypty witryny sieci web i zasobów. Niektóre z tych zasobów nie są wymagane, ale w celu uproszczenia procesu, kliknij przycisk **Dodaj** po wyświetleniu monitu.

## <a name="BKMK_deploy_asp_net"></a> Zainstaluj program ASP.NET 4.5 w systemie Windows Server

Jeśli chcesz, aby uzyskać szczegółowe informacje, aby zainstalować program ASP.NET w usługach IIS, zobacz [IIS 8.0 przy użyciu programu ASP.NET 3.5 i ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

1. W lewym okienku w Menedżerze serwera wybierz **IIS**. Kliknij prawym przyciskiem myszy serwer, a następnie wybierz **Internet Information Services (IIS) Manager**.

1. Instalator platformy sieci Web (WebPI) należy zainstalować funkcję ASP.NET 4.5 (z węzła serwera w systemie Windows Server 2012 R2, wybierz **pobrać nowych składników platformy sieci Web** , a następnie wyszukaj ASP.NET)

    ![RemoteDBG_IIS_AspNet_45](../debugger/media/remotedbg_iis_aspnet_45.png "RemoteDBG_IIS_AspNet_45")

    > [!NOTE]
    > Jeśli używasz systemu Windows Server 2008 R2 można zainstalować programu ASP.NET 4 zamiast za pomocą tego polecenia:

     **C:\Windows\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -ir**

2. Ponowne uruchomienie systemu (lub wykonać **net stop została /y** następuje **net start w3svc** z wiersza polecenia, aby pobrać zmiany systemowej PATH).

## <a name="choose-a-deployment-option"></a>Wybierz opcję wdrożenia

Aby uzyskać pomoc, aby wdrożyć aplikację do usług IIS, należy wziąć pod uwagę następujące opcje:

* Wdrażanie, tworząc plik ustawień publikowania w usługach IIS i importowania ustawień w programie Visual Studio. W niektórych scenariuszach jest szybkim sposobem wdrożenia aplikacji. Podczas tworzenia pliku ustawień publikowania uprawnienia automatycznie są konfigurowane w usługach IIS.

* Wdrożenie przez publikowanie do folderu lokalnego i kopiowanie danych wyjściowych za pomocą preferowanej metody do folderu aplikacji przygotowane w usługach IIS.

## <a name="optional-deploy-using-a-publish-settings-file"></a>(Opcjonalnie) Wdrażanie przy użyciu pliku ustawień publikowania

Tej opcji można użyć Utwórz plik ustawień publikowania i zaimportuj go do programu Visual Studio.

> [!NOTE]
> Ta metoda wdrażania korzysta z narzędzia Web Deploy. Jeśli chcesz skonfigurować narzędzie Web Deploy ręcznie w programie Visual Studio zamiast importowania ustawień, należy zainstalować 3,6 wdrażania sieci Web zamiast 3,6 wdrażania sieci Web Hosting serwerów. Jednak jeśli konfigurujesz narzędzia Web Deploy ręcznie, należy upewnić się, że folder aplikacji na serwerze skonfigurowano poprawne wartości i uprawnienia (zobacz [witryny sieci Web ASP.NET skonfigurować](#BKMK_deploy_asp_net)).

### <a name="install-and-configure-web-deploy-for-hosting-servers-on-windows-server"></a>Instalowanie i Konfigurowanie narzędzia Web Deploy dla hostingu serwerów w systemie Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Utwórz plik ustawień publikowania w usługach IIS w systemie Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importowanie ustawień publikowania w programie Visual Studio i wdrażanie

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

Po aplikacji wdraża się pomyślnie, należy uruchomić automatycznie. Jeśli aplikacja nie zostanie uruchomiony z programu Visual Studio, uruchomić aplikację w usługach IIS.

1. W **ustawienia** okno dialogowe, Włącz debugowanie klikając **dalej**, wybierz **debugowania** konfiguracji, a następnie wybierz pozycję **Usuń dodatkowe pliki w docelowy** w obszarze **publikowania pliku** opcje.

    > [!NOTE]
    > Wybranie opcji konfiguracji wydania, należy wyłączyć debugowanie w *web.config* pliku podczas publikowania.

1. Kliknij przycisk **zapisać** , a następnie ponownie opublikować aplikację.

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>(Opcjonalnie) Wdrażanie poprzez publikowanie do folderu lokalnego

Ta opcja służy do wdrożenia aplikacji, jeśli chcesz skopiować aplikacji usług IIS przy użyciu programu Powershell, RoboCopy, lub chcesz ręcznie skopiować pliki.

### <a name="BKMK_deploy_asp_net"></a> Konfigurowanie witryny sieci Web ASP.NET na komputerze serwera systemu Windows

1. Otwórz Eksploratora Windows i Utwórz nowy folder **C:\Publish**, których później będą wdrażać projektu programu ASP.NET.

2. Jeśli go nie jest jeszcze otwarty, otwórz **Internet Information Services (IIS) Manager**. (W lewym okienku w Menedżerze serwera wybierz **IIS**. Kliknij prawym przyciskiem myszy serwer, a następnie wybierz **Internet Information Services (IIS) Manager**.)

3. W obszarze **połączeń** w okienku po lewej stronie, przejdź do **witryny**.

4. Wybierz **domyślna witryna sieci Web**, wybierz **podstawowe ustawienia**i ustaw **ścieżka fizyczna** do **C:\Publish**.

5. Kliknij prawym przyciskiem myszy **domyślna witryna sieci Web** a następnie wybierz węzeł **Dodawanie aplikacji**.

6. Ustaw **Alias** do **MyASPApp**, zaakceptuj wartość domyślną pulę aplikacji (**DefaultAppPool**) i ustaw **ścieżka fizyczna** do  **C:\Publish**.

7. W obszarze **połączeń**, wybierz pozycję **pul aplikacji**. Otwórz **DefaultAppPool** i ustaw dla pola puli aplikacji **ASP.NET v4.0** (ASP.NET 4.5 nie jest opcją dla puli aplikacji).

8. Z witryną wybrane w Menedżerze usług IIS, wybierz **Edytuj uprawnienia**i upewnij się, że IUSR, IIS_IUSRS lub nazwą użytkownika skonfigurowaną dla puli aplikacji jest autoryzowanym użytkownikiem z prawami Odczyt i wykonywanie. Jeśli żaden z tych użytkowników nie jest obecny, Dodaj konta IUSR jako użytkownik z uprawnieniami Odczyt i wykonywanie.

### <a name="publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>Publikowanie i wdrażanie aplikacji przez publikowanie do folderu lokalnego z programu Visual Studio

Można również publikowanie i wdrażanie aplikacji przy użyciu systemu plików lub innych narzędzi.

1. (PLATFORMY ASP.NET 4.5.2) Upewnij się, że plik web.config zawiera poprawną wersję programu .NET Framework.  Na przykład jeśli ma być przeznaczona dla platformy ASP.NET 4.5.2, upewnij się, że ta wersja jest wymieniony w pliku web.config.
  
    ```xml
    <system.web>
      <compilation debug="true" targetFramework="4.5.2" />
      <httpRuntime targetFramework="4.5.2" />
      <httpModules>
        <add name="ApplicationInsightsWebTracking" type="Microsoft.ApplicationInsights.Web.ApplicationInsightsHttpModule, Microsoft.AI.Web" />
      </httpModules>
    </system.web>
  
    ```

    Powinna to być na przykład, wersja 4.0, instalowanie platformy ASP.NET 4 zamiast 4.5.2.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

## <a name="BKMK_msvsmon"></a> Pobierz i zainstaluj narzędzia zdalnego w systemie Windows Server

W tym samouczku używamy programu Visual Studio 2017 r.

Jeśli masz problem otwarcie strony z pobierania zdalnego debugera, zobacz [odblokować pobierania pliku](../debugger/remote-debugging.md#unblock_msvsmon) Aby uzyskać pomoc.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

> [!TIP]
> W niektórych scenariuszach może być najbardziej efektywny do uruchamiania zdalnego debugera z udziału plików. Aby uzyskać więcej informacji, zobacz [uruchamiania zdalnego debugera z udziału plików](../debugger/remote-debugging.md#fileshare_msvsmon).
  
## <a name="BKMK_setup"></a> Konfigurowanie zdalnego debugera w systemie Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Jeśli należy dodać uprawnienia dla dodatkowych użytkowników do zmiany trybu uwierzytelniania lub numer portu dla zdalnego debugera, zobacz [skonfigurować debugera zdalnego](../debugger/remote-debugging.md#configure_msvsmon).

Aby uzyskać informacje na temat uruchamiania zdalnego debugera jako usługi, zobacz [uruchamiania zdalnego debugera jako usługi](../debugger/remote-debugging.md#bkmk_configureService).

## <a name="BKMK_attach"></a> Dołączanie do aplikacji platformy ASP.NET z komputera programu Visual Studio

1. Na komputerze programu Visual Studio Otwórz rozwiązanie, które chcesz debugować (**MyASPApp** Jeśli wykonujesz kroki opisane w tym artykule).
2. W programie Visual Studio, kliknij przycisk **Debuguj > dołączyć do procesu** (Ctrl + Alt + P).

    > [!TIP]
    > W programie Visual Studio 2017 r, można ponownie dołączyć do tego samego procesu wcześniej podłączany do przy użyciu **Debuguj > ponownie dołączyć do procesu...** (Shift+Alt+P). 

3. Ustaw dla pola kwalifikator  **\<nazwę komputera zdalnego >: 4022**.
4. Kliknij przycisk **Odśwież**.
    Powinny pojawić się niektóre procesy, które są wyświetlane w **dostępne procesy** okna.

    Jeśli nie widać żadnych procesów, spróbuj użyć adresu IP zamiast nazwy komputera zdalnego (wymagana jest port). Można użyć `ipconfig` w wierszu polecenia, aby uzyskać adres IPv4.

5. Sprawdź **Pokaż procesy wszystkich użytkowników**.
6. Wpisz nazwę procesu, aby szybko znaleźć literą **w3wp.exe** przez funkcję ASP.NET 4.5.

    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg_attachtoprocess.png "RemoteDBG_AttachToProcess")

7. Kliknij przycisk **dołączyć**

8. Otwórz witrynę sieci Web na komputerze zdalnym. W przeglądarce przejdź do **http://\<nazwę komputera zdalnego >**.
    
    Powinna zostać wyświetlona strona sieci web ASP.NET.
9. W uruchomionej aplikacji ASP.NET, kliknij łącze, aby **o** strony.

    Punkt przerwania powinien trafienie w programie Visual Studio.

## <a name="bkmk_openports"></a> Rozwiązywanie problemów: Otwórz wymagane porty w systemie Windows Server

W większości konfiguracji są otwarte porty wymagane przez instalację programu ASP.NET i zdalnego debugera. Jednak należy sprawdzić, czy porty są otwarte.

> [!NOTE]
> Na maszynie Wirtualnej platformy Azure, należy otworzyć porty za pośrednictwem [sieciowej grupy zabezpieczeń](/azure/virtual-machines/virtual-machines-windows-hero-role#open-port-80-for-web-traffic). 

Wymagane porty:

- 80 - wymagane dla usług IIS
- 8172 - (opcjonalnie) wymagany dla narzędzia Web Deploy do wdrażania aplikacji w programie Visual Studio
- 4022 — wymagane do zdalnego debugowania z programu Visual Studio 2017 (zobacz [przypisania portów usługi zdalnego debugera](../debugger/remote-debugger-port-assignments.md) Aby uzyskać szczegółowe informacje.
- UDP 3702 — port odnajdywania (opcjonalnie) umożliwia **znaleźć** przycisku związane ze zdalnym debugerem programu Visual Studio.

1. Aby otworzyć port w systemie Windows Server, otwórz **Start** menu, wyszukaj **Zapora systemu Windows z zabezpieczeniami zaawansowanymi**.

2. Następnie wybierz pozycję **reguły ruchu przychodzącego > Nowa reguła > portu**. Wybierz **dalej** i w obszarze **określone porty lokalne**, wprowadź numer portu, kliknij przycisk **dalej**, następnie **zezwalały na połączenie**, kliknij przycisk Dalej, a Dodaj nazwę (**IIS**, **narzędzia Web Deploy**, lub **polecenia msvsmon**) dla reguły ruchu przychodzącego.

    Aby uzyskać więcej informacji na temat konfigurowania Zapory systemu Windows, zobacz [konfigurowania Zapory systemu Windows do zdalnego debugowania](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

3. Utworzenie dodatkowych reguł dla wymaganych portów.