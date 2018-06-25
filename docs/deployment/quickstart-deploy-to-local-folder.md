---
title: Wdrażanie w folderze lokalnym
ms.custom: ''
ms.date: 06/22/2018
ms.technology: vs-ide-deployment
ms.topic: quickstart
helpviewer_keywords:
- deployment, local folder
ms.assetid: adb461c4-812a-4b8c-b2ab-96002379f6a9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 517698aa2e042d74138579dae3633930b338cd61
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36756278"
---
# <a name="deploy-an-app-to-a-local-folder-using-visual-studio"></a>Wdrażanie aplikacji w lokalnym folderze przy użyciu programu Visual Studio

Można użyć **publikowania** narzędzia do publikowania aplikacji platformy ASP.NET, platformy ASP.NET Core .NET Core i języka Python do folderu lokalnego z programu Visual Studio. Dla środowiska Node.js kroki są obsługiwane, ale interfejs użytkownika jest inny.

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]

## <a name="deploy-to-a-local-folder"></a>Wdrażanie w folderze lokalnym

1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **publikowania** (lub użyj **kompilacji** > **publikowania** elementu menu).

    ![Polecenia Opublikuj w menu kontekstowym projekt w Eksploratorze rozwiązań](../deployment/media/quickstart-publish.png "wybierz publikowania")

1. Jeśli wcześniej skonfigurowano żadnych profilów publikowania, **publikowania** pojawi się okienko. Wybierz **Utwórz nowy profil**.

1. W **wybierz element docelowy publikowania** oknie dialogowym wybierz **folderu**.

    ![Wybierz folder lokalny jako docelowy publikowania](../deployment/media/quickstart-publish-folder.png "wybierz Folder")

1. Wprowadź ścieżkę lub wybierz **Przeglądaj** do określenia folderu lokalnego.

1. Wybierz **publikowania**. Visual Studio tworzy projekt i publikuje ją do określonego folderu. Właściwości projektu **publikowania** profil zostanie wyświetlone okienko przedstawiający podsumowania.

    ![Publikowanie właściwości okienko profil podsumowania](../deployment/media/quickstart-publish-folder-summary.png)

1. Aby skonfigurować ustawienia wdrożenia, wybierz **Konfiguruj** w profilu, podsumowanie i wybierz **ustawienia** kartę.

    ![Ustawienia profili](../deployment/media/quickstart-profile-settings.png "ustawień profilu")

1. Skonfiguruj opcje, takie jak czy wdrażanie debugowania lub wersji konfiguracji, a następnie wybierz **zapisać**.

1. Aby opublikować ponownie, wybierz **publikowania**.

Wdrażanie plików publikowanych w dowolny sposób, który chcesz. Na przykład można umieścić je w *.zip* plików, użyj polecenia prostego kopiowania lub wdrożyć je przy użyciu dowolnego pakietu instalacyjnego wybranych przez użytkownika.

## <a name="next-steps"></a>Następne kroki

- [Wdrażanie aplikacji .NET Core za pomocą narzędzia publikowania](/dotnet/core/deploying/deploy-with-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Tworzenie pakietu aplikacji klasycznej dla sklepu Microsoft Store (mostek dla aplikacji klasycznych)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- (.NET) [Wdrażanie programu .NET Framework i aplikacji](/dotnet/framework/deployment/)
