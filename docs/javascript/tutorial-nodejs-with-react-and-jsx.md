---
title: Tworzenie aplikacji Node.js i React
description: W tym samouczku utworzysz aplikację przy użyciu narzędzia Node.js dla programu Visual Studio
ms.custom: mvc
ms.date: 05/23/2018
ms.technology: vs-nodejs
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: douge
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 88810c2e4958e96bd5487ce1a5b059897b725b45
ms.sourcegitcommit: 7a11a094a353f2e2a2077ad863ca4c0fb97f7ec5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/18/2018
ms.locfileid: "39132009"
---
# <a name="tutorial-create-a-nodejs-and-react-app-in-visual-studio"></a>Samouczek: Tworzenie aplikacji Node.js i React w programie Visual Studio

Program Visual Studio umożliwia łatwe tworzenie projektu środowiska Node.js i technologii IntelliSense i innych wbudowanych funkcji, które obsługuje środowiska Node.js. W tym samouczku dla programu Visual Studio utworzysz projekt aplikacji sieci web Node.js za pomocą szablonu programu Visual Studio. Następnie utworzysz prostą aplikację przy użyciu platformy React.

W tym samouczku dowiesz się, jak:
> [!div class="checklist"]
> * Tworzenie projektu środowiska Node.js
> * Dodaj pakiety npm
> * Dodaj kod platformy React z aplikacją
> * Transpiluj JSX
> * Dołącz debuger

## <a name="prerequisites"></a>Wymagania wstępne

* Konieczne jest posiadanie programu Visual Studio 2017 i obciążenie programowania Node.js.

    Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) strony, aby zainstalować go za darmo.

    Jeśli musisz zainstalować obciążenie, ale już program Visual Studio, wybierz **Otwórz Instalator programu Visual Studio** łącze w okienku po lewej stronie **nowy projekt** okno dialogowe. Uruchamia Instalatora programu Visual Studio. Wybierz **programowania Node.js** obciążenia, wybierz **Modyfikuj**.

