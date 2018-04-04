---
title: Tworzenie aplikacji Node.js i Express — Visual Studio | Dokumentacja firmy Microsoft
description: W tym samouczku zostanie utworzona aplikacja Node.js i Express programu Visual Studio
ms.custom: ''
ms.date: 03/13/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: ghogen
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: f7d0774753178c9cb0dbcae1800da6b00ab02a0e
ms.sourcegitcommit: efd8c8e0a9ba515d47efcc7bd370eaaf4771b5bb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/03/2018
---
# <a name="tutorial-create-a-nodejs-and-express-app-in-visual-studio"></a>Samouczek: Tworzenie środowiska Node.js i Express aplikacji w programie Visual Studio
Ten samouczek dotyczący tworzenia Visual Studio przy użyciu środowiska Node.js i Express służy do utworzyć prostą aplikację sieci web Node.js, Dodaj kod, Eksploruj niektóre funkcje IDE i uruchomić aplikację. Jeśli program Visual Studio nie został już zainstalowany, zainstaluj go bezpłatnie [tutaj](http://www.visualstudio.com).  

Z tego samouczka, dowiesz się, jak:
> [!div class="checklist"]
> * Tworzenie projektu środowiska Node.js
> * Dodawanie kodu
> * Używanie IntelliSense
> * Uruchamianie aplikacji
> * Trafiony punkt przerwania

## <a name="prerequisites"></a>Wymagania wstępne

* Musi mieć zainstalowanego programu Visual Studio i obciążenia programowanie Node.js.

    Jeśli program Visual Studio nie został już zainstalowany, zainstaluj go bezpłatnie [tutaj](http://www.visualstudio.com).

    Jeśli musisz zainstalować obciążenie, ale jeszcze programu Visual Studio, kliknij przycisk **Otwórz Instalator programu Visual Studio** łącze w lewym okienku **nowy projekt** okno dialogowe. Uruchamia Instalator programu Visual Studio. Wybierz **programowanie Node.js** obciążenia, a następnie wybierz **Modyfikuj**.

* Musi mieć zainstalowane środowisko uruchomieniowe Node.js.

    Jeśli użytkownik nie jest zainstalowany, zainstaluj wersję LTS z [Node.js](https://nodejs.org/en/download/) witryny sieci Web. Ogólnie rzecz biorąc Visual Studio automatycznie wykrywa zainstalowane środowisko uruchomieniowe Node.js. Nie wykrywa zainstalowane środowisko uruchomieniowe, można skonfigurować do odwołania zainstalowanego środowiska uruchomieniowego na stronie właściwości projektu (po utworzeniu projektu kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **właściwości**).

    W tym samouczku przetestowano za pomocą języka Node.js 8.10.0.

## <a name="create-a-project"></a>Tworzenie projektu
Najpierw utworzysz projekt aplikacji sieci web Node.js.

1. Otwórz program Visual Studio 2017 r.  

1. Na pasku menu u góry wybierz **pliku** > **nowy** > **projektu...** .  

1. W **nowy projekt** okno dialogowe, w lewym okienku rozwiń **JavaScript**, a następnie wybierz pozycję **Node.js**. W środkowym okienku wybierz **Azure Node.js Express 4 aplikacji w warstwie podstawowa**, a następnie wybierz pozycję **OK**.   

     Jeśli nie widzisz **Azure Node.js Express 4 aplikacji w warstwie podstawowa** szablon projektu, należy zainstalować **programowanie Node.js** obciążenia pierwszego. 

    Visual Studio tworzy nowe rozwiązanie i otwiera projektu. *App.js* plik projektu zostanie otwarty w edytorze (lewe okienko).

    - Wyróżnione czcionką pogrubioną jest projekt używa tej nazwy należy nadać w **nowy projekt** okno dialogowe. W systemie plików, ten projekt jest reprezentowany przez *.njsproj* pliku w folderze projektu. Można ustawić właściwości i zmiennych środowiskowych skojarzony z projektem, klikając prawym przyciskiem myszy projekt i wybierając pozycję **właściwości**. Możesz to zrobić dwustronną komunikację z innymi narzędziami programistycznymi, ponieważ plik projektu nie wprowadzać zmian niestandardowe źródło projektu Node.js.

    - Na najwyższym poziomie to rozwiązanie, które domyślnie ma taką samą nazwę jak projektu. Rozwiązanie reprezentowane przez *.sln* plików na dysku, to kontener dla jednego lub więcej projektów powiązanych.

    - Węzeł npm zawiera wszystkie pakiety zainstalowane npm. Możesz kliknąć prawym przyciskiem myszy węzeł npm wyszukiwanie i instalowanie pakietów npm za pomocą okna dialogowego.

    - Pliki takie jak projektu *app.js* wyświetlane w węźle projektu. *App.js* jest plikiem uruchomienia projektu.

1. Otwórz **npm** węzła i upewnij się, że wszystkie pakiety npm wymagane są obecne.

    Wszelkie braku (ikona wykrzyknika), należy kliknąć prawym przyciskiem myszy **npm** węzeł i wybierz polecenie **Zainstaluj brakujące pakietów npm**.

## <a name="add-some-code"></a>Dodawanie kodu

1. W Eksploratorze rozwiązań (po prawej), otwórz folder widoków, a następnie otwórz *index.pug*.

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

1. Otwórz w folderze tras *index.js*.

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

    Występuje błąd w wierszu kodu zawierającego `res.render`. Potrzebujemy go rozwiązać, zanim będzie można uruchomić aplikacji. Firma Microsoft Napraw błąd w następnej sekcji.

## <a name="use-intellisense"></a>Używanie IntelliSense

1. W *index.js*, przejdź do wiersza zawierającego kod `res.render`.

1. Po `data` ciągu, wpisz `: get` i IntelliSense zostanie wyświetlona `getData` funkcji. Wybierz `getData`.

    ![Używanie IntelliSense](../nodejs/media/tutorial-nodejs-intellisense.png) 

1. Usuń przecinkiem (`,`) przed `"data"` i wyróżnianie składni zielony na wyrażeniu. Umieść kursor nad wyróżnianie składni.

    ![Błąd składni w widoku](../nodejs/media/tutorial-nodejs-syntax-checking.png) 

    Ostatni wiersz ten komunikat informuje, że interpreter języka JavaScript Oczekiwano przecinka (`,`).

1. Kliknij przycisk **listy błędów** kartę.

    Zobaczysz ostrzeżenie i opis wraz z liczbą nazwę pliku i wiersza.

    ![Widok listy błędów](../nodejs/media/tutorial-nodejs-error-list.png)

1. Naprawić kod przez dodanie przecinkiem (`,`) przed `"data"`.

## <a name="set-a-breakpoint"></a>Ustaw punkt przerwania

1. W *index.js*, kliknij w lewym odstępu przed następujący wiersz kodu, aby ustawić punkt przerwania:

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

W tym samouczku przedstawiono sposób tworzenia i uruchamiania aplikacji Node.js przy użyciu Express i trafiony punkt przerwania korzystanie z debugera.

> [!div class="nextstepaction"]
> [Narzędzia Node.js dla programu Visual Studio](https://github.com/Microsoft/nodejstools)