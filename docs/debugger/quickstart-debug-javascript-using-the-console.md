---
title: Debugowanie kodu JavaScript przy użyciu konsoli | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
f1_keywords:
- VS.WebClient.JavaScriptConsole
dev_langs:
- JavaScript
helpviewer_keywords:
- JavaScript Console
- JavaScript debugging
- debugging, JavaScript
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: acdb5d1ff42c43dcfc9f5f0168ad39ee9c277088
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="debug-javascript-using-the-console-in-visual-studio"></a>Debugowanie kodu JavaScript przy użyciu konsoli w programie Visual Studio
  
 Okno konsoli JavaScript do interakcji z i debugowania aplikacji platformy uniwersalnej systemu Windows utworzony przy użyciu języka JavaScript. Te funkcje są obsługiwane dla aplikacji platformy uniwersalnej systemu Windows i aplikacje utworzone za pomocą programu Visual Studio Tools for Apache Cordova. Dokumentacja poleceń konsoli, aby zapoznać [polecenia konsoli JavaScript](../debugger/javascript-console-commands.md).  
  
 Okno konsoli JavaScript umożliwia:  
  
-   Wyślij obiektów, wartości i komunikaty z aplikacji w oknie konsoli.  
  
-   Wyświetlanie i modyfikowanie wartości zmiennych lokalnych i globalnych w uruchomionej aplikacji.  
  
-   Widok obiektu wizualizatorów.  
  
-   Uruchom kod JavaScript, która wykonuje w bieżącym kontekście skryptu.  
  
-   Wyświetl JavaScript — błędy i wyjątki, oprócz wyjątków modelu DOM (Document Object) i środowiska wykonawczego systemu Windows.  
  
-   Wykonywanie innych zadań, takich jak czyszczenie ekranu. Zobacz [polecenia konsoli JavaScript](../debugger/javascript-console-commands.md) pełną listę poleceń.  
  
> [!TIP]
>  Jeśli nastąpi zamknięcie okna konsoli języka JavaScript, wybierz **debugowania**> **Windows** > **konsoli JavaScript** otworzyć go ponownie. Okno jest wyświetlane tylko podczas sesji debugowania skryptu.  
  
 Korzystanie z okna konsoli języka JavaScript, możesz użyć aplikacji bez zatrzymania i ponownego uruchomienia debugera. Aby uzyskać więcej informacji, zobacz [odświeżanie aplikacji (JavaScript)](../debugger/refresh-an-app-javascript.md). Aby uzyskać informacje o innych JavaScript debugowania funkcje, takie jak przy użyciu Eksploratora modelu DOM i ustawianie punktów przerwania, zobacz [Szybki Start: debugowanie kodu HTML i CSS](../debugger/quickstart-debug-html-and-css.md) i [debugowania aplikacji w programie Visual Studio](../debugger/debug-store-apps-in-visual-studio.md).  
  
##  <a name="InteractiveConsole"></a> Debugowanie przy użyciu okna konsoli języka JavaScript  
 Poniższe kroki tworzenia `FlipView` aplikacji i przedstawiają sposób interaktywnie debugowania błędu kodowania JavaScript.  
  
> [!NOTE]
>  Przykładową aplikację w tym miejscu jest aplikacją platformy uniwersalnej systemu Windows. Jednak funkcje konsoli opisane tutaj również zastosowanie do aplikacji utworzone przy użyciu programu Visual Studio Tools for Apache Cordova.  
  
#### <a name="to-debug-javascript-code-in-the-flipview-app"></a>Aby debugować kod JavaScript w aplikacji właściwości FlipView  
  
1.  Utwórz nowe rozwiązanie programu Visual Studio, wybierając **pliku** > **nowy projekt**.  
  
2.  Wybierz **JavaScript** > **uniwersalnych systemu Windows**, a następnie wybierz pozycję **aplikacji WinJS**.  
  
3.  Wpisz nazwę projektu, takie jak `FlipViewApp`i wybierz polecenie **OK** do utworzenia aplikacji.  
  
4.  W elemencie BODY index.html Zastąp istniejący kod HTML ten kod:  
  
    ```html  
    <div id="flipTemplate" data-win-control="WinJS.Binding.Template"  
             style="display:none">  
        <div class="fixedItem" >  
            <img src="#" data-win-bind="src: flipImg" />  
        </div>  
    </div>  
    <div id="fView" data-win-control="WinJS.UI.FlipView" data-win-options="{  
        itemDataSource: Data.items.dataSource, itemTemplate: flipTemplate }">  
    </div>  
    ```  
  
