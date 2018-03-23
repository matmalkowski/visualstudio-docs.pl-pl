---
title: Tworzenie środowiska programowania .NET Core z kontenerami przy użyciu Kubernetes w chmurze za pomocą narzędzi Visual Studio — krok 1 — Instalacja | Dokumentacja firmy Microsoft
author: johnsta
ms.author: johnsta
ms.date: 02/20/2018
ms.topic: get-started-article
ms.technology: vsce-kubernetes
description: Szybkie opracowywanie Kubernetes z kontenerów i mikrousług na platformie Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, containers
manager: ghogen
ms.openlocfilehash: 4f25d4ae550f47533628bf073f2f22d9ed158cab
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2018
---
# <a name="get-started-on-connected-environment-with-net-core-and-visual-studio"></a>Rozpoczynanie pracy w środowisku połączonych z platformy .NET Core i Visual Studio

W tym przewodniku będzie dowiesz się, jak:

1. Tworzenie środowisk Kubernetes na platformie Azure, zoptymalizowana pod kątem tworzenia.
1. Wielokrotnie powtarzane Opracuj kodu w kontenerach przy użyciu programu Visual Studio.
1. Opracowywanie niezależnie dwa oddzielne usługi i odnajdowanie usługi DNS Kubernetes używane do wywoływania do innej usługi.
1. Tworzenie i testowanie kodu w środowisku zespołu.

[!INCLUDE[](includes/see-troubleshooting.md)]

## <a name="install-the-connected-environment-cli"></a>Instalowanie środowiska połączonych interfejsu wiersza polecenia
Środowisko połączonych wymaga instalacji minimalnego komputera lokalnego. Większość konfiguracji środowiska deweloperskiego pobiera przechowywane w chmurze i jest udostępniany innym użytkownikom.

1. Zainstaluj [Git dla systemu Windows](https://git-scm.com/downloads), wybierz pozycję Opcje instalacji domyślnej. 
1. Pobierz **kubectl.exe** z [to łącze](https://storage.googleapis.com/kubernetes-release/release/v1.9.0/bin/windows/amd64/kubectl.exe) i **zapisać** go do lokalizacji w ŚCIEŻCE.
1. Pobierz i uruchom [połączone środowiska interfejsu wiersza polecenia Instalatora](https://aka.ms/get-vsce-windows). 

## <a name="get-kubernetes-debugging-tools"></a>Pobierz Kubernetes narzędzia debugowania
Za pomocą połączenia interfejsu wiersza polecenia środowiska jako autonomicznego narzędzia, zaawansowane funkcje, takie jak **debugowania Kubernetes** są dostępne dla deweloperów platformy .NET Core za pomocą **kodzie VS** lub **programu Visual Studio**.

### <a name="visual-studio-debugging"></a>Visual Studio debugging 
1. Zainstaluj najnowszą wersję pakietu [programu Visual Studio 2017 r.](https://www.visualstudio.com/vs/)
1. W Instalatorze programu Visual Studio upewnij się, że wybrano następujące obciążenia:
    * ASP.NET i sieć web development
1. Zainstaluj [rozszerzenie programu Visual Studio dla środowiska połączone](https://aka.ms/get-vsce-visualstudio)

Jest teraz gotowy do utworzenia aplikacji sieci web platformy ASP.NET z programem Visual Studio.

> [!div class="nextstepaction"]
> [Tworzenie aplikacji sieci web platformy ASP.NET](get-started-netcore-visualstudio-02.md)