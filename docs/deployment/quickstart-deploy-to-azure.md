---
title: Publikowanie w usłudze Azure App Service — Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/22/2017
ms.technology: vs-ide-deployment
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
ms.assetid: fc82b1f1-d342-4b82-9a44-590479f0a895
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- azure
ms.openlocfilehash: f28de642d6a1f4f9071099593f990c6197ed34ec
ms.sourcegitcommit: f685fa5e2df9dc307bf1230dd9dc3288aaa408b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2018
ms.locfileid: "36234754"
---
# <a name="publish-an-aspnet-or-aspnet-core-app-to-azure-app-service-using-visual-studio"></a>Publikowanie aplikacji ASP.NET lub ASP.NET Core dla usługi Azure App Service przy użyciu programu Visual Studio

Można użyć **publikowania** narzędzia do publikowania aplikacji platformy ASP.NET, platformy ASP.NET Core, Python, Node.js i .NET Core w usłudze Azure App Service.

Jeśli nie masz już konto platformy Azure, możesz [zarejestrować się tutaj](https://azure.microsoft.com/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=doc&utm_campaign=visualstudio).

## <a name="prerequisites"></a>Wymagania wstępne

* Musi mieć Visual Studio 2017 r zainstalowany i **ASP.NET i sieć web development** obciążenia i. **NET development pulpitu** obciążenia. W przypadku aplikacji .NET Core należy. **NET Core** obciążenia.

    Jeśli nie został już zainstalowany program Visual Studio, przejdź do [program Visual Studio pobiera](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) stronę, aby zainstalować ją bezpłatnie.

## <a name="create-a-new-project"></a>Tworzenie nowego projektu 

1. W programie Visual Studio, wybierz **pliku** > **nowy projekt**.

1. W obszarze **Visual C#** lub **Visual Basic**, wybierz **sieci Web**, a następnie w środkowym okienku wybierz albo **aplikacji sieci Web platformy ASP.NET (.NET Framework)** lub (C# tylko) **aplikacji sieci Web platformy ASP.NET Core**, a następnie kliknij przycisk **OK**.

1. Wybierz **MVC** (lub wybierz **aplikacji sieci Web (Model-View-Controller)** dla platformy .NET Core), upewnij się, że **bez uwierzytelniania** jest zaznaczone, a następnie kliknij przycisk **OK** .

1. Wpisz nazwę, takich jak **MyWebApp** i kliknij przycisk **OK**.

    Program Visual Studio tworzy projekt.

1. Wybierz **kompilacji** > **Kompiluj rozwiązanie** Aby skompilować projekt.

## <a name="publish-to-azure-app-service"></a>Publikowanie w usłudze Azure App Service

1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **publikowania**.

    ![Wybierz publikowania](../deployment/media/quickstart-publish-aspnet.png "wybierz publikowania")

1. Jeśli wcześniej skonfigurowano żadnych profilów publikowania, **publikowania** pojawi się okienko. Kliknij przycisk **Utwórz nowy profil**.

1. W **wybierz element docelowy publikowania** oknie dialogowym wybierz **usługi aplikacji**.

    ![Wybierz usługi aplikacji Azure](../deployment/media/quickstart-publish-azure.png "wybierz usługi aplikacji Azure")

1. Kliknij przycisk **publikowania**.

    **Tworzenie usługi App Service** zostanie wyświetlone okno dialogowe.

    ![Tworzenie aplikacji usługi](../deployment/media/quickstart-publish-settings-app-service.png "Tworzenie usługi aplikacji Azure")
    
1. Jeśli użytkownik nie jest zarejestrowany w programie Visual Studio, zaloguj się, a następnie wypełnij pola ustawień domyślnych aplikacji usługi.

    Profil publikowania ustawień, które zostanie otwarte okno dialogowe.

    ![Wybierz Folder](../deployment/media/quickstart-publish-settings-web.png "wybierz Folder")

    W tym oknie można Wybierz subskrypcję, której używasz, wybierz lub Utwórz grupę zasobów platformy Azure, itd.

1. Kliknij przycisk **Utwórz**.

    Visual Studio aplikacja jest wdrażana na usłudze Azure App Service i ładuje aplikacji sieci web w przeglądarce.

    W podsumowaniu z **publikowania** okienku zostanie wyświetlony adres URL witryny dla nowej usługi aplikacji Azure.

## <a name="next-steps"></a>Następne kroki

W tym szybkiego startu wiesz, jak utworzyć profil publikowania do wdrożenia na platformie Azure za pomocą programu Visual Studio. Można również skonfigurować publikowanie Importowanie profilu publikowania ustawień z usługi aplikacji Azure.

> [!div class="nextstepaction"]
> [Importowanie ustawień publikowania i wdrażanie na platformie Azure](tutorial-import-publish-settings-azure.md)
