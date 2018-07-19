---
title: Wdrażanie platformy ASP.NET w usługach IIS za pomocą narzędzia Web Deploy
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
ms.openlocfilehash: 4705ca6e72001f8930e2fa4270515df53e1213a8
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/17/2018
ms.locfileid: "39080853"
---
# <a name="deploy-aspnet-to-a-remote-iis-computer-using-web-deploy-in-visual-studio"></a>Wdrażanie platformy ASP.NET z komputerem zdalnym usług IIS za pomocą narzędzia Web Deploy w programie Visual Studio

W tym artykule wyjaśniono, jak skonfigurować i konfigurowanie programu Visual Studio 2017 aplikacji platformy ASP.NET MVC 4.5.2 oraz wdrożyć ją w usługach IIS. Ten artykuł zawiera instrukcje dotyczące konfigurowania podstawowej konfiguracji programu IIS na serwerze Windows i wdrażanie aplikacji w programie Visual Studio. Te kroki są uwzględnione, aby upewnić się, że serwer wymaga zainstalowania składników i można przystąpić do wdrażania. Jeśli wdrażasz aplikację ASP.NET Core, niektóre kroki są różne. Aby wdrożyć aplikację ASP.NET Core, zobacz [publikowania aplikacji w usługach IIS przez importowanie ustawień publikowania](../deployment/tutorial-import-publish-settings-iis.md) instrukcje. W niektórych scenariuszach ASP.NET i ASP.NET Core to szybsze do wdrożenia usług IIS przez importowanie ustawień publikowania.

Procedury te zostały przetestowane na te konfiguracje serwera:
* Windows Server 2012 R2 oraz usług IIS 8 (dla systemu Windows Server 2008 R2, server kroki są różne)

## <a name="create-the-aspnet-452-application-on-the-visual-studio-computer"></a>Tworzenie platformy ASP.NET 4.5.2 aplikacji na komputerze programu Visual Studio
  
1. Na komputerze z programem Visual Studio wybierz **pliku** > **nowy projekt**.

1. W obszarze **Visual C#** lub **języka Visual Basic**, wybierz **Web**, a następnie w środkowym okienku wybierz **aplikacji sieci Web platformy ASP.NET (.NET Framework)** a następnie kliknij przycisk **OK**.

    Jeśli nie widzisz szablony określonego projektu, kliknij przycisk **Otwórz Instalator programu Visual Studio** łącze w okienku po lewej stronie **nowy projekt** okno dialogowe. Uruchamia Instalatora programu Visual Studio. Zobacz wymagania wstępne w tym artykule, aby zidentyfikować wymagane obciążeń programu Visual Studio, które trzeba zainstalować.

1. Wybierz **MVC** (.NET Framework) i upewnij się, że **bez uwierzytelniania** jest zaznaczone, a następnie kliknij przycisk **OK**.

1. Wpisz nazwę, takich jak **MyWebApp** i kliknij przycisk **OK**.

    Program Visual Studio tworzy projekt.

1. Wybierz **kompilacji** > **Kompiluj rozwiązanie** do skompilowania projektu.

## <a name="install-and-configure-iis-on-windows-server"></a>Instalowanie i konfigurowanie usług IIS w systemie Windows Server

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Zaktualizuj ustawienia zabezpieczeń przeglądarki w systemie Windows Server

Jeśli Konfiguracja zwiększonych zabezpieczeń jest włączone w programie Internet Explorer (jest włączony domyślnie), następnie należy może być konieczne dodanie niektórych domen jako zaufane witryny, aby umożliwić pobieranie niektóre składniki serwera sieci web. Dodaj zaufanych witryn, przechodząc do **Opcje internetowe** > **zabezpieczeń** > **zaufanych witryn** > **witryn** . Dodaj następujące domeny.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- Program IIS.NET

Po pobraniu oprogramowania, może zostać żądania, aby przyznać uprawnienie do ładowania różnych skrypty witryny sieci web i zasobami. Niektóre z tych zasobów nie są wymagane, ale w celu uproszczenia procesu, należy kliknąć **Dodaj** po wyświetleniu monitu.

## <a name="install-aspnet-45-on-windows-server"></a>Zainstaluj program ASP.NET 4.5 w systemie Windows Server

