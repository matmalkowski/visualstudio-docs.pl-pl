---
title: Utwórz Środowisko deweloperskie .NET Core z kontenerów przy użyciu Kubernetes w chmurze — krok 3 — Tworzenie aplikacji sieci web platformy ASP.NET Core | Dokumentacja firmy Microsoft
author: johnsta
ms.author: johnsta
ms.date: 02/20/2018
ms.topic: get-started-article
ms.technology: vsce-kubernetes
description: Szybkie opracowywanie Kubernetes z kontenerów i mikrousług na platformie Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, containers
manager: ghogen
ms.openlocfilehash: f858a013e4b0c2ce1c30b8f26f2dc33eebf19c27
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2018
---
# <a name="get-started-on-connected-environment-with-net-core"></a>Rozpoczynanie pracy w środowisku połączonych z platformą .NET Core

Poprzedni krok: [Utwórz Środowisko deweloperskie Kubernetes na platformie Azure](get-started-netcore-02.md)

## <a name="create-an-aspnet-core-web-app"></a>Tworzenie aplikacji sieci Web platformy ASP.NET Core
Jeśli masz [.NET Core](https://www.microsoft.com/net) zainstalowana, można szybko utworzyć aplikacji sieci Web platformy ASP.NET Core w folderze o nazwie `webfrontend`.
```cmd
dotnet new mvc --name webfrontend
```

Alternatywnie **pobrać przykładowy kod z usługi GitHub** przechodząc do https://github.com/Azure/vsce i wybierz **klonowania lub pobrać** pobierania do środowiska lokalnego repozytorium GitHub. Kod dla tego przewodnika jest `vsce/samples/dotnetcore/getting-started/webfrontend`.

[!INCLUDE[](includes/vsce-init.md)]

[!INCLUDE[](includes/ensure-env-created.md)]

[!INCLUDE[](includes/build-and-run-in-k8s-cli.md)]

## <a name="update-a-content-file"></a>Aktualizowanie pliku zawartości
Połączone środowisko nie jest tylko o wprowadzenie kodu uruchamianego w Kubernetes - chodzi o co umożliwia szybkie i wielokrotnie powtarzane zobaczyć zmiany kodu zostały zastosowane w środowisku Kubernetes w chmurze.

1. Zlokalizuj plik `./Views/Home/Index.cshtml` i dokonać edycji HTML. Na przykład, zmień wiersz 70 odczytujący `<h2>Application uses</h2>` do wyglądać mniej więcej tak: `<h2>Hello k8s in Azure!</h2>`
1. Zapisz plik. Minut później, w oknie terminalu zobaczysz komunikat informujący, że plik w kontenerze uruchomionych został zaktualizowany.
1. Przejdź do przeglądarki i Odśwież stronę. Powinna zostać wyświetlona strona sieci web, wyświetlanie zaktualizowanych HTML.

Co się stało? Modyfikacje plików zawartości, takich jak HTML i CSS, nie wymagają ponownej kompilacji w aplikacji sieci web platformy .NET Core, więc aktywnego `vsce up` polecenia automatyczne synchronizowanie zmodyfikowanych plików zawartości w kontenerze uruchomionego na platformie Azure, zapewniając szybką Zobacz zawartości Umożliwia edycję.

## <a name="update-a-code-file"></a>Zaktualizuj plik kodu
Aktualizowanie plików kodu wymaga nieco więcej pracy, ponieważ aplikacja .NET Core musi ponownie skompilować i utworzyć pliki binarne zaktualizowaną aplikację.

1. W oknie terminalu, naciśnij klawisz `Ctrl+C` (przestanie `vsce up`).
1. Otwórz plik kodu o nazwie `Controllers/HomeController.cs`i edytowania wiadomości, która będzie wyświetlana na stronie informacje: `ViewData["Message"] = "Your application description page.";`
1. Zapisz plik.
1. Uruchom `vsce up` w oknie terminalu. 

Odtwarza obraz kontenera i wdraża ponownie Helm wykresu. Aby zobaczyć zmiany kodu zostały zastosowane w uruchomionej aplikacji, przejdź do menu informacje w aplikacji sieci web.


Ale nawet *szybszej metody* związane z opracowywaniem kod, który firma Microsoft będzie Eksplorowanie w następnej sekcji. 
> [!div class="nextstepaction"]
> [Debugowanie kontenera w Kubernetes](get-started-netcore-04.md)

