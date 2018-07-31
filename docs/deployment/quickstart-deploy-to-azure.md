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
ms.openlocfilehash: a8de7175b33a91c310da4b3d6d9e4c05c40c3522
ms.sourcegitcommit: 4f82c178b1ac585dcf13b515cc2a9cb547d5f949
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2018
ms.locfileid: "39341693"
---
# <a name="publish-a-web-app-to-azure-app-service-using-visual-studio"></a>Publikowanie aplikacji sieci Web w usłudze Azure App Service przy użyciu programu Visual Studio

Możesz użyć **Publikuj** narzędzie do publikowania aplikacji platformy ASP.NET, ASP.NET Core, Node.js i platformy .NET Core do usługi Azure App Service lub Azure App Service dla systemu Linux (przy użyciu kontenerów). Dla aplikacji w języku Python, postępuj zgodnie z instrukcjami [językiem Python — publikowanie w usłudze Azure App Service](../python/publishing-python-web-applications-to-azure-from-visual-studio.md).

[!INCLUDE [quickstart-prereqs-azure](includes/quickstart-prereqs-azure.md)]

## <a name="publish-to-azure-app-service"></a>Publikowanie w usłudze Azure App Service

1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Publikuj** (lub użyj **kompilacji** > **Publikuj** element menu).

    ![Polecenia Opublikuj w menu kontekstowym projektu w Eksploratorze rozwiązań](../deployment/media/quickstart-publish.png "wybierz polecenie Publikuj")

1. Jeśli wcześniej skonfigurowano żadnych profilów publikowania **Publikuj** zostanie wyświetlone okienko, w których wielkość wybranych **Utwórz nowy profil**.

1. W **wybierz lokalizację docelową publikowania** okna dialogowego wybierz **usługi App Service**.

    ![Usługa Azure App Service wybierz](../deployment/media/quickstart-publish-azure.png "wybierz usługi Azure App Service")

1. Wybierz **publikowania**. **Tworzenie usługi App Service** pojawi się okno dialogowe. Zaloguj się przy użyciu konta platformy Azure możesz, jeśli to konieczne, a następnie domyślnych ustawień usługi app Wypełnij pola.

    ![Utwórz usługę App Service](../deployment/media/quickstart-publish-settings-app-service.png "Tworzenie usługi Azure App Service")

1. Wybierz **tworzenie**. Program Visual Studio wdroży aplikację do usługi Azure App Service i ładowania aplikacji sieci web w przeglądarce. Właściwości projektu **Publikuj** okienko zawiera adres URL witryny oraz inne szczegóły.

    ![Okienko właściwości wyświetlanie podsumowania profil publikowania](../deployment/media/quickstart-publish-app-service-summary.png)

## <a name="clean-up-resources"></a>Oczyszczanie zasobów

W poprzednich krokach utworzono zasoby platformy Azure w grupie zasobów. Jeśli nie będziesz już potrzebować tych zasobów w przyszłości, możesz je usunąć przez usunięcie grupy zasobów.
Wybierz z menu po lewej stronie w witrynie Azure portal, **grup zasobów** , a następnie wybierz **myResourceGroup**.
Na stronie grupy zasobów upewnij się, że zasoby na liście są tymi, które chcesz usunąć.
Wybierz **Usuń**, typ **myResourceGroup** w polu tekstowym, a następnie wybierz pozycję **Usuń**.

## <a name="next-steps"></a>Następne kroki

W tym przewodniku Szybki Start przedstawiono sposób tworzenia profilu publikowania do wdrożenia na platformie Azure przy użyciu programu Visual Studio. Można również skonfigurować publikowanie profilu, importując opublikowania ustawień usługi Azure App Service.

> [!div class="nextstepaction"]
> [Importowanie ustawień publikowania i wdrażanie na platformie Azure](tutorial-import-publish-settings-azure.md)
