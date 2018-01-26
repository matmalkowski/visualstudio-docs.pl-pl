---
title: "Zdalne debugowanie platformy ASP.NET Core na komputerze zdalnym usług IIS | Dokumentacja firmy Microsoft"
ms.custom: remotedebugging
ms.date: 08/14/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 573a3fc5-6901-41f1-bc87-557aa45d8858
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: f1938473a3a5e085e63b9b522bbc31678dedbbd4
ms.sourcegitcommit: 69b898d8d825c1a2d04777abf6d03e03fefcd6da
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2018
---
# <a name="remote-debug-aspnet-core-on-a-remote-iis-computer-in-visual-studio-2017"></a>Zdalne debugowanie platformy ASP.NET Core na komputerze zdalnym usług IIS w Visual Studio 2017 r
Do debugowania aplikacji ASP.NET, która została wdrożona do usług IIS, zainstalować i uruchomić narzędzia zdalnej na komputerze, których wdrożono aplikację, a następnie dołącz do uruchomionej aplikacji z programu Visual Studio.

![Składniki zdalnego debugera](../debugger/media/remote-debugger-aspnet.png "Remote_debugger_components")

W tym przewodniku opisano sposób konfigurowania i konfigurowanie programu Visual Studio 2017 platformy ASP.NET Core, wdrażanie usług IIS i dołączyć debuger zdalny z programu Visual Studio. Do zdalnego debugowania ASP.NET 4.5.2, zobacz [zdalnego debugowania ASP.NET na komputerze IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md). Można także wdrożyć i debugowania w usługach IIS przy użyciu usługi Azure. Dla usługi Azure App Service można łatwe wdrażanie i debugowanie na wstępnie skonfigurowane wystąpienia usług IIS i zdalnego debugera za pomocą [debugera migawki](../debugger/debug-live-azure-applications.md) lub [dołączanie debugera z Eksploratora serwera](../debugger/remote-debugging-azure.md).

Procedury te zostały przetestowane na tych konfiguracji serwera:
* Windows Server 2012 R2 i IIS 8
* Windows Server 2016 i IIS 10

## <a name="requirements"></a>Wymagania

