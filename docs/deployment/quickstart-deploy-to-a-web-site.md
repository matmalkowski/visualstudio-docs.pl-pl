---
title: Publikowanie witryny sieci Web
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
- multiple
ms.openlocfilehash: ede36baefa71e352f6f7e4960403ecbaa6b304b2
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36757224"
---
# <a name="publish-a-web-app-to-a-web-site-using-visual-studio"></a>Publikowanie aplikacji sieci web do witryny sieci web przy użyciu programu Visual Studio

Można użyć **publikowania** narzędzia do publikowania aplikacji platformy ASP.NET, platformy ASP.NET Core .NET Core i języka Python do witryny sieci Web w programie Visual Studio. Dla środowiska Node.js kroki są obsługiwane, ale interfejs użytkownika jest inny.

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]

## <a name="publish-to-a-web-site"></a>Publikowanie witryny sieci web

1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **publikowania** (lub użyj **kompilacji** > **publikowania** elementu menu).

    ![Polecenia Opublikuj w menu kontekstowym projekt w Eksploratorze rozwiązań](../deployment/media/quickstart-publish.png "wybierz publikowania")

1. Jeśli wcześniej skonfigurowano żadnych profilów publikowania, **publikowania** pojawi się okienko. Wybierz **Utwórz nowy profil**.

1. W **wybierz element docelowy publikowania** oknie dialogowym wybierz **usług IIS, FTP, itp**.

    ![Wybierz usług IIS, FTP, itp.](../deployment/media/quickstart-publish-iis-ftp.png "wybierz usług IIS, FTP,... itd.")

1. Wybierz **publikowania**. Profil publikowania ustawień, które zostanie otwarte okno dialogowe.

    ![Wybierz Folder](../deployment/media/quickstart-publish-settings-web.png "wybierz Folder")

1. W **metody publikowania** pola, takie jak wybrać metodę **narzędzia Web Deploy** lub **FTP**. Ustawienia, które są wyświetlane obok odpowiada wybranej metody publikowania. Narzędzie Web Deploy upraszcza wdrażanie aplikacji sieci Web i witryn sieci Web na serwerach usług IIS, a musi być zainstalowany jako aplikacji na serwerze. Użyj [Instalatora platformy sieci Web](https://www.microsoft.com/web/downloads/platform.aspx) go zainstalować.

1. Skonfiguruj wymagane ustawienia dla metody publikowania i wybierz **sprawdzania poprawności połączenia**. Jeśli serwer lub docelowa jest dostępna i ustawienia są poprawne, komunikat informujący, połączenie zostanie zweryfikowany, a wszystko jest gotowe do opublikowania.

    ![Weryfikacja połączenia z](../deployment/media/quickstart-publish-web-deploy.png "Weryfikacja połączenia")

1. Wybierz **ustawienia** skonfigurować inne ustawienia wdrożenia, takie jak czy wdrażanie debugowania lub wersji konfiguracji, a następnie wybierz **zapisać**. Jeśli debugujesz zdalnie, jest wymagana konfiguracja debugowania.

1. Aby opublikować aplikację, wybierz **publikowania**. W oknie danych wyjściowych zawiera wdrożenia postęp i wyniki.

## <a name="next-steps"></a>Następne kroki

W tym szybkiego startu wiesz, jak utworzyć profil publikowania za pomocą programu Visual Studio. Można również skonfigurować publikowanie profilu przez zaimportowanie ustawień publikowania.

> [!div class="nextstepaction"]
> [Importowanie ustawień publikowania i wdrażanie w usługach IIS](tutorial-import-publish-settings-iis.md)
