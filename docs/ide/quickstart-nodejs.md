---
title: 'Szybki Start: Program Visual Studio umożliwia tworzenie pierwszej aplikacji Node.js'
description: W tym szybkiego startu możesz utworzyć aplikację Node.js w programie Visual Studio
ms.date: 06/27/2018
ms.prod: visual-studio-dev15
ms.technology: vs-nodejs
ms.topic: quickstart
ms.devlang: javascript
ms.assetid: b0e4ebed-1a01-41ef-aad1-4d8465ce5322
author: mikejo5000
ms.author: mikejo
manager: douge
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 664eb75fb8fe105058ef78470245500e5e835515
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089280"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-nodejs-app"></a>Szybki Start: Program Visual Studio umożliwia tworzenie pierwszej aplikacji Node.js

W tej 5 – 10 min wprowadzenie do programu Visual Studio zintegrowane środowisko programistyczne (IDE) utworzysz prostą aplikację sieci web Node.js. Jeśli nie została jeszcze zainstalowana Visual Studio 2017, przejdź do [program Visual Studio pobiera](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) stronę, aby zainstalować ją bezpłatnie.

## <a name="create-a-project"></a>Tworzenie projektu

Najpierw utworzysz projekt aplikacji sieci web Node.js.

1. Jeśli nie masz środowisko uruchomieniowe Node.js już zainstalowany, zainstaluj wersję LTS z [Node.js](https://nodejs.org/en/download/) witryny sieci Web.

    Ogólnie rzecz biorąc Visual Studio automatycznie wykrywa zainstalowane środowisko uruchomieniowe Node.js. Nie wykrywa zainstalowane środowisko uruchomieniowe, można skonfigurować do odwołania zainstalowanego środowiska uruchomieniowego na stronie właściwości projektu (po utworzeniu projektu kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **właściwości**).

1. Otwórz program Visual Studio 2017 r.

1. Na pasku menu u góry wybierz **pliku** > **nowy** > **projektu**.

1. W **nowy projekt** okno dialogowe, w lewym okienku rozwiń **JavaScript**, a następnie wybierz **Node.js**. W środkowym okienku wybierz **aplikacji sieci Web Node.js puste**, a następnie wybierz **OK**.

     Jeśli nie widzisz **aplikacji sieci Web Node.js puste** projektu szablonu, kliknij przycisk **Otwórz Instalator programu Visual Studio** łącze w lewym okienku **nowy projekt** okno dialogowe. Uruchamia Instalator programu Visual Studio. Wybierz **programowanie Node.js** obciążenia, a następnie wybierz **Modyfikuj**.

     ![Obciążenie node.js w Instalatorze programu VS](../ide/media/quickstart-nodejs-workload.png)

    Program Visual Studio tworzy i nowe rozwiązanie i otworzy w projekcie. *Server.js* zostanie otwarty w edytorze w okienku po lewej stronie.

## <a name="explore-the-ide"></a>Eksploruj IDE

1. Spójrz na **Eksploratora rozwiązań** w okienku po prawej stronie.

   ![Eksplorator rozwiązań](../ide/media/quickstart-nodejs-solution-explorer.png)

   - Wyróżnione czcionką pogrubioną jest projekt używa tej nazwy należy nadać w **nowy projekt** okno dialogowe. Na dysku, ten projekt jest reprezentowana przez *.njsproj* pliku w folderze projektu.

   - Na najwyższym poziomie to rozwiązanie, które domyślnie ma taką samą nazwę jak projektu. Rozwiązanie reprezentowane przez *.sln* plików na dysku, to kontener dla jednego lub więcej projektów powiązanych.

   - Węzeł npm zawiera wszystkie pakiety zainstalowane npm. Możesz kliknąć prawym przyciskiem myszy węzeł npm wyszukiwanie i instalowanie pakietów npm za pomocą okna dialogowego.

1. Jeśli chcesz zainstalować pakiet npm lub node.js polecenia z wiersza polecenia, kliknij prawym przyciskiem myszy węzeł projektu i wybierz pozycję **Otwórz wiersz polecenia w tym miejscu**.

   ![Wiersz polecenia node.js](../ide/media/quickstart-nodejs-command-prompt.png)

1. W *server.js* plik w edytorze (lewe okienko), wybierz `http.createServer` , a następnie naciśnij klawisz **F12** lub wybierz **przejdź do definicji** z menu kontekstowego (kliknij prawym przyciskiem myszy). To polecenie powoduje przejście do definicji `createServer` działać w *index.d.ts*.

   ![Menu kontekstowe przejdź do definicji](../ide/media/quickstart-nodejs-gotodefinition.png)

1. Otrzymano do *server.js*, następnie umieść kursor na końcu ciągu w tym wierszu kodu, `res.end('Hello World\n');`i zmodyfikuj go, aby wygląda następująco:

    `res.end('Hello World\n' + res.connection.`

    Należy wpisać `connection.`, IntelliSense udostępnia opcje umożliwiające automatyczne zakończenia kod.

   ![Funkcja automatycznego uzupełniania IntelliSense](../ide/media/quickstart-nodejs-intellisense.png)

1. Wybierz **port lokalny**, a następnie wpisz `);` do wykonania instrukcji, dzięki czemu wygląda następująco:

    `res.end('Hello World\n' + res.connection.localPort);`

## <a name="run-the-application"></a>Uruchamianie aplikacji

1. Naciśnij klawisz **Ctrl**+**F5** (lub **Debuguj > Uruchom bez debugowania**) do uruchomienia aplikacji. Aplikacja zostanie otwarty w przeglądarce.

1. W oknie przeglądarki pojawi się "Hello World" oraz numer portu lokalnego.

1. Zamknij przeglądarkę sieci web.

Gratulujemy Kończenie pracy tego przewodnika Szybki Start, w którym został uruchomiony z programu Visual Studio IDE i Node.js. Jeśli chcesz delve głębiej do jego możliwości, kontynuuj samouczek w **samouczki** sekcji spisu treści.

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Wdrażanie aplikacji w usłudze Azure App Service](..//deployment/quickstart-deploy-to-azure.md)

- [Samouczek środowiska Node.js i Express](../nodejs/tutorial-nodejs.md)
- [Samouczek środowiska Node.js i bibliotece React.](../nodejs/tutorial-nodejs-with-react-and-jsx.md)