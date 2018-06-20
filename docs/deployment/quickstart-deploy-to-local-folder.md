---
title: Wdrażanie na folder lokalny — Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 05/08/2018
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
ms.openlocfilehash: 8f17e3214c1222eaadf43f3ea2d0e56742cd1ecf
ms.sourcegitcommit: f685fa5e2df9dc307bf1230dd9dc3288aaa408b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2018
ms.locfileid: "36234663"
---
# <a name="deploy-a-web-app-or-net-core-app-to-a-local-folder-using-the-visual-studio-publish-tool"></a>Wdrażanie aplikacji sieci web lub aplikacji .NET Core w lokalnym folderze przy użyciu narzędzia publikowanie programu Visual Studio

Można użyć **publikowania** narzędzia do publikowania aplikacji do folderu lokalnego. 

Te kroki dotyczą programu ASP.NET, platformy ASP.NET Core .NET Core i Python aplikacji w programie Visual Studio. Dla środowiska Node.js kroki są obsługiwane, ale interfejs użytkownika jest inny.

## <a name="prerequisites"></a>Wymagania wstępne

* Musi mieć Visual Studio 2017 r zainstalowany i. **NET development pulpitu** obciążenia i. **Podstawowe NET** obciążenia.

    Jeśli nie został już zainstalowany program Visual Studio, przejdź do [program Visual Studio pobiera](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) stronę, aby zainstalować ją bezpłatnie.

## <a name="create-a-new-project"></a>Tworzenie nowego projektu 

1. W programie Visual Studio, wybierz **pliku** > **nowy projekt**.

1. W obszarze **Visual C#** lub **Visual Basic**, wybierz **.NET Core**, a następnie w środkowym okienku wybierz **aplikacji konsoli (.NET Core)**.

1. Wpisz nazwę, takich jak **MyLocalApp** i kliknij przycisk **OK**.

    Program Visual Studio tworzy projekt.

## <a name="deploy-to-a-local-folder"></a>Wdrażanie w folderze lokalnym

1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **publikowania**.

    ![Wybierz publikowania](../deployment/media/quickstart-publish.png "wybierz publikowania")

1. Jeśli wcześniej skonfigurowano żadnych profilów publikowania, **publikowania** pojawi się okienko. Kliknij przycisk **Utwórz nowy profil**.

1. W **wybierz element docelowy publikowania** oknie dialogowym wybierz **folderu**.

    ![Wybierz Folder](../deployment/media/quickstart-publish-folder.png "wybierz Folder")

1. Wprowadź ścieżkę lub kliknij przycisk **Przeglądaj** przejdź do folderu lokalnego.

1. Kliknij przycisk **publikowania**.

    Visual Studio tworzy projekt i publikuje ją do określonego folderu.

    W okienku publikowania przedstawia podsumowanie profilu.

1. Kliknij, aby skonfigurować ustawienia wdrażania **ustawienia** w profilu podsumowania.

    ![Ustawienia profili](../deployment/media/quickstart-profile-settings.png "ustawień profilu") 

1. Skonfiguruj opcje, takie jak czy wdrażanie debugowania lub wersji konfiguracji, a następnie kliknij przycisk **zapisać**.

1. Aby opublikować ponownie, kliknij przycisk **publikowania**.

Wdrażanie plików publikowanych w dowolny sposób, który chcesz. Na przykład można umieścić je w pliku Zip, użyj polecenia prostego kopiowania lub wdrożyć je przy użyciu dowolnego pakietu instalacyjnego wybranych przez użytkownika.

## <a name="next-steps"></a>Następne kroki

- [Wdrażanie aplikacji .NET Core za pomocą narzędzia publikowania](/dotnet/core/deploying/deploy-with-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Tworzenie pakietu aplikacji klasycznej dla sklepu Microsoft Store (mostek dla aplikacji klasycznych)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- (.NET) [Wdrażanie programu .NET Framework i aplikacji...](/dotnet/framework/deployment/)
