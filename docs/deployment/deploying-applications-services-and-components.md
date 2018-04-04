---
title: Omówienie wdrażania — Visual Studio | Dokumentacja firmy Microsoft
description: Więcej informacji na temat opcji dotyczących wdrażania aplikacji w programie Visual Studio.
ms.custom: mvc
ms.date: 11/26/2017
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: quickstart
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- .NET applications, deploying
- components [Visual Studio], deploying
- installers
- publishing
- deploying applications [Visual Studio]
- deploying applications [Visual Studio], about deploying applications
- components [.NET Framework], deploying
ms.assetid: 63fcdd5b-2e54-4210-9038-65bc23167725
caps.latest.revision: 33
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: ca458c0234de89fec814cfa5e639c13db9e6ca9b
ms.sourcegitcommit: efd8c8e0a9ba515d47efcc7bd370eaaf4771b5bb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/03/2018
---
# <a name="quickstart-first-look-at-deployment-in-visual-studio"></a>Szybki Start: Pierwsze spojrzenie na wdrożenie w programie Visual Studio

Wdrażanie aplikacji, usług i składników to rozpowszechnianie ich w celu instalacji na innych komputerach, urządzeniach, serwerach lub w chmurze. W programie Visual Studio możesz wybrać odpowiednią metodę w zależności od typu wdrożenia, jakiego potrzebujesz. (Inne narzędzia wdrażania takich jak wdrożenia wiersza polecenia lub NuGet, które nie zostały opisane w tym miejscu obsługuje wiele typów aplikacji.)

Zobacz samouczki krok po kroku.

### <a name="deploy-to-local-folder"></a>Wdrażanie na folder lokalny

- **ASP.NET**, **platformy ASP.NET Core**, **Node.js**, **Python**, i **.NET Core**: Użyj narzędzia do publikowania do wdrożenia na folder lokalny. Dostępne opcje zależą od typu aplikacji. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **publikowania**, a następnie wybierz pozycję **folderu**. Aby uzyskać więcej informacji, zobacz [wdrażanie na folder lokalny](quickstart-deploy-to-local-folder.md).

    ![Wybierz publikowania](../deployment/media/quickstart-publish.png)

- **Środowiska uruchomieniowego Visual C++**: można wdrożyć środowiska uruchomieniowego Visual C++ przy użyciu lokalnego wdrożenia lub statycznego łączenia. Aby uzyskać więcej informacji, zobacz [wdrażanie natywnych pulpitu aplikacji (Visual C++)](/cpp/ide/deploying-native-desktop-applications-visual-cpp). 

### <a name="publish-to-web-or-deploy-to-network-share"></a>Publikowanie w sieci Web lub wdrożyć do udziału sieciowego

