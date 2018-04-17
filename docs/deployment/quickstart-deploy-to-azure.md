---
title: Publikowanie w usłudze Azure App Service — Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/22/2017
ms.technology:
- vs-ide-deployment
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
ms.assetid: fc82b1f1-d342-4b82-9a44-590479f0a895
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- azure
ms.openlocfilehash: d6de76a3f3bd781ec8cd798eef87cce7acd01e69
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="publish-an-aspnet-or-aspnet-core-app-to-azure-app-service-using-visual-studio"></a>Publikowanie aplikacji ASP.NET lub ASP.NET Core dla usługi Azure App Service przy użyciu programu Visual Studio

Można użyć **publikowania** narzędzia do publikowania aplikacji platformy ASP.NET, platformy ASP.NET Core, Python, Node.js i .NET Core w usłudze Azure App Service.

Jeśli nie masz już konto platformy Azure, możesz [zarejestrować się tutaj](https://azure.microsoft.com/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=doc&utm_campaign=visualstudio).

## <a name="create-a-new-project"></a>Tworzenie nowego projektu 

1. W programie Visual Studio, wybierz **Plik > Nowy projekt**.

1. W obszarze **Visual C#** lub **Visual Basic**, wybierz **sieci Web**, a następnie w środkowym okienku wybierz albo **aplikacji sieci Web platformy ASP.NET (.NET Framework)**lub (C# tylko) **aplikacji sieci Web platformy ASP.NET Core**, a następnie kliknij przycisk **OK**.

1. Wybierz **MVC**, upewnij się, że **bez uwierzytelniania** jest zaznaczone, a następnie kliknij przycisk **OK**.

1. Wpisz nazwę, takich jak **MyWebApp** i kliknij przycisk **OK**.

    Program Visual Studio tworzy projekt.

1. Wybierz **kompilacji > Kompiluj rozwiązanie** Aby skompilować projekt.

## <a name="publish-to-azure-app-service"></a>Publikowanie w usłudze Azure App Service

1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **publikowania**.

    ![Wybierz publikowania](../deployment/media/quickstart-publish-aspnet.png "wybierz publikowania")

1. W **publikowania** okienku wybierz **Microsoft Azure App Service**.

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

- [Wdrażanie aplikacji platformy ASP.NET Core w systemie Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs)
- [Ciągłe wdrażanie platformy ASP.NET Core na platformie Azure za pomocą usługi Git](/aspnet/core/publishing/azure-continuous-deployment)
