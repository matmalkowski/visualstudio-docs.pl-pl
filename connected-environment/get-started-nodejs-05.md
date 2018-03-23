---
title: Utwórz Środowisko deweloperskie Node.js z kontenerów przy użyciu Kubernetes w chmurze — krok 5 - wywołanie innego kontenera | Dokumentacja firmy Microsoft
author: johnsta
ms.author: johnsta
ms.date: 02/20/2018
ms.topic: get-started-article
ms.technology: vsce-kubernetes
description: Szybkie opracowywanie Kubernetes z kontenerów i mikrousług na platformie Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, containers
manager: ghogen
ms.openlocfilehash: 5b7065714475ee700fb1a04502a50a4fce0b0e8d
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2018
---
# <a name="get-started-on-connected-environment-with-nodejs"></a>Rozpoczynanie pracy w środowisku połączonych za pomocą języka Node.js

Poprzedni krok: [kontenera w Kubernetes debugowania](get-started-nodejs-04.md)

W tej sekcji zamierzamy utworzyć drugi usługę `mywebapi`i mieć `webfrontend` wywołać ją. Każda usługa będzie działać w osobnych kontenerów. Firma Microsoft będzie następnie debugowania za pośrednictwem obydwu kontenerów.

![](media/multi-container.png)

## <a name="open-sample-code-for-mywebapi"></a>Otwórz przykładowy kod *mywebapi*
Ma już przykładowy kod `mywebapi` tego przewodnika w folderze o nazwie `vsce/samples` (Jeśli nie, przejdź do https://github.com/Azure/vsce i wybierz **klonowania lub pobrać** pobrać repozytorium GitHub.) Kod dla tej sekcji znajduje się w `vsce/samples/nodejs/getting-started/mywebapi`.

## <a name="run-mywebapi"></a>Uruchom *mywebapi*
1. Otwórz folder `mywebapi` w *osobnym oknie kodzie VS*.
1. Naciśnij klawisz F5 i poczekaj, aż usługi do tworzenia i wdrażania. Użytkownik wie, że jest gotowy, gdy zostanie wyświetlony pasek debugowania kodu programu VS.
1. Zwróć uwagę adresu URL punktu końcowego, ekran będzie wyglądać podobnie jak http://localhost:\<numer_portu\>. **Porada: Kodzie VS paska stanu spowoduje wyświetlenie aktywne adresu URL.** Wydaje się, jak kontenera działa lokalnie, ale faktycznie jest uruchomiona w naszym środowisku programistycznym na platformie Azure. Przyczyna adres hosta lokalnego jest ponieważ `mywebapi` nie ma zdefiniowanych żadnych publicznych punktów końcowych i można uzyskać tylko z wewnątrz Kubernetes wystąpienia. Dla wygody użytkownika i ułatwienia interakcji z usługą prywatnych z komputera lokalnego połączone środowiska tworzy tymczasowy tunelu SSH w kontenerze działające na platformie Azure.
1. Gdy `mywebapi` jest gotowe, Otwórz w przeglądarce adres hosta lokalnego. Powinny pojawić się odpowiedzi z `mywebapi` usługi ("Witaj, z mywebapi").


## <a name="make-a-request-from-webfrontend-to-mywebapi"></a>Tworzenie żądania z *webfrontend* do *mywebapi*
Teraz napiszmy kod `webfrontend` który żąda `mywebapi`.
1. Przełącz do okna kodzie VS `webfrontend`.
1. Dodaj następujące wiersze kodu w górnej części `server.js`:
```javascript
var request = require('request');
var propagateHeaders = require('./propagateHeaders');
```

3. *Zastąp* kod `/api` obsługi GET. Podczas obsługi żądania, z kolei nawiązuje połączenie `mywebapi`, a następnie zwraca wyniki z obu usług.

```javascript
app.get('/api', function (req, res) {
    request({
        uri: 'http://mywebapi',
        headers: propagateHeaders.from(req) // propagate headers to outgoing requests
    }, function (error, response, body) {
        res.send('Hello from webfrontend and ' + body);
    });
});
```

Należy zwrócić uwagę, jak odnajdywanie usługi DNS Kubernetes jest stosowane do odwoływania się do usługi, ponieważ `http://mywebapi`. **Kod w naszym środowisku programistycznym działa tak samo zostanie uruchomiony w środowisku produkcyjnym**.

W powyższym przykładzie kodu wykorzystuje moduł pomocnika o nazwie `propagateHeaders`. Tego pomocnika zostało dodane do katalogu z kodem w momencie uruchomienia `vsce init`. `propagateHeaders.from()` Funkcja propaguje określonych nagłówków z istniejącego protokołu http. Obiekt IncomingMessage w obiekcie nagłówki dla żądania wychodzącego. Zajmiemy się później, jak to ułatwia efektywniej środowisko programistyczne w scenariuszach zespołu.


## <a name="debug-across-multiple-services"></a>Debugowanie w wielu usługach
1. W tym momencie `mywebapi` powinny być nadal uruchomione w debugerze. Jeśli nie, naciśnij klawisz F5 w `mywebapi` projektu.
1. Ustaw punkt przerwania w domyślnym GET `/` obsługi.
1. W `webfrontend` projektu, należy ustawić punkt przerwania tuż przed wysłaniem żądania GET do `http://mywebapi`.
1. Naciśnij klawisz F5 w `webfrontend` projektu.
1. Otwórz aplikację sieci web i wykonywać krokowo kodu w obu usług. Aplikacja sieci web powinien być wyświetlany komunikat połączonych przez dwie usługi: "Hello webfrontend i Hello z mywebapi".


Dobra robota! Masz teraz aplikacji wielu kontenera, w którym każdego kontenera mogą być opracowane i wdrażane pojedynczo.

> [!div class="nextstepaction"]
> [Dowiedz się więcej o programowanie zespołowe](get-started-nodejs-06.md)
