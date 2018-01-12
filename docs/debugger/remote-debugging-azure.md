---
title: "Zdalne debugowanie platformy ASP.NET Core w usługach IIS i platformy Azure | Dokumentacja firmy Microsoft"
ms.custom: remotedebugging
ms.date: 08/14/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a6c04b53-d1b9-4552-a8fd-3ed6f4902ce6
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- aspnet
- dotnetcore
- azure
ms.openlocfilehash: 52acd997d1f6dd9f019a6495cfbeab4e459d661b
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="remote-debug-aspnet-core-on-iis-and-azure-in-visual-studio-2017"></a>Zdalne debugowanie platformy ASP.NET Core usług IIS i platformy Azure w programie Visual Studio 2017 r.
Możesz wdrożyć aplikację sieci Web programu ASP.NET na komputerze z systemem Windows Server z usługami IIS i skonfigurować go do zdalnego debugowania. W tym przewodniku opisano sposób konfigurowania i konfigurowania aplikacji programu Visual Studio 2017 platformy ASP.NET Core, wdrożyć ją w usługach IIS przy użyciu usługi Azure i dołączyć debuger zdalny z programu Visual Studio.

> [!WARNING]
> Pamiętaj usunąć zasobów platformy Azure, utworzonych po wykonaniu kroków opisanych w tym samouczku. Dzięki temu można uniknąć naliczania opłat niepotrzebne.

W tym temacie przedstawiono sposób:

* Zdalne debugowanie platformy ASP.NET Core w usłudze Azure App Service

* Zdalne debugowanie platformy ASP.NET Core na maszynie Wirtualnej platformy Azure

Dla usługi Azure App Service należy wdrożyć aplikację z programu Visual Studio na platformie Azure, ale nie trzeba ręcznie zainstalować lub skonfigurować usługi IIS lub zdalnego debugera (te składniki są reprezentowane liniami przerywana), jak pokazano na poniższej ilustracji.

![Składniki zdalnego debugera](../debugger/media/remote-debugger-azure-app-service.png "Remote_debugger_components")

Dla maszyny Wirtualnej platformy Azure należy wdrożyć aplikację z programu Visual Studio na platformie Azure i należy ręcznie zainstalować rolę usług IIS i zdalnego debugera, jak pokazano na poniższej ilustracji.

![Składniki zdalnego debugera](../debugger/media/remote-debugger-azure-vm.png "Remote_debugger_components")

> [!NOTE]
> Aby debugować platformy ASP.NET Core w sieci szkieletowej usług Azure, zobacz [debugowania zdalnego aplikacji sieci szkieletowej usług](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application).

### <a name="requirements"></a>Wymagania

