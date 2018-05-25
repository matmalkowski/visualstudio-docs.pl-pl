---
title: Zdalne debugowanie platformy ASP.NET Core w usługach IIS i platformy Azure | Dokumentacja firmy Microsoft
ms.custom: remotedebugging
ms.date: 05/21/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: a6c04b53-d1b9-4552-a8fd-3ed6f4902ce6
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
- dotnetcore
- azure
ms.openlocfilehash: 202e9ce6e0a53c6967ebe1bacaa6553a1241298e
ms.sourcegitcommit: d1824ab926ebbc4a8057163e0edeaf35cec57433
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2018
---
# <a name="remote-debug-aspnet-core-on-iis-in-azure-in-visual-studio-2017"></a>Zdalne debugowanie platformy ASP.NET Core w usługach IIS na platformie Azure w programie Visual Studio 2017 r.

W tym przewodniku opisano sposób konfigurowania i konfigurowania aplikacji programu Visual Studio 2017 platformy ASP.NET Core, wdrożyć ją w usługach IIS przy użyciu usługi Azure i dołączyć debuger zdalny z programu Visual Studio.

Zalecanym sposobem zdalnego debugowania na platformie Azure jest zależna od danego scenariusza:

* Aby debugować platformy ASP.NET Core w usłudze Azure App Service, zobacz [Azure debugowania aplikacji za pomocą debugera migawki](../debugger/debug-live-azure-applications.md). Jest to zalecana metoda.
* Aby debugować platformy ASP.NET Core w usłudze Azure App Service przy użyciu tradycyjnych więcej funkcji debugowania, wykonaj kroki opisane w tym temacie (zobacz sekcję [zdalnego debugowania w usłudze Azure App Service](#remote_debug_azure_app_service)).

    W tym scenariuszu należy wdrożyć aplikację z programu Visual Studio na platformie Azure, ale nie trzeba ręcznie zainstalować lub skonfigurować usługi IIS lub zdalnego debugera (te składniki są reprezentowane liniami przerywana), jak pokazano na poniższej ilustracji.

    ![Składniki zdalnego debugera](../debugger/media/remote-debugger-azure-app-service.png "Remote_debugger_components")

* Debugowanie usług IIS na maszynie Wirtualnej platformy Azure, wykonaj kroki opisane w tym temacie (zobacz sekcję [zdalnego debugowania na maszynie Wirtualnej platformy Azure](#remote_debug_azure_vm)). Dzięki temu można korzystać z dostosowanego konfiguracji usług IIS, ale kroków instalacji i wdrażania są bardziej skomplikowane.

    Dla maszyny Wirtualnej platformy Azure należy wdrożyć aplikację z programu Visual Studio na platformie Azure i należy ręcznie zainstalować rolę usług IIS i zdalnego debugera, jak pokazano na poniższej ilustracji.

    ![Składniki zdalnego debugera](../debugger/media/remote-debugger-azure-vm.png "Remote_debugger_components")

* Aby debugować platformy ASP.NET Core w sieci szkieletowej usług Azure, zobacz [debugowania zdalnego aplikacji sieci szkieletowej usług](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application).

> [!WARNING]
> Pamiętaj usunąć zasobów platformy Azure, utworzonych po wykonaniu kroków opisanych w tym samouczku. Dzięki temu można uniknąć naliczania opłat niepotrzebne.


### <a name="requirements"></a>Wymagania

Debugowanie między dwoma komputerami połączone za pośrednictwem serwera proxy nie jest obsługiwane. Debugowanie za pośrednictwem duże opóźnienie lub połączenia o niskiej przepustowości, takich jak Internet, połączenia telefonicznego lub przez Internet między krajów nie jest zalecana i może się nie powieść lub zbyt wolno. Aby uzyskać pełną listę wymagań, zobacz [wymagania](../debugger/remote-debugging.md#requirements_msvsmon).

## <a name="create-the-aspnet-core-application-on-the-visual-studio-2017-computer"></a>Tworzenie aplikacji platformy ASP.NET Core na komputerze programu Visual Studio 2017 r. 

1. Tworzenie nowej aplikacji platformy ASP.NET Core. (Wybierz **Plik > Nowy > Projekt**, a następnie wybierz pozycję **Visual C# > sieci Web > Aplikacja sieci Web platformy ASP.NET Core**).

    W **platformy ASP.NET Core** sekcji szablonów, wybierz opcję **aplikacji sieci Web**.

2. Upewnij się, że **ASP.NET Core 2.0** jest zaznaczone, który **Włącz obsługę Docker** jest **nie** wybrany, a **uwierzytelniania** ma ustawioną wartość **Bez uwierzytelniania**.

3. Nazwij projekt **MyASPApp** i kliknij przycisk **OK** do tworzenia nowego rozwiązania.

4. Otwórz plik About.cshtml.cs i ustaw punkt przerwania `OnGet` — metoda (w szablonach starsze HomeController.cs zamiast tego otworzyć i ustawić punkt przerwania `About()` metody).

## <a name="remote_debug_azure_app_service"></a> Zdalne debugowanie platformy ASP.NET Core w usłudze aplikacji Azure

W programie Visual Studio można szybko publikowanie i debugowanie aplikacji do pełni wystąpienia usług IIS. Jednak jest ustawień konfiguracji programu IIS i nie można go dostosować. Aby uzyskać szczegółowe instrukcje, zobacz [wdrażanie aplikacji sieci web platformy ASP.NET Core na platformie Azure przy użyciu programu Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). (Umożliwia dostosowywanie usług IIS, należy spróbować debugowania [maszyny Wirtualnej Azure](#BKMK_azure_vm).) 

#### <a name="to-deploy-the-app-and-remote-debug-using-server-explorer"></a>Aby wdrożyć aplikację i zdalnego debugowania za pomocą Eksploratora serwera

1. W programie Visual Studio, kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **publikowania**.

    Jeśli wcześniej skonfigurowano żadnych profilów publikowania, **publikowania** pojawi się okienko. Kliknij przycisk **nowy profil**.

1. Wybierz **usłudze Azure App Service** z **publikowania** okno dialogowe, wybierz opcję **Utwórz nowy**i postępuj zgodnie z monitami, aby opublikować.

    Aby uzyskać szczegółowe instrukcje, zobacz [wdrażanie aplikacji sieci web platformy ASP.NET Core na platformie Azure przy użyciu programu Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs).

    ![Publikowanie w usłudze Azure App Service](../debugger/media/remotedbg_azure_app_service_profile.png)

1. Otwórz **Eksploratora serwera** (**widoku** > **Eksploratora serwera**), kliknij prawym przyciskiem myszy w wystąpieniu usługi aplikacji i wybierz **dołączyć debuger**.

1. W uruchomionej aplikacji ASP.NET, kliknij łącze, aby **o** strony.

    Punkt przerwania powinien trafienie w programie Visual Studio.

    To już wszystko! Pozostałe kroki w tym temacie dotyczą zdalnego debugowania na maszynie Wirtualnej platformy Azure.

## <a name="remote_debug_azure_vm"></a> Zdalne debugowanie platformy ASP.NET Core na maszynie Wirtualnej platformy Azure

Można utworzyć Azure maszyny Wirtualnej systemu Windows Server i następnie zainstalować i skonfigurowanie usług IIS i innych składników oprogramowania wymagane. Trwa dłużej niż wdrażanie w usłudze Azure App Service i wymaga wykonaj pozostałe kroki w tym samouczku.

Najpierw wykonaj wszystkie kroki opisane w [instalacji i uruchamiania usług IIS](/azure/virtual-machines/windows/quick-create-portal).

Podczas otwierania portu 80 w grupie zabezpieczeń sieci, należy również otworzyć portu 4022 dla zdalnego debugera. Dzięki temu nie trzeba otworzyć go później.

### <a name="app-already-running-in-iis-on-the-azure-vm"></a>Aplikacja już uruchomione w usługach IIS na maszynie Wirtualnej platformy Azure?

Ten artykuł zawiera kroki na konfigurowaniu podstawowych konfiguracji usług IIS w systemie Windows server i wdrażania aplikacji w programie Visual Studio. Te kroki są uwzględnione, aby upewnić się, że serwer ma wymagane składniki zainstalowane, że aplikacja może działać prawidłowo, a można przystąpić do zdalnego debugowania.

* Jeśli aplikacja działa w usługach IIS i po prostu chcesz pobrać zdalnego debugera i Rozpocznij debugowanie, przejdź do [pobrać i zainstalować narzędzia zdalnego w systemie Windows Server](#BKMK_msvsmon).

* Jeśli potrzebujesz pomocy, aby upewnić się, że aplikacja jest skonfigurowany, wdrożona i działają poprawnie w usługach IIS tak, aby umożliwić debugowanie, wykonaj wszystkie kroki opisane w tym temacie.

### <a name="update-browser-security-settings-on-windows-server"></a>Zaktualizuj ustawienia zabezpieczeń przeglądarki w systemie Windows Server

Jeśli Konfiguracja zwiększonych zabezpieczeń jest włączona w programie Internet Explorer (jest ona włączona domyślnie), następnie należy dodać niektóre domeny jako zaufane witryny, aby możliwe było pobrać niektórych składników serwera sieci web. Dodaj zaufanych witryn, przechodząc do **Opcje internetowe > Zabezpieczenia > Zaufane witryny > witryny**. Dodaj następujące domeny.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- Program IIS.NET

Podczas pobierania oprogramowania może otrzymywać żądania udzielenia uprawnienie do ładowania różnych skrypty witryny sieci web i zasobów. Niektóre z tych zasobów nie są wymagane, ale w celu uproszczenia procesu, kliknij przycisk **Dodaj** po wyświetleniu monitu.

### <a name="install-aspnet-core-on-windows-server"></a>Instalowanie platformy ASP.NET Core w systemie Windows Server

1. Zainstaluj [.NET Core systemu Windows serwer obsługujący](https://aka.ms/dotnetcore-2-windowshosting) pakietu przez system operacyjny. Instaluje pakiet podstawowego środowiska wykonawczego platformy .NET, biblioteka programu .NET Core i moduł platformy ASP.NET Core. Aby uzyskać dodatkowe szczegółowe instrukcje, zobacz [publikowania w usługach IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration).

    > [!NOTE]
    > Jeśli system nie ma połączenia internetowego, Uzyskaj i zainstaluj *[Microsoft Visual C++ 2015 Redistributable](https://www.microsoft.com/download/details.aspx?id=53840)* przed zainstalowaniem pakietu Hosting .NET Core systemu Windows Server.

3. Ponowne uruchomienie systemu (lub wykonać **net stop została /y** następuje **net start w3svc** z wiersza polecenia, aby pobrać zmiany systemowej PATH).

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

Po aplikacji wdraża się pomyślnie, należy uruchomić automatycznie. Jeśli aplikacja nie zostanie uruchomiony z programu Visual Studio, uruchomić aplikację w usługach IIS. Dla platformy ASP.NET Core, należy się upewnić, że pula aplikacji pól dla **DefaultAppPool** ustawiono **bez kodu zarządzanego**.

1. W **ustawienia** okno dialogowe, Włącz debugowanie klikając **dalej**, wybierz **debugowania** konfiguracji, a następnie wybierz pozycję **Usuń dodatkowe pliki w docelowy** w obszarze **publikowania pliku** opcje.

    > [!NOTE]
    > Wybranie opcji konfiguracji wydania, należy wyłączyć debugowanie w *web.config* pliku podczas publikowania.

1. Kliknij przycisk **zapisać** , a następnie ponownie opublikować aplikację.

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>(Opcjonalnie) Wdrażanie poprzez publikowanie do folderu lokalnego

Ta opcja służy do wdrożenia aplikacji, jeśli chcesz skopiować aplikacji usług IIS przy użyciu programu Powershell, RoboCopy, lub chcesz ręcznie skopiować pliki.

### <a name="BKMK_deploy_asp_net"></a> Konfigurowanie witryny sieci Web ASP.NET na komputerze serwera systemu Windows

Jeśli są importowane ustawienia publikowania, możesz pominąć tę sekcję.

1. Otwórz **Internet Information Services (IIS) Manager** i przejdź do **witryny**.

2. Kliknij prawym przyciskiem myszy **domyślna witryna sieci Web** a następnie wybierz węzeł **Dodawanie aplikacji**.

3. Ustaw **Alias** do **MyASPApp** i pole puli aplikacji do **bez kodu zarządzanego**. Ustaw **ścieżka fizyczna** do **C:\Publish** (który zostanie później wdrożyć projekt ASP.NET).

4. Z witryną wybrane w Menedżerze usług IIS, wybierz **Edytuj uprawnienia**i upewnij się, że IUSR, IIS_IUSRS lub nazwą użytkownika skonfigurowaną dla puli aplikacji jest autoryzowanym użytkownikiem z prawami Odczyt i wykonywanie.

    Jeśli nie widzisz jednego z tych użytkowników z dostępem, przejść przez kroki, aby dodać konta IUSR jako użytkownik z uprawnieniami Odczyt i wykonywanie.

### <a name="optional-publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>(Opcjonalnie) Publikowanie i wdrażanie aplikacji przez publikowanie do folderu lokalnego z programu Visual Studio

Jeśli nie używasz narzędzia Web Deploy, należy opublikować i wdrażanie aplikacji przy użyciu systemu plików lub innych narzędzi. Możesz rozpocząć od utworzenia pakietu przy użyciu systemu plików, a następnie ręcznie wdrożyć pakiet lub użyć innych narzędzi, takich jak programu PowerShell, RoboCopy lub XCopy. W tej sekcji przyjęto założenie, że są ręczne kopiowanie pakietu, jeśli nie używasz narzędzia Web Deploy.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

### <a name="BKMK_msvsmon"></a> Pobierz i zainstaluj narzędzia zdalnego w systemie Windows Server

W tym samouczku używamy programu Visual Studio 2017 r.

Jeśli masz problem otwarcie strony z pobierania zdalnego debugera, zobacz [odblokować pobierania pliku](../debugger/remote-debugging.md#unblock_msvsmon) Aby uzyskać pomoc.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]
  
### <a name="BKMK_setup"></a> Konfigurowanie zdalnego debugera w systemie Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Jeśli należy dodać uprawnienia dla dodatkowych użytkowników do zmiany trybu uwierzytelniania lub numer portu dla zdalnego debugera, zobacz [skonfigurować debugera zdalnego](../debugger/remote-debugging.md#configure_msvsmon).

### <a name="BKMK_attach"></a> Dołączanie do aplikacji platformy ASP.NET z komputera programu Visual Studio

1. Na komputerze programu Visual Studio Otwórz **MyASPApp** rozwiązania.
2. W programie Visual Studio, kliknij przycisk **Debuguj > dołączyć do procesu** (Ctrl + Alt + P).

    > [!TIP]
    > W programie Visual Studio 2017 r, możesz ponownie dołączyć do tego samego procesu wcześniej podłączany do przy użyciu **Debuguj > ponownie dołączyć do procesu...** (Shift+Alt+P). 

3. Ustaw dla pola kwalifikator  **\<nazwę komputera zdalnego >: 4022**.
4. Kliknij przycisk **Odśwież**.
    Powinny pojawić się niektóre procesy, które są wyświetlane w **dostępne procesy** okna.

    Jeśli nie widać żadnych procesów, spróbuj użyć adresu IP zamiast nazwy komputera zdalnego (wymagana jest port). Można użyć `ipconfig` w wierszu polecenia, aby uzyskać adres IPv4.

    Jeśli chcesz użyć **znaleźć** przycisku, konieczne może być [Otwórz UDP port 3702](#bkmk_openports) na serwerze.

5. Sprawdź **Pokaż procesy wszystkich użytkowników**.

6. Wpisz nazwę procesu, aby szybko znaleźć literą *dotnet.exe* (dla platformy ASP.NET Core).
   
   Dla aplikacji platformy ASP.NET Core poprzedniej nazwy procesu został *dnx.exe*.

    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg_attachtoprocess_aspnetcore.png "RemoteDBG_AttachToProcess")

7. Kliknij przycisk **dołączyć**.

8. Otwórz witrynę sieci Web na komputerze zdalnym. W przeglądarce przejdź do **http://\<nazwę komputera zdalnego >**.
    
    Powinna zostać wyświetlona strona sieci web ASP.NET.
9. W uruchomionej aplikacji ASP.NET, kliknij łącze, aby **o** strony.

    Punkt przerwania powinien trafienie w programie Visual Studio.

### <a name="bkmk_openports"></a> Rozwiązywanie problemów: Otwórz wymagane porty w systemie Windows Server

W większości konfiguracji są otwarte porty wymagane przez instalację programu ASP.NET i zdalnego debugera. Jednak w przypadku rozwiązywania problemów wdrożenia aplikacji znajduje się za zaporą, może być konieczne Sprawdź, czy porty są otwarte.

Na maszynie Wirtualnej platformy Azure, należy otworzyć porty za pośrednictwem [sieciowej grupy zabezpieczeń](/azure/virtual-machines/virtual-machines-windows-hero-role#open-port-80). 

Wymagane porty:

- 80 - wymagane dla usług IIS
- 4022 — wymagane do zdalnego debugowania z programu Visual Studio 2017 (zobacz [przypisania portów usługi zdalnego debugera](../debugger/remote-debugger-port-assignments.md) Aby uzyskać więcej informacji).
- UDP 3702 — port odnajdywania (opcjonalnie) umożliwia **znaleźć** przycisku związane ze zdalnym debugerem programu Visual Studio.

Ponadto te porty już powinny być otwierane przez instalację programu ASP.NET:
- 8172 - (opcjonalnie) wymagany dla narzędzia Web Deploy do wdrażania aplikacji w programie Visual Studio

