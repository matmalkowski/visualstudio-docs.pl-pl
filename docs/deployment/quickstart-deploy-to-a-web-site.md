---
title: Publikowanie witryny sieci Web — Visual Studio | Dokumentacja firmy Microsoft
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
- multiple
ms.openlocfilehash: 1f7fc936211188ee623a8b7c28ccdfe7fde25606
ms.sourcegitcommit: 4667e6ad223642bc4ac525f57281482c9894daf4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/20/2018
ms.locfileid: "36280971"
---
# <a name="publish-a-web-app-or-a-net-core-app-to-a-web-site-using-the-visual-studio-publish-tool"></a>Publikowanie witryny sieci web przy użyciu narzędzia Visual Studio publikowania aplikacji sieci web lub aplikacji .NET Core

Można użyć **publikowania** narzędzia do publikowania aplikacji ASP.NET do witryny sieci Web.

Te kroki dotyczą programu ASP.NET, platformy ASP.NET Core .NET Core i Python aplikacji w programie Visual Studio. Dla środowiska Node.js kroki są obsługiwane, ale interfejs użytkownika jest inny.

## <a name="prerequisites"></a>Wymagania wstępne

* Musi mieć Visual Studio 2017 r zainstalowany i **ASP.NET i sieć web development** obciążenia i. **NET development pulpitu** obciążenia. W przypadku aplikacji .NET Core należy. **NET Core** obciążenia.

    Jeśli nie został już zainstalowany program Visual Studio, przejdź do [program Visual Studio pobiera](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) stronę, aby zainstalować ją bezpłatnie.

## <a name="create-a-new-project"></a>Tworzenie nowego projektu

1. W programie Visual Studio, wybierz **pliku** > **nowy projekt**.

1. W obszarze **Visual C#** lub **Visual Basic**, wybierz **sieci Web**, a następnie w środkowym okienku wybierz albo **aplikacji sieci Web platformy ASP.NET (.NET Framework)** lub (C# tylko) **aplikacji sieci Web platformy ASP.NET Core**, a następnie kliknij przycisk **OK**.

1. Wybierz **MVC** (lub wybierz **aplikacji sieci Web (Model-View-Controller)** dla platformy .NET Core), upewnij się, że **bez uwierzytelniania** jest zaznaczone, a następnie kliknij przycisk **OK** .

1. Wpisz nazwę, takich jak **MyWebApp** i kliknij przycisk **OK**.

    Program Visual Studio tworzy projekt.

1. Wybierz **kompilacji** > **Kompiluj rozwiązanie** Aby skompilować projekt.

## <a name="publish-to-a-web-site"></a>Publikowanie witryny sieci web

1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **publikowania**.

    ![Wybierz publikowania](../deployment/media/quickstart-publish-aspnet.png "wybierz publikowania")

1. Jeśli wcześniej skonfigurowano żadnych profilów publikowania, **publikowania** pojawi się okienko. Kliknij przycisk **Utwórz nowy profil**.

1. W **wybierz element docelowy publikowania** oknie dialogowym wybierz **usług IIS, FTP, itp**.

    ![Wybierz usług IIS, FTP, itp.](../deployment/media/quickstart-publish-iis-ftp.png "wybierz usług IIS, FTP,... itd.")

1. Kliknij przycisk **publikowania**.

    Profil publikowania ustawień, które zostanie otwarte okno dialogowe.

    ![Wybierz Folder](../deployment/media/quickstart-publish-settings-web.png "wybierz Folder")

1. W **metody publikowania** pola, takie jak wybrać metodę **narzędzia Web Deploy** lub **FTP**.

    Ustawienia, które są wyświetlane obok odpowiada wybranej metody publikowania. Narzędzie Web Deploy upraszcza wdrażanie aplikacji sieci Web i witryn sieci Web na serwerach usług IIS, a musi być zainstalowany jako aplikacji na serwerze. Użyj [Instalatora platformy sieci Web](https://www.microsoft.com/web/downloads/platform.aspx) go zainstalować.

1. Skonfiguruj wymagane ustawienia metody publikowania i kliknij przycisk **sprawdzania poprawności połączenia**.

    Jeśli serwer lub docelowa jest dostępna i ustawienia są poprawne, pojawi się komunikat informujący, połączenie zostanie zweryfikowany, a wszystko jest gotowe do publikowania.

    ![Weryfikacja połączenia z](../deployment/media/quickstart-publish-web-deploy.png "Weryfikacja połączenia")

1. Jeśli chcesz skonfigurować inne ustawienia wdrożenia, kliknij przycisk **ustawienia**.

    Można skonfigurować opcje, takie jak czy wdrażanie debugowania lub wersji konfiguracji, a następnie kliknij przycisk **zapisać**. Jeśli debugowanie zdalne konfiguracji debugowania jest wymagany.

1. Aby opublikować aplikację, kliknij przycisk **publikowania**.

    W oknie danych wyjściowych zawiera wdrożenia postęp i wyniki.

## <a name="next-steps"></a>Następne kroki

W tym szybkiego startu wiesz, jak utworzyć profil publikowania za pomocą programu Visual Studio. Można również skonfigurować publikowanie profilu przez zaimportowanie ustawień publikowania.

> [!div class="nextstepaction"]
> [Importowanie ustawień publikowania i wdrażanie w usługach IIS](tutorial-import-publish-settings-iis.md)
