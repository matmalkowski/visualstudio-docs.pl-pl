---
title: Utwórz Środowisko deweloperskie Node.js z kontenerami przy użyciu Kubernetes w chmurze — krok 4 — debugowania a kontenera w Kubernetes | Dokumentacja firmy Microsoft
author: johnsta
ms.author: johnsta
ms.date: 02/20/2018
ms.topic: get-started-article
ms.technology: vsce-kubernetes
description: Szybkie opracowywanie Kubernetes z kontenerów i mikrousług na platformie Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, containers
manager: ghogen
ms.openlocfilehash: 8dca016f3a3feb2d1fb10a80695b82e531e48a74
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2018
---
# <a name="get-started-on-connected-environment-with-nodejs"></a>Rozpoczynanie pracy w środowisku połączonych za pomocą języka Node.js

Poprzedni krok: [utworzyć kontener Node.js w Kubernetes](get-started-nodejs-03.md)

[!INCLUDE[](includes/debug-intro.md)]

[!INCLUDE[](includes/init-debug-assets-vscode.md)]


## <a name="select-the-vsce-debug-configuration"></a>Wybierz konfigurację debugowania VSCE
1. Aby otworzyć widok debugowania, kliknij ikonę debugowania w **działania pasek** boku kodzie VS.
1. Wybierz **uruchamianie programu (VSCE)** co Konfiguracja debugowania aktywnego.

![](media/debug-configuration-nodejs.png)

> [!Note]
> Jeśli nie widać żadnych poleceń środowiska połączone w palecie polecenia, upewnij się, masz [zainstalowane rozszerzenie kodzie VS połączone środowiska](get-started-nodejs-01.md#get-kubernetes-debugging-for-vs-code).

## <a name="debug-the-container-in-kubernetes"></a>Debugowanie kontenera w Kubernetes
Trafienia **F5** do debugowania kodu w Kubernetes!

Podobnie jak `up` polecenia kodu jest synchronizowany do środowiska projektowego po rozpoczęciu debugowania i kontener jest wbudowana i wdrożony Kubernetes. Tym razem oczywiście debuger jest dołączony do zdalnego kontenera.

[!INCLUDE[](includes/tip-vscode-status-bar-url.md)]

Ustaw punkt przerwania w pliku kodu po stronie serwera, na przykład w ramach `app.get('/api'...` w `server.js`. Odśwież stronę przeglądarki lub naciśnij przycisk "Powiedzieć go ponownie", a powinien trafienie punktu przerwania i można wykonywać krokowo kodu.

Masz pełny dostęp do debugowania informacji tak samo, jak gdyby kod było wykonywane lokalnie, takich jak stos wywołań, zmienne lokalne, informacje o wyjątku, itp.

## <a name="edit-code-and-refresh-the-debug-session"></a>Edytuj kod i Odśwież sesji debugowania
Z debugera aktywnego wprowadzić kod, Edytuj; na przykład zmodyfikować wiadomość hello ponownie:

```javascript
app.get('/api', function (req, res) {
    res.send('**** Hello from webfrontend running in Azure! ****');
});
```

Zapisz plik i w **okienka Akcje debugowania**, kliknij przycisk **Odśwież** przycisku. 

![](media/debug-action-refresh-nodejs.png)

Zamiast odbudowywania ani ponownego wdrażania nowego obrazu kontenera zawsze wprowadzono zmiany kodu, które często będą zająć wiele czasu, połączone środowiska uruchomi proces Node.js Between sesji debugowania, aby zapewnić szybszy pętli edycji/debug.

Odświeżanie aplikacji sieci web w przeglądarce lub naciśnij klawisz *powiedz ponownie* przycisku. Powinna zostać wyświetlona niestandardowe komunikatu są wyświetlane w interfejsie użytkownika.


## <a name="use-nodemon-to-develop-even-faster"></a>Umożliwia tworzenie szybciej NodeMon
*Nodemon* jest narzędziem do popularnych używające deweloperów środowiska Node.js do szybkiego opracowywania. Zamiast ponowne ręczne uruchomienie procesu węzłów przy każdym staje się edycji kodu po stronie serwera, deweloperzy często skonfiguruje ich węzła projektu mają *nodemon* monitorowanie zmian w plikach i automatycznie uruchom ponownie proces serwera. W tym stylu pracy dewelopera tylko odświeża przeglądarce po wprowadzeniu kodu edycji.

Celem połączonych środowiska jest dla Ciebie można było korzystać z tej samej i wydajne programowanie przepływów pracy, który zostanie zastosowana podczas opracowywania lokalnie. Ten przykład ilustrujący `webfrontend` projektu został skonfigurowany do używania *nodemon* (jest on skonfigurowany jako zależność deweloperów w `package.json`).

Spróbuj wykonać następujące czynności:
1. Zatrzymywanie działania debugera kodzie VS.
1. Kliknij ikonę debugowania w **działania pasek** boku kodzie VS. 
1. Wybierz **dołączyć (VSCE)** co Konfiguracja debugowania aktywnego.
1. Hit F5.

W tej konfiguracji kontenera jest skonfigurowany do uruchamiania *nodemon*. Gdy zostaną wprowadzone zmiany kodu serwera, *nodemon* spowoduje automatyczne ponowne uruchomienie procesu węzła tak samo jak robi podczas opracowywania lokalnie. 
1. Edytuj wiadomość hello ponownie w `server.js`i Zapisz plik.
1. Odśwież przeglądarkę, lub kliknij przycisk *powiedz ponownie* przycisk, aby zobaczyć wprowadzone zmiany!

**Teraz masz metody do szybkiego iteracja na kod i debugowanie bezpośrednio w Kubernetes!** Następnie możemy wyświetlony, jak możemy tworzyć i wywołać drugi kontenera.

> [!div class="nextstepaction"]
> [Wywołanie usługi uruchomione w kontenerze oddzielne](get-started-nodejs-05.md)

