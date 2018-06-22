---
title: Publikowanie na platformie Azure przez zaimportowanie ustawień publikowania
ms.description: Create and import a publishing profile to deploy an application from Visual Studio to Azure App Service
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
ms.openlocfilehash: 2b4b0e4ea963f20199267f32a8c87440c8cc350b
ms.sourcegitcommit: 4667e6ad223642bc4ac525f57281482c9894daf4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/20/2018
ms.locfileid: "36283165"
---
# <a name="publish-an-application-to-azure-app-service-by-importing-publish-settings-in-visual-studio"></a>Publikowanie aplikacji w usłudze Azure App Service przez zaimportowanie ustawień publikowania w programie Visual Studio

Można użyć **publikowania** narzędzia do zaimportowania ustawień publikowania, a następnie wdrożyć aplikację. W tym artykule używamy ustawienia publikowania dla usługi aplikacji Azure, ale można użyć publikowania podobne kroki, aby zaimportować ustawienia z [IIS](../deployment/tutorial-import-publish-settings-iis.md). W niektórych scenariuszach stosowania Publikowanie profilu ustawień może być szybsza niż ręcznie konfigurować wdrożenia usługi dla każdej instalacji programu Visual Studio.

Te kroki dotyczą aplikacji ASP.NET, platformy ASP.NET Core i .NET Core w programie Visual Studio. Możesz również zaimportować ustawienia publikowania dla [Python](../python/publishing-python-web-applications-to-azure-from-visual-studio.md) aplikacji. Visual Studio 2017 wersji 15,6 odpowiada kroki.

W tym samouczku obejmują:

> [!div class="checklist"]
> * Generuj plik ustawień publikowania w usłudze Azure App Service
> * Zaimportuj plik ustawień publikowania do programu Visual Studio
> * Wdrażanie aplikacji w usłudze Azure App Service

Plik ustawień publikowania (*\*.publishsettings*) różni się od profilu publikowania (*\*.pubxml*) utworzone w programie Visual Studio. Plik ustawień publikowania jest tworzony przez usługę Azure App Service, a następnie go zaimportować do programu Visual Studio.

> [!NOTE]
> Jeśli jest potrzebna do skopiowania Visual Studio profilu publikowania (*\*.pubxml* plik) z jednej instalacji programu Visual Studio do innego, można znaleźć profilu publikowania  *\<profilename\>.pubxml*w  *\\< projectname\>\Properties\PublishProfiles* folderu dla typów projektów zarządzanych. Dla witryn sieci Web, sprawdź w obszarze *\App_Data* folderu. Profile publikowania są plikami XML programu MSBuild.

## <a name="prerequisites"></a>Wymagania wstępne

* Musi mieć Visual Studio 2017 r zainstalowany i **ASP.NET** i. **NET Framework** programowanie obciążenia. W przypadku aplikacji .NET Core może też być konieczne. **NET Core** obciążenia.

    Jeśli nie został już zainstalowany program Visual Studio, przejdź do [program Visual Studio pobiera](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) stronę, aby zainstalować ją bezpłatnie.

* Tworzenie usługi aplikacji Azure. Aby uzyskać szczegółowe instrukcje, zobacz [wdrażanie aplikacji sieci web platformy ASP.NET Core na platformie Azure przy użyciu programu Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs).

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Utwórz nowy projekt ASP.NET w programie Visual Studio

1. Na komputerze, działanie programu Visual Studio, wybierz **pliku** > **nowy projekt**.

1. W obszarze **Visual C#** lub **Visual Basic**, wybierz **sieci Web**, a następnie w środkowym okienku wybierz albo **aplikacji sieci Web platformy ASP.NET (.NET Framework)** lub (C# tylko) **aplikacji sieci Web platformy ASP.NET Core**, a następnie kliknij przycisk **OK**.

    Jeśli szablony określony projekt nie jest widoczny, kliknij przycisk **Otwórz Instalator programu Visual Studio** łącze w lewym okienku **nowy projekt** okno dialogowe. Uruchamia Instalator programu Visual Studio. Zobacz wymagania wstępne w tym artykule, aby zidentyfikować wymagane obciążenia programu Visual Studio, które trzeba zainstalować.

1. Wybierz **MVC** (.NET Framework) lub **aplikacji sieci Web (Model-View-Controller)** (dla platformy .NET Core) i upewnij się, że **bez uwierzytelniania** jest zaznaczone, a następnie kliknij przycisk **OK**.

1. Wpisz nazwę, takich jak **MyWebApp** i kliknij przycisk **OK**.

    Program Visual Studio tworzy projekt.

1. Wybierz **kompilacji** > **Kompiluj rozwiązanie** Aby skompilować projekt.

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

[!INCLUDE [import publish settings](../deployment/includes/import-publish-settings-vs.md)]

## <a name="next-steps"></a>Następne kroki

W tym samouczku utworzony plik ustawień publikowania, zaimportowany do programu Visual Studio i wdrożeniu aplikacji ASP.NET w usłudze Azure App Service. Możesz Omówienie opcji publikowania w programie Visual Studio.

> [!div class="nextstepaction"]
> [Pierwsze spojrzenie na wdrażanie](../deployment/deploying-applications-services-and-components.md)
