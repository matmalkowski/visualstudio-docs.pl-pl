---
title: Przegląd funkcji wdrażania
description: Więcej informacji na temat opcji dotyczących wdrażania aplikacji w programie Visual Studio.
ms.custom: mvc
ms.date: 11/26/2017
ms.technology: vs-ide-deployment
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8d2c84b8e5d37876d890d40144b281e236fdcd0c
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2018
ms.locfileid: "34766314"
---
# <a name="quickstart-first-look-at-deployment-in-visual-studio"></a>Szybki Start: Pierwsze spojrzenie na wdrożenie w programie Visual Studio

Wdrażanie aplikacji, usług i składników to rozpowszechnianie ich w celu instalacji na innych komputerach, urządzeniach, serwerach lub w chmurze. W programie Visual Studio możesz wybrać odpowiednią metodę w zależności od typu wdrożenia, jakiego potrzebujesz. (Inne narzędzia wdrażania takich jak wdrożenia wiersza polecenia lub NuGet, które nie zostały opisane w tym miejscu obsługuje wiele typów aplikacji.)

Zobacz samouczki, aby uzyskać instrukcje krok po kroku wdrażania. Jeśli wdrażana aplikacja sieci web i uzyskać bardziej szczegółowe informacje do podejmowania decyzji o najlepszej opcji wdrażania z programu Visual Studio, zobacz [jakie opcje publikowania jest dla mnie odpowiednia?](../ide/not-in-toc/web-publish-options.md).

## <a name="deploy-to-local-folder"></a>Wdrażanie na folder lokalny

Wdrożenia na folder lokalny jest zwykle używane do testowania lub rozpocząć wdrożenia etapowego, w którym innego narzędzia będzie służyć do końcowego wdrożenia.

- **ASP.NET**, **platformy ASP.NET Core**, **Node.js**, **Python**, i. **Podstawowe NET**: Użyj narzędzia do publikowania do wdrożenia na folder lokalny. Dostępne opcje zależą od typu aplikacji. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **publikowania**. (Jeśli wcześniej skonfigurowano żadnych profilów publikowania, należy kliknąć **Utwórz nowy profil**.) Następnie wybierz **folderu**. Aby uzyskać więcej informacji, zobacz [wdrażanie na folder lokalny](quickstart-deploy-to-local-folder.md).

    ![Wybierz publikowania](../deployment/media/quickstart-publish.png)

- **Środowiska uruchomieniowego Visual C++**: można wdrożyć środowiska uruchomieniowego Visual C++ przy użyciu lokalnego wdrożenia lub statycznego łączenia. Aby uzyskać więcej informacji, zobacz [wdrażanie natywnych pulpitu aplikacji (Visual C++)](/cpp/ide/deploying-native-desktop-applications-visual-cpp). 

## <a name="azure"></a> Publikowanie na platformie Azure

