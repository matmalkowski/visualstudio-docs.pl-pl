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
ms.openlocfilehash: e6df935578955d3c72b6f4fa61efdf614229bca0
ms.sourcegitcommit: 4667e6ad223642bc4ac525f57281482c9894daf4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/20/2018
ms.locfileid: "36282164"
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

Plik ustawień publikowania (*\*.publishsettings*) różni się od profilu publikowania (*\*.pubxml*) utworzone w programie Visual Studio. Plik ustawień publikowania jest tworzony przez usługi IIS lub usłudze Azure App Service, lub można utworzyć ręcznie, a następnie go zaimportować do programu Visual Studio.

> [!NOTE]
> Jeśli jest potrzebna do skopiowania Visual Studio profilu publikowania (\*pliku .pubxml) z jednej instalacji programu Visual Studio do innego, można znaleźć profilu publikowania  *\<profilename\>.pubxml*, w  *\\< projectname\>\Properties\PublishProfiles* folderu dla typów projektów zarządzanych. Dla witryn sieci Web, sprawdź w obszarze *\App_Data* folderu. Profile publikowania są plikami XML programu MSBuild.

## <a name="prerequisites"></a>Wymagania wstępne

* Musi mieć Visual Studio 2017 r zainstalowany i **ASP.NET** i **.NET Framework** programowanie obciążenia. W przypadku aplikacji .NET Core należy również **.NET Core** obciążenia.

    Jeśli nie został już zainstalowany program Visual Studio, przejdź do [program Visual Studio pobiera](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) stronę, aby zainstalować ją bezpłatnie.

* Aby wygenerować plik ustawień publikowania za pomocą programu IIS, musi mieć komputer z systemem Windows Server 2012 lub Windows Server 2016, a musi mieć rolę serwera sieci Web usług IIS, poprawnie skonfigurowany. Należy także zainstalować funkcję ASP.NET 4.5 lub platformy ASP.NET Core. Dla platformy ASP.NET Core, zobacz [publikowania w usługach IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration). Dla platformy ASP.NET 4.5, zobacz [IIS 8.0 przy użyciu programu ASP.NET 3.5 i ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Utwórz nowy projekt ASP.NET w programie Visual Studio

1. Na komputerze, działanie programu Visual Studio, wybierz **pliku** > **nowy projekt**.

1. W obszarze **Visual C#** lub **Visual Basic**, wybierz **sieci Web**, a następnie w środkowym okienku wybierz albo **aplikacji sieci Web platformy ASP.NET (.NET Framework)** lub (C# tylko) **aplikacji sieci Web platformy ASP.NET Core**, a następnie kliknij przycisk **OK**.

    Jeśli szablony określony projekt nie jest widoczny, kliknij przycisk **Otwórz Instalator programu Visual Studio** łącze w lewym okienku **nowy projekt** okno dialogowe. Uruchamia Instalator programu Visual Studio. Zobacz wymagania wstępne w tym artykule, aby zidentyfikować wymagane obciążenia programu Visual Studio, które trzeba zainstalować.

1. Wybierz **MVC** (.NET Framework) lub **aplikacji sieci Web (Model-View-Controller)** (dla platformy .NET Core) i upewnij się, że **bez uwierzytelniania** jest zaznaczone, a następnie kliknij przycisk **OK**.

1. Wpisz nazwę, takich jak **MyWebApp** i kliknij przycisk **OK**.

    Program Visual Studio tworzy projekt.

1. Wybierz **kompilacji** > **Kompiluj rozwiązanie** Aby skompilować projekt.

## <a name="install-and-configure-web-deploy-on-windows-server"></a>Instalowanie i Konfigurowanie narzędzia Web Deploy w systemie Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

## <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Utwórz plik ustawień publikowania w usługach IIS w systemie Windows Server

[!INCLUDE [create-publish-settings-iis](../deployment/includes/create-publish-settings-iis.md)]

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importowanie ustawień publikowania w programie Visual Studio i wdrażanie

[!INCLUDE [import-publish-settings](../deployment/includes/import-publish-settings-vs.md)]

Po aplikacji wdraża się pomyślnie, należy uruchomić automatycznie. Jeśli nie zostanie uruchomiony z programu Visual Studio, uruchomić aplikację w usługach IIS. Dla platformy ASP.NET Core, należy się upewnić, że pula aplikacji pól dla **DefaultAppPool** ustawiono **bez kodu zarządzanego**.

## <a name="next-steps"></a>Następne kroki

W tym samouczku utworzony plik ustawień publikowania, zaimportowany do programu Visual Studio i wdrożeniu aplikacji ASP.NET w usługach IIS. Możesz omówienie inne opcje publikowania w programie Visual Studio.

> [!div class="nextstepaction"]
> [Pierwsze spojrzenie na wdrażanie](../deployment/deploying-applications-services-and-components.md)
