---
title: Debugowanie kodu HTML i CSS w aplikacjach platformy uniwersalnej systemu Windows | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 07/17/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.DomExplorer
dev_langs: JavaScript
helpviewer_keywords:
- debugging, CSS
- debugging, HTML
- debugging, JavaScript [UWP apps]
- DOM Explorer [UWP apps]
caps.latest.revision: "101"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: uwp
ms.openlocfilehash: bb410c6279b2910dfcb1af98ff75293d60a7e3e7
ms.sourcegitcommit: 5d43e9590e2246084670b79269cc9d99124bb3df
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="debug-html-and-css-in-uwp-apps-in-visual-studio"></a>Debugowanie HTML i CSS w aplikacjach platformy uniwersalnej systemu Windows w programie Visual Studio
  
 W przypadku aplikacji JavaScript programu Visual Studio zapewnia kompleksowe środowisko debugowania, które zawiera funkcje, które są znane deweloperom korzystającym z programu Internet Explorer i Visual Studio. Te funkcje są obsługiwane dla aplikacji platformy uniwersalnej systemu Windows i aplikacje utworzone za pomocą programu Visual Studio Tools for Apache Cordova.  
  
 Przy użyciu interaktywnych model debugowania dostarczone przez narzędzia inspekcji w modelu DOM, można wyświetlać i modyfikować renderowany kod HTML i CSS. Można to zrobić bez zatrzymania i ponownego uruchomienia debugera.
  
 Aby uzyskać informacje o innych JavaScript debugowania funkcje, takie jak korzystanie z okna konsoli języka JavaScript i ustawianie punktów przerwania, zobacz [Szybki Start: debugowanie JavaScript](../debugger/quickstart-debug-javascript-using-the-console.md) i [debugowania aplikacji w programie Visual Studio](../debugger/debug-store-apps-in-visual-studio.md).  
  
##  <a name="InspectingDOM"></a>Zapoznanie się na żywo modelu DOM  
 Narzędzia DOM Explorer przedstawiono widok służący do renderowanej strony, a następnie można użyć narzędzia DOM Explorer Aby zmienić wartości i od razu Zobacz wyniki. Umożliwia testowanie zmian bez zatrzymania i ponownego uruchomienia debugera. Kod źródłowy w projekcie nie powoduje zmiany interakcji ze strony za pomocą tej metody, więc po znalezieniu poprawki odpowiedni kod, wprowadź zmiany w kodzie źródłowym.  
  
> [!TIP]
>  Aby uniknąć zatrzymywanie i ponowne uruchamianie debugera podczas wprowadzania zmian w kodzie źródłowym, należy odświeżyć aplikacji przy użyciu **aplikacji odświeżania systemu Windows** przycisk na pasku narzędzi debugowania (lub naciskając klawisz F4). Aby uzyskać więcej informacji, zobacz [odświeżanie aplikacji (JavaScript)](../debugger/refresh-an-app-javascript.md).  
  
 Można użyć narzędzia DOM Explorer do:  
  
-   Przejdź poddrzewo element modelu DOM i sprawdzić renderowany kod HTML, CSS i JavaScript.  
  
-   Dynamicznie edytować atrybuty i style CSS renderowany elementów i od razu Zobacz wyniki.  
  
