---
title: Tworzenie środowiska programowania .NET Core z kontenerami przy użyciu Kubernetes w chmurze za pomocą narzędzi Visual Studio — krok 1 — Instalacja | Dokumentacja firmy Microsoft
author: ghogen
ms.author: ghogen
ms.date: 04/05/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Szybkie opracowywanie Kubernetes z kontenerów i mikrousług na platformie Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, containers
manager: douge
ms.openlocfilehash: b2edc476ffd4648f9ddb0e3d076f8eb400458242
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31884955"
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

1. Pobierz i uruchom [połączone środowiska interfejsu wiersza polecenia Instalatora](https://aka.ms/get-vsce-windows). 

## <a name="get-kubernetes-debugging-tools"></a>Pobierz Kubernetes narzędzia debugowania
Za pomocą połączenia interfejsu wiersza polecenia środowiska jako autonomicznego narzędzia, zaawansowane funkcje, takie jak **debugowania Kubernetes** są dostępne dla deweloperów platformy .NET Core za pomocą **kodzie VS** lub **programu Visual Studio** .

### <a name="visual-studio-debugging"></a>Debugowanie programu Visual Studio 
1. Zainstaluj najnowszą wersję pakietu [programu Visual Studio 2017 r.](https://www.visualstudio.com/vs/)
1. W Instalatorze programu Visual Studio upewnij się, że wybrano następujące obciążenia:
    * ASP.NET i sieć web development
1. Zainstaluj [rozszerzenie programu Visual Studio dla środowiska połączone](https://aka.ms/get-vsce-visualstudio)

Jest teraz gotowy do utworzenia aplikacji sieci web platformy ASP.NET z programem Visual Studio.

> [!div class="nextstepaction"]
> [Tworzenie aplikacji sieci web platformy ASP.NET](get-started-netcore-visualstudio-02.md)
