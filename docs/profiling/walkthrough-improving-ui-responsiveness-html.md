---
title: "Wskazówki: Poprawa czasu odpowiedzi interfejsu użytkownika (HTML) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- performance tools, JavaScript [UWP apps]
- performance, JavaScript [UWP apps]
- performance, HTML [UWP apps]
- performance tools, HTML [UWP apps]
ms.assetid: 7e5a2524-dbf5-4a40-b5d6-2d1ed7fff3de
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8b7e6a534d1a9c3b665b72f0af8257c0915e7a29
ms.sourcegitcommit: ebe9fb5eda724936f7a059d35d987c29dffdb50d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2017
---
# <a name="walkthrough-improving-ui-responsiveness-html"></a>Wskazówki: Poprawa czasu odpowiedzi interfejsu użytkownika (HTML)
W tym przewodniku poprowadzi Cię przez proces identyfikacji i rozwiązywania problemu z wydajnością przy użyciu [profiler czasu odpowiedzi interfejsu użytkownika HTML](../profiling/html-ui-responsiveness.md). Profiler jest dostępna w programie Visual Studio dla aplikacji platformy uniwersalnej systemu Windows przy użyciu języka JavaScript. W tym scenariuszu utworzysz aplikację test wydajności, która aktualizuje zbyt często elementy modelu DOM i używasz profilera, aby zidentyfikować i rozwiązać ten problem.  
  
### <a name="creating-and-running-the-performance-test-app"></a>Tworzenie i uruchamianie wykonywania testów aplikacji  
  
