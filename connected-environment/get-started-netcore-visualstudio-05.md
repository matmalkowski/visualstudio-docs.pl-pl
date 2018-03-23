---
title: Tworzenie środowiska programowania .NET Core z kontenerami przy użyciu Kubernetes w chmurze za pomocą programu Visual Studio — krok 5 - wywołanie innego kontenera | Dokumentacja firmy Microsoft
author: johnsta
ms.author: johnsta
ms.date: 02/20/2018
ms.topic: get-started-article
ms.technology: vsce-kubernetes
description: Szybkie opracowywanie Kubernetes z kontenerów i mikrousług na platformie Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, containers
manager: ghogen
ms.openlocfilehash: 8b0a0c78496b8f57764383d737e2a1cebb2dd6b9
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2018
---
# <a name="get-started-on-connected-environment-with-net-core-and-visual-studio"></a>Rozpoczynanie pracy w środowisku połączonych z platformy .NET Core i Visual Studio

Poprzedni krok: [kontenera w Kubernetes debugowania](get-started-netcore-visualstudio-04.md)

## <a name="call-another-container"></a>Wywołanie innego kontenera
W tej sekcji zamierzamy utworzyć drugi usługę `mywebapi`i mieć `webfrontend` wywołać ją. Każda usługa będzie działać w osobnych kontenerów. Firma Microsoft będzie następnie debugowania za pośrednictwem obydwu kontenerów.

![](media/multi-container.png)

## <a name="download-sample-code-for-mywebapi"></a>Pobierz przykładowy kod *mywebapi*
Ze względu na czas możemy pobrać przykładowy kod z repozytorium GitHub. Przejdź do https://github.com/Azure/vsce i wybierz **klonowania lub pobrać** pobrać repozytorium GitHub. Kod dla tej sekcji znajduje się w `vsce/samples/dotnetcore/getting-started/mywebapi`.

## <a name="run-mywebapi"></a>Uruchom *mywebapi*
1. Otwórz projekt `mywebapi` w *osobne okno programu Visual Studio*.
1. Wybierz **połączone środowisko AKS** z listy rozwijanej Ustawienia uruchamiania podczas została wcześniej `webfrontend` projektu. Zamiast tworzyć nowe środowisko deweloperskie teraz, wybierz ten sam już utworzone. Przed pozostaw domyślnie ustawiony miejsce `mainline` i kliknij przycisk **OK**. W oknie dane wyjściowe mogą pojawić się rozpocznie "rozgrzewki" nowej usługi w środowisku projektowania aby przyspieszyć rzeczy się po rozpoczęciu debugowania, Visual Studio
1. Naciśnij klawisz F5 i poczekaj, aż usługi do tworzenia i wdrażania. Będzie wiadomo, że jest gotowa przy pomarańczowy pasek stanu programu Visual Studio
1. Zwróć uwagę na punkt końcowy adres URL wyświetlany w **połączone środowisko AKS** okienka w **dane wyjściowe** okna, jego będzie wyglądać jak http://localhost:\<numer_portu\>. Wydaje się, jak kontenera działa lokalnie, ale faktycznie jest uruchomiona w naszym środowisku programistycznym na platformie Azure.
1. Gdy `mywebapi` jest gotowy, otwórz przeglądarkę z adresem localhost i Dołącz `/api/values` do adresu URL do wywołania interfejsu API GET domyślny dla `ValuesController`. 
1. Jeśli wszystkie kroki zostały wprowadzone pomyślnie, można wyświetlić na odpowiedź z `mywebapi` usługi, która wygląda następująco.

    ![](images/WebAPIResponse.png)

## <a name="make-a-request-from-webfrontend-to-mywebapi"></a>Tworzenie żądania z *webfrontend* do *mywebapi*
Teraz napiszmy kod `webfrontend` który żąda `mywebapi`. Przełącz do okna programu Visual Studio, który ma `webfrontend` projektu. W `HomeController.cs` pliku *Zastąp* kod metody o z następujących czynności:

 ```csharp
    public async Task<IActionResult> About()
    {
        ViewData["Message"] = "Hello from webfrontend";
        
        // Use HeaderPropagatingHttpClient instead of HttpClient so we can propagate
        // headers in the incoming request to any outgoing requests
        using (var client = new HeaderPropagatingHttpClient(this.Request))
        {
            // Call *mywebapi*, and display its response in the page
            var response = await client.GetAsync("http://mywebapi/api/values/1");
            ViewData["Message"] += " and " + await response.Content.ReadAsStringAsync();
        }
    
        return View();
    }

```

Należy zwrócić uwagę, jak odnajdywanie usługi DNS Kubernetes jest stosowane do odwoływania się do usługi, ponieważ `http://mywebapi`. **Kod w naszym środowisku programistycznym działa tak samo zostanie uruchomiony w środowisku produkcyjnym**.

W powyższym przykładzie kodu również sprawia, że użycie `HeaderPropagatingHttpClient` klasy. Ta klasa pomocy jest plik `HeaderPropagation.cs` który został dodany do projektu podczas konfigurowania go do korzystania ze środowiska połączony. `HeaderPropagatingHttpClient` jest określana na podstawie dobrze znanych `HttpClient` klasy który dodaje funkcje propagację określonych nagłówków z istniejącego obiektu ASP .NET HttpRequest do wychodzących obiektu HttpRequestMessage. Zajmiemy się później, jak to ułatwia efektywniej środowisko programistyczne w scenariuszach zespołu.

## <a name="debug-across-multiple-services"></a>Debugowanie w wielu usługach
1. W tym momencie `mywebapi` powinny być nadal uruchomione w debugerze. Jeśli nie, naciśnij klawisz F5 w `mywebapi` projektu.
1. Ustaw punkt przerwania `Get(int id)` metody w `ValuesController.cs` pliku, który obsługuje `api/values/{id}` żądania GET.
1. W `webfrontend` projektu, w którym firma Microsoft wklejony kod powyżej, ustaw punkt przerwania tuż przed wysłaniem żądania GET do `mywebapi/api/values`.
1. Naciśnij klawisz F5 w `webfrontend` projektu. Visual Studio będzie ponownie otwórz przeglądarkę do portu localhost odpowiednie i aplikacja sieci web zostanie wyświetlona.
1. Kliknij pozycję "**o**" łącze w górnej części strony, aby wyzwolić punkt przerwania w `webfrontend` projektu. 
1. Trafienia F10, aby kontynuować. Punkt przerwania w `mywebapi` projektu zostanie teraz wyzwolone.
1. Trafień F5, aby kontynuować i będzie w kodzie w `webfrontend` projektu.
1. Naciśnięcie klawisza F5 jeszcze raz wykonać żądania i zwraca stronę w przeglądarce. W aplikacji sieci web na stronie informacje zostanie wyświetlony komunikat połączonych przez dwie usługi: "Hello webfrontend i Hello z mywebapi".

Dobra robota! Masz teraz aplikacji wielu kontenera, w którym każdego kontenera mogą być opracowane i wdrażane pojedynczo.

> [!div class="nextstepaction"]
> [Dowiedz się więcej o programowanie zespołowe](get-started-netcore-visualstudio-06.md)

