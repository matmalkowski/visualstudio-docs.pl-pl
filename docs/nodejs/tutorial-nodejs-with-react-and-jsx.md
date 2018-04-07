---
title: Tworzenie aplikacji Node.js i platformy React — Visual Studio | Dokumentacja firmy Microsoft
description: W tym samouczku zostanie utworzona aplikacja Node.js i platformy React w programie Visual Studio
ms.custom: mvc
ms.date: 02/19/2018
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
ms.openlocfilehash: f99b1bef93fcbe968f23f0bb63653d825235385e
ms.sourcegitcommit: 3724338a5da5a6d75ba00452b0a607388b93ed0c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2018
---
# <a name="tutorial-create-a-nodejs-and-react-app-in-visual-studio"></a>Samouczek: Tworzenie aplikacji Node.js i platformy React w programie Visual Studio
Program Visual Studio umożliwia łatwe tworzenie projektu środowiska Node.js i korzystać z funkcji IntelliSense i innych wbudowanych funkcji, które obsługują Node.js. W tym samouczku dla programu Visual Studio utworzeniu projektu aplikacji sieci web Node.js za pomocą szablonu Visual Studio. Następnie można utworzyć prostej aplikacji przy użyciu platformy React. 

Z tego samouczka, dowiesz się, jak:
> [!div class="checklist"]
> * Tworzenie projektu środowiska Node.js
> * Dodawanie pakietów npm
> * Dodaj kod platformy React do aplikacji
> * Transpile JSX
> * Dołącz debuger

## <a name="prerequisites"></a>Wymagania wstępne

