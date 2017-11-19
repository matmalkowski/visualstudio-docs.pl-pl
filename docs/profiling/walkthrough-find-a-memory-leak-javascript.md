---
title: "Wskazówki: Znajdowanie wycieku pamięci (JavaScript) | Dokumentacja firmy Microsoft"
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
helpviewer_keywords: memory leaks, JavaScript example
ms.assetid: f595412f-776b-49a2-8433-ea0062c6904d
caps.latest.revision: "31"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1f31221f52e9e944dcfc82c98d18e2cf5ec263bf
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/11/2017
---
# <a name="walkthrough-find-a-memory-leak-javascript"></a>Wskazówki: Znajdowanie wycieku pamięci (JavaScript)
![Ma zastosowanie do systemu Windows i Windows Phone](../debugger/media/windows_and_phone_content.png "windows_and_phone_content")  
  
 W tym przewodniku poprowadzi Cię przez proces identyfikacji i rozwiązywania problemu proste pamięci za pomocą analizator pamięci JavaScript. Analizator pamięci JavaScript jest dostępna w programie Visual Studio dla aplikacji platformy uniwersalnej systemu Windows dla systemu Windows przy użyciu języka JavaScript. W tym scenariuszu utworzysz aplikację, która zachowuje niepoprawnie elementy modelu DOM w pamięci, zamiast usuwania elementów szybkością taką, w którym są tworzone.  
  
 Chociaż przyczynę przeciek pamięci w tej aplikacji jest bardzo specyficznego, kroki opisane w tym miejscu pokazują przepływu pracy, który zazwyczaj skutecznie izolowanie obiektów, które są przeciek pamięci.  
  
### <a name="running-the-javascript-memory-analyzer-test-app"></a>Aplikację test analizator pamięci JavaScript  
  
1.  W programie Visual Studio, wybierz **pliku**, **nowy**, **projektu**.  
  
2.  Wybierz **JavaScript** w okienku po lewej stronie, a następnie wybierz pozycję **Windows**, **systemu Windows 8**, następnie albo **uniwersalnych** lub  **Aplikacje Windows Phone**.  
  
    > [!IMPORTANT]
    >  Wyniki użycia pamięci, które są wyświetlane w tym temacie są sprawdzane pod względem aplikacji systemu Windows 8.  
  
3.  Wybierz **pusta aplikacja** szablonu projektu w środkowym okienku.  
  
4.  W **nazwa** polu Określ nazwę, taką jak `JS_Mem_Tester`, a następnie wybierz pozycję **OK**.  
  
5.  W **Eksploratora rozwiązań**, otwórz default.html i wklej następujący kod między \<treści > tagów:  
  
    ```html  
    <div class="wrapper">  
        <div id="item"></div>  
        <button class="memleak" style="display: block" >Leak Memory</button>  
    </div>  
    ```  
  
    > [!IMPORTANT]
    >  Jeśli używasz szablonu aplikacji uniwersalnej Windows 8.1, musisz zaktualizować kod HTML i CSS w obu. System Windows i. Projekty WindowsPhone.  
  
6.  Otwórz default.css i Dodaj następujący kod CSS:  
  
    ```css  
    .memleak {  
        position: absolute; top: 100px; left: 100px;  
    }  
    ```  
  
