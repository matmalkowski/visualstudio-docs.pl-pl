---
title: Wdrażanie programu ASP.NET w usługach IIS za pomocą narzędzia Web Deploy
ms.custom: ''
ms.date: 06/04/2018
ms.technology: vs-ide-deployment
ms.topic: tutorial
ms.assetid: 9cb339b5-3caf-4755-aad1-4a5da54b2a23
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: a63d9947f544ddff1de81aaf34ed62c9646fba3d
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2018
ms.locfileid: "34794226"
---
# <a name="deploy-aspnet-to-a-remote-iis-computer-using-web-deploy-in-visual-studio"></a>Wdrażanie programu ASP.NET z komputerem zdalnym usług IIS przy użyciu narzędzia Web Deploy w programie Visual Studio

W tym artykule wyjaśniono, jak skonfigurować i konfigurowania aplikacji programu Visual Studio 2017 ASP.NET MVC 4.5.2 i wdrożyć ją w usługach IIS. Ten artykuł zawiera kroki na konfigurowaniu podstawowych konfiguracji usług IIS w systemie Windows server i wdrażania aplikacji w programie Visual Studio. Te kroki są dołączone do upewnij się, że serwer ma wymagane składniki zainstalowane i można przystąpić do wdrażania. Jeśli wdrażana aplikacja platformy ASP.NET Core, niektóre kroki są różne. Aby wdrożyć aplikację ASP.NET Core, zobacz [publikowania aplikacji usług IIS przez zaimportowanie ustawień publikowania](../deployment/tutorial-import-publish-settings-iis.md) instrukcje. W niektórych scenariuszach ASP.NET i ASP.NET Core to szybsze do wdrożenia usług IIS przez zaimportowanie ustawień publikowania.

Procedury te zostały przetestowane na tych konfiguracji serwera:
* Windows Server 2012 R2 i IIS 8 (dla systemu Windows Server 2008 R2 kroki serwera są różne)

## <a name="create-the-aspnet-452-application-on-the-visual-studio-computer"></a>Utwórz platformy ASP.NET 4.5.2 aplikacji na komputerze programu Visual Studio
  
1. Na komputerze, działanie programu Visual Studio, wybierz **Plik > Nowy projekt**.

1. W obszarze **Visual C#** lub **Visual Basic**, wybierz **sieci Web**, a następnie w środkowym okienku wybierz albo **aplikacji sieci Web platformy ASP.NET (.NET Framework)**, a następnie kliknij przycisk **OK**.

    Jeśli szablony określony projekt nie jest widoczny, kliknij przycisk **Otwórz Instalator programu Visual Studio** łącze w lewym okienku **nowy projekt** okno dialogowe. Uruchamia Instalator programu Visual Studio. Zobacz wymagania wstępne w tym artykule, aby zidentyfikować wymagane obciążenia programu Visual Studio, które trzeba zainstalować.

1. Wybierz **MVC** (.NET Framework) i upewnij się, że **bez uwierzytelniania** jest zaznaczone, a następnie kliknij przycisk **OK**.

1. Wpisz nazwę, takich jak **MyWebApp** i kliknij przycisk **OK**.

    Program Visual Studio tworzy projekt.

1. Wybierz **kompilacji > Kompiluj rozwiązanie** Aby skompilować projekt.

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

## <a name="BKMK_install_webdeploy"></a> Instalacja narzędzia Web Deploy 3,6 w systemie Windows Server

[!INCLUDE [remote-debugger-install-web-deploy](../debugger/includes/remote-debugger-install-web-deploy.md)]

## <a name="BKMK_deploy_asp_net"></a> Konfiguruj witrynę sieci Web platformy ASP.NET na komputerze serwera systemu Windows

1. Otwórz Eksploratora Windows i Utwórz nowy folder **C:\Publish**, których później będą wdrażać projektu programu ASP.NET.