Debugowanie między dwoma komputerami połączone za pośrednictwem serwera proxy nie jest obsługiwane. Debugowanie za pośrednictwem duże opóźnienie lub połączenie o niskiej przepustowości, takich jak Internet, połączenia telefonicznego lub przez Internet między krajów nie jest zalecana i może się nie powieść lub zbyt wolno. Aby uzyskać pełną listę wymagań, zobacz [wymagania](../debugger/remote-debugging.md#requirements_msvsmon).

## <a name="create-the-aspnet-core-application-on-the-visual-studio-2017-computer"></a>Tworzenie aplikacji platformy ASP.NET Core na komputerze programu Visual Studio 2017 r. 

1. Tworzenie nowej aplikacji platformy ASP.NET Core. (**Plik > Nowy > Projekt**, a następnie wybierz pozycję **Visual C# > sieci Web > Aplikacja sieci Web platformy ASP.NET Core**).

    W **platformy ASP.NET Core** sekcji szablonów, wybierz opcję **aplikacji sieci Web**.

2. Upewnij się, że **ASP.NET Core 2.0** jest zaznaczone, który **Włącz obsługę Docker** jest **nie** wybrany, a **uwierzytelniania** ma ustawioną wartość **Bez uwierzytelniania**.

3. Nazwij projekt **MyASPApp** i kliknij przycisk **OK** do tworzenia nowego rozwiązania.

4. Otwórz plik About.cshtml.cs i ustaw punkt przerwania `OnGet` — metoda (w szablonach starsze HomeController.cs zamiast tego otworzyć i ustawić punkt przerwania `About()` metody).

## <a name="bkmk_configureIIS"></a>Instalowanie i konfigurowanie usług IIS w systemie Windows Server

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Zaktualizuj ustawienia zabezpieczeń przeglądarki w systemie Windows Server

W zależności od ustawienia zabezpieczeń mogą go zapisać czasu, należy dodać następujące zaufanych witryn do przeglądarki, można łatwo pobrać opisane w tym samouczku oprogramowanie. Może być wymagany dostęp do tych witryn:

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- visualstudio.com

Jeśli korzystasz z programu Internet Explorer, możesz dodać zaufanych witryn, przechodząc do **Opcje internetowe > Zabezpieczenia > Zaufane witryny > witryny**. Te kroki są różne dla innych przeglądarek. (Jeśli chcesz pobrać starszej wersji zdalnego debugera z my.visualstudio.com niektóre dodatkowe zaufanych witryn są wymagane do logowania).

Podczas pobierania oprogramowania może otrzymywać żądania udzielenia uprawnienie do ładowania różnych skrypty witryny sieci web i zasobów. W większości przypadków te dodatkowe zasoby nie są wymagane do zainstalowania oprogramowania.

## <a name="install-aspnet-core-on-windows-server"></a>Instalowanie platformy ASP.NET Core w systemie Windows Server

1. Zainstaluj [.NET Core systemu Windows serwer obsługujący](https://aka.ms/dotnetcore-2-windowshosting) pakietu przez system operacyjny. Pakiet instaluje podstawowego środowiska wykonawczego platformy .NET, biblioteka programu .NET Core i moduł platformy ASP.NET Core. Aby uzyskać dodatkowe szczegółowe instrukcje, zobacz [publikowania w usługach IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration).

    > [!NOTE]
    > Jeśli system nie ma połączenia internetowego, Uzyskaj i zainstaluj  *[Microsoft Visual C++ 2015 Redistributable](https://www.microsoft.com/download/details.aspx?id=53840)*  przed zainstalowaniem pakietu Hosting .NET Core systemu Windows Server.

3. Ponowne uruchomienie systemu (lub wykonać **net stop została /y** następuje **net start w3svc** z wiersza polecenia, aby pobrać zmiany systemowej PATH).

## <a name="BKMK_install_webdeploy"></a>(Opcjonalnie) Instalacja narzędzia Web Deploy 3,6 w systemie Windows Server

[!INCLUDE [remote-debugger-install-web-deploy](../debugger/includes/remote-debugger-install-web-deploy.md)]

## <a name="BKMK_deploy_asp_net"></a>Konfiguruj witrynę sieci Web platformy ASP.NET na komputerze serwera systemu Windows

1. Otwórz Eksploratora Windows i Utwórz nowy folder **C:\Publish**, których później będą wdrażać projektu programu ASP.NET.

2. Otwórz **internetowych usług informacyjnych (IIS) Manager**. (W lewym okienku w Menedżerze serwera wybierz **IIS**. Kliknij prawym przyciskiem myszy serwer, a następnie wybierz **Internet Information Services (IIS) Manager**.)

3. W obszarze **połączeń** w okienku po lewej stronie, przejdź do **witryny**.

4. Wybierz **domyślna witryna sieci Web**, wybierz **podstawowe ustawienia**i ustaw **ścieżka fizyczna** do **C:\Publish**.

4. Kliknij prawym przyciskiem myszy **domyślna witryna sieci Web** a następnie wybierz węzeł **Dodawanie aplikacji**.

5. Ustaw **Alias** do **MyASPApp**, zaakceptuj wartość domyślną pulę aplikacji (**DefaultAppPool**) i ustaw **ścieżka fizyczna** do  **C:\Publish**.

6. W obszarze **połączeń**, wybierz pozycję **pul aplikacji**. Otwórz **DefaultAppPool** i ustaw dla pola puli aplikacji **bez kodu zarządzanego**.

7. Kliknij prawym przyciskiem myszy nową lokację w Menedżerze usług IIS, wybierz **Edytuj uprawnienia**i upewnij się, że IUSR, IIS_IUSRS lub nazwą użytkownika skonfigurowaną dla dostępu do aplikacji sieci web jest autoryzowanym użytkownikiem z prawami Odczyt i wykonywanie.

    Jeśli nie widzisz jednego z tych użytkowników z dostępem, przejść przez kroki, aby dodać konta IUSR jako użytkownik z uprawnieniami Odczyt i wykonywanie.

## <a name="bkmk_webdeploy"></a>(Opcjonalnie) Publikowanie i wdrażanie aplikacji przy użyciu narzędzia Web Deploy w programie Visual Studio

[!INCLUDE [remote-debugger-deploy-app-web-deploy](../debugger/includes/remote-debugger-deploy-app-web-deploy.md)]

## <a name="optional-publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>(Opcjonalnie) Publikowanie i wdrażanie aplikacji przez publikowanie do folderu lokalnego z programu Visual Studio

Można również publikowanie i wdrażanie aplikacji przy użyciu systemu plików lub innych narzędzi.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

## <a name="BKMK_msvsmon"></a>Pobierz i zainstaluj narzędzia zdalnego w systemie Windows Server

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

> [!TIP]
> W niektórych scenariuszach może być najbardziej efektywny do uruchamiania zdalnego debugera z udziału plików. Aby uzyskać więcej informacji, zobacz [uruchamiania zdalnego debugera z udziału plików](../debugger/remote-debugging.md#fileshare_msvsmon).
  
## <a name="BKMK_setup"></a>Konfigurowanie zdalnego debugera w systemie Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Jeśli należy dodać uprawnienia dla dodatkowych użytkowników do zmiany trybu uwierzytelniania lub numer portu dla zdalnego debugera, zobacz [skonfigurować debugera zdalnego](../debugger/remote-debugging.md#configure_msvsmon).

Aby uzyskać informacje na temat uruchamiania zdalnego debugera jako usługi, zobacz [uruchamiania zdalnego debugera jako usługi](../debugger/remote-debugging.md#bkmk_configureService).

## <a name="BKMK_attach"></a>Dołączanie do aplikacji platformy ASP.NET z komputera programu Visual Studio

1. Na komputerze programu Visual Studio Otwórz **MyASPApp** rozwiązania.
2. W programie Visual Studio, kliknij przycisk **Debuguj > dołączyć do procesu** (Ctrl + Alt + P).

    > [!TIP]
    > W programie Visual Studio 2017 r, można ponownie dołączyć do tego samego procesu wcześniej podłączany do przy użyciu **Debuguj > ponownie dołączyć do procesu...** (Shift + Alt + P). 

3. Ustaw dla pola kwalifikator  **\<nazwę komputera zdalnego >: 4022**.
4. Kliknij przycisk **Odśwież**.
    Powinny pojawić się niektóre procesy, które są wyświetlane w **dostępne procesy** okna.

    Jeśli nie widać żadnych procesów, spróbuj użyć adresu IP zamiast nazwy komputera zdalnego (wymagana jest port). Można użyć `ipconfig` w wierszu polecenia, aby uzyskać adres IPv4.

    Jeśli chcesz użyć **znaleźć** przycisku, konieczne może być [Otwórz UDP port 3702](#bkmk_openports) na serwerze.

5. Sprawdź **Pokaż procesy wszystkich użytkowników**.
6. Wpisz nazwę procesu, aby szybko znaleźć literą **dotnet.exe** (dla platformy ASP.NET Core).

    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg_attachtoprocess_aspnetcore.png "RemoteDBG_AttachToProcess")

7. Kliknij przycisk **dołączyć**.

8. Otwórz witrynę sieci Web na komputerze zdalnym. W przeglądarce przejdź do **http://\<nazwę komputera zdalnego >**.
    
    Powinna zostać wyświetlona strona sieci web ASP.NET.

9. W uruchomionej aplikacji ASP.NET, kliknij łącze, aby **o** strony.

    Punkt przerwania powinien trafienie w programie Visual Studio.

## <a name="bkmk_openports"></a>Rozwiązywanie problemów: Otwórz wymagane porty w systemie Windows Server

W większości konfiguracji są otwarte porty wymagane przez instalację programu ASP.NET i zdalnego debugera. Jednak należy sprawdzić, czy porty są otwarte.

> [!NOTE]
> Na maszynie Wirtualnej platformy Azure, należy otworzyć porty za pośrednictwem [sieciowej grupy zabezpieczeń](/azure/virtual-machines/virtual-machines-windows-hero-role#open-port-80). 

Wymagane porty:

- 80 - wymagane dla usług IIS
- 4022 — wymagane do zdalnego debugowania z programu Visual Studio 2017 (zobacz [przypisania portów usługi zdalnego debugera](../debugger/remote-debugger-port-assignments.md) Aby uzyskać szczegółowe informacje.
- 8172 - (opcjonalnie) wymagany dla narzędzia Web Deploy do wdrażania aplikacji w programie Visual Studio.
- UDP 3702 — port odnajdywania (opcjonalnie) umożliwia **znaleźć** przycisku związane ze zdalnym debugerem programu Visual Studio.

1. Aby otworzyć port w systemie Windows Server, otwórz **Start** menu, wyszukaj **Zapora systemu Windows z zabezpieczeniami zaawansowanymi**.

2. Następnie wybierz pozycję **reguły ruchu przychodzącego > Nowa reguła > portu**, a następnie kliknij przycisk **dalej**. (Wybierz UDP 3702 **reguły wychodzące** zamiast tego.)

3. W obszarze **określone porty lokalne**, wprowadź numer portu, kliknij przycisk **dalej**.

4. Kliknij przycisk **zezwalały na połączenie**, kliknij przycisk **dalej**.

5. Wybierz co najmniej jeden typ sieci można włączyć dla portu, a następnie kliknij przycisk **dalej**.

    Wybrany typ musi zawierać sieci, do którego jest podłączony komputera zdalnego.
6. Dodaj nazwę (na przykład **IIS**, **narzędzia Web Deploy**, lub **polecenia msvsmon**) reguły ruchu przychodzącego i kliknij **Zakończ**.

    Powinna zostać wyświetlona nowej reguły na liście reguły ruchu przychodzącego lub wychodzącego reguły.

    Aby uzyskać więcej informacji na temat konfigurowania Zapory systemu Windows, zobacz [konfigurowania Zapory systemu Windows do zdalnego debugowania](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

3. Utworzenie dodatkowych reguł dla wymaganych portów.