Aby uzyskać bardziej szczegółowe informacje, aby zainstalować program ASP.NET w usługach IIS, zobacz [IIS 8.0 przy użyciu ASP.NET 3.5 i program ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

1. W okienku po lewej stronie w Menedżerze serwera wybierz **IIS**. Kliknij prawym przyciskiem myszy serwer, a następnie wybierz pozycję **Internet Information Services (IIS) Manager**.

1. Użyj Instalatora platformy sieci Web (WebPI), aby zainstalować program ASP.NET 4.5 (z węzła serwera w systemie Windows Server 2012 R2, wybierz **pobieranie nowych składników platformy sieci Web** i wyszukaj program ASP.NET)

    ![RemoteDBG_IIS_AspNet_45](../debugger/media/remotedbg_iis_aspnet_45.png "RemoteDBG_IIS_AspNet_45")

    > [!NOTE]
    > Jeśli używasz systemu Windows Server 2008 R2, zainstaluj platformy ASP.NET 4, zamiast tego za pomocą tego polecenia:

     **C:\Windows\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -ir**

2. Ponowne uruchomienie systemu (lub wykonania **net stop został /y** następuje **net start w3svc** z wiersza polecenia, aby wczytać zmiany w systemie ścieżki).

## <a name="install-web-deploy-36-on-windows-server"></a>Instalacja narzędzia Web Deploy 3.6 w systemie Windows Server

[!INCLUDE [remote-debugger-install-web-deploy](../debugger/includes/remote-debugger-install-web-deploy.md)]

## <a name="configure-aspnet-web-site-on-the-windows-server-computer"></a>Konfigurowanie witryny sieci Web ASP.NET na komputerze z systemem Windows Server

1. Otwórz Eksploratora Windows i Utwórz nowy folder **C:\Publish**, gdzie będą później wdrożyć projekt ASP.NET.

2. Jeśli nie jest jeszcze otwarty, otwórz **Internet Information Services (IIS) Manager**. (W lewym okienku w Menedżerze serwera wybierz **IIS**. Kliknij prawym przyciskiem myszy serwer, a następnie wybierz pozycję **Internet Information Services (IIS) Manager**.)

3. W obszarze **połączeń** w okienku po lewej stronie przejdź do **witryn**.

4. Wybierz **domyślna witryna sieci Web**, wybierz **podstawowych ustawień**i ustaw **ścieżkę fizyczną** do **C:\Publish**.

5. Kliknij prawym przyciskiem myszy **domyślna witryna sieci Web** a następnie wybierz węzeł **Add Application**.

6. Ustaw **Alias** pole **MyASPApp**, zaakceptuj domyślne ustawienie puli aplikacji (**DefaultAppPool**) i ustaw **ścieżkę fizyczną** do  **C:\Publish**.

7. W obszarze **połączeń**, wybierz opcję **pul aplikacji**. Otwórz **DefaultAppPool** i ustawić pole puli aplikacji **ASP.NET v4.0** (ASP.NET 4.5 nie jest opcją dla puli aplikacji).

8. Z witryną wybrane w Menedżerze usług IIS, wybierz **Edytuj uprawnienia**i upewnij się, że IUSR, IIS_IUSRS lub użytkownika skonfigurowane dla puli aplikacji jest autoryzowanym użytkownikiem z uprawnień Odczyt i wykonywanie. Jeśli żaden z tych użytkowników jest obecny, Dodaj IUSR jako użytkownik z uprawnieniami Odczyt i wykonywanie.

## <a name="publish-and-deploy-the-app-using-web-deploy-from-visual-studio"></a>Publikowanie i wdrażanie aplikacji za pomocą narzędzia Web Deploy w programie Visual Studio

[!INCLUDE [deploy-app-web-deploy](../deployment/includes/deploy-app-web-deploy.md)]

Ponadto należy do odczytu w poniższej sekcji na temat rozwiązywania problemów portów.

## <a name="troubleshoot-open-required-ports-on-windows-server"></a>Rozwiązywanie problemów: Otworzyć wymagane porty w systemie Windows Server

W większości konfiguracji wymagane porty są otwarte przez instalację programu ASP.NET i narzędzia Web Deploy. Jednak może być konieczne Sprawdź, czy porty zostały otwarte.

> [!NOTE]
> Na Maszynie wirtualnej platformy Azure, należy otworzyć porty za pośrednictwem [sieciowej grupy zabezpieczeń](/azure/virtual-machines/virtual-machines-windows-hero-role#open-port-80). 

Wymagane porty:

* 80 - wymagane dla usług IIS
* 8172 - wymagane dla narzędzia Web Deploy do wdrażania aplikacji w programie Visual Studio

1. Aby otworzyć port w systemie Windows Server, należy otworzyć **Start** menu, wyszukaj **Zapora Windows z zabezpieczeniami zaawansowanymi**.

2. Następnie wybierz **reguły ruchu przychodzącego** > **nową regułę** > **portu**. Wybierz **dalej** i w obszarze **określone porty lokalne**, wprowadź numer portu, kliknij przycisk **dalej**, następnie **Zezwalaj na połączenie**, kliknij przycisk Dalej, i Dodaj nazwę (**IIS**, **narzędzia Web Deploy**, lub **msvsmon**) dla reguły ruchu przychodzącego.

    Jeśli chcesz, aby uzyskać więcej informacji na temat konfigurowania zapory Windows, zobacz [skonfigurować zaporę Windows do zdalnego debugowania](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

3. Utwórz dodatkowe reguły dla wymaganych portów.

## <a name="next-steps"></a>Następne kroki

W tym samouczku utworzono plik ustawień publikowania, zaimportowany do programu Visual Studio i wdrożoną aplikację ASP.NET w usługach IIS. Można także wdrożyć przez zaimportowanie ustawień publikowania.

> [!div class="nextstepaction"]
> [Wdrażanie usług IIS przez importowanie ustawień publikowania](../deployment/tutorial-import-publish-settings-iis.md)
