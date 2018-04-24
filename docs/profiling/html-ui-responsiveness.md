---
title: Analizowanie czasu odpowiedzi interfejsu użytkownika HTML w aplikacji platformy uniwersalnej systemu Windows | Dokumentacja firmy Microsoft
ms.custom: H1Hack27Feb2017
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- JavaScript
helpviewer_keywords:
- performance, JavaScript [UWP apps]
- performance tools, JavaScript [UWP apps]
- UI Responsiveness Profiler [JavaScript]
- profiler, UI responsiveness [JavaScript]
- profiler, JavaScript [UWP apps]
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 7dd31d94552895d42c803df81e1e66cd9a3947f0
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="analyze-html-ui-responsiveness-in-universal-windows-apps"></a>Analizowanie czasu odpowiedzi interfejsu użytkownika HTML w aplikacji uniwersalnych systemu Windows
W tym temacie opisano, jak do izolowania problemów z wydajnością w aplikacjach za pomocą Profiler czasu odpowiedzi interfejsu użytkownika, narzędzie wydajność, dostępna dla uniwersalnych aplikacji systemu Windows.  
  
 Profiler czasu odpowiedzi interfejsu użytkownika można wyizolować problemy, takie jak problemy dotyczące czasu odpowiedzi interfejsu użytkownika lub platformy efekty uboczne, których zwykle występują w przypadku następujące symptomy:  
  
-   Brak reakcji w interfejsie użytkownika. Aplikacja może wolno odpowiadać wątku interfejsu użytkownika jest wprowadzenie zablokowany. Kilka rzeczy, które mogłyby zablokować wątku interfejsu użytkownika to nadmiernego synchroniczne kod JavaScript, nadmiernego układ CSS lub pracy obliczania CSS, synchroniczne żądań XHR, wyrzucanie elementów bezużytecznych, nadmiernego paint razy lub kod JavaScript obciążenie procesora.  
  
-   Powolna czasu ładowania aplikacji lub strony. Jest to zazwyczaj spowodowane nadmiernego czas ładowania zasobów.  
  
-   Visual aktualizacje, które są rzadziej niż oczekiwano. Dzieje się tak, jeśli wątek interfejsu użytkownika jest zbyt zajęty, aby zachować płynne szybkości. Na przykład jeśli trwa wątku interfejsu użytkownika mogą być opuszczane ramki. Niektóre wątku bez interfejsu użytkownika pracy, takich jak żądania sieci, dekodowanie obrazu, oraz farby można również ograniczyć częstotliwości aktualizacji visual. (Nie wszystkie rysowania odbywa się w wątku interfejsu użytkownika).  
  
##  <a name="RunningProfiler"></a> Uruchom narzędzie czasu odpowiedzi interfejsu użytkownika HTML  
 Jeśli masz pracy aplikacji platformy uniwersalnej systemu Windows, Otwórz w programie Visual Studio, można użyć narzędzia czasu odpowiedzi interfejsu użytkownika HTML.  
  
1.  Jeśli korzystasz z aplikacji z programu Visual Studio na **standardowe** paska narzędzi w **Rozpocznij debugowanie** wybierz cel wdrożenia, takich jak **komputera lokalnego** lub **Urządzenia**.  
  
2.  Na **debugowania** menu, wybierz **profilera wydajności...** .  
  
     Jeśli chcesz zmienić element docelowy analizy dla profilera, wybierz**zmienić docelowy**.  
  
     ![Zmień docelowy analizy](../profiling/media/js_tools_target.png "JS_Tools_Target")  
  
     Poniższe opcje są dostępne dla obiektu docelowego analizy:  
  
    -   **Projekt startowy**. Wybierz tę opcję, aby przeanalizować bieżący projekt startowy. Jeśli korzystasz z aplikacji na urządzeniu lub komputerze zdalnym, należy użyć to ustawienie, która jest wartością domyślną.  
  
    -   **Uruchomiona aplikacja**. Wybierz tę opcję, aby wybrać z listy uruchomionych aplikacji aplikacji platformy uniwersalnej systemu Windows. Nie można użyć tej opcji, po uruchomieniu aplikacji na urządzeniu lub komputerze zdalnym.  
  
         Ta opcja umożliwia analizowanie wydajności aplikacji, które są uruchomione na komputerze, jeśli nie masz dostępu do kodu źródłowego.  
  
    -   **Aplikacja zainstalowana**. Wybierz tę opcję, aby wybrać zainstalowaną aplikację, która do przeanalizowania. Nie można użyć tej opcji, po uruchomieniu aplikacji na urządzeniu lub komputerze zdalnym.  
  
         Ta opcja umożliwia analizowanie wydajności aplikacji, które zainstalowano na tym komputerze, jeśli nie masz dostępu do kodu źródłowego. Ta opcja może także służyć tylko umożliwia analizowanie wydajności z dowolnych aplikacji poza tworzenia własnych aplikacji.  
  
