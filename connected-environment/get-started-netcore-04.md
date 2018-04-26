---
title: Tworzenie środowiska programowania .NET Core z kontenerami przy użyciu Kubernetes w chmurze — krok 4 — debugowania a kontenera w Kubernetes | Dokumentacja firmy Microsoft
author: ghogen
ms.author: ghogen
ms.date: 02/20/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Szybkie opracowywanie Kubernetes z kontenerów i mikrousług na platformie Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, containers
manager: douge
ms.openlocfilehash: 043052dec78251647a3ef12e0b612355b6334692
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="get-started-on-connected-environment-with-net-core"></a>Rozpoczynanie pracy w środowisku połączonych z platformą .NET Core
 
Poprzedni krok: [tworzenie aplikacji sieci Web platformy ASP.NET Core](get-started-netcore-03.md)

[!INCLUDE[](includes/debug-intro.md)]

[!INCLUDE[](includes/init-debug-assets-vscode.md)]


## <a name="select-the-vsce-debug-configuration"></a>Wybierz konfigurację debugowania VSCE
1. Aby otworzyć widok debugowania, kliknij ikonę debugowania w **działania pasek** boku kodzie VS.
1. Wybierz **.NET Core uruchom (VSCE)** co Konfiguracja debugowania aktywnego.

![](media/debug-configuration.png)

> [!Note]
> Jeśli nie widać żadnych poleceń środowiska połączone w palecie polecenia, upewnij się, masz [zainstalowane rozszerzenie kodzie VS połączone środowiska](get-started-netcore-01.md#get-kubernetes-debugging-for-vs-code).


## <a name="debug-the-container-in-kubernetes"></a>Debugowanie kontenera w Kubernetes
Trafienia **F5** do debugowania kodu w Kubernetes.

Jak `up` polecenia kodu jest synchronizowany do środowiska projektowego i kontener jest wbudowana i wdrożony Kubernetes. Tym razem oczywiście debuger jest dołączony do zdalnego kontenera.

[!INCLUDE[](includes/tip-vscode-status-bar-url.md)]

Ustaw punkt przerwania w pliku kodu po stronie serwera, na przykład w ramach `Index()` działać w `Controllers/HomeController.cs` pliku źródłowego. Odśwież stronę, przeglądarki powoduje trafienie punktu przerwania.

Masz pełny dostęp do debugowania informacji tak samo, jak gdyby kod było wykonywane lokalnie, takich jak stos wywołań, zmienne lokalne, informacje o wyjątku, itp.

## <a name="edit-code-and-refresh"></a>Edytuj kod i Odśwież
Z debugera aktywnego należy edytować kod. Na przykład zmodyfikować komunikat strony informacje w `Controllers/HomeController.cs`. 

```csharp
public IActionResult About()
{
    ViewData["Message"] = "My custom message in the About page.";
    return View();
}
```

Zapisz plik i w **okienka Akcje debugowania**, kliknij przycisk **Odśwież** przycisku. 

![](media/debug-action-refresh.png)

Zamiast odbudowywania ani ponownego wdrażania nowego obrazu kontenera zawsze wprowadzono zmiany kodu, które często będą zająć wiele czasu, połączone środowiska przyrostowo będzie ponownie kompilować kod w istniejących kontener, aby zapewnić szybszy pętli edycji/debug.

Odświeżanie aplikacji sieci web w przeglądarce, a następnie przejdź do strony informacje. Powinna zostać wyświetlona niestandardowe komunikatu są wyświetlane w interfejsie użytkownika.

**Teraz masz metody do szybkiego iteracja na kod i debugowanie bezpośrednio w Kubernetes!** Następnie możemy wyświetlony, jak możemy tworzyć i wywołać drugi kontenera.

> [!div class="nextstepaction"]
> [Wywołanie usługi uruchomione w kontenerze oddzielne](get-started-netcore-05.md)