* Konieczne jest posiadanie zainstalowanego środowiska uruchomieniowego Node.js.

    W tym samouczku został przetestowany przy użyciu wersji 8.11.2.

    Jeśli nie jest ona zainstalowana, zainstaluj wersję LTS z [Node.js](https://nodejs.org/en/download/) witryny sieci Web. Ogólnie rzecz biorąc program Visual Studio automatycznie wykrywa zainstalowane środowisko uruchomieniowe Node.js. Jeśli nie zostanie wykryta zainstalowanego środowiska uruchomieniowego, można skonfigurować projekt, aby odwoływać się do zainstalowanego środowiska uruchomieniowego na stronie właściwości (po utworzeniu projektu, kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **właściwości**).

## <a name="create-a-project"></a>Tworzenie projektu

Najpierw utwórz projekt aplikacji sieci web środowiska Node.js.

1. Otwórz program Visual Studio 2017.

1. Na pasku menu u góry wybierz **pliku** > **New** > **projektu**.

1. W **nowy projekt** rozwiń w lewym okienku w oknie dialogowym **JavaScript**, a następnie wybierz **Node.js**. W środkowym okienku wybierz **pusta aplikacja sieci Web Node.js**, wpisz nazwę **NodejsWebAppBlank**, a następnie wybierz **OK**.

     Jeśli nie widzisz **pusta aplikacja sieci Web Node.js** szablon projektu, należy najpierw zainstalować obciążenia programowanie Node.js.

    Visual Studio tworzy nowego rozwiązania i otwiera projekt.

    ![Projekt node.js w Eksploratorze rozwiązań](../javascript/media/tutorial-nodejs-react-project-structure.png)

    * Wyróżnione czcionką pogrubioną jest projektu, przy użyciu nazwę nadaną w **nowy projekt** okno dialogowe. W systemie plików tego projektu jest reprezentowany przez *.njsproj* pliku w folderze projektu. Można ustawić właściwości i zmienne środowiskowe związane z projektem, klikając prawym przyciskiem myszy projekt i wybierając pozycję **właściwości**. Możesz tworzyć Pełna zgodnooć wersji z innymi narzędziami deweloperskimi, ponieważ plik projektu nie wprowadzać zmian niestandardowego źródła projektu środowiska Node.js.

    * Na najwyższym poziomie to rozwiązanie, która domyślnie ma taką samą nazwę jak projektu. To rozwiązanie, reprezentowane przez *.sln* plików na dysku, to kontener dla jednego lub kilku powiązanych projektów.

    * Węzeł npm zawiera wszystkie pakiety npm zainstalowane. Możesz kliknąć prawym przyciskiem myszy węzeł npm, aby wyszukać i zainstalować pakiety npm przy użyciu okna dialogowego.

    * Pliki, takie jak projektu *server.js* wyświetlane w węźle projektu. *Server.js* jest plikiem uruchomienia projektu.

## <a name="add-npm-packages"></a>Dodaj pakiety npm

Ta aplikacja wymaga numeru moduły npm, by działała poprawnie.

* react
* react-dom
* Express
* ścieżka
* ts-loader
* typescript
* webpack
* webpack-cli

1. W Eksploratorze rozwiązań (w okienku po prawej stronie), kliknij prawym przyciskiem myszy **npm** węzeł projektu i wybierz polecenie **zainstalować nowe pakiety npm**.

    W **zainstalować nowe pakiety npm** okno dialogowe, możesz zainstalować najnowszą wersję pakietu lub określ wersję. Jeśli zdecydujesz się zainstalować najnowszą wersję tych pakietów, ale wystąpiły nieoczekiwane błędy później, konieczne może być zainstalować wersje dokładny pakietu opisane w dalszej części tych kroków.

1. W **zainstalować nowe pakiety npm** okno dialogowe, wyszukaj pakiet platformy react, a następnie wybierz pozycję **zainstaluj pakiet** go zainstalować.

    ![Instalowanie pakietów npm](../javascript/media/tutorial-nodejs-react-install-packages.png)

    Wybierz **dane wyjściowe** okno, aby wyświetlić postęp na temat instalowania pakietu (wybierz **Npm** w **Pokaż dane wyjściowe z** pola). Po zainstalowaniu pakietu jest wyświetlany w obszarze **npm** węzła.

    Projekt *package.json* plik został zaktualizowany o nowe informacje o pakiecie, łącznie z wersją pakietu.

1. Zamiast używania interfejsu użytkownika, aby wyszukać i dodać pozostałe pakiety pojedynczo, wklej następujący kod do pliku package.json. Zastąp `dependencies` sekcji przy użyciu tego kodu:

    ```js
    "dependencies": {
      "express": "4.16.2",
      "path": "0.12.7",
      "react": "16.4.0",
      "react-dom": "16.4.0",
      "ts-loader": "4.0.1",
      "typescript": "2.7.2",
      "webpack": "4.1.1",
      "webpack-cli": "2.0.11"
    }
    ```

1. Kliknij prawym przyciskiem myszy **npm** węzeł projektu i wybierz polecenie **zaktualizuj pakiety npm**.

    Wybierz **dane wyjściowe** okno, aby wyświetlić postęp na temat instalowania pakietów. Instalacja może zająć kilka minut i może nie od razu Zobacz wyniki.

    Poniżej przedstawiono moduły npm, w jakiej występują w Eksploratorze rozwiązań po ich zainstalowaniu.

    ![pakiety npm](../javascript/media/tutorial-nodejs-react-npm-modules.png)

    > [!NOTE]
    > Jeśli wolisz zainstalować pakiety npm przy użyciu wiersza polecenia, kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Otwórz wiersz polecenia w tym miejscu**. Użyj standardowych poleceń środowiska Node.js, aby zainstalować pakiety.

## <a name="add-project-files"></a>Dodaj pliki projektów

W ramach tej procedury dodasz cztery nowe pliki do projektu.

* *app.tsx*
* *webpack-config.js*
* *index.html*
* *tsconfig.json*

Dla tej prostej aplikacji możesz dodawać nowe pliki projektu, w katalogu głównym projektu. (W przypadku większości aplikacji są zazwyczaj Dodaj pliki do podfolderów i odpowiednio dostosować odwołania do ścieżki względnej.)

1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt **NodejsWebAppBlank** i wybierz polecenie **Dodaj** > **nowy element**.

1. W **Dodaj nowy element** okna dialogowego wybierz **plik TypeScript JSX**, wpisz nazwę *app.tsx*i wybierz **OK**.

1. Powtórz te kroki, aby dodać *webpack config.js*. A nie plikiem TypeScript JSX wybierz **plik JavaScript**.

1. Powtórz te same kroki, aby dodać *index.html* do projektu. Zamiast pliku JavaScript, wybierz **plik HTML**.

1. Powtórz te same kroki, aby dodać *tsconfig.json* do projektu. Zamiast pliku JavaScript, wybierz **pliku konfiguracji JSON TypeScript**.

## <a name="add-app-code"></a>Dodawanie kodu aplikacji

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

   Powyższy kod używa Express, aby uruchomić środowisko Node.js jako serwer aplikacji sieci web. Ten kod ustawia port numer portu we właściwościach projektu skonfigurowano (domyślnie port skonfigurowano 1337 we właściwościach). Aby otworzyć okno właściwości projektu, kliknij prawym przyciskiem myszy projekt w Eksploratorze rozwiązań, a następnie wybierz **właściwości**.

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

    Powyższy kod użyto składnia JSX i React, aby wyświetlić wiadomość proste.

1. Otwórz *index.html* i Zastąp **treści** sekcję poniższym kodem:

    ```html
    <body>
        <div id="root"></div>
        <!-- scripts -->
        <script src="./dist/app-bundle.js"></script>
    </body>
    ```

    Ta strona HTML ładuje się *bundle.js aplikacji*, zawierającą transpiled kodu JSX i React zwykły języka JavaScript. Obecnie *bundle.js aplikacji* plik jest pusty. W następnej sekcji skonfigurujesz opcje transpiluj kodu.

## <a name="configure-webpack-and-typescript-compiler-options"></a>Skonfiguruj opcje kompilatora TypeScript i webpack

W poprzednich krokach dodano *webpack config.js* do projektu. Następnie dodasz kod konfiguracji webpack. Doda konfiguracji webpack prostego, który określa plik wejściowy (*app.tsx*) i plik wyjściowy (*bundle.js aplikacji*) do tworzenia pakietów i transpiling JSX do zwykłego kodu JavaScript. Dla transpiling możesz również skonfigurować niektóre opcje kompilatora TypeScript. Ten kod jest podstawowej konfiguracji, który jest przeznaczony jako wprowadzenie do webpack i kompilatora TypeScript.

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

    Kod konfiguracji webpack powoduje, że Webpack, aby użyć modułu ładującego TypeScript do transpiluj JSX.

1. Otwórz *tsconfig.json* i Zastąp następujący kod, który określa opcje kompilatora TypeScript w kodzie domyślnym:

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

    *App.tsx* jest określony jako pliku źródłowego.

## <a name="transpile-the-jsx"></a>Transpiluj JSX

1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy węzeł projektu, a następnie wybierz **Otwórz wiersz polecenia w tym miejscu**.

1. W wierszu polecenia wpisz następujące polecenie:

    `node_modules\.bin\webpack app.tsx --config webpack-config.js`

    W oknie wiersza polecenia zawiera wynik.

    ![Uruchom webpack](../javascript/media/tutorial-nodejs-react-run-webpack.png)

    Jeśli widzisz błędy zamiast powyższym danych wyjściowych, należy je rozwiązać, zanim aplikacja będzie działać. Jeśli Twojej wersji pakietu npm różnią się od wersji przedstawiona w tym samouczku, który może być źródłem błędów. Jest jednym ze sposobów, aby naprawić błędy do użycia wersje dokładny pokazano w poprzednich krokach. Ponadto w przypadku co najmniej jeden z tych wersji pakietu jest przestarzała i powoduje błąd, może być konieczne zainstalowanie nowszej wersji, aby naprawić błędy.

1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy węzeł projektu, a następnie wybierz **Dodaj** > **istniejący Folder**, następnie wybierz *dist* folder i wybierz polecenie  **Wybierz Folder**.

    Program Visual Studio dodaje *dist* folderu do projektu, który zawiera *bundle.js aplikacji* i *bundle.js.map aplikacji*.

1. Otwórz *bundle.js aplikacji* się transpiled kodu JavaScript.

1. Jeśli zostanie wyświetlony monit, aby ponownie załadować zewnętrznie zmodyfikowane pliki, wybierz opcję **tak na wszystko**.

    ![Obciążenia zmodyfikowanych plików](../javascript/media/tutorial-nodejs-react-reload-files.png)

Każdym wprowadzeniu zmiany *app.tsx*, należy ponownie uruchomić polecenie webpack.

## <a name="run-the-app"></a>Uruchamianie aplikacji

1. Upewnij się, że dla programu Chrome jest wybrany jako bieżący obiekt docelowy debugowania.

    ![Wybierz cel debugowania Chrome](../javascript/media/tutorial-nodejs-react-debug-target.png)

1. Aby uruchomić aplikację, naciśnij klawisz **F5** (**debugowania** > **Rozpocznij debugowanie**) lub przycisku zieloną strzałkę.

    Zostanie otwarte okno konsoli środowiska Node.js, pokazujący port, na którym nasłuchuje debugera.

    Program Visual Studio uruchamia aplikację, uruchamiając plik startowy *server.js*.

    ![Uruchamianie platformy React w przeglądarce](../javascript/media/tutorial-nodejs-react-running-react.png)

1. Zamknij okno przeglądarki.

1. Zamknij okno konsoli.

## <a name="set-a-breakpoint-and-run-the-app"></a>Ustaw punkt przerwania i uruchamianie aplikacji

1. W *server.js*, kliknij na marginesie po lewej stronie `staticPath` deklaracji, aby ustawić punkt przerwania:

    ![Ustaw punkt przerwania](../javascript/media/tutorial-nodejs-react-set-breakpoint.png)

    Punkty przerwania są najbardziej podstawowa i podstawowych funkcji niezawodne debugowanie. Punkt przerwania wskazuje, gdzie programu Visual Studio powinny zawiesić uruchamianie kodu, dzięki czemu możesz zapoznaj się z wartości zmiennych lub zachowanie pamięci lub czy gałąź kodu wprowadzenie uruchomieniu.

1. Aby uruchomić aplikację, naciśnij klawisz **F5** (**debugowania** > **Rozpocznij debugowanie**).

    Debuger zatrzymuje się w punkcie przerwania zestawu (bieżąca instrukcja jest oznaczona kolorem żółtym). Teraz możesz sprawdzić stan swojej aplikacji, ustawiając kursor nad zmiennych, które obecnie znajdują się w zakresie, za pomocą okna debugera, takie jak **lokalne** i **Obejrzyj** systemu windows.

1. Naciśnij klawisz **F5** kontynuowanie działania aplikacji.

1. Jeśli chcesz użyć narzędzia deweloperskie dla programu Chrome, naciśnij klawisz **F12**. Można użyć tych narzędzi do badania modelu DOM i interakcji z aplikacją przy użyciu konsoli języka JavaScript.

1. Zamknij przeglądarkę sieci web i konsoli.

## <a name="set-and-hit-a-breakpoint-in-the-client-side-react-code"></a>Ustaw i Traf punkt przerwania w kodzie po stronie klienta platformy React

W poprzedniej sekcji debuger jest dołączony do kodu w języku Node.js po stronie serwera. Aby dołączyć debuger za pomocą programu Visual Studio i identyfikować punkty przerwania w kodzie platformy React po stronie klienta, debuger potrzebuje pomocy, aby zidentyfikować korygowania procesu. Oto jeden ze sposobów, aby włączyć tę opcję.

1. Zamknij wszystkie okna przeglądarki Chrome.

1. Otwórz **Uruchom** polecenia Windows **Start** przycisk (kliknij prawym przyciskiem myszy i wybierz polecenie **Uruchom**), a następnie wprowadź następujące polecenie:

    `chrome.exe --remote-debugging-port=9222`

    Spowoduje to uruchomienie przeglądarki Chrome z włączonym debugowaniem.

1. Przełącz się do programu Visual Studio i ustaw punkt przerwania *bundle.js aplikacji* możesz pisać kod w `render()` funkcji, jak pokazano na poniższej ilustracji:

    ![Ustaw punkt przerwania](../javascript/media/tutorial-nodejs-react-set-breakpoint-client-code.png)

1. Za pomocą przeglądarki Chrome wybrany jako cel debugowania w programie Visual Studio, naciśnij klawisz **Ctrl**+**F5** (**debugowania** > **Rozpocznij bez debugowania** ) do uruchomienia aplikacji w przeglądarce.

    Aplikacja zostanie otwarta nowa karta przeglądarki.

1. Wybierz **debugowania** > **dołączyć do procesu**.

1. W **dołączyć do procesu** okna dialogowego wybierz **kodu aparatu Webkit** w **dołączyć do** wpisz **chrome** w polu filtru, aby filtrować wyniki wyszukiwania.

1. Wybierz proces dla programu Chrome przy użyciu właściwy host port (1337, w tym przykładzie), a następnie wybierz pozycję **Dołącz**.

    ![Dołącz do procesu](../javascript/media/tutorial-nodejs-react-attach-to-process.png)

    Wiesz, że debuger został dołączony poprawnie otwieraniu konsoli języka JavaScript i narzędzia DOM Explorer w programie Visual Studio. Te narzędzia debugowania są podobne do narzędzia F12 Microsoft Edge i przeglądarki Chrome Developer Tools.

    > [!NOTE]
    > Jeśli debuger nie dołączy i zostanie wyświetlony komunikat "nie można dołączyć do procesu. Operacja jest niedozwolona w bieżącym stanie. ", zamknij wszystkie wystąpienia programu Chrome, przed rozpoczęciem Chrome w trybie debugowania za pomocą Menedżera zadań. Rozszerzenia dla programu Chrome może być uruchomiony i zapobieganie tryb pełnego debugowania.

1. Ponieważ kod za pomocą punktu przerwania zostały już wykonane czynności, Odśwież stronę przeglądarki w taki sposób, aby trafiony punkt przerwania.

    Gdy wstrzymaniu w debugerze, można sprawdzić stan swojej aplikacji, przenosząc kursor myszy nad zmienne okien i korzystanie z debugera. Debuger może przejść przez krokowe wykonywanie kodu (**F5**, **F10**, i **F11**).

    Może być trafiony punkt przerwania w jednym *bundle.js aplikacji* lub lokalizacji zamapowanych w *app.tsx*, w zależności od stanu usługi środowisko i przeglądarki. W obu przypadkach możesz przejść przez kod i Sprawdź zmienne.

    * Jeśli potrzebujesz wszedł do kodu w *app.tsx* i nie można to zrobić, użyj **dołączyć do procesu** zgodnie z opisem w poprzednich krokach, aby dołączyć debuger. Następnie otwórz dynamicznie generowanym *app.tsx* pliku z Eksploratora rozwiązań, otwierając **dokumenty skryptów** > **app.tsx**, a następnie ustaw punkt przerwania i Odśwież strony w przeglądarce (ustawić punkt przerwania w wierszu kodu, który umożliwia punkty przerwania, takich jak `return` instrukcji lub `var` deklaracji).

        Alternatywnie Jeśli potrzebujesz wszedł do kodu w *app.tsx* i nie można to zrobić, spróbuj użyć `debugger;` instrukcji w *app.tsx*, lub zamiast tego ustawić punkty przerwania w Developer Tools dla programu Chrome.

    * Jeśli potrzebujesz wszedł do kodu w *bundle.js aplikacji* i nie można to zrobić, usuń plik mapy źródłowej *bundle.js.map aplikacji*.

    > [!TIP]
    > Po dołączeniu do procesu po raz pierwszy wykonać następujące kroki, możesz szybko dołączyć do tego samego procesu w programie Visual Studio 2017, wybierając **debugowania** > **ponownie Dołącz do procesu**.

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Wdrażanie aplikacji do usługi App Service w systemie Linux](../javascript/publish-nodejs-app-azure.md)