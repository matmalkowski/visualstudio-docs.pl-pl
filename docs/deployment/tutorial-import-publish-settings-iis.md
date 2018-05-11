---
title: Publikowanie usług IIS przez zaimportowanie ustawień publikowania
ms.custom: Create and import a publishing profile to deploy an application from Visual Studio to IIS
ms.date: 05/07/2018
ms.technology: vs-ide-deployment
ms.topic: tutorial
helpviewer_keywords:
- deployment, publish settings
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1db8ca68453cff105f2bbefcd384b8afa9efea9d
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2018
---
# <a name="publish-an-application-to-iis-by-importing-publish-settings-in-visual-studio"></a>Publikowanie aplikacji usług IIS przez zaimportowanie ustawień publikowania w programie Visual Studio

Można użyć **publikowania** narzędzia do zaimportowania ustawień publikowania, a następnie wdrożyć aplikację. W tym artykule używamy ustawienia publikowania dla usług IIS, ale może użyć podobne kroki, aby zaimportować ustawienia publikowania dla [usłudze Azure App Service](../deployment/tutorial-import-publish-settings-azure.md). W niektórych scenariuszach stosowania Publikowanie profilu ustawień może być szybsza niż ręcznie konfigurować wdrożenia usług IIS dla każdej instalacji programu Visual Studio.

Te kroki dotyczą aplikacji ASP.NET, platformy ASP.NET Core i .NET Core w programie Visual Studio. Visual Studio 2017 wersji 15,6 odpowiada kroki.

W tym samouczku obejmują:

> [!div class="checklist"]
> * Skonfiguruj usługi IIS, dzięki czemu można wygenerować plik ustawień publikowania
> * Utwórz plik ustawień publikowania
> * Zaimportuj plik ustawień publikowania do programu Visual Studio
> * Wdrażanie aplikacji w usługach IIS

Plik ustawień publikowania (\*.publishsettings) różni się od profilu publikowania (\*.pubxml) utworzone w programie Visual Studio. Plik ustawień publikowania jest tworzony przez usługi IIS lub usłudze Azure App Service, lub można utworzyć ręcznie, a następnie go zaimportować do programu Visual Studio.

> [!NOTE]
> Jeśli jest potrzebna do skopiowania Visual Studio profilu publikowania (\*pliku .pubxml) z jednej instalacji programu Visual Studio do innego, można znaleźć profilu publikowania  *\<profilename\>.pubxml*, w  *\\< projectname\>\Properties\PublishProfiles* folderu dla typów projektów zarządzanych. Dla witryn sieci Web, sprawdź w obszarze *\App_Data* folderu. Profile publikowania są plikami XML programu MSBuild.

## <a name="prerequisites"></a>Wymagania wstępne

