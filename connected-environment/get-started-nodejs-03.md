---
title: Utwórz Środowisko deweloperskie Node.js z kontenerów przy użyciu Kubernetes w chmurze — krok 3 — Tworzenie aplikacji sieci web platformy ASP.NET | Dokumentacja firmy Microsoft
author: johnsta
ms.author: johnsta
ms.date: 02/20/2018
ms.topic: get-started-article
ms.technology: vsce-kubernetes
description: Szybkie opracowywanie Kubernetes z kontenerów i mikrousług na platformie Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, containers
manager: ghogen
ms.openlocfilehash: 26d6753bf17b459c33cd11c46186d272d477fe10
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2018
---
# <a name="get-started-on-connected-environment-with-nodejs"></a>Rozpoczynanie pracy w środowisku połączonych za pomocą języka Node.js

Poprzedni krok: [Utwórz Środowisko deweloperskie Kubernetes na platformie Azure](get-started-nodejs-02.md)

## <a name="create-a-nodejs-web-app"></a>Tworzenie aplikacji sieci Web Node.js
Pobierz kod z serwisu GitHub, przechodząc do https://github.com/Azure/vsce i wybierz **klonowania lub pobrać** pobierania do środowiska lokalnego repozytorium GitHub. Kod dla tego przewodnika jest `vsce/samples/nodejs/getting-started/webfrontend`.

[!INCLUDE[](includes/vsce-init.md)]

[!INCLUDE[](includes/ensure-env-created.md)]

[!INCLUDE[](includes/build-and-run-in-k8s-cli.md)]

## <a name="update-a-content-file"></a>Aktualizowanie pliku zawartości
Połączone środowisko nie jest tylko o wprowadzenie kodu uruchamianego w Kubernetes - chodzi o co umożliwia szybkie i wielokrotnie powtarzane zobaczyć zmiany kodu zostały zastosowane w środowisku Kubernetes w chmurze.

1. Zlokalizuj plik `./public/index.html` i dokonać edycji HTML. Na przykład zmienić cień niebieski kolor tła strony:

```html
<body style="background-color: #95B9C7; margin-left:10px; margin-right:10px;">
```

2. Zapisz plik. Minut później, w oknie terminalu zobaczysz komunikat informujący, że plik w kontenerze uruchomionych został zaktualizowany.
1. Przejdź do przeglądarki i Odśwież stronę. Powinny pojawić się koloru aktualizacji.

Co się stało? Modyfikacje plików zawartości, takich jak HTML i CSS, nie wymagają procesu Node.js ponowne uruchomienie, dlatego aktywnego `vsce up` polecenia automatyczne synchronizowanie zmodyfikowanych plików zawartości bezpośrednio w kontenerze uruchomionego na platformie Azure, zapewniając szybką Zobacz sieci zmiany zawartości.

### <a name="test-from-a-mobile-device"></a>Test z urządzeń przenośnych
Po otwarciu aplikacji sieci web na urządzeniu przenośnym, można zauważyć, że interfejsu użytkownika nie jest poprawnie wyświetlany na urządzeniu mała.

Aby rozwiązać ten problem, dodamy `viewport` meta tag:
1. Otwórz plik `./public/index.html`
1. Dodaj `viewport` metatag w istniejących `head` elementu:

```html
<head>
    <!-- Add this line -->
    <meta name="viewport" content="width=device-width, initial-scale=1">
</head>
```

1. Zapisz plik.
1. Odśwież przeglądarki na urządzeniu. Powinna zostać wyświetlona poprawnie renderowana aplikacji sieci web. 

To jest przykładowy sposób niektórych problemów, po prostu nie zostaną znalezione dopóki test na urządzeniach, na których aplikacja jest przeznaczona do użycia. Ze środowiskiem połączone VS można szybko przejść w kodzie i weryfikacji żadnych zmian na urządzeniach docelowych.

## <a name="update-a-code-file"></a>Zaktualizuj plik kodu
Aktualizowanie kodu po stronie serwera plików wymaga nieco więcej pracy, ponieważ aplikacja Node.js musi zostać uruchomiony ponownie.

1. W oknie terminalu, naciśnij klawisz `Ctrl+C` (przestanie `vsce up`).
1. Otwórz plik kodu o nazwie `server.js`i edytować wiadomość hello usługi: 

```javascript
res.send('Hello from webfrontend running in Azure!');
```

3. Zapisz plik.
1. Uruchom `vsce up` w oknie terminalu. 

Odtwarza obraz kontenera i wdraża ponownie Helm wykresu. Załaduj ponownie stronę przeglądarki, aby zobaczyć wprowadzone zmiany kodu.


Ale nawet *szybszej metody* związane z opracowywaniem kod, który firma Microsoft będzie Eksplorowanie w następnej sekcji. 
> [!div class="nextstepaction"]
> [Debugowanie kontenera w Kubernetes](get-started-nodejs-04.md)
