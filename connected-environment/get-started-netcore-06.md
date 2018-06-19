---
title: Tworzenie środowiska programowania .NET Core z kontenerami przy użyciu Kubernetes w chmurze — krok 6 — więcej informacji na temat tworzenia zespołu | Dokumentacja firmy Microsoft
author: ghogen
ms.author: ghogen
ms.date: 02/20/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Szybkie opracowywanie Kubernetes z kontenerów i mikrousług na platformie Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, containers
manager: douge
ms.openlocfilehash: 4da5051b760a12f8fd8837072ada44c8c5a9b239
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31884346"
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