7.  Otwórz default.js i Zastąp cały kod z tego kodu:  
  
    ```javascript  
    (function () {  
        "use strict";  
  
        var app = WinJS.Application;  
        var activation = Windows.ApplicationModel.Activation;  
  
        var wrapper;  
        var elem;  
  
        app.onactivated = function (args) {  
            if (args.detail.kind === activation.ActivationKind.launch) {  
                if (args.detail.previousExecutionState !== activation.ApplicationExecutionState.terminated) {  
                } else {  
                }  
                args.setPromise(WinJS.UI.processAll());  
  
                elem = document.getElementById("item");  
                wrapper = document.querySelector(".wrapper");  
                var btn = document.querySelector(".memleak");  
                btn.addEventListener("click", btnHandler);  
                run();  
            }  
        };  
  
        app.oncheckpoint = function (args) {  
        };  
  
        app.start();  
  
        function run() {  
            initialize();  
            load();  
        }  
  
        function initialize() {  
  
            if (wrapper != null) {  
                elem.removeNode(true);  
            }  
        }  
  
        function load() {  
  
            var newDiv = document.createElement("div");  
  
            newDiv.style.zIndex = "-1";  
            newDiv.id = "item";  
  
            wrapper.appendChild(newDiv);  
        }  
  
        function btnHandler(args) {  
            run();  
        }  
  
    })();  
    ```  
  
8.  Wybierz klawisz F5, aby rozpocząć debugowania. Sprawdź, czy **przeciek pamięci** przycisku zostanie wyświetlone na stronie.  
  
9. Przełącza z powrotem do programu Visual Studio (Alt + Tab), a następnie wybierz Shift + F5, aby zatrzymać debugowanie.  
  
     Teraz, gdy upewnieniu się, że aplikacja działa, należy zbadać użycie pamięci.  
  
### <a name="analyzing-the-memory-usage"></a>Analizowanie danych użycia pamięci  
  
1.  Na **debugowania** paska narzędzi w **Rozpocznij debugowanie** wybierz cel debugowania dla projektu zaktualizowane: dowolny emulatory Windows Phone lub **symulatora**.  
  
    > [!TIP]
    >  W przypadku aplikacji platformy uniwersalnej systemu Windows można także **komputera lokalnego** lub **maszyny zdalnej** na tej liście. 
  
2.  Na **debugowania** menu, wybierz **profilera wydajności...** .  
  
3.  W **dostępne narzędzia**, wybierz **pamięci JavaScript**, a następnie wybierz pozycję **Start**.  
  
     W tym samouczku jest będzie dołączanie analizator pamięci do projektu startowego. Informacje o innych opcji, takich jak dołączanie analizator pamięci do zainstalowanych aplikacji, zobacz [pamięci JavaScript](../profiling/javascript-memory.md).  
  
     Po uruchomieniu analizator pamięci można napotkać Kontrola konta użytkownika, Twoje uprawnienia do uruchamiania VsEtwCollector.exe żądania. Wybierz **tak**.  
  
4.  Wybierz **przeciek pamięci** przycisk cztery razy pod rząd.  
  
     Po wybraniu przycisku, Obsługa kodu w pracy wykonuje default.js, która spowoduje przeciek pamięci zdarzeń. Służy to do celów diagnostycznych.  
  
    > [!TIP]
    >  Powtarzanie scenariusz, który chcesz przetestować przeciek pamięci ułatwia odfiltrowywania postrzegać informacje, takie jak obiekty, które są dodawane do sterty podczas inicjowania aplikacji lub podczas ładowania strony.  
  
5.  W uruchomionej aplikacji Przełącz się do programu Visual Studio (Alt + Tab).  
  
     Analizator pamięci JavaScript Wyświetla informacje na nowej karcie w programie Visual Studio.  
  
     Wykres pamięci w tym użycie pamięci przez widok podsumowania przedstawia proces wraz z upływem czasu. Widok zawiera również poleceń, takich jak **wykonaj migawkę sterty**. Migawka zawiera szczegółowe informacje na temat użycia pamięci w określonym czasie. Aby uzyskać więcej informacji, zobacz [pamięci JavaScript](../profiling/javascript-memory.md).  
  
6.  Wybierz **wykonaj migawkę sterty**.  
  
7.  Przełącz się do aplikacji i wybierz **przeciek pamięci**.  
  