-   Sprawdź, jak zastosowano style CSS do elementów strony, a śledzenia reguł, które zostały zastosowane.  
  
 Podczas debugowania aplikacji, często konieczne wybranie elementów w programie DOM Explorer. Po wybraniu elementu wartości, które są wyświetlane na kartach po prawej stronie Eksploratora modelu DOM automatycznie zaktualizowany, aby pokazać wybranego elementu w modelu DOM Explorer. Są to karty: **style**, **Computed**, **układu**. Aplikacji platformy uniwersalnej systemu Windows obsługują także **zdarzenia** i **zmiany** karty. Aby uzyskać więcej informacji na temat wybierania elementów, zobacz [Zaznaczanie elementów](#SelectingElements).  
  
> [!TIP]
>  Jeśli okno Eksploratora DOM jest zamknięty, wybierz **debugowania**>**Windows** > **Eksploratora modelu DOM** otworzyć go ponownie. Okno jest wyświetlane tylko podczas sesji debugowania skryptu.  
  
 W poniższej procedurze znajdują się za pośrednictwem procesu interakcyjnego debugowania aplikacji za pomocą narzędzia DOM Explorer. Utworzymy aplikację, która używa `FlipView` kontroli i następnie jego debugowania. Ta aplikacja zawiera kilka błędów.  
  
> [!WARNING]
>  Następujące Przykładowa aplikacja jest aplikacji platformy uniwersalnej systemu Windows. Te same funkcje są obsługiwane dla oprogramowania Cordova, ale aplikacja będzie inny.  
  
#### <a name="to-debug-by-inspecting-the-live-dom"></a>Aby debugować sprawdzając na żywo modelu DOM  
  
1.  Utwórz nowe rozwiązanie programu Visual Studio, wybierając **pliku** > **nowy projekt**.  
  
2.  Wybierz **JavaScript** > **uniwersalnych systemu Windows**, a następnie wybierz pozycję **aplikacji WinJS**.  
  
3.  Wpisz nazwę projektu, takie jak `FlipViewApp`i wybierz polecenie **OK** do utworzenia aplikacji.  
  
4.  W elemencie BODY index.html Dodaj ten kod:  
  
    ```html  
    <div id="flipTemplate" data-win-control="WinJS.Binding.Template"  
             style="display:none">  
        <div class="fixedItem" >  
            <img src="#" data-win-bind="src: flipImg" />  
        </div>  
    </div>  
    <div id="fView" style="width:100px;height:100px"  
        data-win-control="WinJS.UI.FlipView" data-win-options="{  
        itemDataSource: Data.items.dataSource, itemTemplate: flipTemplate }">  
    </div>  
    ```  
  
5.  Otwórz default.css i Dodaj następujący kod CSS:  
  
    ```css  
    #fView {  
        background-color:#0094ff;  
        height: 100%;  
        width: 100%;  
        margin: 25%;  
    }  
    ```  
  
6.  Zastąp kod w default.js ten kod:  
  
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
  
            pages.setAt(0, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-76.jpg" });  
            pages.setAt(1, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-77.jpg" });  
            pages.setAt(2, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-78.jpg" });  
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
  
     Na poniższej ilustracji przedstawiono co chcesz zobaczyć, jeśli firma Microsoft uruchomić tej aplikacji. Aby pobrać aplikację w tym stanie firma Microsoft będzie jednak ustalenie liczbę usterek.  
  
     ![Właściwości FlipView aplikacji przedstawiający oczekiwanych rezultatów](../debugger/media/js_dom_appfixed.png "JS_DOM_AppFixed")  
  
7.  Wybierz **komputera lokalnego** z listy rozwijanej obok pozycji listy **Rozpocznij debugowanie** znajdującego się na **debugowania** narzędzi:  
  
     ![Wybierz opcję debugowania listy docelowej](../debugger/media/js_select_target.png "JS_Select_Target")  
  
8.  Wybierz **debugowania** > **Rozpocznij debugowanie**, lub naciśnij klawisz F5, aby uruchomić aplikację w trybie debugowania.  
  
     Ta funkcja jest uruchamiana aplikacja, ale zobaczysz ekran przede wszystkim puste, ponieważ style ma kilka błędów. Pierwszy `FlipView` obraz zostanie wyświetlony w małych kwadratowe pobliżu środka ekranu.  
  
10. Przełącz się do programu Visual Studio i wybierz **Eksploratora modelu DOM** kartę.  
  
    > [!TIP]
    >  Możesz nacisnąć klawisze Alt + Tab lub F12 w celu przełączania się między Visual Studio i uruchomionej aplikacji.  
  
11. W oknie Eksploratora modelu DOM, wybierz element DIV sekcji, która ma identyfikator równy `"fView"`. Aby wyświetlić i wybrać poprawny element DIV, użyj klawiszy strzałek. (Klawisz strzałki w prawo umożliwia wyświetlanie elementów podrzędnych).  
  
     ![DOM Explorer](../debugger/media/js_dom_explorer.png "JS_DOM_Explorer")  
  
    > [!TIP]
    >  DIV element można wybrać w lewym dolnym rogu okna konsoli języka JavaScript, wpisując `select(fView)` na >> danych wejściowych wiersza, a następnie naciśnij klawisz Enter.  
  
     Wartości, które są wyświetlane na kartach po prawej stronie okna narzędzia DOM Explorer automatycznie zaktualizować aby odzwierciedlały bieżący element w modelu DOM Explorer.  
  
12. Wybierz **Computed** kartę po prawej stronie.  
  
     Ta karta przedstawia wartość obliczona lub ostatecznego, dla każdej właściwości wybranego elementu DOM.  
  
13. Otwórz regułę CSS wysokość. Należy zauważyć, że jest wbudowany zestaw stylów do 100px, która pojawia się niespójna z wartość wysokości 100%, ustaw dla `#fView` selektora CSS. Przekreślone dla `#fView` selektora wskazuje styl wbudowany jest pierwszeństwo przed tym stylem.  
  
     Na poniższej ilustracji pokazano **Computed** kartę.  
  
     ![Obliczony Eksploratora modelu DOM kartę](../debugger/media/js_dom_explorer_computed.png "JS_DOM_Explorer_Computed")  
  
14. W głównym oknie Eksploratora modelu DOM, kliknij dwukrotnie styl wbudowany wysokość i szerokość `fView` DIV element. Można teraz edytować wartości w tym miejscu. W tym scenariuszu chcemy całkowicie usunąć.  
  
15. W oknie głównym kliknij dwukrotnie `width: 100px;height: 100px;`, naciśnij klawisz **usunąć** klucza, a następnie naciśnij klawisz **Enter**. Po naciśnięciu klawisza Enter nowe wartości są natychmiast odzwierciedlone w aplikacji, chociaż nie zostało to jeszcze zatrzymać sesję debugowania.  
  
    > [!IMPORTANT]
    >  Jak można zaktualizować atrybutów w oknie Eksploratora modelu DOM, można także zaktualizować wartości, które znajdują się w **style**, **Computed**, i **układu** karty. Aby uzyskać więcej informacji, zobacz [stylów CSS debugowania przy użyciu Eksploratora modelu DOM](../debugger/debug-css-styles-using-dom-explorer.md) i [układu debugowania za pomocą narzędzia DOM Explorer](../debugger/debug-layout-using-dom-explorer.md).  
  
16. Przełącz się do aplikacji, wybierając go lub za pomocą Alt + Tab.  
  
     Teraz `FlipView` formantu jest większy niż rozmiar ekranu symulator lub w emulatorze telefonu. To nie jest zamierzone wynik. Aby zbadać, przełącz się do programu Visual Studio.  
  
17. W programie DOM Explorer wybierz **Computed** karcie ponownie, a następnie otwórz reguły wysokość. FView element nadal znajduje się wartość 100%, zgodnie z oczekiwaniami z CSS, ale obliczona wartość jest równa wysokość ekranu aplikacji (na przykład 800 piks 667.67px lub wartość), który jest nie co chcemy dla tej aplikacji. Aby zbadać w następnych krokach usuwamy wysokość i szerokość dla `fView` DIV element.  
  
18. W **style** karcie, usuń zaznaczenie pola wyboru właściwości wysokość i szerokość dla `#fView` selektora CSS.  
  
     **Computed** karta zawiera teraz wysokość 400 piks. Informacje wskazują, że ta wartość pochodzi z właściwości flipview .win selektor określone w ui-dark.css, czyli pliku CSS platformy.  
  
19. Przełącz się do aplikacji.  
  
     Ulepszono rzeczy. Istnieje jednak nadal jeden problem więcej ustalenie: marginesy są zbyt duże.  
  
20. Aby zbadać, przełącz się do programu Visual Studio i wybierz **układu** kartę, aby przyjrzeć się elementu pola modelu.  
  
     W **układu** kartę, pojawi się następujące:  
  
    -   255px (przesunięcie) i 255px (marginesu) lub wartości podobnie, w zależności od rozdzielczości urządzenia. 
  
     Na poniższej ilustracji pokazano sposób **układu** wygląda kartę, jeśli używasz emulatora z przesunięcia 100px i marginesu).  
  
     ![Karta Układ Eksploratora modelu DOM](../debugger/media/js_dom_explorer_layout.png "JS_DOM_Explorer_Layout")  
  
     To wygląda na prawo. **Computed** karta zawiera również margines takich samych wartości.  
  
21. Wybierz **style** karcie i Znajdź `#fView` selektora CSS. W tym miejscu jest widoczna wartość 25% do **margines** właściwości.  
  
22. Wybierz 25% i zmień ją na 25px, a następnie naciśnij klawisz Enter.  
  
23. Również w **style** , wybrać regułę wysokość selektora właściwości flipview .win i zmień 400 piks do 500 px, i naciśnij klawisz Enter.  
  
24. Przełącza z powrotem do aplikacji, aby zobaczyć, że położenie elementów dane są poprawne. Aby naprawić błędy w źródle i odświeżyć aplikacji bez zatrzymywanie i ponowne uruchamianie debugera, przejrzyj następującą procedurę.  
  
#### <a name="to-refresh-your-app-while-debugging"></a>Aby odświeżyć podczas debugowania aplikacji  
  
1.  Gdy aplikacja jest nadal uruchomiona, przełącz się do programu Visual Studio.  
  
2.  Otwórz default.html i zmodyfikować kod źródłowy, zmieniając wysokość i szerokość `"fView"` element DIV 100%.  
  
3.  Wybierz **aplikacji odświeżania systemu Windows** znajdującego się na pasku narzędzi debugowania (lub naciśnij klawisz F4). Przycisk wygląda następująco: ![przycisk aplikacji odświeżania systemu Windows](../debugger/media/js_refresh.png "JS_Refresh").  
  
     Ponowne ładowanie stron aplikacji i symulator lub w emulatorze telefonu zwraca na pierwszy plan.  
  
     Aby uzyskać więcej informacji na temat funkcji odświeżania, zobacz [odświeżanie aplikacji (JavaScript)](../debugger/refresh-an-app-javascript.md).  
  
##  <a name="SelectingElements"></a>Zaznaczanie elementów  
 Podczas debugowania aplikacji, możesz wybrać elementy modelu DOM na trzy sposoby:  
  
-   Klikając elementy bezpośrednio w oknie Eksploratora modelu DOM (lub przy użyciu klawiszy strzałek).  
  
-   Za pomocą **wybierz Element** przycisk (Ctrl + B).  
  
-   Za pomocą `select` polecenia, które jest jednym z [polecenia konsoli JavaScript](../debugger/javascript-console-commands.md).  
  
 Gdy używasz okno Eksploratora DOM wybierz elementy, a wskaźnik myszy w elemencie odpowiadającego mu elementu zostanie wyróżniona w uruchomionej aplikacji. Należy kliknąć opcję w elemencie w programie DOM Explorer, aby go zaznaczyć, lub można użyj klawiszy strzałek, aby zaznaczyć, a następnie wybierz elementy. Elementy można wybrać w programie DOM Explorer, za pomocą **Select element** przycisku. Na poniższej ilustracji pokazano **wybierz Element** przycisku.  
  
 ![Wybierz przycisk elementu w Eksploratorze DOM](../debugger/media/js_dom_select_element_button.png "JS_DOM_Select_Element_Button")  
  
 Po kliknięciu **Select element** (lub naciśnij klawisze Ctrl + B), spowoduje to zmianę trybu wyboru, w którym można wybrać elementu w Eksploratorze DOM, klikając go w uruchomionej aplikacji. Powrót do trybu normalnego wyboru zmiany trybu po jednym kliknięciem. Po kliknięciu **Select element**, aplikacja jest dostępna na pierwszy plan i kursor zmienia się na odzwierciedlają nowy tryb zaznaczania. Po kliknięciu elementu obramowane Eksploratora modelu DOM zwraca na pierwszy plan określony wybranego elementu.  
  
 Przed wybraniem **wybierz Element**, można określić opcję podświetlania elementów w uruchomionej aplikacji przełączając **wyświetlania strony sieci web prezentuje** przycisku. Na poniższej ilustracji przedstawiono ten przycisk. Najważniejsze funkcje są domyślnie wyświetlane.  
  
 ![Strony sieci web wyświetlaną wyróżnia przycisk](../debugger/media/js_dom_display_highlights_button.png "JS_DOM_Display_Highlights_Button")  
  
 W przypadku Wyróżnij elementy wyróżniono elementy, które umieść kursor nad w symulatorze. Kolory dla wyróżnionych elementów jest zgodny z modelem pola, w **układu** na karcie Narzędzia DOM Explorer.  
  
> [!NOTE]
>  Wyróżnianie elementów poprzez ustawienie nad nimi wskaźnika jest obsługiwane tylko częściowo w Emulator Windows Phone.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji w programie Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)   
 [Odświeżanie aplikacji (JavaScript)](../debugger/refresh-an-app-javascript.md)   
 [Debugowanie kontrolki WebView](../debugger/debug-a-webview-control.md)   
 [Skróty klawiaturowe](../debugger/keyboard-shortcuts-html-and-javascript.md)   
 [Polecenia konsoli JavaScript](../debugger/javascript-console-commands.md)   
 [Debugowanie przykładowy kod HTML, CSS i JavaScript](../debugger/debug-html-css-and-javascript-sample-code.md)   
 [Pomoc techniczna i ułatwień dostępu](http://msdn.microsoft.com/library/tzbxw1af\(VS.120\).aspx)