- **ASP.NET**, **platformy ASP.NET Core**, **Node.js**, **Python**, i **.NET Core**: narzędzie publikowania do wdrożenia Witryna sieci Web przy użyciu protokołu FTP lub narzędzie Web Deploy. Aby uzyskać więcej informacji, zobacz [Wdróż do witryny sieci web](quickstart-deploy-to-a-web-site.md).

    W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **publikowania**. W narzędziu do publikowania wybierz opcję mają i wykonaj kroki konfiguracji.

    ![Choose IIS, FTP, etc.](../deployment/media/quickstart-publish-iis-ftp.png)

    Można także wdrożyć aplikacje ASP.NET i usługi na kilka różnych sposobów. Aby uzyskać więcej informacji, zobacz [usług i aplikacji sieci web ASP.NET wdrażanie](http://www.asp.net/aspnet/overview/deployment).

- **Środowiska uruchomieniowego Visual C++**: można wdrożyć środowisko uruchomieniowe Visual C++ przy użyciu centralnej wdrożenia. Aby uzyskać więcej informacji, zobacz [wdrażanie natywnych pulpitu aplikacji (Visual C++)](/cpp/ide/deploying-native-desktop-applications-visual-cpp). 

- **System Windows desktop** opublikowaniem aplikacji pulpitu systemu Windows na serwerze sieci web lub sieciowego udziału plików przy użyciu wdrażania ClickOnce. Użytkownicy mogą następnie zainstalować aplikację za pomocą jednego kliknięcia. Aby uzyskać więcej informacji, zobacz [wdrażanie aplikacji komputerowej za pomocą aplikacji ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) i [wdrażanie natywnych aplikacji za pomocą aplikacji ClickOnce](/cpp/ide/clickonce-deployment-for-visual-cpp-applications).

### <a name="publish-to-azure"></a>Publikowanie na platformie Azure

- **ASP.NET, platformy ASP.NET Core, Python, Node.js i .NET Core** aplikacji sieci web: narzędzie publikowania umożliwia szybkie wdrażanie aplikacji w usłudze Azure App Service lub do maszyny wirtualnej platformy Azure. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **publikowania**. W oknie dialogowym Publikowanie wybierz **Microsoft Azure App Service** lub **maszyny wirtualne Microsoft Azure**, a następnie wykonaj kroki konfiguracji.

    ![Wybierz usługi aplikacji Azure](../deployment/media/quickstart-publish-azure.png "wybierz usługi aplikacji Azure")

    Aby opublikować do maszyny wirtualnej platformy Azure, przewiń w prawo, a następnie wybierz **maszyny wirtualne Microsoft Azure**.

    Szybkie wprowadzenie, zobacz [publikowania na platformie Azure](quickstart-deploy-to-azure.md). Zobacz też [publikowanie aplikacji platformy ASP.NET Core Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). Dla wdrożenia przy użyciu narzędzia Git, zobacz [ciągłego wdrażania platformy ASP.NET Core na platformie Azure za pomocą narzędzia Git](/aspnet/core/publishing/azure-continuous-deployment).

    > [!NOTE]
    > Jeśli nie masz już konto platformy Azure, możesz [zarejestrować się tutaj](https://azure.microsoft.com/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=doc&utm_campaign=visualstudio).

- Inne **usług Azure**: Zobacz konkretnym [usługi Azure](/azure/#pivot=products) dokumentacji dla różnych opcji wdrażania obsługiwane przez program Visual Studio.

### <a name="publish-to-microsoft-store"></a>Publikowanie w sklepie Microsoft

W programie Visual Studio można utworzyć pakiety aplikacji do wdrożenia na Microsoft Store.

- **Platformy uniwersalnej systemu Windows**: można Tworzenie pakietu dla aplikacji i wdróż je za pomocą elementów menu. Aby uzyskać więcej informacji, zobacz [pakietu dla aplikacji platformy uniwersalnej systemu Windows za pomocą programu Visual Studio](/windows/uwp/packaging/packaging-uwp-apps).

    ![Tworzenie pakietu aplikacji](../deployment/media/feature-tour-create-app-package.jpg)

- **System Windows desktop**: Microsoft Store przy użyciu mostu pulpitu w programie Visual Studio 2017 wersji 15.4 można wdrożyć. Aby to zrobić, Rozpocznij od utworzenia projektu tworzenia pakietów aplikacji systemu Windows. Aby uzyskać więcej informacji, zobacz [pakietu aplikacji komputerowej Microsoft Store (mostek pulpitu)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net).

    ![Mostek pulpitu](../deployment/media/feature-tour-desktop-bridge.png)

### <a name="create-an-installer-package-windows-client"></a>Utwórz pakiet Instalatora (klient z systemem Windows)

- Instalator MSI na podstawie WiX mogą być tworzone przy użyciu [WiX zestaw narzędzi Visual Studio 2017 rozszerzenia](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).

- [InstallShield](https://www.flexerasoftware.com/producer/products/software-installation/installshield-software-installer/tab/requirements) Flexera oprogramowania może być używana z programu Visual Studio 2017 (Community Edition nie jest obsługiwane). Należy pamiętać, że InstallShield Limited Edition nie jest już dołączony do programu Visual Studio i nie jest obsługiwane w programie Visual Studio 2017; Skontaktuj się z [oprogramowania Flexera](http://learn.flexerasoftware.com/content/IS-EVAL-InstallShield-Limited-Edition-Visual-Studio) o dostępności w przyszłości.

- Jeśli chcesz utworzyć projekt Instalatora (vdproj), zainstaluj [rozszerzenia programu Visual Studio 2017 Instalator projekty](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.MicrosoftVisualStudio2017InstallerProjects#overview).

- Konfigurując ogólnego Instalatora nosi nazwę programu inicjującego, należy zainstalować wstępnie wymagane składniki aplikacji klasycznych. Aby uzyskać więcej informacji, zobacz [wymagania wstępne dotyczące wdrażania aplikacji](../deployment/application-deployment-prerequisites.md).

### <a name="deploy-to-test-lab"></a>Wdrażanie w laboratorium testowego

Można włączyć bardziej złożone projektowania i testowania przez wdrożenie aplikacji w środowiskach wirtualnych. Aby uzyskać więcej informacji, zobacz [testów w środowisku laboratoryjnym](../test/lab-management/using-a-lab-environment-for-your-application-lifecycle.md).

### <a name="devops-deployment"></a>Wdrożenie opracowywania oprogramowania

W środowisku zespołu można używać programu Visual Studio Team Services (VSTS) umożliwiające ciągłego wdrażania aplikacji. Aby uzyskać więcej informacji, zobacz [kompilacji i wydania](/vsts/build-release/index) i [wdrażanie na platformie Azure](/vsts/deploy-azure/index).

### <a name="deployment-for-other-app-types"></a>Wdrożenia dla innych typów aplikacji

| Typ aplikacji | Scenariusz wdrażania | Łącze |
| --- | --- | --- |
| **Aplikacja pakietu Office** | Możesz opublikować dodatek dla pakietu Office w Visual Studio. | [Wdrażanie oraz publikowanie dodatek pakietu Office](https://dev.office.com/docs/add-ins/publish/publish) |
| **Usługi WCF lub OData**  | Inne aplikacje mogą używać usług WCF RIA, które są wdrażane na serwerze sieci web. | [Tworzenie i wdrażanie usług danych WCF](/dotnet/framework/data/wcf/developing-and-deploying-wcf-data-services) |
| **LightSwitch** | LightSwitch nie jest już obsługiwana w programie Visual Studio 2017, ale nadal można wdrożyć z programu Visual Studio 2015 i starszych wersji. | [Wdrażanie aplikacji LightSwitch](http://msdn.microsoft.com/Library/4818d933-295c-4ecc-9148-7ad9ca28dcdb) | 