3.  Z **dostępne narzędzia**, wybierz pozycję **czasu odpowiedzi interfejsu użytkownika HTML**, a następnie wybierz pozycję **Start**.  
  
4.  Po uruchomieniu Profiler czasu odpowiedzi interfejsu użytkownika okno Kontrola konta użytkownika może zażądać Twoje uprawnienia do uruchamiania programu Visual Studio ETW Collector.exe. Wybierz **tak**.  
  
     Interakcji z aplikacją do przetestowania tego scenariusza odpowiednich wydajności. Szczegółowy przepływ pracy dla [wyizolować problem czasu odpowiedzi interfejsu użytkownika](#Workflow) i [wyizolować problem przepływność wizualną](#IsolateVisualThroughput).  
  
5.  Przełącz się do programu Visual Studio, naciskając klawisze Alt + Tab.  
  
6.  Aby zatrzymać profilowanie profilera zebrane dane aplikacji i widok, wybierz **zatrzymać zbieranie**.  
  
##  <a name="IsolateAnIssue"></a> Izolowanie problemu  
 W poniższej sekcji przedstawiono sugestie ułatwiające wyizolować problemy z wydajnością. Opis krok po kroku instrukcje zidentyfikować i rozwiązać problemy z wydajnością przy użyciu przykładowych testowania aplikacji, zobacz [wskazówki: czas odpowiedzi poprawy interfejsu użytkownika (HTML)](../profiling/walkthrough-improving-ui-responsiveness-html.md).  
  
###  <a name="Workflow"></a> Izolowanie problem czasu odpowiedzi interfejsu użytkownika  
 Poniższe kroki zawierają sugerowane przepływu pracy, które mogą ułatwić wydajniej wykorzystywać Profiler czasu odpowiedzi interfejsu użytkownika:  
  
1.  Otwórz aplikację w programie Visual Studio.  
  
2.  Testowanie aplikacji problemów czasu odpowiedzi interfejsu użytkownika. (Naciśnij klawisze Ctrl + F5, aby uruchomić aplikację bez debugowania).  
  
     Jeśli napotkasz problem kontynuować testowanie próby zawęzić przedział czasu, w którym występuje problem, lub do identyfikowania wyzwalacze, które powodują zachowanie.  
  
3.  Przełącz się do programu Visual Studio (naciśnij klawisze Alt + Tab) i zatrzymać aplikację (Shift + F5).  
  
4.  Opcjonalnie dodaj znaczniki użytkownika przy użyciu kodu [oznaczyć kod analizy](#ProfileMark).  
  
    > [!TIP]
    >  Znaczniki użytkowników może pomóc zidentyfikować problem czas odpowiedzi podczas przeglądania danych profilera. Na przykład można dodać znacznik użytkownika na początku i na końcu sekcji kodu, który jest przyczyną problemu czas odpowiedzi.  
  
5.  Uruchom Profiler czasu odpowiedzi interfejsu użytkownika, postępując zgodnie z instrukcjami w poprzedniej sekcji.  
  
6.  Umieść aplikacji w stan, który powoduje problem czasu odpowiedzi interfejsu użytkownika.  
  
7.  Przełącz się do programu Visual Studio (naciśnij klawisze Alt + Tab) i wybierz **zatrzymać zbieranie** na karcie profilera Profiler czasu odpowiedzi interfejsu użytkownika.  
  
8.  Jeśli dodano znaczniki użytkownika, będą wyświetlane w [wyświetlania osi czasu sesji diagnostycznej](#Ruler) profilera. Na poniższej ilustracji przedstawiono znacznik pojedynczego użytkownika używana do określania określonej operacji w kodzie.  
  
     ![Diagnostyka linijki przedstawiający znacznik użytkownika](../profiling/media/js_htmlvizprofiler_usermark.png "JS_HTMLVizProfiler_UserMark")  
  
9. Identyfikowanie obszaru zainteresowania oś czasu i wykresy profilera przy użyciu znaków użytkownika, zdarzenia cyklu życia aplikacji lub widoczny na wykresach danych. Oto wskazówki, które ułatwiają analizowanie i używania danych na wykresach:  
  
    -   Użyj [wyświetlania osi czasu sesji diagnostycznej](#Ruler) Aby wyświetlić [oznaczyć kod analizy](#ProfileMark), zdarzenia cyklu życia aplikacji i skojarzonych osi czasu dla tych zdarzeń i oś czasu dla danych w innych wykresów.  
  
    -   Użyj [Wykres wykorzystania CPU](#CPUutilization) Aby wyświetlić ogólne informacje o aktywności Procesora i typ pracy go obsługuje w danym okresie czasu. Okresy nadmiernej aktywności Procesora więcej mogą spowodować problemy z czasu reakcji i porzucić ramki.  
  
    -   Jeśli projektujesz aplikacji gry lub sformatowanego nośnika, użyj [przepływność wizualną widoku (kl. / s)](#VisualThroughput) do identyfikacji okresów czasu, w którym porzucony szybkość klatek.  
  
10. Wybierz obszar w jednym wykresów częścią wykresu będącego klikając i przeciągając wskaźnik, aby dokonać wyboru (lub za pomocą klawisza Tab i klawiszy strzałek). Po wybraniu w czasie dokonując wyboru oś czasu wykresu szczegółów w dolnym okienku profilera zmiany Pokaż tylko wybrany okres czasu.  
  
     Na poniższej ilustracji przedstawiono wykres wykorzystania CPU z obszaru zainteresowania wyróżnione.  
  
     ![CPU utilization graph](../profiling/media/js_htmlvizprof_cpu_util.png "JS_HTMLVizProf_CPU_Util")  
  
11. Użyj [wyświetlić szczegóły osi czasu](#TimelineDetails) Aby uzyskać szczegółowe informacje o zdarzeniach, które są uruchamiane zbyt często lub biorąc zbyt dużo czasu. Na przykład wyszukaj następujące czynności:  
  
    -   Odbiorniki zdarzeń, czasomierze i wywołania zwrotne ramek animacji. W zależności od konkretnego zdarzenia dane przekazane mogą obejmować identyfikator zmodyfikowane elementy modelu DOM, nazwę zmodyfikowane właściwości CSS, łącze do lokalizacji źródłowej i nazwa funkcji skojarzonego zdarzenia lub wywołania zwrotnego.  
  
    -   Układ lub zdarzeń, które spowodowało renderowania elementów, takich jak skrypty wywołania do `window.getComputedStyles`. Podano skojarzony element DOM dla zdarzenia.  
  
    -   Strony lub adres URL zasobów, które są ładowane przez aplikację, takich jak oceny skrypt dla zdarzenia z przetwarzaniem plików HTML. Podano nazwę pliku lub zasobu.  
  
    -   Inne zdarzenia, określona w [odwołanie do zdarzenia profilera](#ProfilerEvents).  
  
    > [!TIP]
    >  Większość użyteczne informacje w profilera znajduje się na wykresie szczegóły osi czasu.  
  
12. Obszar wybrana wykorzystanie procesora CPU lub wykres przepływność wizualną (kl. / s), wybierz polecenie **powiększać** (przycisk lub kontekstu menu), aby uzyskać więcej szczegółowych informacji. Oś czasu zmian grafu wyświetlić tylko wybrany okres czasu.  
  
13. Gdy powiększona, wybierz część wykorzystanie procesora CPU lub przepływność wizualną wykresu. Po dokonaniu wyboru oś czasu wykresu szczegóły profilera dolnym okienku zmiany w Pokaż tylko wybrany okres czasu.  
  
###  <a name="IsolateVisualThroughput"></a> Izolowanie problem przepływność wizualną  
 Okresy nadmiernego użycia procesora CPU może spowodować szybkość klatek niskim lub niespójne. W przypadku tworzenia aplikacji multimedialnej oraz gier, wykres przepływność wizualną może udostępnić dane większe znaczenie niż wykres wykorzystania CPU.  
  
 Aby wyizolować przepływność wizualną problem, wykonaj czynności opisane w poprzedniej sekcji, ale za pomocą graph przepływność wizualną jako jednego z punktów danych klucza.  
  
###  <a name="ProfileMark"></a> Oznacz kod — analiza  
 Aby wyizolować sekcji kodu aplikacji, który został skojarzony z dane wyświetlane na wykresach, można dodać wywołanie funkcji w swojej aplikacji, która sprawia, że profiler pole użytkownika — odwrócony trójkąt — na osi czasu w momencie funkcji jest wykonywany. Każdego znaku użytkownika, który możesz dodać pojawia się na osi czasu Wykres wykorzystania CPU, wykres przepływność wizualną i wykres szczegóły osi czasu.  
  
 Aby dodać znacznik użytkownika, Dodaj następujący kod do aplikacji. W tym przykładzie używane "Pobieranie danych" jako opis zdarzenia.  
  
```javascript  
if (performance && performance.mark) {  
    performance.mark("getting data");  
}  
  
```  
  
 Opis zdarzenia jest wyświetlany jako etykietka narzędzia, gdy wskaźnik myszy nad oznaczenie użytkownika. Możesz dodać dowolną liczbę znaków użytkownika zgodnie z potrzebami.  
  
> [!NOTE]
>  `console.timeStamp`, polecenie Chrome jest także wyświetlany jako znacznik użytkownika.  
  
 Na poniższej ilustracji przedstawiono linijki diagnostics znaku pojedynczego użytkownika i jego etykietka narzędzia.  
  
 ![Diagnostyka linijki przedstawiający znacznik użytkownika](../profiling/media/js_htmlvizprofiler_usermark.png "JS_HTMLVizProfiler_UserMark")  
  
 W widoku szczegółów osi czasu pokazanie okres czasu, który przechodzi między dwoma znakami użytkownika można również utworzyć zdarzenia generowane przez narzędzie. Poniższy kod dodaje znacznik drugiego użytkownika i pomiar czas, jaki upływa między wykonaniem użytkownika dwóch znaków (poprzedni kod Pokazuje pierwszy znak użytkownika).  
  
```javascript  
if (performance.mark && performance.measure) {  
    performance.mark("data retrieved");  
    performance.measure("data measure", "getting data", "data retrieved");  
}  
```  
  
 Jeśli drugi znacznik użytkownika nie zostanie określona, `performance.measure` używa sygnaturę czasową jako drugi znacznik użytkownika. Pierwszy znak użytkownika jest wymagany.  
  
 Pomiar czasu trwania pojawia się jako **miara użytkownika** zdarzeń na osi czasu widoku szczegółów i zawiera szczegółowe informacje w przypadku wybrania.  
  
 ![Widok szczegółów zdarzenia miara użytkownika na osi czasu](../profiling/media/js_htmlvizprofiler_user_measure.png "JS_HTMLVizProfiler_User_Measure")  
  
##  <a name="AnalyzeData"></a> Analizowanie danych  
 Poniższe sekcje zawierają informacje dotyczące interpretowania danych wyświetlanych w profilera.  
  
###  <a name="Ruler"></a> Widok osi czasu sesji diagnostycznej  
 Linijki w górnej części profilera przedstawiono oś czasu PROFILOWANEGO informacji. Oś czasu dotyczy zarówno Wykres wykorzystania CPU, jak i przepływność wizualną wykresu.  
  
 Oto, jak wygląda na osi czasu sesji diagnostycznej z etykietki narzędzia wyświetlany dla kilku zdarzenia cyklu życia aplikacji:  
  
 ![Sesja diagnostyczna linijki](../profiling/media/js_htmlvizprof_ruler.png "JS_HTMLVizProf_Ruler")  
  
 Pokazuje osi czasu, w przypadku wystąpienia zdarzeń lifecyle aplikacji, takich jak zdarzenia aktywacji i zawiera znaki użytkownika (użytkownik znacznik trójkąty) który można dodać do kodu. Możesz wybrać zdarzeń, aby wyświetlić etykietkę zawierającą więcej informacji. Aby uzyskać więcej informacji na temat znaczników użytkownika, zobacz [oznaczyć kod analizy](#ProfileMark) w tym temacie.  
  
 Zdarzenia cyklu życia aplikacji są wyświetlane jako symbole romb. Są to zdarzenia modelu DOM, takich jak:  
  
-   `DOMContentLoaded` i `Load` zdarzenia, których zwykle występują w obsłudze zdarzeń aktywowana w kodzie. Etykietka narzędzia dla zdarzenia zawiera konkretnego zdarzenia i adresu URL.  
  
-   Zdarzenie nawigacji, co następuje po przejściu do innej strony. Etykietka narzędzia dla zdarzenia zawiera adres URL strony docelowej.  
  
###  <a name="CPUUtilization"></a> Użycie procesora CPU widoku  
 Wykres wykorzystania CPU umożliwia identyfikacji okresów czasu, w którym jest nadmiernej aktywności Procesora. Zawiera informacje o aplikacji średnie użycie Procesora w danym okresie czasu. Informacje są oznaczone kolorami reprezentują określonych kategoriach: **ładowania**, **skryptów**, wyrzucanie elementów bezużytecznych (**GC**), **stylów**, **Renderowania**, i **dekodowanie obrazu**. Aby uzyskać więcej informacji na temat tych kategorii, zobacz [odwołanie do zdarzenia profilera](#ProfilerEvents) dalszej części tego tematu.  
  
 Wykres wykorzystania CPU pokazuje ilość czasu przeznaczonego na wszystkie wątki aplikacji w celu łączenia wartości użycie procesora CPU dla co najmniej jednego procesora CPU do pojedynczej wartości procentowej. Wartość wykorzystanie Procesora może przekroczyć 100 procent, gdy używany jest więcej niż jeden Procesor.  
  
> [!NOTE]
>  Użycie procesora GPU nie są wyświetlane na wykresie.  
  
 Ten przykład przedstawia Wykres wykorzystania CPU wygląda następująco:  
  
 ![CPU utilization graph](../profiling/media/js_htmlvizprof_cpu_util.png "JS_HTMLVizProf_CPU_Util")  
  
 Użyj tego wykresu na:  
  
-   Określ ogólne obszary zainteresowania.  
  
-   Wybierz w określonym przedziale czasu do wyświetlenia na wykresie szczegóły osi czasu. Aby wybrać okres czasu, wybierz częścią wykresu będącego i przeciągnij wskaźnik, aby dokonać wyboru.  
  
-   Uzyskanie bardziej szczegółowych widoku w wybranym okresie, wybierając **powiększać** przycisku.  
  
 Aby uzyskać więcej informacji na temat używania wykresu, zobacz [wyizolować problem czasu odpowiedzi interfejsu użytkownika](#Workflow) w tym temacie.  
  
###  <a name="VisualThroughput"></a> Przepływność wizualną widoku (kl. / s)  
 Wykres przepływność wizualną umożliwia identyfikacji okresów czasu, w którym porzucony szybkość klatek. Pokazuje liczbę klatek na sekundę (kl. / s) dla aplikacji. Ten wykres jest najbardziej przydatny w przypadku tworzenia gier i aplikacji multimediów.  
  
 Wyświetlana wartość kl. / s może się różnić od liczba klatek na sekundę. Podczas analizowania danych w tego wykresu, należy pamiętać o tych informacji:  
  
-   Wykres przedstawia klatek na Sekundę, że dana aplikacja jest możliwość osiągnięcia określonej godzinie. Gdy aplikacja jest w stanie bezczynności, kl. / s jest taka sama jak częstotliwość odświeżania monitora.  
  
-   Wykres przedstawia rzeczywiste kl. / s, jeśli aplikacja jest wykonywania pracy, który wymaga aktualizacji visual.  
  
-   Wykres przedstawia wartość zero, jeśli ramki są usuwane.  
  
 Ten przykład przedstawia wykres przepływność wizualną wygląda następująco:  
  
 ![Wykres przepływność wizualną](../profiling/media/js_htmlvizprof_vizthru.png "JS_HTMLVizProf_VizThru")  
  
 Użyj wykresu przepływność wizualną:  
  
-   Określ ogólne obszary zainteresowania.  
  
-   Wybierz w określonym przedziale czasu do wyświetlenia na wykresie szczegóły osi czasu. Aby wybrać okres czasu, wybierz częścią wykresu będącego i przeciągnij wskaźnik, aby dokonać wyboru.  
  
-   Uzyskanie bardziej szczegółowych widoku w wybranym okresie, wybierając **powiększać** przycisku.  
  
###  <a name="TimelineDetails"></a> Wyświetl szczegóły osi czasu  
 Oś czasu wykresu szczegółów zostanie wyświetlony w dolnym okienku Profiler czasu odpowiedzi interfejsu użytkownika. Zawiera hierarchicznej i sekwencyjny informacje o zdarzeniach, które są używane podczas wybranych okresów najwięcej czasu Procesora. Ten wykres może pomóc w określeniu, co wyzwoliło konkretnego zdarzenia i dla niektórych zdarzeń, jak zdarzenia mapy do kodu źródłowego. Ten wykres pomaga również określić czas wymagany do malowania visual aktualizacje na ekranie.  
  
 Wykres zawiera Praca wątku interfejsu użytkownika i wątki w tle, które może przyczynić się do powolna aktualizacji visual. Wykres nie wyświetla pracy JavaScript JIT, asynchroniczne działanie procesora GPU, pracy wykonanej poza procesu hosta (na przykład RuntimeBroker.exe i dwm.exe pracy) lub pracy obszarów środowiska uruchomieniowego systemu Windows, które jeszcze nie został zinstrumentowany na potrzeby profilowania (na przykład we/wy dysku).  
  
> [!TIP]
>  Gdy wystąpi zdarzenie wątku w tle, identyfikator wątku jest wyświetlana w nawiasach obok nazwy zdarzenia.  
  
 Ten przykład przedstawia jakie oś czasu wykresu szczegóły wygląda kliknięcie odbiornik zdarzeń dla modelu DOM wybrano zdarzeń:  
  
 ![Oś czasu wykresu szczegóły](../profiling/media/js_htmlvizprof_timelinedet.png "JS_HTMLVizProf_TimelineDet")  
  
 Na tej ilustracji **spinAction** obsługi zdarzeń w **Nazwa zdarzenia** kolumny jest łączem, gdy zaznaczone, spowoduje przejście do obsługi zdarzeń w kodzie źródłowym. W okienku po prawej stronie **funkcja wywołania zwrotnego** właściwość zapewnia tego samego łącza do kodu źródłowego. Inne właściwości zawierają również informacje dotyczące zdarzeń, takich jak skojarzony element DOM.  
  
 W przypadku wybrania część oś czasu wykresu przepływność wizualną (kl. / s) i czasu procesora oś czasu wykresu szczegóły zawiera szczegółowe informacje dotyczące wybranego okresu.  
  
 Zdarzenia na wykresie szczegóły osi czasu są oznaczone kolorami reprezentują tego samego kategorie pracy, które są wyświetlane na wykresie użycia procesora CPU. Aby uzyskać więcej informacji o kategorii zdarzeń i określonych zdarzeń, zobacz [odwołanie do zdarzenia profilera](#ProfilerEvents) w tym temacie.  
  
 Użyj wykresu szczegóły osi czasu:  
  
-   Wyświetlanie godziny rozpoczęcia przybliżoną, czasu i godziny zakończenia zdarzenia na osi czasu i widoku siatki. Oś czasu wykresu szczegółowe informacje można wyświetlić okresy od 30 milisekund do 30 sekund w widoku siatki w zależności od stanu powiększenia. Dla wartości typu duration:  
  
    -   Całkowity czas reprezentuje czas trwania zdarzenia, łącznie z elementami podrzędnymi zdarzeń. W widoku siatki tej wartości jako pierwsze.  
  
    -   Wyłącznego razy reprezentuje czas trwania zdarzenia nie łącznie z elementami podrzędnymi zdarzeń. Ta wartość jest wyświetlana w widoku siatki w nawiasach.  
  
-   Rozwiń zdarzenia w hierarchii, aby wyświetlić elementy podrzędne danego zdarzenia. Elementy podrzędne zdarzeń są inne zdarzenia, które są wywoływane przez zdarzenia nadrzędnego. Na przykład zdarzenia modelu DOM może być odbiorników zdarzeń, które są wyświetlane jako elementy podrzędne. Odbiornik zdarzeń może mieć inne zdarzenia, które są wynikiem, takich jak zdarzenia układu.  
  
-   Sortuj zdarzenia według początek godziny (ustawienie domyślne) lub czas trwania. Użyj **sortować** listę, aby wybrać metodę sortowania.  
  
-   Przejrzyj szczegóły dotyczące każdego zdarzenia w okienku szczegółów (po prawej). Właściwości różnić w zależności od konkretnego zdarzenia, jak pokazują powyższe przykłady:  
  
    -   Czasomierze, odbiorniki zdarzeń (zdarzenia DOM) i wywołania zwrotne ramek animacji **funkcja wywołania zwrotnego** właściwość zawiera również link do lokalizacji kodu źródłowego, wraz z nazwą funkcji obsługi lub wywołania zwrotnego zdarzeń.  
  
    -   Czasomierze, odbiorniki zdarzeń (zdarzenia DOM), układ zdarzeń i wywołania zwrotne ramek animacji, oznaczone kolorami podsumowanie wybranego zdarzenia i wszystkie jego elementy podrzędne są wyświetlane w **całkowity czas podsumowania** sekcji (oznaczone kolorami pierścień). Każdy wycinek oznaczone kolorami obrazu reprezentuje typ zdarzenia. Etykietki narzędzi, podaj nazwę typu zdarzenia.  
  
    > [!TIP]
    >  Oś czasu wykresu szczegóły i **całkowity czas podsumowania** może ułatwić określenie obszarów dla optymalizacji. Jeśli jeden z tych widoków zawiera dużą liczbę małych zadań, zdarzenie może być kandydatem do optymalizacji. Na przykład aplikacji może być odświeżanie elementów modelu DOM często, co spowoduje dużą liczbę układ i analizowanie zdarzeń HTML. Dzięki temu można zoptymalizować wydajność przez przetwarzanie wsadowe tę pracę.  
  
###  <a name="FilterTimelineDetails"></a> Szczegóły filtru osi czasu  
 Można filtrować widok w szczegółach osi czasu do konkretnego zdarzenia, wybierając **filtr, aby zdarzenia** z menu kontekstowego dla określonego zdarzenia. Po wybraniu tej opcji widoku osi czasu i siatki ograniczone do wybranego zdarzenia. Zaznaczenie w wykres wykorzystania CPU również zakresów do określonego zdarzenia.  
  
 ![Filtrowanie osi czasu na zdarzenie](../profiling/media/js_htmlvizprofiler_filtertoevent.png "JS_HTMLVizProfiler_FilterToEvent")  
  
###  <a name="FilterEvents"></a> Filtruj zdarzenia  
 Niektóre zdarzenia z oś czasu wykresu szczegóły redukcji szumu w danych lub usunąć dane, które nie jest interesujące dla danego scenariusza wydajność można odfiltrować. Można filtrować według nazwy zdarzenia lub czas trwania zdarzenia lub przez określone filtry opisane w tym miejscu.  
  
 Aby odfiltrować dekodowanie obrazu, rozważana pobierania i zdarzenia GC, wyczyść **działania w tle** opcję ikonę filtra w dolnym okienku. Ponieważ te zdarzenia nie są bardzo umożliwiająca wykonanie akcji, są ukryte domyślnie.  
  
 ![Filtrowanie zdarzeń na osi czasu](../profiling/media/js_htmlvizprofiler_event_filter.png "JS_HTMLVizProfiler_Event_Filter")  
  
 Aby filtrować zdarzenia żądania HTTP, wyczyść **ruch sieciowy** opcję ikonę filtra w dolnym okienku. Domyślnie te zdarzenia są wyświetlane na wykresie szczegóły osi czasu.  
  
 Aby odfiltrować aktywności wątku interfejsu użytkownika, wyczyść **działania interfejsu użytkownika** opcji.  
  
> [!TIP]
>  Usuń zaznaczenie tej opcji, a następnie wybierz opcję ruchu sieciowego do badania problemów związanych z opóźnieniem sieci.  
  
 Aby filtrować środków użytkownika, wyczyść **środki użytkownika** opcji. Środki użytkownika są zdarzenia najwyższego poziomu bez elementów podrzędnych.  
  
###  <a name="GroupFrames"></a> Grupuj zdarzenia według ramki  
 Możesz grupować zdarzenia, które są wyświetlane w widoku szczegółów osi czasu do poszczególnych klatek. Te zdarzenia ramki są zdarzeniami generowanymi przez narzędzie i reprezentują kontenery zdarzenia najwyższego poziomu dla wszystkich pracy wątku interfejsu użytkownika, która występuje między zdarzeniami malowania. Aby włączyć ten widok, wybierz **Grupuj zdarzenia najwyższego poziomu według klatek**.  
  
 ![Grupuj zdarzenia najwyższego poziomu według ramki](../profiling/media/js_htmlvizprofiler_frame_grouping_button.png "JS_HTMLVizProfiler_Frame_Grouping_Button")  
  
 Zdarzenia w przypadku grupowania ramką, zdarzenia najwyższego poziomu w szczegółach osi czasu wyświetlić odpowiadają każdej ramce.  
  
 ![Oś czasu zdarzeń pogrupowane według ramki](../profiling/media/js_htmlvizprofiler_frame_grouping.png "JS_HTMLVizProfiler_Frame_Grouping")  
  
##  <a name="SaveSession"></a> Zapisywanie sesji diagnostycznej  
 W programie Visual Studio można zapisać sesji diagnostycznej podczas zamykania kartę, który został skojarzony z sesją. Zapisane sesje, można je otworzyć ponownie w późniejszym czasie.  
  
##  <a name="ProfilerEvents"></a> Odwołanie do zdarzenia profilera  
 Profiler zdarzenia są skategoryzowane i oznaczanie kolorami w Profiler czasu odpowiedzi interfejsu użytkownika. Są to kategorie zdarzeń:  
  
-   **Podczas ładowania.** Wskazuje czas spędzony na zasoby aplikacji podczas pobierania i analizowania HTML i CSS po pierwszym załadowaniu aplikacji. Może to obejmować żądania sieciowe.  
  
-   **Wykonywanie skryptów.** Wskazuje czas analizowania i uruchamianie JavaScript. Obejmuje to zdarzenia modelu DOM, czasomierze, skryptów i pracy ramki animacji. Zawiera zarówno kod użytkownika i kod biblioteki.  
  
-   **GC.** Wskazuje czas spędzony na wyrzucanie elementów bezużytecznych.  
  
-   **Style.** Wskazuje czas spędzony analizy CSS i obliczanie prezentacji i układu elementu.  
  
-   **Renderowanie.** Wskazuje czas spędzony na malowaniu ekranu.  
  
-   **Dekodowanie obrazu.** Wskazuje czas spędzony na dekompresowaniu i dekodowaniu obrazów.  
  
 Dla skryptów i stylów kategorii Profiler czasu odpowiedzi interfejsu użytkownika może zawierać dane, które może działać na wykresie szczegóły osi czasu. Po zidentyfikowaniu zagadnienia dotyczące skryptów jako problem, możesz uruchomić Procesora próbkowania profilera z Profiler czasu odpowiedzi interfejsu użytkownika. Alternatywnie można użyć funkcji profilera Visual Studio do uzyskania bardziej szczegółowych danych. Aby uzyskać więcej informacji, zobacz [pamięci JavaScript](../profiling/javascript-memory.md).  
  
 Dla innych kategorii zdarzeń można zidentyfikować platformy efekty uboczne, których wynikiem Dodawanie funkcji do aplikacji, ale w takim przypadku nie można spróbować rozwiązać problemy z wydajnością określonego za pomocą Profiler czasu odpowiedzi interfejsu użytkownika.  
  
 Ta tabela pokazuje zdarzenia i ich opisy:  
  
|Zdarzenie|Kategoria zdarzenia|Występuje, gdy|  
|-----------|--------------------|-----------------|  
|Analiza kodu CSS|Podczas ładowania|Napotkano nową zawartość arkusza CSS, a następnie podjęto przeanalizować zawartość arkusza CSS.|  
|Analiza kodu HTML|Podczas ładowania|Napotkano nową zawartość HTML i podjęto próbę analizy zawartości w węzłach i Wstaw zawartość w drzewie DOM.|  
|Żądania HTTP|Podczas ładowania|Zasób zdalny został znaleziony w modelu DOM lub utworzono żądanie XMLHttpRequest, które spowodowały żądania HTTP.|  
|Rozważana pobierania|Podczas ładowania|Zawartość HTML strony zostało wyszukiwane wymaganych zasobów, aby można było szybko zaplanować kolejne żądania HTTP dla zasobów.|  
|Funkcja wywołania zwrotnego ramki animacji|Wykonywanie skryptów|Przeglądarka został przechodzi do innej ramki renderowania i to wyzwalane funkcja wywołania zwrotnego dostarczony do aplikacji.|  
|Zdarzenia modelu DOM.|Wykonywanie skryptów|Zdarzenia modelu DOM wystąpił i zostało wykonane.<br /><br /> `context` Właściwości zdarzenia modelu DOM, takich jak `DOMContentLoaded` lub `click`, jest wyświetlana w nawiasie.|  
|Odbiornik zdarzeń|Wykonywanie skryptów|Odbiornik zdarzeń został wywoływane i wykonywane.|  
|Odbiornik kwerendy nośnika|Wykonywanie skryptów|Zarejestrowane zapytanie o multimedia zostało unieważnione, co spowodowało wykonanie skojarzonych z nim odbiorników.|  
|Obserwator mutacji|Wykonywanie skryptów|Co najmniej jeden zauważyć, że elementów DOM został zmodyfikowany, co spowodowało wykonanie wywołania zwrotnego skojarzonego z elementem MutationObserver.|  
|Ocena skryptu|Wykonywanie skryptów|Nowy element skrypt został znaleziony w modelu DOM, a nastąpiła próba do analizowania i uruchom skrypt.|  
|Czasomierz|Wykonywanie skryptów|Zaplanowany czasomierz zakończył odliczanie, a to spowodowało wykonanie funkcji wywołania zwrotnego skojarzonego.|  
|Funkcja wywołania zwrotnego async środowiska wykonawczego systemu Windows|Wykonywanie skryptów|Operacja asynchroniczna, która wyzwoliła `Promise` funkcja wywołania zwrotnego wykonał obiektu środowiska wykonawczego systemu Windows.|  
|Zdarzenie środowiska wykonawczego systemu Windows|Wykonywanie skryptów|Zdarzenie, które wystąpiły w obiekcie środowiska wykonawczego systemu Windows wyzwalane zarejestrowanego odbiornika.|  
|Wyrzucanie elementów bezużytecznych|GC|Czasu zbieranie pamięci obiektów, które zostały już w użyciu.|  
|Obliczanie CSS|Ustawianie stylów|Wprowadzono zmiany w modelu DOM, co wymagało obliczenia właściwości stylu dla wszystkich elementów objętych działaniem.|  
|Układ|Ustawianie stylów|Wprowadzono zmiany w modelu DOM, co wymagało obliczenia rozmiaru i/lub pozycji wszystkich elementów objętych działaniem.|  
|Malowania|Renderowanie|Wprowadzono zmiany wizualne w modelu DOM, a nastąpiła próba ponownego renderowanie części strony.|  
|Renderowanie warstwy|Renderowanie|Wprowadzono zmiany wizualne na renderowanym niezależnie we fragmencie modelu DOM (nazywane warstwy), a część strony do renderowania wymaganych zmian.|  
|Dekodowanie obrazu|Dekodowanie obrazu|Obraz został uwzględniony w modelu DOM, a nastąpiła próba dekompresja i zdekodować obrazu z oryginalnego formatu do mapy bitowej.|  
|Klatka|Brak|Wprowadzono zmiany wizualne w modelu DOM, co wymagało wszystkich części strony objętych działaniem. Jest to zdarzenie generowane przez narzędzie używane do grupowania.|  
|Miara użytkownika|Brak|Scenariusz specyficzny dla aplikacji został zmierzony za pomocą `performance.measure` metody. Jest to zdarzenie generowane przez narzędzie używane do analizowania kodu.|  
  
##  <a name="Tips"></a> Dodatkowe informacje  
  
-   Obejrzyj [ten film](http://channel9.msdn.com/Events/Build/2013/3-316) z konferencji 2013 kompilacji o Profiler czasu odpowiedzi interfejsu użytkownika.  
  
-   Przeczytaj porady dotyczące wydajności dla aplikacji platformy uniwersalnej systemu Windows dla systemu Windows przy użyciu języka JavaScript. Aby uzyskać więcej informacji, zobacz [wydajności najlepszych rozwiązań dotyczących aplikacji platformy uniwersalnej systemu Windows przy użyciu języka JavaScript](http://msdn.microsoft.com/library/windows/apps/hh465194.aspx).  
  
-   Informacje na kod jednowątkowego wykonywania modelu i wydajność zawiera [wykonywanie kodu](http://msdn.microsoft.com/library/windows/apps/hh781217.aspx).  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzia profilowania](../profiling/profiling-tools.md)