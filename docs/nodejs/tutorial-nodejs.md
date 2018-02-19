---
title: "Wprowadzenie do środowiska Node.js w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/30/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-acquisition
ms.tgt_pltfrm: 
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: ghogen
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 1d91d46b20f82a1700c2d20639b3a8827c92bcb0
ms.sourcegitcommit: a07b789cc41ed72664f2c700c1f114476e7b0ddd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2018
---
# <a name="getting-started-with-nodejs-in-visual-studio"></a>Wprowadzenie do środowiska Node.js w programie Visual Studio
W tym samouczku do tworzenia aplikacji Node.js przy użyciu programu Visual Studio będzie utworzyć prostą aplikację sieci web Node.js, Dodaj kod, Eksploruj niektóre funkcje IDE i uruchomić aplikację. Jeśli program Visual Studio nie został już zainstalowany, zainstaluj go bezpłatnie [tutaj](http://www.visualstudio.com).  

## <a name="create-a-project"></a>Tworzenie projektu
Najpierw utworzysz projekt aplikacji sieci web Node.js.

1. Otwórz program Visual Studio 2017 r.  

2. Na pasku menu u góry wybierz **pliku** > **nowy** > **projektu...** .  

3. W **nowy projekt** okno dialogowe, w lewym okienku rozwiń **JavaScript**, a następnie wybierz **Node.js**. W środkowym okienku wybierz **Azure Node.js Express 4 aplikacji w warstwie podstawowa**, a następnie wybierz **OK**.   

     Jeśli nie widzisz **Azure Node.js Express 4 aplikacji w warstwie podstawowa** projektu szablonu, kliknij przycisk **Otwórz Instalator programu Visual Studio** łącze w lewym okienku **nowy projekt** okno dialogowe. Uruchamia Instalator programu Visual Studio. Wybierz **programowanie Node.js** obciążenia, a następnie wybierz **Modyfikuj**. 

    Visual Studio tworzy nowe rozwiązanie i otwiera projektu. **App.js** plik projektu zostanie otwarty w edytorze (lewe okienko). Jeśli nie masz doświadczenia z projektów i rozwiązań programu Visual Studio, zobacz [Szybki Start: program Visual Studio umożliwia tworzenie pierwszej aplikacji Node.js](../ide/quickstart-nodejs.md).

4. Jeśli nie masz środowisko uruchomieniowe Node.js już zainstalowany, zainstaluj go z [Node.js](https://nodejs.org/en/download/) witryny sieci Web.

    Ogólnie rzecz biorąc Visual Studio automatycznie wykrywa zainstalowane środowisko uruchomieniowe Node.js. Jeśli nie wykryje zainstalowanego środowiska uruchomieniowego można skonfigurować projektu do odwołania zainstalowanego środowiska uruchomieniowego.

## <a name="add-some-code"></a>Dodawanie kodu

1. W Eksploratorze rozwiązań (po prawej) otwórz folder widoków, a następnie otwórz index.pug.

1. Zamień zawartość następujących znaczników.

    ```js
    extends layout

    block content
      h1= title
      p Welcome to #{title}
      script.
        var f1 = function() { document.getElementById('myImage').src='#{data.item1}' }
      script.
        var f2 = function() { document.getElementById('myImage').src='#{data.item2}' }
      script.
        var f3 = function() { document.getElementById('myImage').src='#{data.item3}' }

      button(onclick='f1()') One!
      button(onclick='f2()') Two!
      button(onclick='f3()') Three!
      p
      a: img(id='myImage' height='200' width='200' src='')
    ```

1. Otwórz index.js w folderze trasy.

1. Dodaj następujący kod przed wywołaniem do `router.get`:

    ```js
    var getData = function () {
        var data = {
            'item1': 'http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-76.jpg',
            'item2': 'http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-77.jpg',
            'item3': 'http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-78.jpg'
        }
        return data;
    }
    ````

1. Zastąp `router.get` wywołania funkcji z następującym kodem:

    ```js
    router.get('/', function (req, res) {
        res.render('index', { title: 'Express', "data" });
    });
    ```

1. Po `data`, typ `: get` i IntelliSense wyświetli funkcja getData. Wybierz `getData`.

    ![Używanie IntelliSense](../nodejs/media/tutorial-nodejs-intellisense.png) 

1. Usuń przecinkiem (`,`) przed `"data"` i wyróżnianie składni zielony na wyrażeniu. Umieść kursor nad wyróżnianie składni.

    ![Błąd składni w widoku](../nodejs/media/tutorial-nodejs-syntax-checking.png) 

    Ostatni wiersz ten komunikat informuje, że interpreter języka JavaScript Oczekiwano przecinka (`,`).

1. Kliknij przycisk **listy błędów** kartę.

    Zobaczysz ostrzeżenie i opis wraz z liczbą nazwę pliku i wiersza.

    ![Widok listy błędów](../nodejs/media/tutorial-nodejs-error-list.png)

1. Naprawić kod przez dodanie przecinkiem (`,`) przed `"data"`.

## <a name="set-a-breakpoint"></a>Ustaw punkt przerwania

1. W index.js kliknij w lewym odstępu przed następujący wiersz kodu, aby ustawić punkt przerwania:

    `res.render('index', { title: 'Express', "data": getData() });`

    Punkty przerwania są najbardziej podstawowa i podstawowych funkcji niezawodne debugowanie. Punkt przerwania wskazuje, gdzie programu Visual Studio należy zawiesić kodu uruchomionej, aby móc przeglądać wartości zmiennych, ani zachowanie pamięci lub czy jest pobieranie uruchamiana gałąź kodu. 

    ![Ustaw punkt przerwania](../nodejs/media/tutorial-nodejs-set-breakpoint.png) 

## <a name="run-the-application"></a>Uruchamianie aplikacji

1. Wybierz cel debugowania na pasku narzędzi debugowania.

    ![Wybierz cel debugowania](../nodejs/media/tutorial-nodejs-deploy-target.png) 

1. Naciśnij klawisz **F5** (**debugowania** > **Rozpocznij debugowanie**) do uruchomienia aplikacji.

    Debuger wstrzymuje na ustawić punktu przerwania. Teraz możesz sprawdzić stan Twojej aplikacji.

1. Umieść kursor nad `getData` Aby wyświetlić jego właściwości w etykietki danych

    ![Sprawdź zmienne](../nodejs/media/tutorial-nodejs-inspect-variables.png)

1. Naciśnij klawisz **F5** (**debugowania** > **Kontynuuj**), aby kontynuować.

    Aplikacja zostanie otwarty w przeglądarce.

    W oknie przeglądarki zostanie wyświetlony "Express" jako tytuł i "Zapraszamy Express" w pierwszym akapicie.

1. Kliknij przyciski do wyświetlania różnych obrazów.

    ![Aplikacja uruchomiona w przeglądarce](../nodejs/media/tutorial-nodejs-running-in-browser.png)  

1. Otwórz okno interaktywne Node.js, wybierając **widoku** > **inne okna** > **okna interaktywnego Node.js**.

   ![Otwórz okno interaktywne Node.js](../nodejs/media/tutorial-nodejs-interactive-window.png)  

    Okno interaktywne obsługuje wszystko, co można zrobić w kodzie, łącznie z użyciem `require()` instrukcje. Kod na poniższym zrzucie ekranu definiuje zmienną i wyświetla lokalizację Node.js interpreter.

   ![Okno interaktywne node.js](../nodejs/media/tutorial-nodejs-interactive-window-example.png)  

1. Zamknij przeglądarkę sieci web.  

## <a name="optional-publish-to-azure-app-service"></a>(Opcjonalnie) Publikowanie w usłudze Azure App Service

1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **publikowania**.

   ![Publikowanie w usłudze Azure App Service](../nodejs/media/tutorial-nodejs-publish-to-azure.png)  

1. Wybierz **usługi Microsoft Azure App Service**.

    W **usługi aplikacji** okno dialogowe, możesz zalogować się do konta platformy Azure i nawiązać połączenia z istniejącej subskrypcji platformy Azure.

1. Wykonaj pozostałe kroki, aby wybrać subskrypcję, wybierz lub Utwórz grupę zasobów, wybierz lub Utwórz płaszczyzna usługi aplikacji, a następnie wykonaj kroki po wyświetleniu monitu o publikowanie na platformie Azure. Aby uzyskać szczegółowe instrukcje, zobacz [publikowanie witryny sieci Web Azure za pomocą narzędzia Web Deploy](https://github.com/Microsoft/nodejstools/wiki/Publish-to-Azure-Website-using-Web-Deploy).

1. **Dane wyjściowe** Pokazuje okno postęp wdrażania na platformie Azure.

    Na pomyślne wdrożenie aplikacji otwiera w przeglądarce uruchomionej w usłudze Azure App Service. Kliknij przycisk, aby wyświetlić obraz.

   ![Aplikacji uruchomionej w usłudze Azure App Service](../nodejs/media/tutorial-nodejs-running-in-azure.png)  

Gratulujemy wykonanie kroków tego samouczka!

## <a name="next-steps"></a>Następne kroki 

- Dowiedz się więcej o [narzędzia Node.js dla programu Visual Studio](https://github.com/Microsoft/nodejstools/wiki)  
- Dowiedz się więcej o [programu Visual Studio IDE](../ide/visual-studio-ide.md)  