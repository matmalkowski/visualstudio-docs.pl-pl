---
title: Utwórz Środowisko deweloperskie .NET Core z kontenerów przy użyciu Kubernetes w chmurze — krok 5 - wywołanie innego kontenera | Dokumentacja firmy Microsoft
author: johnsta
ms.author: johnsta
ms.date: 02/20/2018
ms.topic: get-started-article
ms.technology: vsce-kubernetes
description: Szybkie opracowywanie Kubernetes z kontenerów i mikrousług na platformie Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, containers
manager: ghogen
ms.openlocfilehash: 15ca1db26bc57aafa704a57b4464b31a1ada8c92
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2018
---
# <a name="get-started-on-connected-environment-with-net-core"></a>Rozpoczynanie pracy w środowisku połączonych z platformą .NET Core

Poprzedni krok: [kontenera w Kubernetes debugowania](get-started-netcore-04.md)

W tej sekcji zamierzamy utworzyć drugi usługę `mywebapi`i mieć `webfrontend` wywołać ją. Każda usługa będzie działać w osobnych kontenerów. Firma Microsoft będzie następnie debugowania za pośrednictwem obydwu kontenerów.

![](media/multi-container.png)

## <a name="download-sample-code-for-mywebapi"></a>Pobierz przykładowy kod *mywebapi*
Ze względu na czas możemy pobrać przykładowy kod z repozytorium GitHub. Przejdź do https://github.com/Azure/vsce i wybierz **klonowania lub pobrać** pobrać repozytorium GitHub. Kod dla tej sekcji znajduje się w `vsce/samples/dotnetcore/getting-started/mywebapi`.


## <a name="run-mywebapi"></a>Uruchom *mywebapi*
1. Otwórz folder `mywebapi` w *osobnym oknie kodzie VS*.
1. Naciśnij klawisz F5 i poczekaj, aż usługi do tworzenia i wdrażania. Użytkownik wie, że jest gotowy, gdy zostanie wyświetlony pasek debugowania kodu programu VS.
1. Zwróć uwagę adresu URL punktu końcowego, ekran będzie wyglądać podobnie jak http://localhost:\<numer_portu\>. **Porada: Kodzie VS paska stanu spowoduje wyświetlenie aktywne adresu URL.** Wydaje się, jak kontenera działa lokalnie, ale faktycznie jest uruchomiona w naszym środowisku programistycznym na platformie Azure. Przyczyna adres hosta lokalnego jest ponieważ `mywebapi` nie ma zdefiniowanych żadnych publicznych punktów końcowych i można uzyskać tylko z wewnątrz Kubernetes wystąpienia. Dla wygody użytkownika i ułatwienia interakcji z usługą prywatnych z komputera lokalnego połączone środowiska tworzy tymczasowy tunelu SSH w kontenerze działające na platformie Azure.
1. Gdy `mywebapi` jest gotowe, Otwórz w przeglądarce adres hosta lokalnego. Dołącz `/api/values` do adresu URL do wywołania interfejsu API GET domyślny dla `ValuesController`. 
1. Jeśli wszystkie kroki zostały wprowadzone pomyślnie, można wyświetlić na odpowiedź z `mywebapi` usługi.


## <a name="make-a-request-from-webfrontend-to-mywebapi"></a>Tworzenie żądania z *webfrontend* do *mywebapi*
Teraz napiszmy kod `webfrontend` który żąda `mywebapi`.
1. Przełącz do okna kodzie VS `webfrontend`.
1. *Zastąp* kod metody informacje:

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

W powyższym przykładzie kodu również sprawia, że użycie `HeaderPropagatingHttpClient` klasy. Ta klasa pomocy został dodany do folderu kodu w czasie uruchomienia `vsce init`. `HeaderPropagatingHttpClient` jest dervied z dobrze znanego `HttpClient` klasy który dodaje funkcje propagację określonych nagłówków z istniejącego obiektu ASP .NET HttpRequest do wychodzących obiektu HttpRequestMessage. Zajmiemy się później, jak to ułatwia efektywniej środowisko programistyczne w scenariuszach zespołu.


## <a name="debug-across-multiple-services"></a>Debugowanie w wielu usługach
1. W tym momencie `mywebapi` powinny być nadal uruchomione w debugerze. Jeśli nie, naciśnij klawisz F5 w `mywebapi` projektu.
1. Ustaw punkt przerwania `Get(int id)` metoda obsługująca `api/values/{id}` żądania GET.
1. W `webfrontend` projektu, należy ustawić punkt przerwania tuż przed wysłaniem żądania GET do `mywebapi/api/values`.
1. Naciśnij klawisz F5 w `webfrontend` projektu.
1. Wywołanie aplikacji sieci web i wykonywać krokowo kodu w obu usług.
1. W aplikacji sieci web na stronie informacje zostanie wyświetlony komunikat połączonych przez dwie usługi: "Hello webfrontend i Hello z mywebapi".


Dobra robota! Masz teraz aplikacji wielu kontenera, w którym każdego kontenera mogą być opracowane i wdrażane pojedynczo.

> [!div class="nextstepaction"]
> [Dowiedz się więcej o programowanie zespołowe](get-started-netcore-06.md)

