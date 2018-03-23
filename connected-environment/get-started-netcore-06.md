---
title: Tworzenie środowiska programowania .NET Core z kontenerami przy użyciu Kubernetes w chmurze — krok 6 — więcej informacji na temat tworzenia zespołu | Dokumentacja firmy Microsoft
author: johnsta
ms.author: johnsta
ms.date: 02/20/2018
ms.topic: get-started-article
ms.technology: vsce-kubernetes
description: Szybkie opracowywanie Kubernetes z kontenerów i mikrousług na platformie Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, containers
manager: ghogen
ms.openlocfilehash: 80e02e6ce1299278ba1abf530f38cb10b9f36c51
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2018
---
# <a name="get-started-on-connected-environment-with-net-core"></a>Rozpoczynanie pracy w środowisku połączonych z platformą .NET Core

Poprzedni krok: [wywołanie innego kontenera](get-started-netcore-05.md)

[!INCLUDE[](includes/team-development-1.md)]

Zobaczmy ją w akcji:
1. Przejdź do okna kodzie VS `mywebapi` i wprowadź kod Edytuj, aby `string Get(int id)` metody, na przykład:

```csharp
[HttpGet("{id}")]
public string Get(int id)
{
    return "mywebapi now says something new";
}
```

[!INCLUDE[](includes/team-development-2.md)]

> [!div class="nextstepaction"]
> [Next](get-started-netcore-07.md)
