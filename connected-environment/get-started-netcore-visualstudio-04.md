---
title: Tworzenie środowiska programowania .NET Core z kontenerami przy użyciu Kubernetes w chmurze za pomocą debugowania programu Visual Studio — krok 4 - kontenera w Kubernetes | Dokumentacja firmy Microsoft
author: johnsta
ms.author: johnsta
ms.date: 02/20/2018
ms.topic: get-started-article
ms.technology: vsce-kubernetes
description: Szybkie opracowywanie Kubernetes z kontenerów i mikrousług na platformie Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, containers
manager: ghogen
ms.openlocfilehash: 9b3aa6b0f710707800ea9a1f0533b0c37681ea05
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2018
---
# <a name="get-started-on-connected-environment-with-net-core-and-visual-studio"></a>Rozpoczynanie pracy w środowisku połączonych z platformy .NET Core i Visual Studio

Poprzedni krok: [tworzenie środowiska deweloperskiego na platformie Azure](get-started-netcore-visualstudio-03.md)

## <a name="debug-a-container-in-kubernetes"></a>Debugowanie kontenera w Kubernetes
Po pomyślnym utworzeniu środowiska programistycznego można debugować aplikacji. Ustaw punkt przerwania w kodzie, na przykład w wierszu 20 w pliku `HomeController.cs` gdzie `Message` zmienna jest ustawiona. Kliknij przycisk **F5** można rozpocząć debugowania. 

Visual Studio będzie komunikować się z Środowisko deweloperskie do tworzenia i wdrażania aplikacji i następnie otwórz przeglądarkę z aplikacji sieci web. Wydaje się, jak kontenera działa lokalnie, ale faktycznie jest uruchomiona w naszym środowisku programistycznym na platformie Azure. Powodem adres hosta lokalnego jest połączony środowiska tworzy tymczasowy tunelu SSH w kontenerze działające na platformie Azure.

Kliknij pozycję "**o**" łącze w górnej części strony, aby wyzwolić punktu przerwania. Masz pełny dostęp do debugowania informacji tak samo, jak gdyby kod było wykonywane lokalnie, takich jak stos wywołań, zmienne lokalne, informacje o wyjątku, itp.

> [!div class="nextstepaction"]
> [Wywołanie innego kontenera](get-started-netcore-visualstudio-05.md)