2. Jeśli go nie jest jeszcze otwarty, otwórz **Internet Information Services (IIS) Manager**. (W lewym okienku w Menedżerze serwera wybierz **IIS**. Kliknij prawym przyciskiem myszy serwer, a następnie wybierz **Internet Information Services (IIS) Manager**.)

3. W obszarze **połączeń** w okienku po lewej stronie, przejdź do **witryny**.

4. Wybierz **domyślna witryna sieci Web**, wybierz **podstawowe ustawienia**i ustaw **ścieżka fizyczna** do **C:\Publish**.

5. Kliknij prawym przyciskiem myszy **domyślna witryna sieci Web** a następnie wybierz węzeł **Dodawanie aplikacji**.

6. Ustaw **Alias** do **MyASPApp**, zaakceptuj wartość domyślną pulę aplikacji (**DefaultAppPool**) i ustaw **ścieżka fizyczna** do  **C:\Publish**.

7. W obszarze **połączeń**, wybierz pozycję **pul aplikacji**. Otwórz **DefaultAppPool** i ustaw dla pola puli aplikacji **ASP.NET v4.0** (ASP.NET 4.5 nie jest opcją dla puli aplikacji).

8. Z witryną wybrane w Menedżerze usług IIS, wybierz **Edytuj uprawnienia**i upewnij się, że IUSR, IIS_IUSRS lub nazwą użytkownika skonfigurowaną dla puli aplikacji jest autoryzowanym użytkownikiem z prawami Odczyt i wykonywanie. Jeśli żaden z tych użytkowników nie jest obecny, Dodaj konta IUSR jako użytkownik z uprawnieniami Odczyt i wykonywanie.

## <a name="bkmk_webdeploy"></a> Publikowanie i wdrażanie aplikacji przy użyciu narzędzia Web Deploy w programie Visual Studio

[!INCLUDE [deploy-app-web-deploy](../deployment/includes/deploy-app-web-deploy.md)]

Ponadto należy przeczytać sekcję na [Rozwiązywanie problemów z portów](#bkmk_openports).

## <a name="bkmk_openports"></a> Rozwiązywanie problemów: Otwórz wymagane porty w systemie Windows Server

W większości konfiguracji są otwarte porty wymagane przez instalację programu ASP.NET i narzędzia Web Deploy. Jednak należy sprawdzić, czy porty są otwarte.

> [!NOTE]
> Na maszynie Wirtualnej platformy Azure, należy otworzyć porty za pośrednictwem [sieciowej grupy zabezpieczeń](/azure/virtual-machines/virtual-machines-windows-hero-role#open-port-80). 

Wymagane porty:

* 80 - wymagane dla usług IIS
* 8172 — wymagane dla narzędzia Web Deploy do wdrażania aplikacji w programie Visual Studio

1. Aby otworzyć port w systemie Windows Server, otwórz **Start** menu, wyszukaj **Zapora systemu Windows z zabezpieczeniami zaawansowanymi**.

2. Następnie wybierz pozycję **reguły ruchu przychodzącego > Nowa reguła > portu**. Wybierz **dalej** i w obszarze **określone porty lokalne**, wprowadź numer portu, kliknij przycisk **dalej**, następnie **zezwalały na połączenie**, kliknij przycisk Dalej, a Dodaj nazwę (**IIS**, **narzędzia Web Deploy**, lub **polecenia msvsmon**) dla reguły ruchu przychodzącego.

    Aby uzyskać więcej informacji na temat konfigurowania Zapory systemu Windows, zobacz [konfigurowania Zapory systemu Windows do zdalnego debugowania](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

3. Utworzenie dodatkowych reguł dla wymaganych portów.

## <a name="next-steps"></a>Następne kroki

W tym samouczku utworzony plik ustawień publikowania, zaimportowany do programu Visual Studio i wdrożeniu aplikacji ASP.NET w usługach IIS. Można także wdrożyć przez zaimportowanie ustawień publikowania.

> [!div class="nextstepaction"]
> [Wdróż do usług IIS przez zaimportowanie ustawień publikowania](../deployment/tutorial-import-publish-settings-iis.md)