* Musi mieć zainstalowanego programu Visual Studio i obciążenia programowanie Node.js.

    Jeśli program Visual Studio nie został już zainstalowany, zainstaluj go bezpłatnie [tutaj](http://www.visualstudio.com).

    Jeśli musisz zainstalować obciążenie, ale jeszcze programu Visual Studio, kliknij przycisk **Otwórz Instalator programu Visual Studio** łącze w lewym okienku **nowy projekt** okno dialogowe. Uruchamia Instalator programu Visual Studio. Wybierz **programowanie Node.js** obciążenia, a następnie wybierz **Modyfikuj**.

* Musi mieć zainstalowane środowisko uruchomieniowe Node.js.

    Jeśli użytkownik nie jest zainstalowany, zainstaluj wersję LTS z [Node.js](https://nodejs.org/en/download/) witryny sieci Web. Ogólnie rzecz biorąc Visual Studio automatycznie wykrywa zainstalowane środowisko uruchomieniowe Node.js. Nie wykrywa zainstalowane środowisko uruchomieniowe, można skonfigurować do odwołania zainstalowanego środowiska uruchomieniowego na stronie właściwości projektu (po utworzeniu projektu kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **właściwości**).

    W tym samouczku przetestowano z wersją 8.9.4.

## <a name="create-a-project"></a>Tworzenie projektu
Najpierw utwórz projekt aplikacji sieci web Node.js.

1. Otwórz program Visual Studio 2017 r.  

1. Na pasku menu u góry wybierz **pliku** > **nowy** > **projektu...** .  

1. W **nowy projekt** okno dialogowe, w lewym okienku rozwiń **JavaScript**, a następnie wybierz pozycję **Node.js**. W środkowym okienku wybierz **pusta aplikacja sieci Web Node.js**, wpisz nazwę **NodejsWebAppBlank**, a następnie wybierz pozycję **OK**.   

     Jeśli nie widzisz **pusta aplikacja sieci Web Node.js** szablon projektu, należy najpierw zainstalować obciążenia programowanie Node.js. 

    Visual Studio tworzy nowe rozwiązanie i otwiera projektu.

    ![Node.js projekt w Eksploratorze rozwiązań](../nodejs/media/tutorial-nodejs-react-project-structure.png)  

    - Wyróżnione czcionką pogrubioną jest projekt używa tej nazwy należy nadać w **nowy projekt** okno dialogowe. W systemie plików, ten projekt jest reprezentowany przez *.njsproj* pliku w folderze projektu. Można ustawić właściwości i zmiennych środowiskowych skojarzony z projektem, klikając prawym przyciskiem myszy projekt i wybierając pozycję **właściwości**. Możesz to zrobić dwustronną komunikację z innymi narzędziami programistycznymi, ponieważ plik projektu nie wprowadzać zmian niestandardowe źródło projektu Node.js.

    - Na najwyższym poziomie to rozwiązanie, które domyślnie ma taką samą nazwę jak projektu. Rozwiązanie reprezentowane przez *.sln* plików na dysku, to kontener dla jednego lub więcej projektów powiązanych.

    - Węzeł npm zawiera wszystkie pakiety zainstalowane npm. Możesz kliknąć prawym przyciskiem myszy węzeł npm wyszukiwanie i instalowanie pakietów npm za pomocą okna dialogowego.

    - Pliki takie jak projektu *server.js* wyświetlane w węźle projektu. *Server.js* jest plikiem uruchomienia projektu.

## <a name="add-npm-packages"></a>Dodawanie pakietów npm

Ta aplikacja wymaga liczba moduły npm by działała poprawnie.

* Reakcji
* dom bibliotece react.
* Express
* ścieżka
* ts-loader
* typescript
* webpack
* webpack-cli

1. W Eksploratorze rozwiązań (po prawej) kliknij prawym przyciskiem myszy **npm** węzeł projektu i wybierz polecenie **zainstalować nowych pakietów npm**.

    W **zainstalować nowych pakietów npm** okno dialogowe, są dostępne do zainstalowania najnowszej wersji pakietu lub określ wersję. Jeśli zostanie zainstalowana bieżąca wersja te pakiety, ale wystąpiły nieoczekiwane błędy później, może być konieczne zainstalowanie wersji pakietu dokładnie opisane w dalszej części następujące kroki.

1. W **zainstalować nowych pakietów npm** okno dialogowe Wyszukiwanie pakietu platformy react, a następnie kliknij przycisk **zainstaluj pakiet** go zainstalować.

    ![Instalowanie pakietów npm](../nodejs/media/tutorial-nodejs-react-install-packages.png)

    **Dane wyjściowe** Pokazuje okno postęp instalacji pakietu. Po zainstalowaniu pakietu jest wyświetlany w obszarze **npm** węzła.

    Projektu *package.json* plik został zaktualizowany przy użyciu nowych informacji pakietu, łącznie z wersją pakietu.

1. Zamiast przy użyciu interfejsu użytkownika do wyszukiwania i Dodaj pozostałe pakiety pojedynczo, wklej następujący kod do pliku package.json. Zastąp `dependencies` sekcji o tym kodzie:

    ```js
    "dependencies": {
      "express": "4.16.2",
      "path": "0.12.7",
      "react": "16.2.0",
      "react-dom": "16.2.0",
      "ts-loader": "4.0.1",
      "typescript": "2.7.2",
      "webpack": "4.1.1",
      "webpack-cli": "2.0.11"
    }
    ```

1. Kliknij prawym przyciskiem myszy **npm** węzeł projektu i wybierz polecenie **Zainstaluj brakujące pakietów npm**.

    **Dane wyjściowe** okno wyświetla postęp instalowania pakietów.

    Poniżej przedstawiono moduły npm, w jakiej występują w Eksploratorze rozwiązań po ich zainstalowaniu.

    ![pakietów npm](../nodejs/media/tutorial-nodejs-react-npm-modules.png) 

    > [!NOTE]
    > Jeśli chcesz wykonać instalację pakietów npm przy użyciu wiersza polecenia, kliknij prawym przyciskiem myszy węzeł projektu i wybierz pozycję **Otwórz wiersz polecenia w tym miejscu**. Należy zainstalować pakiety standardowe polecenia Node.js.

## <a name="add-project-files"></a>Dodaj pliki projektu

Te kroki możesz dodać cztery nowe pliki do projektu.

* *app.tsx*
* *webpack-config.js*
* *index.html*
* *tsconfig.json*

Dla tej aplikacji proste dodawane są pliki projektu w katalogu głównym projektu. (W przypadku większości aplikacji zazwyczaj Dodaj pliki do podfolderów i odpowiednio zmienić odwołuje się do ścieżki względnej.)

1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt **NodejsWebAppBlank** i wybierz polecenie **Dodaj** > **nowy element**.

1. W **Dodaj nowy element** oknie dialogowym wybierz **plików TypeScript JSX**, wpisz nazwę *app.tsx*i kliknij przycisk **OK**.

1. Powtórz te kroki, aby dodać *webpack config.js*.

1. Powtórz te same kroki, aby dodać *index.html* do projektu. Zamiast pliku JavaScript, wybierz **plik HTML**.

1. Powtórz te same kroki, aby dodać *tsconfig.json* do projektu. Zamiast pliku JavaScript, wybierz **pliku konfiguracji JSON TypeScript**.

## <a name="add-app-code"></a>Dodaj kod aplikacji

1. Otwórz *server.js* i Zastąp kod następującym kodem:

    ```javascript
    'use strict';
    var path = require('path');
    var express = require('express');

    var app = express();

    var staticPath = path.join(__dirname, '/');
    app.use(express.static(staticPath));

    // Allows you to set port in the project properties.
    app.set('port', process.env.PORT || 3000);

    var server = app.listen(app.get('port'), function() {
        console.log('listening');
    });
    ```

   Poprzedni kod używa Express, można uruchomić jako serwer aplikacji sieci web Node.js. Ten kod ustawia port numer portu skonfigurowane we właściwościach projektu (domyślnie port skonfigurowano 1337 we właściwościach). Aby otworzyć okno właściwości projektu, kliknij prawym przyciskiem myszy projekt w Eksploratorze rozwiązań i wybierz polecenie **właściwości**.

1. Otwórz *app.tsx* i Dodaj następujący kod:

    ```javascript
    declare var require: any
    
    var React = require('react');
    var ReactDOM = require('react-dom');

    class Hello extends React.Component {
        render() {
            return (
                <h1>Welcome to React!!</h1>
            );
        }
    }

    ReactDOM.render(<Hello />, document.getElementById('root'));
    ```

    Poprzedni kod używa składnia JSX i platformy React do wyświetlania komunikatu proste.

1. Otwórz *index.html* i Zastąp **treści** sekcji z następującym kodem:

    ```html
    <body>
        <div id="root"></div>
        <!-- scripts -->
        <script src="./dist/app-bundle.js"></script>
    </body>
    ```

    Ładowania tej strony HTML *bundle.js aplikacji*, zawierającą transpiled kodu JSX i platformy React dla zwykły JavaScript. Obecnie *bundle.js aplikacji* plik jest pusty. W następnej sekcji możesz skonfigurować opcje do transpile kod.

## <a name="configure-webpack-and-typescript-compiler-options"></a>Skonfiguruj opcje kompilatora języka TypeScript i webpack

W poprzednich krokach, możesz dodać *webpack config.js* do projektu. Następnie możesz dodać kod konfiguracji webpack. Doda konfigurację webpack proste, która określa plik wejściowy (*app.tsx*) i pliku wyjściowego (*bundle.js aplikacji*) dla tworzenie pakietów i transpiling JSX w zwykłym kodzie JavaScript. Dla transpiling możesz także skonfigurować niektóre opcje kompilatora języka TypeScript. Ten kod jest podstawową konfigurację, która ma pełnić rolę wprowadzenie do webpack i kompilatora języka TypeScript.

1. W Eksploratorze rozwiązań Otwórz *webpack config.js* i Dodaj następujący kod.

    ```json
    module.exports = {
        devtool: 'source-map',
        entry: "./app.tsx",
        mode: "development",
        output: {
            filename: "./app-bundle.js"
        },
        resolve: {
            extensions: ['.Webpack.js', '.web.js', '.ts', '.js', '.jsx', '.tsx']
        },
        module: {
            rules: [
                {
                    test: /\.tsx$/,
                    exclude: /(node_modules|bower_components)/,
                    use: {
                        loader: 'ts-loader'
                    }
                }
            ]
        }
    }
    ```

    Kod konfiguracji webpack nakazuje Webpack do używania języka TypeScript, moduł ładujący transpile JSX.

1. Otwórz tsconfig.json i Dodaj następujący kod, który określa opcje kompilatora języka TypeScript:

    ```json
    {
      "compilerOptions": {
        "noImplicitAny": false,
        "module": "commonjs",
        "noEmitOnError": true,
        "removeComments": false,
        "sourceMap": true,
        "target": "es5",
        "jsx": "react"
      },
      "exclude": [
        "node_modules"
      ],
      "files": [
        "app.tsx"
      ]
    }
    ```

    App.tsx jest określony jako plik źródłowy.

## <a name="transpile-the-jsx"></a>Transpile JSX

1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Otwórz wiersz polecenia w tym miejscu**.

1. W wierszu polecenia wpisz następujące polecenie:

    `node_modules\.bin\webpack app.tsx --config webpack-config.js`

    W oknie wiersza polecenia wyświetlane wynik.

    ![Uruchom webpack](../nodejs/media/tutorial-nodejs-react-run-webpack.png) 

    Jeśli są wyświetlane błędy zamiast powyższych danych wyjściowych, należy rozwiązać problemy przed aplikacja będzie działać. Jeśli Twojej wersji pakietu npm są inne niż wersje przedstawiona w tym samouczku, który jest źródłem błędów. Jednym ze sposobów na błędy jest umożliwia dokładną wersję wyświetlane we wcześniejszych krokach. Ponadto jeśli co najmniej jeden z tych wersji pakietu jest przestarzała i powoduje błąd, może być konieczne Zainstaluj nowszą wersję, aby naprawić błędy.

1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Dodaj** > **istniejący Folder**, a następnie wybierz *dist* folder i kliknij przycisk  **Wybierz Folder**.

    Dodaje programu Visual Studio *dist* folderu do projektu, który zawiera *bundle.js aplikacji* i *bundle.js.map aplikacji*.

1. Otwórz *bundle.js aplikacji* wyświetlić transpiled kodu JavaScript.

1. Jeśli zostanie wyświetlony monit, aby ponownie załadować zewnętrznie zmodyfikowane pliki, kliknij przycisk **tak, aby wszystkie**.

    ![Ładowanie plików zmodyfikowanych](../nodejs/media/tutorial-nodejs-react-reload-files.png) 

Zawsze należy wprowadzić zmiany w *app.tsx*, należy ponownie uruchomić polecenie webpack.

## <a name="run-the-app"></a>Uruchamianie aplikacji

1. Upewnij się, że Chrome jest wybrany jako bieżącą lokalizację docelową debugowania.

    ![Wybierz Chrome jako cel debugowania](../nodejs/media/tutorial-nodejs-react-debug-target.png)  

1. Aby uruchomić aplikację, naciśnij klawisz **F5** (**debugowania** > **Rozpocznij debugowanie**) lub przycisku zieloną strzałkę.

    Zostanie otwarte okno konsoli Node.js pokazujący portu, na którym nasłuchuje debugera.

    Visual Studio uruchomienia aplikacji, uruchamiając plik uruchamiania *server.js*.

    ![Uruchom platformy React w przeglądarce](../nodejs/media/tutorial-nodejs-react-running-react.png) 

1. Zamknij okno przeglądarki.

1. Zamknij okno konsoli.

## <a name="set-a-breakpoint-and-run-the-app"></a>Ustaw punkt przerwania i uruchamianie aplikacji

1. W *server.js*, kliknij odstępu na lewo od `staticPath` deklaracji można ustawić punktu przerwania:

    ![Ustaw punkt przerwania](../nodejs/media/tutorial-nodejs-react-set-breakpoint.png) 

    Punkty przerwania są najbardziej podstawowa i podstawowych funkcji niezawodne debugowanie. Punkt przerwania wskazuje, gdzie programu Visual Studio należy zawiesić kodu uruchomionej, aby móc przeglądać wartości zmiennych, ani zachowanie pamięci lub czy jest pobieranie uruchamiana gałąź kodu. 

1. Aby uruchomić aplikację, naciśnij klawisz **F5** (**debugowania** > **Rozpocznij debugowanie**).

    Debuger zatrzymuje się na punkt przerwania zestawu (bieżącej instrukcji oznaczone kolorem żółtym). Teraz, możesz sprawdzić stan Twojej aplikacji, ustawiając kursor nad zmiennych, które aktualnie znajdują się w zakresie, za pomocą debugera systemu windows, takich jak **zmiennych lokalnych** i **czujki** systemu windows.

1. Naciśnij klawisz **F5** kontynuowanie aplikacji.

1. Jeśli chcesz użyć narzędzi deweloperskich programu Chrome, naciśnij klawisz **F12**. Te narzędzia do badania modelu DOM i interakcję z aplikacji przy użyciu konsoli języka JavaScript.

1. Zamknij przeglądarkę sieci web i konsoli.

## <a name="set-and-hit-a-breakpoint-in-the-client-side-react-code"></a>Ustaw i trafiony punkt przerwania w kodzie po stronie klienta w bibliotece React.

W poprzedniej sekcji debuger jest dołączony do kodu Node.js po stronie serwera. Aby dołączyć debuger za pomocą programu Visual Studio i kliknij punkty przerwania w kodzie platformy React po stronie klienta, debuger musi pomoc, aby zidentyfikować korygowania procesu. W tym miejscu jest jedną z metod aby je włączyć.

1. Zamknij wszystkie okna przeglądarki Chrome.

1. Otwórz **Uruchom** polecenia systemu Windows **Start** przycisk (kliknij prawym przyciskiem myszy i wybierz polecenie **Uruchom**) i wprowadź następujące polecenie:

    `chrome.exe --remote-debugging-port=9222`

    Spowoduje to uruchomienie programu Chrome z włączonym debugowaniem.

1. Przełącz się do programu Visual Studio i ustaw punkt przerwania *bundle.js aplikacji* kod w `render()` funkcji, jak pokazano na poniższej ilustracji:

    ![Ustaw punkt przerwania](../nodejs/media/tutorial-nodejs-react-set-breakpoint-client-code.png) 

1. Chrome wybrany jako cel debugowania w programie Visual Studio, naciśnij **Ctrl + F5** (**debugowania** > **uruchomić bez debugowania**) aby uruchomić aplikację w przeglądarce.

    Aplikacja otwiera nową kartę przeglądarki.

1. Wybierz **debugowania** > **dołączyć do procesu**.

1. W **dołączyć do procesu** oknie dialogowym wybierz **kod Webkit** w **dołączyć do** wpisz **chrome** w polu filtru do filtrowania wyniki wyszukiwania.

1. Wybierz proces Chrome o właściwy host port (1337 w tym przykładzie), a następnie kliknij przycisk **Attach**.

    ![Dołączanie do procesu](../nodejs/media/tutorial-nodejs-react-attach-to-process.png) 

    Wiadomo, że debuger został dołączony poprawnie, gdy konsoli JavaScript i narzędzia DOM Explorer Otwórz w programie Visual Studio. Te narzędzia debugowania są podobne do narzędzia F12 Edge i przeglądarki Chrome Developer Tools.

    > [!NOTE]
    > Jeśli nie dołączyć debuger i zostanie wyświetlony komunikat "nie można dołączyć do procesu. Operacja jest niedozwolona w bieżącym stanie." następnie użyj Menedżera zadań, aby zamknąć wszystkie wystąpienia przeglądarki Chrome przed rozpoczęciem Chrome w trybie debugowania. Rozszerzenia programu Chrome mogą być uruchomione i uniemożliwia trybu pełnego debugowania.

1. Ponieważ kodu przy użyciu punktu przerwania już wykonane, Odśwież stronę przeglądarki trafienie punktu przerwania.

    Podczas wstrzymaniu w debugerze, można sprawdzić stan Twojej aplikacji kursora myszy nad zmienne i korzystanie z debugera systemu windows. Debuger może przejść przez krokowe wykonywanie kodu (**F5**, **F10**, i **F11**).

    Można napotkać punkt przerwania w jednej *bundle.js aplikacji* lub lokalizacji zamapowanych *app.tsx*w zależności od stanu Twojego środowiska i przeglądarki. W obu przypadkach można wykonywać krokowo kodu i Sprawdź zmienne.

    * Jeśli chcesz podzielić kodu w *app.tsx* i nie można to zrobić, użyj **dołączyć do procesu** zgodnie z opisem w poprzednich krokach można dołączyć debugera. Następnie otwórz dynamicznie generowanym *app.tsx* plików w Eksploratorze rozwiązań, otwierając **dokumentów skryptu** > **app.tsx**, ustaw punkt przerwania i Odśwież strony w przeglądarce.

        Alternatywnie Jeśli chcesz podzielić kodu w *app.tsx* i nie można to zrobić, spróbuj użyć `debugger;` instrukcji w *app.tsx*, lub ustaw punkty przerwania w narzędziach Developer Chrome zamiast tego.

    * Jeśli chcesz podzielić kodu w *bundle.js aplikacji* i nie można to zrobić, usuń plik mapy źródłowej *bundle.js.map aplikacji*.

    > [!TIP]
    > Po podłączeniu do procesu po raz pierwszy wykonać następujące kroki, możesz można szybko ponownie dołączyć do tego samego procesu w programie Visual Studio 2017, wybierając **debugowania** > **ponownie dołączyć do procesu**.

## <a name="next-steps"></a>Następne kroki 

W tym samouczku przedstawiono sposób tworzenia aplikacji Node.js i platformy React, transpile JSX i debugowania. Aby dowiedzieć się więcej na temat narzędzia Node.js dla programu Visual Studio, zobacz strony typu Wiki.

> [!div class="nextstepaction"]
> [Narzędzia Node.js dla programu Visual Studio](https://github.com/Microsoft/nodejstools)