1.  W programie Visual Studio Utwórz nowy projekt JavaScript uniwersalnych systemu Windows. (Wybierz **pliku / New / Project**. Wybierz **JavaScript** w okienku po lewej stronie, a następnie wybierz pozycję **Windows**, **systemu Windows 10**, następnie albo **uniwersalnych**, lub  **Windows Phone**.  
  
2.  > [!IMPORTANT]
    >  Wyniki diagnostyki wyświetlane w tym temacie przedstawiono dla aplikacji systemu Windows 8.  
  
3.  Wybierz jedną z szablonów pustego projektu w środkowym okienku, takich jak **pusta aplikacja**.  
  
4.  W **nazwa** polu Określ nazwę, taką jak `JS_Perf_Tester`, a następnie wybierz pozycję **OK**.  
  
5.  W **Eksploratora rozwiązań**, otwórz default.html i wklej następujący kod między \<treści > tagów:  
  
    ```html  
    <div class="wrapper">  
        <button id="content">Waiting for values</button>  
    </div>  
    ```  
  
6.  Otwórz default.css i Dodaj następujący kod CSS:  
  
    ```css  
    #content {  
        margin-left: 100px;  
        margin-top: 100px;  
    }  
    ```  
  
7.  Otwórz default.js i Zastąp cały kod z tego kodu:  
  
    ```javascript  
    (function () {  
        "use strict";  
  
        var app = WinJS.Application;  
        var activation = Windows.ApplicationModel.Activation;  
  
        var content;  
        var wrapper;  
  
        app.onactivated = function (args) {  
            if (args.detail.kind === activation.ActivationKind.launch) {  
                if (args.detail.previousExecutionState !== activation.ApplicationExecutionState.terminated) {  
  
                    content = document.getElementById("content");  
                    wrapper = document.querySelector(".wrapper");  
  
                    content.addEventListener("click", handler);  
  
                } else {  
                }  
  
                args.setPromise(WinJS.UI.processAll());  
            }  
        };  
  
        app.oncheckpoint = function (args) {  
        };  
  
        app.start();  
  
        var idx = 0;  
        var count = 0;  
        var max = 5000;  
        var text = ["what", "is", "the", "Matrix?"];  
        var color = ["red", "crimson", "maroon", "purple"];  
  
        function increment() {  
  
            setTimeout(function () {  
  
                idx++;  
                count++;  
  
                if (idx > 3) { idx = 0; }  
                if (count < max) { increment(); }  
  
            }, 1000);  
        }  
  
        function setValues() {  
  
            content = document.getElementById("content");  
            content.removeNode(true);  
  
            var newNode = document.createElement("button");  
            newNode.id = "content";  
            newNode.textContent = text[idx];  
            //newNode.textContent = getData();  
            newNode.style.backgroundColor = color[idx];  
            //newNode.style.animationName = "move";  
            //count++;  
  
            wrapper.appendChild(newNode);  
  
        }  
  
        function update() {  
  
            setTimeout(function () {  
  
                setValues();  
                if (count < max) { update(); }  
            });  
        }  
  
        function handler(args) {  
  
            content.textContent = "eenie";  
            increment();  
            update();  
        }  
  
    })();  
  
    ```  
  
8.  Wybierz klawisz F5, aby rozpocząć debugowania. Sprawdź, czy **oczekiwanie na wartości** przycisku zostanie wyświetlone na stronie.  
  
9. Wybierz **oczekiwanie na wartości** i sprawdź, czy tekst przycisku i kolor około aktualizacji raz na sekundę. To jest celowe.  
  
10. Przełącza z powrotem do programu Visual Studio (Alt + Tab), a następnie wybierz Shift + F5, aby zatrzymać debugowanie.  
  
     Teraz, gdy upewnieniu się, że aplikacja działa, jego wydajność, można sprawdzić za pomocą profilera.  
  
### <a name="analyzing-performance-data"></a>Analizowanie danych dotyczących wydajności  
  
1.  Na **debugowania** paska narzędzi w **Rozpocznij debugowanie** listy, wybierz jedną z emulatory Windows Phone lub **symulatora**.  
  
2.  Na **debugowania** menu, wybierz **wydajności i diagnostyki**.  
  
3.  W **dostępne narzędzia**, wybierz **czasu odpowiedzi interfejsu użytkownika HTML**, a następnie wybierz pozycję **Start**.  
  
     W tym samouczku jest będzie dołączanie profilera do projektu startowego. Informacje o innych opcji, takich jak dołączanie profilera do aplikacji zainstalowanych zawiera [czasu odpowiedzi interfejsu użytkownika HTML](../profiling/html-ui-responsiveness.md).  
  
     Podczas uruchamiania profilera można napotkać Kontrola konta użytkownika, Twoje uprawnienia do uruchamiania VsEtwCollector.exe żądania. Wybierz **tak**.  
  
4.  W uruchomionej aplikacji, wybierz **oczekiwanie na wartości** i poczekaj około 10 sekund. Upewnij się, że tekst przycisku i kolor około aktualizacji raz na sekundę.  
  
5.  W uruchomionej aplikacji Przełącz się do programu Visual Studio (Alt + Tab).  
  
6.  Wybierz **zatrzymać zbieranie**.  
  
     Profiler Wyświetla informacje na nowej karcie w programie Visual Studio. Po wyświetleniu wykorzystanie procesora CPU i dane przepływność wizualną (kl. / s), można łatwo zidentyfikować trendy kilka:  
  
    -   Użycie procesora CPU zwiększa się znacznie po około 3 sekundy (po naciśnięciu **oczekiwanie na wartości** przycisku) i zawiera wyraźnego zdarzeń (spójne kombinację skryptów, style i zdarzenia renderowania) z tego punktu.  
  
    -   Nie ma wpływu na przepływność wizualną i klatek na Sekundę nadal 60 w całym (to znaczy, że nie ma żadnych elementów usuniętych ramek).  
  
     Oto typowy części Wykres wykorzystania CPU, aby dowiedzieć się, aplikacja czynności w tym okresie intensywnego działania.  
  
7.  Wybierz jedną do dwóch drugiej części środku Wykres wykorzystania CPU (albo kliknij przycisk i przeciągania lub użyj klawiszy kartę i strzałkę). Na poniższej ilustracji przedstawiono wykres wykorzystania CPU po dokonaniu wyboru. Obszar nieudostępnione jest zaznaczenie.  
  
     ![Wykres wykorzystania CPU](../profiling/media/js_htmlviz_app_cpu.png "JS_HTMLViz_App_CPU")  
  
8.  Wybierz **powiększać**.  
  
     Zmiany wykresu Pokaż szczegółowo w wybranym okresie. Na poniższej ilustracji przedstawiono wykres wykorzystania CPU po powiększeniu. (Określonych danych może się różnić, ale ogólne wzorzec będzie widoczna).  
  
     ![W widoku powiększony](../profiling/media/js_htmlviz_app_zoom.png "JS_HTMLViz_App_Zoom")  
  
     Szczegóły osi czasu, w dolnym okienku przedstawiono przykład szczegółów dla wybranego okresu.  
  
     ![Szczegóły osi czasu](../profiling/media/js_htmlviz_app_details.png "JS_HTMLViz_App_Details")  
  
     Zdarzenia w szczegółach osi czasu potwierdzić widoczne tendencji Wykres wykorzystania CPU: istnieje wiele zdarzeń odbywa się w krótkich okresach czasu. Oś czasu widoku szczegółów pokazuje, że te zdarzenia są `Timer`, `Layout`, i `Paint` zdarzenia.  
  
9. Użyj menu kontekstowe (lub kliknij prawym przyciskiem myszy) jednego z `Timer` zdarzenia w dolnym okienku i wybierz polecenie **filtr, aby zdarzenia**. Na poniższej ilustracji przedstawiono przykład szczegóły typowe dla jednego z `Timer` zdarzenia w tej aplikacji testu.  
  
     ![Zdarzenie czasomierza](../profiling/media/js_htmlviz_app_timer.png "JS_HTMLViz_App_Timer")  
  
     Różne okoliczności mogą zgromadzone z danych. Na przykład:  
  
    -   Każdy `Timer` zdarzeń, oznaczanie kolorami, aby zidentyfikować go jako zdarzenie skryptów, zawiera wywołanie `document.createElement`, a następnie obliczania styl i wywołanie `style.backgroundColor` i `appendChild()`.  
  
    -   W krótkim czasie przedział wybrane (około jednej do dwóch sekund), są wielu `Timer`, `Layout`, i `Paint` zdarzenia. `Timer` Zdarzenia występują daleko częściej niż jedna aktualizacja, na sekundę, gdy jest widoczny widoczny po uruchomieniu aplikacji i wybierz **oczekiwanie na wartości** przycisku.  
  
10. Aby zbadać, wybierz link, aby funkcja anonimowa dla jednego z `Timer` zdarzenia w dolnym okienku po lewej stronie. Następująca funkcja otworzy się w default.js:  
  
    ```javascript  
    function update() {  
  
        setTimeout(function () {  
  
            setValues();  
            if (count < max) { update(); }  
        });  
    }  
    ```  
  
     Ta funkcja cykliczne konfiguruje pętli, które wywołuje `setValues()` funkcji, która aktualizuje przycisku w interfejsie użytkownika. Sprawdzając zdarzeń czasomierza innego profilera, użytkownik stwierdza, że większość lub wszystkie zdarzenia czasomierza w wyniku tego kod, który działa zbyt często, więc prawdopodobnie prawdopodobnie tutaj pochodzi ten problem.  
  
### <a name="fixing-the-performance-issue"></a>Rozwiązania problemu wydajności  
  
1.  Zastąp `update()` funkcja następującym kodem:  
  
    ```javascript  
    function update() {  
  
        setTimeout(function () {  
  
            setValues();  
            if (count < max) { update(); }  
        }, 1000 );  
    }  
    ```  
  
     Ta wersja stałym kod zawiera opóźnienie 1000 milisekund, który został pominięty w poprzedniej wersji kodu, co spowoduje użycie wartości opóźnienia domyślne. Z danych profilera, wygląda na to, że wartość domyślna to zero milisekund, które spowodowały `setValues()` funkcji, aby uruchomić zbyt często.  
  
2.  Ponownie uruchom profiler czasu odpowiedzi interfejsu użytkownika HTML i sprawdź wykres wykorzystania CPU. Można znaleźć znikną nadmiernego zdarzeń, czy użycie procesora CPU spadła prawie zero. Stałe!  
  
## <a name="see-also"></a>Zobacz też  
 [Czas odpowiedzi interfejsu użytkownika HTML](../profiling/html-ui-responsiveness.md)