- **ASP.NET**, **platformy ASP.NET Core**, **Python**, i **Node.js**: narzędzie publikowania umożliwia szybkie wdrażanie aplikacji w usłudze Azure App Service lub wirtualnych Azure Maszyny. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **publikowania**. (Jeśli wcześniej skonfigurowano żadnych profilów publikowania, należy kliknąć **Utwórz nowy profil**.) W oknie dialogowym Publikowanie wybierz **usługi aplikacji** lub **maszyny wirtualne Azure**, a następnie wykonaj kroki konfiguracji.

    ![Wybierz usługi aplikacji Azure](../deployment/media/quickstart-publish-azure.png "wybierz usługi aplikacji Azure")

    W programie Visual Studio 2017 wersji 15.7, można wdrażać aplikacje platformy ASP.NET Core do **usługi aplikacji dla systemu Linux**.

    Aby uzyskać informacje na temat importowania profilu publikowania w usłudze Azure App Service dla programu Visual Studio, zobacz [importowanie ustawień publikowania i wdrażanie na platformie Azure](../deployment/tutorial-import-publish-settings-azure.md).

    Szybkie wprowadzenie, zobacz [publikowania na platformie Azure](quickstart-deploy-to-azure.md). Zobacz też [publikowanie aplikacji platformy ASP.NET Core Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). Dla wdrożenia przy użyciu narzędzia Git, zobacz [ciągłego wdrażania platformy ASP.NET Core na platformie Azure za pomocą narzędzia Git](/aspnet/core/publishing/azure-continuous-deployment).

    > [!NOTE]
    > Jeśli nie masz już konto platformy Azure, możesz [zarejestrować się tutaj](https://azure.microsoft.com/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=doc&utm_campaign=visualstudio).

## <a name="web"></a> Publikowanie w sieci Web lub wdrożyć do udziału sieciowego

- **ASP.NET**, **platformy ASP.NET Core**, **Node.js**, i **Python**: narzędzie publikowania do wdrożenia witryny sieci Web przy użyciu protokołu FTP lub narzędzie Web Deploy. Aby uzyskać więcej informacji, zobacz [Wdróż do witryny sieci web](quickstart-deploy-to-a-web-site.md).

    W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **publikowania**. (Jeśli wcześniej skonfigurowano żadnych profilów publikowania, należy kliknąć **Utwórz nowy profil**.) W narzędziu do publikowania wybierz opcję mają i wykonaj kroki konfiguracji.

    ![Choose IIS, FTP, etc.](../deployment/media/quickstart-publish-iis-ftp.png)

    Aby uzyskać informacje na temat importowania profilu publikowania w programie Visual Studio, zobacz [importowanie ustawień publikowania i wdrażanie usług IIS](../deployment/tutorial-import-publish-settings-iis.md).

    Można także wdrożyć aplikacje ASP.NET i usługi na kilka różnych sposobów. Aby uzyskać więcej informacji, zobacz [usług i aplikacji sieci web ASP.NET wdrażanie](http://www.asp.net/aspnet/overview/deployment).

- **Środowiska uruchomieniowego Visual C++**: można wdrożyć środowisko uruchomieniowe Visual C++ przy użyciu centralnej wdrożenia. Aby uzyskać więcej informacji, zobacz [wdrażanie natywnych pulpitu aplikacji (Visual C++)](/cpp/ide/deploying-native-desktop-applications-visual-cpp). 

- **System Windows desktop** opublikowaniem aplikacji pulpitu systemu Windows na serwerze sieci web lub sieciowego udziału plików przy użyciu wdrażania ClickOnce. Użytkownicy mogą następnie zainstalować aplikację za pomocą jednego kliknięcia. Aby uzyskać więcej informacji, zobacz [wdrażanie aplikacji komputerowej za pomocą aplikacji ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) i [wdrażanie natywnych aplikacji za pomocą aplikacji ClickOnce](/cpp/ide/clickonce-deployment-for-visual-cpp-applications).

## <a name="microsoft_store"></a> Publikowanie w sklepie Microsoft

W programie Visual Studio można utworzyć pakiety aplikacji do wdrożenia na Microsoft Store.

- **Platformy uniwersalnej systemu Windows**: można Tworzenie pakietu dla aplikacji i wdróż je za pomocą elementów menu. Aby uzyskać więcej informacji, zobacz [pakietu dla aplikacji platformy uniwersalnej systemu Windows za pomocą programu Visual Studio](/windows/uwp/packaging/packaging-uwp-apps).

    ![Tworzenie pakietu aplikacji](../deployment/media/feature-tour-create-app-package.jpg)

- **System Windows desktop**: Microsoft Store przy użyciu mostu pulpitu w programie Visual Studio 2017 wersji 15.4 można wdrożyć. Aby to zrobić, Rozpocznij od utworzenia projektu tworzenia pakietów aplikacji systemu Windows. Aby uzyskać więcej informacji, zobacz [pakietu aplikacji komputerowej Microsoft Store (mostek pulpitu)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net).

    ![Mostek pulpitu](../deployment/media/feature-tour-desktop-bridge.png)

## <a name="deploy-to-a-device-uwp"></a>Wdrożenia na urządzeniu (UWP)

Jeśli wdrażasz aplikacji platformy uniwersalnej systemu Windows, do testowania na urządzeniu, zobacz [aplikacji platformy uniwersalnej systemu Windows uruchom na komputerze zdalnym w programie Visual Studio](../debugger/run-windows-store-apps-on-a-remote-machine.md).

## <a name="installer"></a> Utwórz pakiet Instalatora (klient z systemem Windows)

Jeśli wymagane bardziej złożonych instalacji aplikacji pulpitu niż [ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) zapewniają można utworzyć pakietu, instalacja projektu lub niestandardowego programu inicjującego.

- Instalator MSI na podstawie WiX mogą być tworzone przy użyciu [WiX zestaw narzędzi Visual Studio 2017 rozszerzenia](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).

- [InstallShield](https://www.flexerasoftware.com/producer/products/software-installation/installshield-software-installer/tab/requirements) Flexera oprogramowania może być używana z programu Visual Studio 2017 (Community Edition nie jest obsługiwane). Należy pamiętać, że InstallShield Limited Edition nie jest już dołączony do programu Visual Studio i nie jest obsługiwane w programie Visual Studio 2017; Skontaktuj się z [oprogramowania Flexera](http://learn.flexerasoftware.com/content/IS-EVAL-InstallShield-Limited-Edition-Visual-Studio) o dostępności w przyszłości.

- Jeśli chcesz utworzyć projekt Instalatora (vdproj), zainstaluj [rozszerzenia programu Visual Studio 2017 Instalator projekty](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.MicrosoftVisualStudio2017InstallerProjects#overview).

- Konfigurując ogólnego Instalatora nosi nazwę programu inicjującego, należy zainstalować wstępnie wymagane składniki aplikacji klasycznych. Aby uzyskać więcej informacji, zobacz [wymagania wstępne dotyczące wdrażania aplikacji](../deployment/application-deployment-prerequisites.md).

## <a name="deploy-to-test-lab"></a>Wdrażanie w laboratorium testowego

Można włączyć bardziej złożone projektowania i testowania przez wdrożenie aplikacji w środowiskach wirtualnych. Aby uzyskać więcej informacji, zobacz [testów w środowisku laboratoryjnym](../test/lab-management/using-a-lab-environment-for-your-application-lifecycle.md).

## <a name="devops-deployment"></a>Wdrożenie opracowywania oprogramowania

W środowisku zespołu można używać programu Visual Studio Team Services (VSTS) umożliwiające ciągłego wdrażania aplikacji. Aby uzyskać więcej informacji, zobacz [kompilacji i wydania](/vsts/build-release/index) i [wdrażanie na platformie Azure](/vsts/deploy-azure/index).

## <a name="deployment-for-other-app-types"></a>Wdrożenia dla innych typów aplikacji

| Typ aplikacji | Scenariusz wdrażania | Łącze |
| --- | --- | --- |
| **Aplikacja pakietu Office** | Możesz opublikować dodatek dla pakietu Office w Visual Studio. | [Wdrażanie oraz publikowanie dodatek pakietu Office](https://dev.office.com/docs/add-ins/publish/publish) |
| **Usługi WCF lub OData**  | Inne aplikacje mogą używać usług WCF RIA, które są wdrażane na serwerze sieci web. | [Tworzenie i wdrażanie usług danych WCF](/dotnet/framework/data/wcf/developing-and-deploying-wcf-data-services) |
| **LightSwitch** | LightSwitch nie jest już obsługiwana w programie Visual Studio 2017, ale nadal można wdrożyć z programu Visual Studio 2015 i starszych wersji. | [Wdrażanie aplikacji LightSwitch](http://msdn.microsoft.com/Library/4818d933-295c-4ecc-9148-7ad9ca28dcdb) | 

## <a name="next-steps"></a>Następne kroki

W tym samouczku wykonane krótki przegląd opcje wdrażania dla różnych aplikacji. Jeśli wdrażana jest aplikacja sieci web, takich jak ASP.NET, przeczytaj więcej informacji na temat o niektórych opcji wdrażania dostępnych w programie Visual Studio.

> [!div class="nextstepaction"]
> [Jakie opcje publikowania jest dla mnie odpowiednia?](../ide/not-in-toc/web-publish-options.md)