8.  Przełącz się do programu Visual Studio i wybierz **wykonaj migawkę sterty** ponownie.  
  
     Na ilustracji przedstawiono migawką bazową (#1) i migawki nr 2.  
  
     ![Linia bazowa snapshot i snapshot 2](../profiling/media/js_mem_app_snapshot2.png "JS_Mem_App_Snapshot2")  
  
    > [!NOTE]
    >  Emulator Windows Phone nie są wyświetlane zrzut ekranu aplikacji z chwili utworzenia migawki.  
  
9. Przełącz się do aplikacji i wybierz **przeciek pamięci** przycisk ponownie.  
  
10. Przełącz się do programu Visual Studio i wybierz **wykonaj migawkę sterty** raz trzeci.  
  
    > [!TIP]
    >  Wykonując innej migawki, w tym przepływie pracy można odfiltrować zmian z migawką bazową na drugi migawki nieskojarzone z przecieki pamięci. Na przykład może być oczekiwany zmian, takich jak Aktualizowanie nagłówków i stopek na stronie, która spowoduje wygenerowanie pewne zmiany użycia pamięci, ale może być związana z przecieki pamięci.  
  
     Na ilustracji przedstawiono migawki nr 2 i &#3; migawki.  
  
     ![Migawki 2 i 3 migawki](../profiling/media/js_mem_app_snapshot3.png "JS_Mem_App_Snapshot3")  
  
11. W programie Visual Studio, wybierz **zatrzymać** Aby zatrzymać profilowanie.  
  
12. W programie Visual Studio Porównaj migawki. Migawki #2 zawiera następujące czynności:  
  
    -   Rozmiar stosu (reprezentowany przez czerwona strzałka w górę na lewym) wzrosła o kilka KB w porównaniu do migawki nr 1.  
  
        > [!IMPORTANT]
        >  Wartości użycie pamięci dokładnie dla rozmiaru sterty zależą od docelowego debugowania.  
  
    -   Zwiększa liczbę obiektów na stercie (reprezentowany przez czerwona strzałka w górę na prawo) w porównaniu do migawki nr 1. Jeden obiekt został dodany (+ 1), a żadne obiekty nie zostały usunięte (-0).  
  
     Migawki #3 przedstawiono poniżej:  
  
    -   Rozmiar sterty wzrosło ponownie za kilka kilkuset bajtów w porównaniu do migawki nr 2.  
  
    -   Zwiększa liczbę obiektów na stercie ponownie w porównaniu do migawki nr 2. Jeden obiekt został dodany (+ 1), a żadne obiekty nie zostały usunięte (-0).  
  
13. W migawce nr 3, wybierz tekst łącza po prawej stronie, która znajduje się wartość + 1 i - 0 obok czerwona strzałka w górę.  
  
     ![Link do innego widoku sterty obiektów](../profiling/media/js_mem_app_link.png "JS_Mem_App_Link")  
  
     Spowoduje to otwarcie różnicowej widoku obiektów na stercie o nazwie **migawki nr 3 - migawki nr 2**, z widokiem typy wyświetlane domyślnie. Domyślnie możesz wyświetlić listę obiektów dodanych do stosu między migawki nr 2 i &#3; migawki.  
  
14. W **zakres** filtrów, wybierz **obiekty pozostałe z migawki nr 2**.  
  
15. Otwórz obiekt HTMLDivElement w górnej części drzewa obiektów, jak pokazano poniżej.  
  
     ![Widok porównania obiektu liczba na stercie](../profiling/media/js_mem_app_typesdiff.png "JS_Mem_App_TypesDiff")  
  
     Ten widok przedstawia pomocne informacje dotyczące przeciek pamięci, takie jak następujące:  
  
    -   Ten widok przedstawia element DIV o identyfikatorze `item`, i rozmiaru zachowanego dla obiekt jest kilka kilkuset bajtów (dokładną wartość różnią się).  
  
    -   Ten obiekt jest obiektem pozostałość z migawki nr 2 i reprezentuje potencjalny wyciek pamięci.  
  
     Pewna znajomość aplikacji pomaga w tym momencie: wybieranie **przeciek pamięci** przycisk Usuń DIV element i Dodaj element, aby kod nie wydają się działać w prawo (to znaczy go występuje przeciek pamięci). Następna sekcja wyjaśniono, jak rozwiązać ten problem.  
  
    > [!TIP]
    >  Czasami znajdowania obiektu w odniesieniu do `Global` obiektu może pomóc w zidentyfikowaniu tego obiektu. Aby to zrobić, otwórz menu skrótów dla identyfikatora, a następnie wybierz **Pokaż w widoku elementów głównych**.  
  
##  <a name="FixingMemory"></a>Rozwiązania problemu pamięci  
  
1.  Przy użyciu danych ujawniony przez profiler, należy zbadać kod, który jest odpowiedzialny za usuwanie elementów modelu DOM o identyfikatorze "item". Występuje w `initialize()` funkcji.  
  
    ```javascript  
    function initialize() {  
  
        if (wrapper != null) {  
            elem.removeNode(true);  
        }  
    }  
    ```  
  
     `elem.removeNode(true)`być może, nie działa prawidłowo. Sprawdź, jak kod jest buforowanie elementu DOM i Znajdź problem; Odwołanie do elementu pamięci podręcznej nie są aktualizowane.  
  
2.  W default.js, Dodaj następujący wiersz kodu funkcji obciążenia, bezpośrednio przed wywołaniem `appendChild`:  
  
    ```javascript  
    elem = newDiv;  
    ```  
  
     Ten kod aktualizacji odwołania do elementu pamięci podręcznej, aby element poprawnie zostanie usunięty po wybraniu **przeciek pamięci** przycisku. Kompletny kod dla funkcji obciążenia teraz wygląda następująco:  
  
    ```javascript  
    function load() {  
  
        wrapper = document.querySelector(".wrapper");  
  
        var newDiv = document.createElement("div");  
  
        newDiv.style.zIndex = "-1";  
        newDiv.id = "item";  
        elem = newDiv;  
  
        wrapper.appendChild(newDiv);  
    }  
    ```  
  
3.  Na **debugowania** menu, wybierz **wydajności i diagnostyki**.  
  
4.  W **dostępne narzędzia**, wybierz **pamięci JavaScript**, a następnie wybierz pozycję **Start**.  
  
5.  Postępuj zgodnie z tym samym jako przed do trzech migawek. Poniżej przedstawiono kroki:  
  
    1.  W aplikacji, wybierz **przeciek pamięci** przycisk cztery razy pod rząd.  
  
    2.  Przełącz się do programu Visual Studio i wybierz **wykonaj migawkę sterty** dla migawki linii bazowej.  
  
    3.  W aplikacji, wybierz **przeciek pamięci** przycisku.  
  
    4.  Przełącz się do programu Visual Studio i wybierz **wykonaj migawkę sterty** dla drugiego migawki.  
  
    5.  W aplikacji, wybierz **przeciek pamięci** przycisku.  
  
    6.  Przełącz się do programu Visual Studio i wybierz **wykonaj migawkę sterty** trzeci migawki.  
  
     Migawki #3 zawiera obecnie rozmiar stosu jako **bez zwiększania** z migawki nr 2, a obiekt są liczone jak + 1 / -1, co oznacza, że jeden obiekty został dodany i jeden obiekt został usunięty. To jest zamierzone zachowanie.  
  
     Na poniższej ilustracji przedstawiono migawki nr 2 i &#3; migawki.  
  
     ![Migawki przedstawiający przeciek pamięci stałej](../profiling/media/js_mem_app_fixed_snapshot3.png "JS_Mem_App_Fixed_Snapshot3")  
  
## <a name="see-also"></a>Zobacz też  
 [Pamięć języka JavaScript](../profiling/javascript-memory.md)