* Musi mieć zainstalowanego programu Visual Studio i **ASP.NET** i **.NET Framework** programowanie obciążenia. W przypadku aplikacji .NET Core należy również **.NET Core** obciążenia.

    Jeśli program Visual Studio nie został już zainstalowany, zainstaluj go bezpłatnie [tutaj](http://www.visualstudio.com).

    Kroki opisane w tym artykule są oparte na programie Visual Studio 2017 r.

* Aby wygenerować plik ustawień publikowania za pomocą programu IIS, musi być innym komputerze z systemem Windows Server 2012 z rolą serwera sieci Web programu IIS 8.0, poprawnie skonfigurowany i albo ASP.NET 4.5 lub zainstalowany program ASP.NET Core. Dla platformy ASP.NET Core, zobacz [publikowania w usługach IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration). Dla platformy ASP.NET 4.5, zobacz [IIS 8.0 przy użyciu programu ASP.NET 3.5 i ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Utwórz nowy projekt ASP.NET w programie Visual Studio

1. Na komputerze, działanie programu Visual Studio, wybierz **Plik > Nowy projekt**.

1. W obszarze **Visual C#** lub **Visual Basic**, wybierz **sieci Web**, a następnie w środkowym okienku wybierz albo **aplikacji sieci Web platformy ASP.NET (.NET Framework)** lub (C# tylko) **aplikacji sieci Web platformy ASP.NET Core**, a następnie kliknij przycisk **OK**.

    Jeśli szablony określony projekt nie jest widoczny, kliknij przycisk **Otwórz Instalator programu Visual Studio** łącze w lewym okienku **nowy projekt** okno dialogowe. Uruchamia Instalator programu Visual Studio. Zobacz wymagania wstępne w tym artykule, aby zidentyfikować wymagane obciążenia programu Visual Studio, które trzeba zainstalować.

1. Wybierz **MVC** (.NET Framework) lub **aplikacji sieci Web (Model-View-Controller)** (dla platformy .NET Core) i upewnij się, że **bez uwierzytelniania** jest zaznaczone, a następnie kliknij przycisk **OK**.

1. Wpisz nazwę, takich jak **MyWebApp** i kliknij przycisk **OK**.

    Program Visual Studio tworzy projekt.

1. Wybierz **kompilacji > Kompiluj rozwiązanie** Aby skompilować projekt.

## <a name="install-and-configure-web-deploy-on-windows-server"></a>Instalowanie i Konfigurowanie narzędzia Web Deploy w systemie Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

## <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Utwórz plik ustawień publikowania w usługach IIS w systemie Windows Server

1. W usługach IIS, kliknij prawym przyciskiem myszy **domyślna witryna sieci Web**, wybierz **Wdróż** > **skonfigurować wdrażanie publikowania w sieci Web**.

    ![Skonfiguruj ustawienia narzędzia Web Deploy](../deployment/media/tutorial-configure-web-deploy-publishing.png)

1. W **skonfigurować wdrażanie publikowania w sieci Web** okna dialogowego Sprawdź ustawienia.

1. Kliknij przycisk **Instalatora**.

    W **wyniki** panelu przedstawiono dane wyjściowe, które prawa dostępu przyznane określonego użytkownika, a plik z *.publishsettings* rozszerzenie pliku został wygenerowany w pokazanej w lokalizacji okno dialogowe.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <publishData>
      <publishProfile
        publishUrl="https://myhostname:8172/msdeploy.axd"
        msdeploySite="Default Web Site"
        destinationAppUrl="http://myhostname:80/"
        mySQLDBConnectionString=""
        SQLServerDBConnectionString=""
        profileName="Default Settings"
        publishMethod="MSDeploy"
        userName="myhostname\myusername" />
    </publishData>
    ```

    W zależności od konfiguracji systemu Windows Server i usług IIS zostanie wyświetlone różne wartości. Poniżej przedstawiono kilka szczegółowe informacje o wartości, które są wyświetlane:

    * *Msdeploy.axd* pliku, do którego odwołuje się `publishUrl` atrybut jest generowane dynamicznie pliku programu obsługi HTTP dla narzędzia Web Deploy. (Podczas testowania, `http://myhostname:8172` zazwyczaj będzie również działać.)
    * `publishUrl` Portu zwykle ma ustawioną wartość portu 8172, który jest domyślnym dla narzędzia Web Deploy.
    * `destinationAppUrl` Zwykle ustawiony port do portu 80, który jest domyślnym dla usług IIS.
    * Jeśli nie można nawiązać połączenia z hostem zdalnym w programie Visual Studio przy użyciu nazwy hosta (w kolejnych krokach), przetestuj adresów IP zamiast nazwy hosta.

    > [!NOTE]
    > Jeśli jest publikowana w usługach IIS działających na maszynie Wirtualnej platformy Azure, narzędzie Web Deploy i porty usługi IIS musi zostać otwarte w grupie zabezpieczeń sieci. Aby uzyskać szczegółowe informacje, zobacz [instalacji i uruchamiania usług IIS](/azure/virtual-machines/windows/quick-create-portal#open-port-80-for-web-traffic).

1. Skopiuj ten plik do komputera, na którym uruchomiony jest program Visual Studio.

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importowanie ustawień publikowania w programie Visual Studio i wdrażanie

1. Na komputerze, na którym znajduje się projekt ASP.NET jest otwarty w programie Visual Studio, kliknij prawym przyciskiem myszy projekt w Eksploratorze rozwiązań i wybierz polecenie **publikowania**.

1. Jeśli wcześniej skonfigurowano żadnych profilów publikowania, **publikowania** pojawi się okienko. Kliknij przycisk **Utwórz nowy profil**.

1. W **wybierz element docelowy publikowania** okno dialogowe, kliknij przycisk **Importuj profil**.

    ![Wybierz publikowania](../deployment/media/tutorial-publish-tool-import-profile.png)

1. Przejdź do lokalizacji pliku ustawień publikowania, który został utworzony w poprzedniej sekcji.

1. W **pliku ustawień publikowania importu** okno dialogowe, przejdź do i wybierz profil, który został utworzony w poprzedniej sekcji i kliknij **Otwórz**.

    Visual Studio rozpoczyna proces wdrażania oraz w oknie danych wyjściowych przedstawia postęp i wyniki.

    Wszystkie wdrożenia występują błędy, kliknij przycisk **ustawienia** Aby edytować ustawienia. Zmodyfikuj ustawienia i kliknij przycisk **weryfikacji** do testowania nowych ustawień.

    ![Edytuj ustawienia w narzędziu do publikowania](../deployment/media/tutorial-configure-publish-settings-in-tool.png)

## <a name="next-steps"></a>Następne kroki

W tym samouczku utworzony plik ustawień publikowania, zaimportowany do programu Visual Studio i wdrożeniu aplikacji ASP.NET w usługach IIS.

> [!div class="nextstepaction"]
> [Pierwsze spojrzenie na wdrażanie](../deployment/deploying-applications-services-and-components.md)
