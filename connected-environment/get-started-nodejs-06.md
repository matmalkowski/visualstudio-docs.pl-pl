---
title: Utwórz Środowisko deweloperskie Node.js z kontenerami przy użyciu Kubernetes w chmurze — krok 6 — więcej informacji na temat tworzenia zespołu | Dokumentacja firmy Microsoft
author: ghogen
ms.author: ghogen
ms.date: 02/20/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Szybkie opracowywanie Kubernetes z kontenerów i mikrousług na platformie Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, containers
manager: douge
ms.openlocfilehash: 6a17dfc3eeebccf1508ea3f69aecb53d067de7af
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="get-started-on-connected-environment-with-nodejs"></a>Rozpoczynanie pracy w środowisku połączonych za pomocą języka Node.js

Poprzedni krok: [wywołań w usłudze działającej w oddzielnych kontenera](get-started-nodejs-05.md)

[!INCLUDE[](includes/team-development-1.md)]

Zobaczmy ją w akcji:
1. Przejdź do okna kodzie VS `mywebapi` i wprowadź kod Edytuj domyślne GET `/` obsługi, na przykład:

```javascript
app.get('/', function (req, res) {
    res.send('mywebapi now says something new');
});
```

[!INCLUDE[](includes/team-development-2.md)]

> [!div class="nextstepaction"]
> [Next](get-started-nodejs-07.md)

