---
title: Publikowanie na platformie Azure przez zaimportowanie ustawień publikowania
ms.custom: Create and import a publishing profile to deploy an application from Visual Studio to Azure App Service
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
ms.openlocfilehash: a0fcc9f6ec4143a757139a9e013f1a1f4dbe666e
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2018
---
# <a name="publish-an-application-to-azure-app-service-by-importing-publish-settings-in-visual-studio"></a>Publikowanie aplikacji w usłudze Azure App Service przez zaimportowanie ustawień publikowania w programie Visual Studio

Można użyć **publikowania** narzędzia do zaimportowania ustawień publikowania, a następnie wdrożyć aplikację. W tym artykule używamy ustawienia publikowania dla usługi aplikacji Azure, ale można użyć publikowania podobne kroki, aby zaimportować ustawienia z [IIS](../deployment/tutorial-import-publish-settings-iis.md). W niektórych scenariuszach stosowania Publikowanie profilu ustawień może być szybsza niż ręcznie konfigurować wdrożenia usługi dla każdej instalacji programu Visual Studio.

Te kroki dotyczą aplikacji ASP.NET, platformy ASP.NET Core i .NET Core w programie Visual Studio. Visual Studio 2017 wersji 15,6 odpowiada kroki.

W tym samouczku obejmują:

> [!div class="checklist"]
> * Generuj plik ustawień publikowania w usłudze Azure App Service
> * Zaimportuj plik ustawień publikowania do programu Visual Studio
> * Wdrażanie aplikacji w usłudze Azure App Service

Plik ustawień publikowania (*.publishsettings) różni się od profilu publikowania (*.pubxml) utworzone w programie Visual Studio. Plik ustawień publikowania jest tworzony przez usługę Azure App Service, a następnie go zaimportować do programu Visual Studio.

> [!NOTE]
> Jeśli jest potrzebna do skopiowania Visual Studio profilu publikowania (\*pliku .pubxml) z jednej instalacji programu Visual Studio do innego, można znaleźć profilu publikowania  *\<profilename\>.pubxml*, w  *\\< projectname\>\Properties\PublishProfiles* folderu dla typów projektów zarządzanych. Dla witryn sieci Web, sprawdź w obszarze *\App_Data* folderu. Profile publikowania są plikami XML programu MSBuild.

## <a name="prerequisites"></a>Wymagania wstępne

* Musi mieć zainstalowanego programu Visual Studio i **ASP.NET** i **.NET Framework** programowanie obciążenia. W przypadku aplikacji .NET Core należy również **.NET Core** obciążenia.

    Jeśli program Visual Studio nie został już zainstalowany, zainstaluj go bezpłatnie [tutaj](http://www.visualstudio.com).

* Tworzenie usługi aplikacji Azure. Aby uzyskać szczegółowe instrukcje, zobacz [wdrażanie aplikacji sieci web platformy ASP.NET Core na platformie Azure przy użyciu programu Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). 

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Utwórz nowy projekt ASP.NET w programie Visual Studio

1. Na komputerze, działanie programu Visual Studio, wybierz **Plik > Nowy projekt**.

1. W obszarze **Visual C#** lub **Visual Basic**, wybierz **sieci Web**, a następnie w środkowym okienku wybierz albo **aplikacji sieci Web platformy ASP.NET (.NET Framework)** lub (C# tylko) **aplikacji sieci Web platformy ASP.NET Core**, a następnie kliknij przycisk **OK**.

    Jeśli szablony określony projekt nie jest widoczny, kliknij przycisk **Otwórz Instalator programu Visual Studio** łącze w lewym okienku **nowy projekt** okno dialogowe. Uruchamia Instalator programu Visual Studio. Zobacz wymagania wstępne w tym artykule, aby zidentyfikować wymagane obciążenia programu Visual Studio, które trzeba zainstalować.

1. Wybierz **MVC** (.NET Framework) lub **aplikacji sieci Web (Model-View-Controller)** (dla platformy .NET Core) i upewnij się, że **bez uwierzytelniania** jest zaznaczone, a następnie kliknij przycisk **OK**.

1. Wpisz nazwę, takich jak **MyWebApp** i kliknij przycisk **OK**.

    Program Visual Studio tworzy projekt.

1. Wybierz **kompilacji > Kompiluj rozwiązanie** Aby skompilować projekt.

## <a name="create-the-publish-settings-file-in-azure-app-service"></a>Utwórz plik ustawień publikowania w usłudze Azure App Service

1. W portalu Azure Otwórz usługi Azure App Service.

1. Kliknij przycisk **profilu publikowania Get** profilu i zapisz go lokalnie.

    ![Pobierz profil publikacji](../deployment/media/tutorial-azure-app-service-get-publish-profile.png)

    Plik o *.publishsettings* rozszerzenie pliku został wygenerowany w lokalizacji, w którym został zapisany. Poniższy kod przedstawia częściowe przykład pliku (w bardziej czytelnym formatowanie).

    ```xml
    <publishData>
      <publishProfile
        profileName="DeployASPDotNetCore - Web Deploy"
        publishMethod="MSDeploy"
        publishUrl="deployaspdotnetcore.scm.azurewebsites.net:443"
        msdeploySite="DeployASPDotNetCore"
        userName="$DeployASPDotNetCore"
        userPWD="abcdefghijklmnopqrstuzwxyz"
        destinationAppUrl="http://deployaspdotnetcore20180508031824.azurewebsites.net"
        SQLServerDBConnectionString=""
        mySQLDBConnectionString=""
        hostingProviderForumLink=""
        controlPanelLink="http://windows.azure.com"
        webSystem="WebSites">
        <databases />
      </publishProfile>
    </publishData>
    ```
    Zwykle poprzedniego pliku *.publishsettings zawiera dwa profile publikowania, których można używać w programie Visual Studio do wdrażania za pomocą narzędzia Web Deploy, a drugi do wdrożenia za pomocą protokołu FTP. Poprzedni kod Pokazuje profil narzędzia Web Deploy. Oba profile zostaną później zaimportowane podczas importowania profilu.

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importowanie ustawień publikowania w programie Visual Studio i wdrażanie

1. Na komputerze, na którym znajduje się projekt ASP.NET jest otwarty w programie Visual Studio, kliknij prawym przyciskiem myszy projekt w Eksploratorze rozwiązań i wybierz polecenie **publikowania**.

1. Jeśli wcześniej skonfigurowano żadnych profilów publikowania, **publikowania** pojawi się okienko. Kliknij przycisk **Utwórz nowy profil**.

1. W **wybierz element docelowy publikowania** okno dialogowe, kliknij przycisk **Importuj profil**.

    ![Wybierz publikowania](../deployment/media/tutorial-publish-tool-import-profile.png)

1. Przejdź do lokalizacji pliku ustawień publikowania, który został utworzony w poprzedniej sekcji.

1. W **pliku ustawień publikowania importu** okno dialogowe, wybierz profil, który został utworzony w poprzedniej sekcji, a następnie kliknij przycisk **Otwórz**.

1. Wybierz jedną z dwóch profilów zaimportowane, a następnie kliknij przycisk **publikowania**.

    Visual Studio rozpoczyna proces wdrażania oraz w oknie danych wyjściowych przedstawia postęp i wyniki.

## <a name="next-steps"></a>Następne kroki

W tym samouczku utworzony plik ustawień publikowania, zaimportowany do programu Visual Studio i wdrożeniu aplikacji ASP.NET w usłudze Azure App Service.

> [!div class="nextstepaction"]
> [Pierwsze spojrzenie na wdrażanie](../deployment/deploying-applications-services-and-components.md)
