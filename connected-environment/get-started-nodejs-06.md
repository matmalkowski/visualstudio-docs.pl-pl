---
title: Utwórz Środowisko deweloperskie Node.js z kontenerami przy użyciu Kubernetes w chmurze — krok 6 — więcej informacji na temat tworzenia zespołu | Dokumentacja firmy Microsoft
author: johnsta
ms.author: johnsta
ms.date: 02/20/2018
ms.topic: get-started-article
ms.technology: vsce-kubernetes
description: Szybkie opracowywanie Kubernetes z kontenerów i mikrousług na platformie Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, containers
manager: ghogen
ms.openlocfilehash: 4db1d71c96da29a06884e562a277a7ca427910d4
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2018
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