Debugowanie między dwoma komputerami połączone za pośrednictwem serwera proxy nie jest obsługiwane. Debugowanie za pośrednictwem duże opóźnienie lub połączenia o niskiej przepustowości, takich jak Internet, połączenia telefonicznego lub przez Internet między krajów nie jest zalecana i może się nie powieść lub zbyt wolno. Aby uzyskać pełną listę wymagań, zobacz [wymagania](../debugger/remote-debugging.md#requirements_msvsmon).

## <a name="create-the-aspnet-core-application-on-the-visual-studio-2017-computer"></a>Tworzenie aplikacji platformy ASP.NET Core na komputerze programu Visual Studio 2017 r. 

1. Tworzenie nowej aplikacji platformy ASP.NET Core. (Wybierz **Plik > Nowy > Projekt**, a następnie wybierz pozycję **Visual C# > sieci Web > Aplikacja sieci Web platformy ASP.NET Core**).

    W **platformy ASP.NET Core** sekcji szablonów, wybierz opcję **aplikacji sieci Web**.

2. Upewnij się, że **ASP.NET Core 2.0** jest zaznaczone, który **Włącz obsługę Docker** jest **nie** wybrany, a **uwierzytelniania** ma ustawioną wartość **Bez uwierzytelniania**.

3. Nazwij projekt **MyASPApp** i kliknij przycisk **OK** do tworzenia nowego rozwiązania.

4. Otwórz plik About.cshtml.cs i ustaw punkt przerwania `OnGet` — metoda (w szablonach starsze HomeController.cs zamiast tego otworzyć i ustawić punkt przerwania `About()` metody).

## <a name="remote-debug-aspnet-core-on-an-azure-app-service"></a>Zdalne debugowanie platformy ASP.NET Core w usłudze aplikacji Azure

W programie Visual Studio można szybko publikowanie i debugowanie aplikacji do pełni wystąpienia usług IIS. Jednak jest ustawień konfiguracji programu IIS i nie można go dostosować. Aby uzyskać szczegółowe instrukcje, zobacz [wdrażanie aplikacji sieci web platformy ASP.NET Core na platformie Azure przy użyciu programu Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). (Umożliwia dostosowywanie usług IIS, należy spróbować debugowania [maszyny Wirtualnej Azure](#BKMK_azure_vm).) 

#### <a name="to-deploy-the-app-and-remote-debug"></a>Aby wdrożyć aplikację i zdalnego debugowania

1. W programie Visual Studio, kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **publikowania**.

2. Wybierz **Microsoft Azure App Service** z **publikowania** okno dialogowe, wybierz **Utwórz nowy**, a następnie postępuj zgodnie z monitami, aby opublikować.

    Aby uzyskać szczegółowe instrukcje, zobacz [wdrażanie aplikacji sieci web platformy ASP.NET Core na platformie Azure przy użyciu programu Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs).

3. W **Eksploratora serwera**, kliknij prawym przyciskiem myszy w wystąpieniu usługi aplikacji i wybierz **dołączyć debuger**.

4. W uruchomionej aplikacji ASP.NET, kliknij łącze, aby **o** strony.

    Punkt przerwania powinien trafienie w programie Visual Studio.

    To już wszystko! Pozostałe kroki w tym temacie dotyczą zdalnego debugowania na maszynie Wirtualnej platformy Azure.

## <a name="BKMK_azure_vm"></a>Zdalne debugowanie platformy ASP.NET Core na maszynie Wirtualnej platformy Azure

Można utworzyć Azure maszyny Wirtualnej systemu Windows Server i następnie zainstalować i skonfigurowanie usług IIS i innych składników oprogramowania wymagane. Trwa dłużej niż wdrażanie w usłudze Azure App Service i wymaga wykonaj pozostałe kroki w tym samouczku.

Najpierw wykonaj wszystkie kroki opisane w [instalacji i uruchamiania usług IIS](/azure/virtual-machines/virtual-machines-windows-hero-role).

Podczas otwierania portu 80 w grupie zabezpieczeń sieci, należy również otworzyć portu 4022 dla zdalnego debugera. Dzięki temu nie trzeba otworzyć go później.

### <a name="update-browser-security-settings-on-windows-server"></a>Zaktualizuj ustawienia zabezpieczeń przeglądarki w systemie Windows Server

W zależności od ustawień zabezpieczeń przeglądarki go zapisać czasu, należy dodać następujące zaufanych witryn do przeglądarki, można łatwo pobrać opisane w tym samouczku oprogramowanie. Może być wymagany dostęp do tych witryn:

- Microsoft.com
- go.microsoft.com
- witrynie Download.microsoft.com
- Visual Studio —

Jeśli korzystasz z programu Internet Explorer, możesz dodać zaufanych witryn, przechodząc do **Opcje internetowe > Zabezpieczenia > Zaufane witryny > witryny**. Te kroki są różne dla innych przeglądarek. (Jeśli chcesz pobrać starszej wersji zdalnego debugera z my.visualstudio.com niektóre dodatkowe zaufanych witryn są wymagane do logowania).

Podczas pobierania oprogramowania może otrzymywać żądania udzielenia uprawnienie do ładowania różnych skrypty witryny sieci web i zasobów. W większości przypadków te dodatkowe zasoby nie są wymagane do zainstalowania oprogramowania.

### <a name="install-aspnet-core-on-windows-server"></a>Instalowanie platformy ASP.NET Core w systemie Windows Server

1. Zainstaluj [.NET Core systemu Windows serwer obsługujący](https://aka.ms/dotnetcore-2-windowshosting) pakietu przez system operacyjny. Instaluje pakiet podstawowego środowiska wykonawczego platformy .NET, biblioteka programu .NET Core i moduł platformy ASP.NET Core. Aby uzyskać dodatkowe szczegółowe instrukcje, zobacz [publikowania w usługach IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration).

    > [!NOTE]
    > Jeśli system nie ma połączenia internetowego, Uzyskaj i zainstaluj  *[Microsoft Visual C++ 2015 Redistributable](https://www.microsoft.com/download/details.aspx?id=53840)*  przed zainstalowaniem pakietu Hosting .NET Core systemu Windows Server.

3. Ponowne uruchomienie systemu (lub wykonać **net stop została /y** następuje **net start w3svc** z wiersza polecenia, aby pobrać zmiany systemowej PATH).

### <a name="BKMK_install_webdeploy"></a>(Opcjonalnie) Instalacja narzędzia Web Deploy 3,6 w systemie Windows Server

[!INCLUDE [remote-debugger-install-web-deploy](../debugger/includes/remote-debugger-install-web-deploy.md)]

### <a name="BKMK_deploy_asp_net"></a>Konfiguruj witrynę sieci Web platformy ASP.NET na komputerze serwera systemu Windows

1. Otwórz **Internet Information Services (IIS) Manager** i przejdź do **witryny**.

2. Kliknij prawym przyciskiem myszy **domyślna witryna sieci Web** a następnie wybierz węzeł **Dodawanie aplikacji**.

3. Ustaw **Alias** do **MyASPApp** i pole puli aplikacji do **bez kodu zarządzanego**. Ustaw **ścieżka fizyczna** do **C:\Publish** (który zostanie później wdrożyć projekt ASP.NET).

4. Z witryną wybrane w Menedżerze usług IIS, wybierz **Edytuj uprawnienia**i upewnij się, że IUSR, IIS_IUSRS lub nazwą użytkownika skonfigurowaną dla puli aplikacji jest autoryzowanym użytkownikiem z prawami Odczyt i wykonywanie.

    Jeśli nie widzisz jednego z tych użytkowników z dostępem, przejść przez kroki, aby dodać konta IUSR jako użytkownik z uprawnieniami Odczyt i wykonywanie.

### <a name="bkmk_webdeploy"></a>(Opcjonalnie) Publikowanie i wdrażanie aplikacji przy użyciu narzędzia Web Deploy w programie Visual Studio

Jeśli zainstalowano za pomocą Instalatora platformy sieci Web narzędzia Web Deploy, można wdrożyć aplikacji bezpośrednio z programu Visual Studio.

1. Uruchom program Visual Studio z podwyższonym poziomem uprawnień, a następnie ponownie otwórz projekt.

    Może to być wymagane do wdrożenia aplikacji za pomocą narzędzia Web Deploy.

2. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu i wybierz **publikowania**.

3. Dla **wybierz cel publikowania**, wybierz pozycję **maszyny wirtualnej platformy Microsoft Azure** i kliknij przycisk **publikowania**.

    ![RemoteDBG_Publish_IISl](../debugger/media/remotedbg_azure_vm_profile.png "RemoteDBG_Publish_IIS")

4. W oknie dialogowym wybierz utworzony wcześniej maszyny Wirtualnej Azure.

4. Wprowadź parametry konfiguracji korekty ustawień maszyny Wirtualnej platformy Azure i usług IIS.

    ![RemoteDBG_Publish_WebDeployl](../debugger/media/remotedbg_iis_webdeploy_config.png "RemoteDBG_Publish_WebDeploy")

    Jeśli nie jest rozpoznawane nazwy hosta podczas sprawdzania poprawności w kolejnych kroków w **serwera** tekst pola, spróbuj adresu IP. Upewnij się, że korzystanie z portu 80 w **serwera** tekst pole i upewnij się, że port 80 jest otwarty w zaporze.

6. Kliknij przycisk **dalej**, wybierz **debugowania** konfiguracji i wybierz polecenie **Usuń dodatkowe pliki w miejscu docelowym** w obszarze **publikowania pliku** Opcje.

5. Kliknij przycisk **Prev**, a następnie wybierz pozycję **weryfikacji**. Sprawdza ustawienia połączenia, możesz opublikować.

6. Kliknij przycisk **publikowania** do publikowania aplikacji.

    Na karcie dane wyjściowe zostanie wyświetlona Jeśli publikowanie zakończy się pomyślnie, a przeglądarce zostanie otwarta aplikacja.

    Jeśli wystąpi błąd zauważyć narzędzia Web Deploy, sprawdź ponownie kroki instalacji narzędzia Web Deploy i upewnij się, że [prawidłowe porty są otwarte](#bkmk_openports) znajdują się na serwerze.

    Jeśli aplikacja wdraża się pomyślnie, ale nie działa poprawnie, ponownie sprawdź, czy zarówno usług IIS, jak i projektu programu Visual Studio korzystają z tej samej wersji platformy ASP.NET. Jeśli to znaczy nie problem, może być problem z konfiguracji usług IIS lub konfiguracji witryny sieci Web. W systemie Windows Server otwórz witrynę sieci Web za pomocą programu IIS, aby uzyskać bardziej szczegółowe komunikaty o błędach, a następnie ponownie sprawdzić wcześniejszych krokach.

### <a name="optional-publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>(Opcjonalnie) Publikowanie i wdrażanie aplikacji przez publikowanie do folderu lokalnego z programu Visual Studio

Jeśli nie używasz narzędzia Web Deploy, należy opublikować i wdrażanie aplikacji przy użyciu systemu plików lub innych narzędzi. Możesz rozpocząć od utworzenia pakietu przy użyciu systemu plików, a następnie ręcznie wdrożyć pakiet lub użyć innych narzędzi, takich jak programu PowerShell, RoboCopy lub XCopy. W tej sekcji przyjęto założenie, że są ręczne kopiowanie pakietu, jeśli nie używasz narzędzia Web Deploy.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

### <a name="BKMK_msvsmon"></a>Pobierz i zainstaluj narzędzia zdalnego w systemie Windows Server

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]
  
### <a name="BKMK_setup"></a>Konfigurowanie zdalnego debugera w systemie Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Jeśli należy dodać uprawnienia dla dodatkowych użytkowników do zmiany trybu uwierzytelniania lub numer portu dla zdalnego debugera, zobacz [skonfigurować debugera zdalnego](../debugger/remote-debugging.md#configure_msvsmon).

### <a name="BKMK_attach"></a>Dołączanie do aplikacji platformy ASP.NET z komputera programu Visual Studio

1. Na komputerze programu Visual Studio Otwórz **MyASPApp** rozwiązania.
2. W programie Visual Studio, kliknij przycisk **Debuguj > dołączyć do procesu** (Ctrl + Alt + P).

    > [!TIP]
    > W programie Visual Studio 2017 r, możesz ponownie dołączyć do tego samego procesu wcześniej podłączany do przy użyciu **Debuguj > ponownie dołączyć do procesu...** (Shift + Alt + P). 

3. Ustaw dla pola kwalifikator  **\<nazwę komputera zdalnego >: 4022**.
4. Kliknij przycisk **Odśwież**.
    Powinny pojawić się niektóre procesy, które są wyświetlane w **dostępne procesy** okna.

    Jeśli nie widać żadnych procesów, spróbuj użyć adresu IP zamiast nazwy komputera zdalnego (wymagana jest port). Można użyć `ipconfig` w wierszu polecenia, aby uzyskać adres IPv4.

    Jeśli chcesz użyć **znaleźć** przycisku, konieczne może być [Otwórz UDP port 3702](#bkmk_openports) na serwerze.

5. Sprawdź **Pokaż procesy wszystkich użytkowników**.
6. Wpisz nazwę procesu, aby szybko znaleźć literą **dotnet.exe** (dla platformy ASP.NET Core).
    >Uwaga: Dla aplikacji platformy ASP.NET Core poprzednia nazwa procesu jest dnx.exe.

    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg_attachtoprocess_aspnetcore.png "RemoteDBG_AttachToProcess")

7. Kliknij przycisk **dołączyć**.

8. Otwórz witrynę sieci Web na komputerze zdalnym. W przeglądarce przejdź do **http://\<nazwę komputera zdalnego >**.
    
    Powinna zostać wyświetlona strona sieci web ASP.NET.
9. W uruchomionej aplikacji ASP.NET, kliknij łącze, aby **o** strony.

    Punkt przerwania powinien trafienie w programie Visual Studio.

### <a name="bkmk_openports"></a>Rozwiązywanie problemów: Otwórz wymagane porty w systemie Windows Server

W większości konfiguracji są otwarte porty wymagane przez instalację programu ASP.NET i zdalnego debugera. Jednak w przypadku rozwiązywania problemów wdrożenia aplikacji znajduje się za zaporą, może być konieczne Sprawdź, czy porty są otwarte.

Na maszynie Wirtualnej platformy Azure, należy otworzyć porty za pośrednictwem [sieciowej grupy zabezpieczeń](/azure/virtual-machines/virtual-machines-windows-hero-role#open-port-80). 

Wymagane porty:

- 80 - wymagane dla usług IIS
- 4022 — wymagane do zdalnego debugowania z programu Visual Studio 2017 (zobacz [przypisania portów usługi zdalnego debugera](../debugger/remote-debugger-port-assignments.md) Aby uzyskać więcej informacji).
- UDP 3702 — port odnajdywania (opcjonalnie) umożliwia **znaleźć** przycisku związane ze zdalnym debugerem programu Visual Studio.

Ponadto te porty już powinny być otwierane przez instalację programu ASP.NET:
- 8172 - (opcjonalnie) wymagany dla narzędzia Web Deploy do wdrażania aplikacji w programie Visual Studio