5.  Otwórz default.css i Dodaj CSS w przypadku `#fView` selektora:  
  
    ```css  
    #fView {  
        background-color:#0094ff;  
        height: 500px;  
        margin: 25px;  
    }  
    ```  
  
6.  Otwórz default.js i Zastąp kod następujący kod JavaScript:  
  
    ```javascript  
    (function () {  
        "use strict";  
  
        var app = WinJS.Application;  
        var activation = Windows.ApplicationModel.Activation;  
  
        var myData = [];  
        for (var x = 0; x < 4; x++) {  
            myData[x] = { flipImg: "/images/logo.png" }  
        };  
  
        var pages = new WinJS.Binding.List(myData, { proxy: true });  
  
        app.onactivated = function (args) {  
            if (args.detail.kind === activation.ActivationKind.launch) {  
                if (args.detail.previousExecutionState !==  
                activation.ApplicationExecutionState.terminated) {  
                    // TODO: . . .  
                } else {  
                    // TODO: . . .  
                }  
                args.setPromise(WinJS.UI.processAll());  
  
                updateImages();  
            }  
        };  
  
        function updateImages() {  
  
            pages.push(0, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-76.jpg" });  
            pages.push(1, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-77.jpg" });  
            pages.push(2, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-78.jpg" });  
  
        };  
  
        app.oncheckpoint = function (args) {  
        };  
  
        app.start();  
  
        var publicMembers = {  
            items: pages  
        };  
  
        WinJS.Namespace.define("Data", publicMembers);  
  
    })();  
    ```  
  
7.  Jeśli cel debugowania nie została jeszcze wybrana, wybierz **komputera lokalnego** z listy rozwijanej obok pozycji listy **urządzenia** znajdującego się na **debugowania** narzędzi:  
  
     ![Wybierz opcję debugowania listy docelowej](../debugger/media/js_select_target.png "JS_Select_Target")  
  
8.  Naciśnij klawisz F5, aby uruchomić debugera.  
  
     Brak aplikacja działa, ale obrazów. Błędy APPHOST w oknie konsoli JavaScript wskazuje brak obrazów.  
  
9. Z `FlipView` aplikacji, typ `Data.items` w konsoli okno danych wejściowych (obok pozycji ">>" symbol) i naciśnij klawisz Enter.  
  
     Wizualizator dla `items` obiekt jest wyświetlany w oknie konsoli. Oznacza to, że `items` obiektu wystąpienie zostało utworzone i jest dostępny w bieżącym kontekście skryptu. W oknie konsoli możesz kliknąć przez węzły obiektu do wyświetlenia wartości właściwości (lub użyj klawiszy strzałek). Jeśli klikniesz przycisk w dół do `items._data` obiektu, jak widać na tej ilustracji, można znaleźć odniesienia źródła obrazu są niepoprawne, zgodnie z oczekiwaniami. Domyślne obrazy (logo.png) są nadal dostępne w obiekcie, a istnieją obrazy Brak przeplatane przy użyciu oczekiwanego obrazów.  
  
     ![Okno konsoli JavaScript](../debugger/media/js_console_window.png "JS_Console_Window")  
  
     Należy również zauważyć, że są dużo więcej elementów w `items._data` obiekt z oczekiwaniami.  
  
10. W wierszu polecenia wpisz `Data.items.push` i naciśnij klawisz Enter. W oknie konsoli wyświetlane dla niego Wizualizator `push` funkcja, która jest zaimplementowana w [!INCLUDE[winjs_long](../debugger/includes/winjs_long_md.md)] pliku projektu. W tej aplikacji użyto `push` można dodać odpowiednie elementy. Nieco postępowaniu za pomocą funkcji IntelliSense, firma Microsoft sprawdzić, że firma Microsoft używa `setAt` zastąpić domyślne obrazy.  
  
