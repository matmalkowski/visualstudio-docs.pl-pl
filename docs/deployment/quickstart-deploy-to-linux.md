---
title: Publikowanie w usłudze App Service w systemie Linux
ms.custom: ''
ms.date: 07/23/2018
ms.technology: vs-ide-deployment
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- azure
ms.openlocfilehash: 9f79cef595b3a58426b596fc1019c59b801a02d5
ms.sourcegitcommit: 71b307ce86c4079cc7ad686d8d5f96a6a123aadd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/25/2018
ms.locfileid: "39252365"
---
# <a name="publish-an-aspnet-core-app-to-app-service-on-linux-using-visual-studio"></a>Publikowanie aplikacji platformy ASP.NET Core w usłudze App Service w systemie Linux przy użyciu programu Visual Studio

Możesz użyć **Publikuj** narzędzie do publikowania aplikacji platformy ASP.NET Core w usłudze Azure App Service w systemie Linux.

Wdrażanie w usłudze App Service w systemie Linux przy użyciu **Publikuj** narzędzie wymaga programu Visual Studio 2017 w wersji 15.7.

[!INCLUDE [quickstart-prereqs-azure-linux](includes/quickstart-prereqs-azure-linux.md)]

## <a name="publish-to-app-service-on-linux"></a>Publikowanie w usłudze App Service w systemie Linux

1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Publikuj** (lub użyj **kompilacji** > **Publikuj** element menu).

    ![Polecenia Opublikuj w menu kontekstowym projektu w Eksploratorze rozwiązań](../deployment/media/quickstart-publish.png "wybierz polecenie Publikuj")

1. Jeśli wcześniej skonfigurowano żadnych profilów publikowania **Publikuj** zostanie wyświetlone okienko, w których wielkość wybranych **Utwórz nowy profil**.

1. W **wybierz lokalizację docelową publikowania** okna dialogowego wybierz **App Service Linux**.

    ![Usługa Azure App Service wybierz](../deployment/media/quickstart-publish-linux.png "wybierz usługi Azure App Service")

1. Wybierz **publikowania**. **Tworzenie usługi App Service** pojawi się okno dialogowe. Zaloguj się przy użyciu konta platformy Azure możesz, jeśli to konieczne, a następnie domyślnych ustawień usługi app Wypełnij pola.

    ![Utwórz usługę App Service](../deployment/media/quickstart-publish-settings-app-service-linux.png "Tworzenie usługi Azure App Service")

1. Wybierz **tworzenie**. Program Visual Studio wdroży aplikację do usługi Azure App Service i ładowania aplikacji sieci web w przeglądarce. Właściwości projektu **Publikuj** okienko zawiera adres URL witryny oraz inne szczegóły.

    ![Okienko właściwości wyświetlanie podsumowania profil publikowania](../deployment/media/quickstart-publish-app-service-summary.png)

## <a name="next-steps"></a>Następne kroki

W tym przewodniku Szybki Start przedstawiono sposób tworzenia profilu publikowania do wdrożenia usługi App Service w systemie Linux przy użyciu programu Visual Studio. Może być więcej informacji na temat publikowania w systemie Linux przy użyciu platformy Azure.

> [!div class="nextstepaction"]
> [Usługa App Service w systemie Linux](/azure/app-service/containers/app-service-linux-intro)
