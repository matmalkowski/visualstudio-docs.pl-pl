---
title: Publikowanie w usłudze Azure App Service
ms.custom: ''
ms.date: 06/22/2018
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
ms.openlocfilehash: 3d15cc293f2b2b22b63e0af202bfcee8afa2cf13
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36755999"
---
# <a name="publish-a-web-app-to-azure-app-service-using-visual-studio"></a>Publikowanie aplikacji sieci web w usłudze Azure App Service przy użyciu programu Visual Studio

Można użyć **publikowania** narzędzia do publikowania aplikacji platformy ASP.NET, platformy ASP.NET Core, Node.js i .NET Core usłudze Azure App Service lub Linux usługi aplikacji Azure (przy użyciu kontenery). W przypadku aplikacji Python, wykonaj kroki opisane [Python - publikowania w usłudze Azure App Service](../python/publishing-python-web-applications-to-azure-from-visual-studio.md).

[!INCLUDE [quickstart-prereqs-azure](includes/quickstart-prereqs-azure.md)]

## <a name="publish-to-azure-app-service"></a>Publikowanie w usłudze Azure App Service

1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **publikowania** (lub użyj **kompilacji** > **publikowania** elementu menu).

    ![Polecenia Opublikuj w menu kontekstowym projekt w Eksploratorze rozwiązań](../deployment/media/quickstart-publish.png "wybierz publikowania")

1. Jeśli wcześniej skonfigurowano żadnych profilów publikowania, **publikowania** zostanie wyświetlone okienko, w których przypadku wybierz **Utwórz nowy profil**.

1. W **wybierz element docelowy publikowania** oknie dialogowym wybierz **usługi aplikacji**.

    ![Wybierz usługi aplikacji Azure](../deployment/media/quickstart-publish-azure.png "wybierz usługi aplikacji Azure")

1. Wybierz **publikowania**. **Tworzenie usługi App Service** zostanie wyświetlone okno dialogowe. Zaloguj się przy użyciu konta platformy Azure możesz, jeśli to konieczne, a następnie ustawienia domyślne aplikacji usługi należy wypełnić pola.

    ![Tworzenie aplikacji usługi](../deployment/media/quickstart-publish-settings-app-service.png "Tworzenie usługi aplikacji Azure")

1. Wybierz **utworzyć**. Visual Studio aplikacja jest wdrażana na usłudze Azure App Service i ładuje aplikacji sieci web w przeglądarce. Właściwości projektu **publikowania** w okienku zostaną wyświetlone adres URL witryny i inne szczegóły.

    ![Publikowanie właściwości okienko profil podsumowania](../deployment/media/quickstart-publish-app-service-summary.png)

## <a name="next-steps"></a>Następne kroki

W tym szybkiego startu wiesz, jak utworzyć profil publikowania do wdrożenia na platformie Azure za pomocą programu Visual Studio. Można również skonfigurować publikowanie Importowanie profilu publikowania ustawień z usługi aplikacji Azure.

> [!div class="nextstepaction"]
> [Importowanie ustawień publikowania i wdrażanie na platformie Azure](tutorial-import-publish-settings-azure.md)