11. Aby rozwiązać ten problem interaktywnie bez zatrzymywania sesji debugowania, otwórz default.js i wybierz ten kod z `updateImages` funkcji:  
  
    ```javascript  
    pages.push(0, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-76.jpg" });  
    pages.push(1, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-77.jpg" });  
    pages.push(2, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-78.jpg" });  
    ```  
  
     Skopiuj i wklej ten kod w wierszu danych wejściowych konsoli języka JavaScript.  
  
    > [!TIP]
    >  Po wklejeniu wiele wierszy kodu w wierszu danych wejściowych konsoli języka JavaScript, wiersz danych wejściowych konsoli następuje automatyczne przełączenie do trybu wielowierszowego. Możesz nacisnąć klawisze Ctrl + Alt + M, aby włączyć tryb wspólny, włączać i wyłączać. Aby uruchomić skrypt w trybie wielowierszowe, naciśnij klawisze Ctrl + Enter lub wybierz symbol strzałkę w prawym dolnym rogu okna. Aby uzyskać więcej informacji, zobacz [jednowierszowy tryb i trybu wielowierszowego w oknie konsoli JavaScript](#SinglelineMultilineMode).  
  
12. Popraw `push` wywołania funkcji w wierszu polecenia, zastępując `pages.push` z `Data.items.setAt`. Poprawiony kod powinien wyglądać następująco:  
  
    ```javascript  
    Data.items.setAt(0, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-76.jpg" });  
    Data.items.setAt(1, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-77.jpg" });  
    Data.items.setAt(2, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-78.jpg" });  
    ```  
  
    > [!TIP]
    >  Jeśli chcesz użyć `pages` obiekt zamiast `Data.items`, musisz ustawić punkt przerwania w kodzie, aby zachować `pages` obiekt w zakresie.  
  
13. Wybierz symbol zieloną strzałkę, aby uruchomić skrypt.  
  
14. Naciśnij klawisze Ctrl + Alt + M, aby przełączyć do trybu jednowierszowego wiersz danych wejściowych konsoli, a następnie wybierz **wyczyścić dane wejściowe** (czerwony "X") do Usuń kod z monit wejściowy.  
  
15. Typ `Data.items.length = 3` w wierszu polecenia, a następnie naciśnij klawisz Enter. Spowoduje to usunięcie elementów niezwiązanych z danych.  
  
16. Sprawdź aplikację ponownie i zostanie wyświetlony, czy obrazy poprawne rozpoczął `FlipView` stron.  
  
17. W programie DOM Explorer mogą zobaczyć zaktualizowane element DIV, a można nawigować do poddrzewo można znaleźć oczekiwanego elementy IMG.  
  
18. Zatrzymaj debugowanie, wybierając **debugowania** > **Zatrzymaj debugowanie** lub przez naciśnięcie klawisza Shift + F5, a następnie napraw kodu źródłowego.  
  
     Dla default.html ukończone zawierających strony poprawione przykładowy kod, zobacz [debugowania kodu HTML, CSS i JavaScript przykładowy kod](../debugger/debug-html-css-and-javascript-sample-code.md).  
  
##  <a name="InteractiveDebuggingBreakMode"></a> Tryb interaktywny debugowania i podziału  
 Można użyć punktów przerwania i wykonywanie kodu podczas korzystania JavaScript debugowania narzędzi, takich jak okna konsoli języka JavaScript. Gdy program, który działa w debugerze napotka punkt przerwania, debuger tymczasowo wstrzymuje wykonywanie programu. Podczas wykonywania jest wstrzymana, program zmienia się z trybu wykonywania do tryb przerwania. Można wznowić wykonywania w dowolnym momencie.  
  
 Gdy program jest w trybie przerwania, służy okna konsoli języka JavaScript do uruchamiania skryptów i poleceń, które są prawidłowe w bieżącym kontekście wykonanie skryptu. W tej procedurze użyjesz stałym wersja `FlipView` aplikacji utworzony wcześniej do zaprezentowania trybu przerwania.  
  
#### <a name="to-set-a-breakpoint-and-debug-the-app"></a>Ustaw punkt przerwania i debugowania aplikacji  
  
1.  W pliku default.html `FlipView` aplikację, która wcześniej utworzona, otwórz menu skrótów `updateImages()` funkcji, a następnie wybierz pozycję **punktu przerwania** > **wstawić punktu przerwania**.  
  
2.  Wybierz **komputera lokalnego** w listy rozwijanej obok pozycji listy **Rozpocznij debugowanie** znajdującego się na **debugowania** paska narzędzi.  
  
3.  Wybierz **debugowania** > **Rozpocznij debugowanie**, lub naciśnij klawisz F5.  
  
     Aplikacja przechodzi do trybu przerwania podczas wykonywania osiągnie `updateImages()` funkcji i bieżącego wiersza wykonanie programu jest wyróżnione kolorem żółtym.  
  
     ![W konsoli JavaScript w trybie przerwania](../debugger/media/js_breakmode.png "JS_BreakMode")  
  
     Można zmienić wartości zmiennych bezpośrednio wpływa na stan program bez przerywania w bieżącej sesji debugowania.  
  
4.  Typ `updateImages` w wierszu polecenia, a następnie naciśnij klawisz Enter. Wizualizator dla funkcji zostanie wyświetlony w oknie konsoli.  
  
5.  Wybierz funkcję w oknie konsoli do wyświetlenia implementację funkcji.  
  
     Na poniższej ilustracji przedstawiono okno konsoli w tym momencie.  
  
     ![Okno konsoli JavaScript przedstawiający wizualizatora](../debugger/media/js_console_function_visualizer.png "JS_Console_Function_Visualizer")  
  
6.  Skopiuj jeden wiersz w funkcji w oknie danych wyjściowych na monit wejściowy i zmień wartość indeksu z 3:  
  
    ```javascript  
    pages.setAt(3, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-76.jpg" });  
    ```  
  
7.  Naciśnij klawisz Enter, aby uruchomić wiersz kodu.  
  
     Jeśli chcesz wykonywać krokowo kodu wiersz po wierszu, naciśnij klawisz F11 lub naciśnij klawisz F5, aby kontynuować wykonywanie programu.  
  
8.  Naciśnij klawisz F5, aby kontynuować wykonywanie programu. `FlipView` Aplikacji zostanie wyświetlony, a teraz wszystkie cztery strony Pokaż jeden z obrazów z systemem innym niż domyślny.  
  
     Aby powrócić do programu Visual Studio, naciśnij klawisz F12 lub Alt + Tab.  
  
##  <a name="SinglelineMultilineMode"></a> Jednowierszowy tryb i trybu wielowierszowego w oknie konsoli JavaScript  
 Monit wejściowy dla okna konsoli języka JavaScript obsługuje zarówno w trybie pojedynczej linii, jak i w trybie wielowierszowy. Interakcyjne debugowania procedurze w tym temacie zawiera przykład w obu tych trybach. Możesz nacisnąć klawisze Ctrl + Alt + M do przełączania między trybami.  
  
 Jednowierszowy tryb zawiera historię wejściowego. Historia wejściowych można nawigować przy użyciu klawiszy Strzałka w górę i Strzałka w dół. Jednowierszowy tryb czyści monit wejściowy podczas uruchamiania skryptów. Aby uruchomić skrypt w trybie pojedynczej linii, naciśnij klawisz Enter.  
  
 Wielowierszowy tryb nie czyści monit wejściowy podczas uruchamiania skryptów. Po przełączeniu do trybu jednowierszowego z trybu wielowierszowego można wyczyścić wierszu danych wejściowych, naciskając **wyczyścić dane wejściowe** (czerwony "X"). Aby uruchomić skrypt w trybie wielowierszowe, naciśnij klawisze Ctrl + Enter lub wybierz symbol strzałkę w prawym dolnym rogu okna.  
  
##  <a name="Switching"></a> Przełączenie kontekstu wykonywania skryptu  
 Okno konsoli JavaScript umożliwia interakcję z kontekstem pojedynczego uruchomienia, który reprezentuje pojedyncze wystąpienie hosta platformy sieci web (WWAHost.exe), w czasie. W niektórych scenariuszach aplikacji może uruchomić inne wystąpienie hosta, na przykład przy użyciu `iframe`, kontraktu udostępniania, sieć web proces roboczy lub `WebView` formantu. Jeśli jest uruchomione inne wystąpienie hosta, możesz wybrać kontekstu wykonywania różnych podczas uruchamiania aplikacji przez wybranie kontekstu wykonywania w **docelowej** listy.  
  
 Na poniższej ilustracji przedstawiono listę docelową w oknie konsoli języka JavaScript.  
  
 ![Docelowa zaznaczenia w oknie konsoli JavaScript](../debugger/media/js_console_target.png "JS_Console_Target")  
  
 Można również przełączyć kontekst wykonywania przy użyciu `cd` polecenia, ale musisz znać nazwę kontekstu wykonywania i odwołanie używasz musi należeć do zakresu. **Docelowej** listy zapewnia lepszy dostęp do innych kontekstach wykonywania.   
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji w programie Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)   
 [Polecenia konsoli JavaScript](../debugger/javascript-console-commands.md)   
 [Odświeżanie aplikacji (JavaScript)](../debugger/refresh-an-app-javascript.md)   
 [Skróty klawiaturowe](../debugger/keyboard-shortcuts-html-and-javascript.md)   
 [Debugowanie przykładowy kod HTML, CSS i JavaScript](../debugger/debug-html-css-and-javascript-sample-code.md)   
 [Szybki Start: Debugowanie kodu HTML i CSS](../debugger/quickstart-debug-html-and-css.md)   
 [Debugowanie kontrolki WebView](../debugger/debug-a-webview-control.md)   
 [Pomoc techniczna i ułatwień dostępu](http://msdn.microsoft.com/library/tzbxw1af\(VS.120\).aspx)