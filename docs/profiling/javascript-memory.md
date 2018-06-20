---
title: Analizowanie użycia pamięci JavaScript w aplikacji platformy uniwersalnej systemu Windows | Dokumentacja firmy Microsoft
ms.custom: H1Hack27Feb2017
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- JavaScript
helpviewer_keywords:
- dominators, memory analyzer (JavaScript)
- memory leaks (JavaScript)
- heap memory, JavaScript
- leaks, memory (JavaScript)
- snapshots, memory analyzer (JavaScript)
- JavaScript Memory Analyzer
- analyzing memory, JavaScript
- memory analyzer, JavaScript
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8a4c29855cb9a771660fa5070f6d34a4d10c557a
ms.sourcegitcommit: f685fa5e2df9dc307bf1230dd9dc3288aaa408b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2018
ms.locfileid: "36238403"
---
# <a name="analyze-javascript-memory-usage-in-uwp-apps"></a>Analizowanie użycia pamięci JavaScript w aplikacji platformy uniwersalnej systemu Windows
Analizator pamięci JavaScript jest dostępna w programie Visual Studio, aby określić sposób użycia pamięci i Znajdź przecieki pamięci w aplikacjach platformy uniwersalnej systemu Windows dla systemu Windows przy użyciu języka JavaScript. Obsługiwane aplikacje to aplikacje dla uniwersalnych aplikacji systemu Windows.
  
 Analizator pamięci JavaScript można wykonać te czynności dla Ciebie:  
  
-   Pomaga szybko znajdować pamięci problemów z wykorzystaniem w aplikacji przez wyróżnianie ważnych danych.  
  
     Otrzymasz dane w podsumowania migawki, które przedstawiał różnice między dwiema migawkami i udostępniają linki do bardziej szczegółowych widoków.  
  
-   Podaj widoków dominatorów, typy i elementy główne wyizolować problemy.  
  
-   Zmniejsz nieprzetwarzalnych informacji w danych sterty JavaScript.  
  
     Obiekty, które nie są tworzone bezpośrednio w kodzie aplikacji automatycznie są odfiltrowywane. Można także filtrować dane według nazwy obiektu.  
  
## <a name="run-the-javascript-memory-analyzer"></a>Uruchom narzędzie JavaScript memory analyzer  
 Analizator pamięci można użyć podczas pracy aplikacji platformy uniwersalnej systemu Windows, Otwórz w programie Visual Studio.
  
#### <a name="to-run-the-memory-analyzer"></a>Aby uruchomić analizator pamięci  
  
1.  Otwórz program Visual Studio.  
  
2.  Jeśli korzystasz z aplikacji z programu Visual Studio w **Rozpocznij debugowanie** listy na **standardowe** narzędzi wybierz cel debugowania dla projektu: albo **komputera lokalnego** lub **Urządzenia**.  
  
3.  Na pasku menu wybierz **debugowania** > **wydajności programu profilującego**.  
  
     Domyślnie są analizowane bieżący projekt startowy. Jeśli chcesz zmienić element docelowy analizy, wybierz **zmienić docelowy**.  
  
     ![Zmień docelowy analizy](../profiling/media/js_tools_target.png "JS_Tools_Target")  
  
     Poniższe opcje są dostępne dla obiektu docelowego analizy:  
  
    -   **Projekt startowy**. Analizuje bieżący projekt startowy. Jeśli korzystasz z aplikacji na komputerze zdalnym, musisz wybrać tę opcję, która jest ustawiona domyślnie.  
  
    -   **Uruchomiona aplikacja**. Umożliwia wybranie aplikacji platformy uniwersalnej systemu Windows z listy działających aplikacji. Nie można użyć tej opcji, po uruchomieniu aplikacji na komputerze zdalnym.  
  
         Ta opcja umożliwia analizowanie użycia pamięci aplikacji, które są uruchomione na komputerze, jeśli nie masz dostępu do kodu źródłowego.  
  
    -   **Aplikacja zainstalowana**. Pozwala wybrać zainstalowaną aplikację platformy uniwersalnej systemu Windows, które mają być analizowane. Nie można użyć tej opcji, po uruchomieniu aplikacji na komputerze zdalnym.  
  
         Ta opcja umożliwia analizowanie użycia pamięci aplikacji, które zainstalowano na tym komputerze, jeśli nie masz dostępu do kodu źródłowego. Ta opcja również może być przydatne, gdy chcesz, aby przeanalizować użycie pamięci przez dowolną aplikację poza tworzenia własnych aplikacji.  
  
4.  Z **dostępne narzędzia**, wybierz pozycję **pamięci JavaScript** pole wyboru, a następnie wybierz pozycję **Start**.  
  
5.  Po uruchomieniu analizator pamięci okno Kontrola konta użytkownika może zażądać Twoje uprawnienia do uruchamiania programu Visual Studio ETW Collector.exe. Wybierz **tak**.  
  
     Współdziałanie z aplikacją do testowania scenariuszy użycia pamięci odpowiednich i wyświetlić wykres pamięci zgodnie z opisem w poniższych sekcjach.  
  
6.  Przełącz się do programu Visual Studio, naciskając klawisz **Alt**+**kartę**.  
  
7.  Aby wyświetlić dane, które zbiera analizator pamięci, wybierz **wykonać migawki sterty**. Zobacz [wyświetlić podsumowanie migawki](#view-a-snapshot-summary) dalszej części tego tematu.  
  
## <a name="check-memory-usage"></a>Sprawdź użycie pamięci  
 Możesz spróbować identyfikowania przecieków pamięci za pomocą różnych widoków w analizator pamięci JavaScript. Jeśli już podejrzewasz, że w aplikacji występuje przeciek pamięci, zobacz [izolować przeciek pamięci](#isolate-a-memory-leak) sugerowane przepływu pracy.  
  
 Aby ułatwić identyfikację przecieki pamięci w aplikacji, należy użyć następujące widoki:  
  
-   [Wyświetl podsumowanie użycia pamięci na żywo](#view-live-memory-usage-summary). Użyj wykres użycia pamięci, aby wyszukać nagły wzrost użycia pamięci lub stale zwiększenie użycia pamięci, będącą wynikiem określonej akcji. Widok podsumowania użycia pamięci na żywo umożliwia wykonywanie migawek sterty. Migawki są wyświetlane jako kolekcję w obszarze wykresu użycia pamięci.  
  
    > [!TIP]
    >  Zobaczysz kolekcji użycia pamięci podczas wykonywania migawki. Użyj podsumowania migawki dla oznaczenie dokładniejsze przyrostu.  
  
-   [Wyświetlanie podsumowania migawki](#view-a-snapshot-summary). Można wyświetlić podsumowanie informacji o migawki podczas lub po sesji profilowania pamięci. Użyj podsumowania migawki do połączenia z widoków różnicowego migawki i szczegóły migawki.  
  
    > [!TIP]
    >  Zazwyczaj widoków różnicowego migawki zapewni najbardziej przydatnych informacji o przecieki pamięci.  
  
-   [Wyświetl szczegóły migawki](#view-snapshot-details). Przedstawia szczegółowe dane użycia pamięci dla pojedynczego migawki.  
  
-   [Wyświetlić diff migawki](#view-a-snapshot-diff). Pokazuje różnicowej wartości między migawki. Widoki te Pokaż różnice w obiekcie rozmiar i obiektu liczby.  
  
## <a name="isolate-a-memory-leak"></a>Izolowanie przeciek pamięci  
 Kroki te zapewniają przepływu pracy, które mogą ułatwić wydajniej wykorzystywać analizator pamięci JavaScript. Te kroki mogą być przydatne, jeśli zachodzi podejrzenie, że aplikacja ma przeciek pamięci. Samouczek, który poprowadzi Cię przez proces identyfikowania przeciek pamięci w pracy aplikacji, zobacz [wskazówki: znajdowanie wycieku pamięci (JavaScript)](../profiling/walkthrough-find-a-memory-leak-javascript.md).  
  
1.  Otwórz aplikację w programie Visual Studio.  
  
2.  Uruchom analizator pamięci JavaScript. Aby uzyskać więcej informacji, zobacz [Uruchom narzędzie JavaScript memory analyzer](#run-the-JavaScript-memory-analyzer).  
  
3.  Uruchom aplikację za pomocą tego scenariusza, który ma zostać przetestowana. Na przykład scenariusz mogą dotyczyć dużych mutacji modelu DOM, podczas ładowania określonej strony lub po uruchomieniu aplikacji.  
  
4.  Powtórz scenariusz 1-4 dodatkowe razy.  
  
    > [!TIP]
    >  Powtarzając scenariusza testów kilka razy, może pomóc upewnić się, że inicjalizację można filtrować poza wyniki.  
  
5.  Przełącz się do programu Visual Studio (naciśnij klawisz **Alt**+**kartę**).  
  
6.  Utwórz migawkę sterty linii bazowej, wybierając **wykonać migawki sterty**.  
  
     Na poniższej ilustracji przedstawiono przykład migawką bazową.  
  
     ![Migawką bazową](../profiling/media/js_mem_leak_workflow_baseline.png "JS_Mem_Leak_Workflow_Baseline")  
  
    > [!TIP]
    >  Aby uzyskać bardziej precyzyjną kontrolę nad chronometrażu migawek, można użyć [skojarzyć kodu źródłowego z danych użycia pamięci](#associate-source-code-with-memory-usage-data) w kodzie.  
  
7.  Przełącz się do aplikacji i powtórz scenariuszu testowania (Powtórz tylko jeden raz).  
  
8.  Przełącz się do programu Visual Studio i drugi migawki.  
  
9. Przełącz się do aplikacji i powtórz scenariuszu testowania (Powtórz tylko jeden raz).  
  
10. Przełącz się do programu Visual Studio i trzeci migawki.  
  
     Na poniższej ilustracji przedstawiono przykład drugi i trzeci migawki.  
  
     ![Drugi i trzeci migawki](../profiling/media/js_mem_leak_workflow.png "JS_Mem_Leak_Workflow")  
  
     Wykonując linii bazowej, drugi i trzeci migawki w tym przepływie pracy, można odfiltrować zmiany, które nie są skojarzone z przecieki pamięci łatwiej. Na przykład może być oczekiwany zmian, takich jak Aktualizowanie nagłówków i stopek na stronie, która spowoduje wygenerowanie pewne zmiany użycia pamięci, ale może być związana z przecieki pamięci.  
  
11. Z trzeci migawki wybierz łącze do jednego z widoków różnicowej:  
  
    -   Rozmiar sterty różnicowa (po lewej stronie link poniżej rozmiar stosu). Tekst łącza pokazano różnicę między rozmiaru sterty bieżącej migawki oraz Rozmiar sterty poprzednią migawkę.  
  
    -   Liczba obiektów różnicowa (prawo link poniżej liczba obiektów). Tekst łącza zawiera dwie wartości (na przykład +1858 /-1765): pierwsza wartość to liczba nowych obiektów dodanych od momentu poprzedniej migawki, a druga wartość jest liczba obiektów usuniętych od wcześniejszej migawki.  
  
     Te linki otwarcie widoku Szczegóły migawki różnicowej typów na stercie sortowane przez rozmiaru zachowanego lub liczba obiektów, w zależności od tego, które łącze jest otwarty.  
  
12. Wybierz jedną z następujących **zakres** opcje do identyfikowania problemów użycia pamięci filtru:  
  
    -   **Obiekty pozostałe z migawki nr 2**.  
  
    -   **Obiekty dodane między migawki nr 2 i #3**  
  
    > [!TIP]
    >  Filtrowany widok obiekty pozostałe z poprzednią migawkę umożliwia badanie przecieki pamięci. Na przykład, jeśli liczba obiektów różnicowej +205 /-195, Widok ten wyświetli 10 obiektów pozostawione i są prawdopodobnie kandydatów do przecieki pamięci.  
  
     Na poniższej ilustracji przedstawiono widok różnicowej obiekty pozostałe z migawki nr 2.  
  
     ![Migawki widoku różnic, wyświetlanie typów](../profiling/media/js_mem_snapshot_diff.png "JS_Mem_Snapshot_Diff")  
  
     Na powyższej ilustracji przedstawiono pozostałe dwa obiekty z wcześniejszej migawki. Sprawdź, czy jest to oczekiwane zachowanie dla określonej aplikacji. Jeśli nie, może to wskazywać przeciek pamięci.  
  
13. Aby sprawdzić, gdzie są umieszczone obiektów w widokach diff do globalnego obiektu, który uniemożliwia ich zbierane pamięci, otwórz menu skrótów dla obiekt, a następnie wybierz **Pokaż w widoku elementów głównych**. Dużą liczbę obiektów mogą być zachowane w pamięci, ponieważ odwołuje się przez jeden obiekt lub kilka obiektów które są umieszczone do globalnego obiektu.  
  
14. Jeśli ma zbyt wiele obiektów w widoku obiekty pozostałe, spróbuj rozwiązać okres, w której występuje przeciek pamięci, a następnie wznawiać trzy migawki. Aby rozwiązać przeciek pamięci, należy użyć [skojarzyć kodu źródłowego z danych użycia pamięci](#associate-source-code-with-memory-usage-data), [skojarzyć kodu źródłowego z danych użycia pamięci](#associate-source-code-with-memory-usage-data)oraz inne dane użycia pamięci dostępne w analizatorze pamięci.  
  
## <a name="view-live-memory-usage-summary"></a>Wyświetl podsumowanie użycia pamięci na żywo  
 Widok podsumowania użycia pamięci na żywo zapewnia wykres użycia pamięci dla uruchomionej aplikacji i kolekcji wszystkich kafelków podsumowania migawki. W tym widoku może wykonywać podstawowe zadania, takie jak tworzenie migawek, analizowania informacji podsumowujących i przechodząc do innych widoków. Po zatrzymaniu zbierania danych, wykres pamięci zniknie i zostanie wyświetlony tylko [wyświetlić podsumowanie migawki](#view-a-snapshot-summary) widoku.  
  
 Wykres pamięci przedstawia widok na żywo pamięci procesu aplikacji, w tym bajtów prywatnych, natywnej pamięci i sterty JavaScript. Wykres pamięci jest widokiem przewijanego pamięci procesu. Oto wygląda następująco:  
  
 ![Wykres pamięci JavaScript Memory Analyzer](../profiling/media/js_mem_memory_graph.png "JS_Mem_Memory_Graph")  
  
 Jeśli dodano użytkownika znaczniki kodu aplikacji (zobacz [skojarzyć kodu źródłowego z danych użycia pamięci](#associate-source-code-with-memory-usage-data)), odwrócony trójkąt pojawia się w wykres użycia pamięci, aby wskazać, po osiągnięciu tej części kodu.  
  
 Niektóre pamięci wyświetlane na wykresie pamięci jest przydzielany przez środowisko uruchomieniowe JavaScript. Nie można sterować tego użycia pamięci w aplikacji. Użycie pamięci wyświetlane na wykresie zwiększa Twojego pierwszego migawki, a minimalny zwiększa, dla każdego dodatkowego migawki.  
  
## <a name="view-a-snapshot-summary"></a>Wyświetlanie podsumowania migawki  
 Aby migawki bieżący stan użycia pamięci aplikacji, wybierz pozycję **wykonać migawki sterty** z wykresu pamięci. Kafelek podsumowania migawki, która jest wyświetlana w obu Podsumowanie użycia pamięci na żywo (gdy aplikacja jest uruchomiona) i migawki — Podsumowanie (Jeśli aplikacja jest zatrzymany), udostępnia informacje dotyczące sterty JavaScript i łącza do bardziej szczegółowych informacji. Migawka zawiera dodatkowe informacje o porównywanie jego danych do tego poprzednią migawkę, jeśli tworzenia migawek co najmniej dwa.  
  
> [!NOTE]
>  Analizator pamięci JavaScript wymusza wyrzucania elementów bezużytecznych przed każdym migawki. Pomaga to zapewnić bardziej spójne wyniki między działa.  
  
 Oto przykład podsumowania migawki podczas tworzenia wielu migawek.  
  
 ![Podsumowanie migawki](../profiling/media/js_mem_snapshot_summary.png "JS_Mem_Snapshot_Summary")  
  
 Zawiera podsumowanie migawki:  
  
-   Migawki tytuł i sygnaturę czasową.  
  
-   Liczba potencjalnych problemów (oznaczony ikoną informacji niebieski). Ten numer, jeśli jest obecny, identyfikuje potencjalne problemy z pamięcią takich jak węzły, które nie są dołączone do modelu DOM. Liczba łącza do typów widoku migawki, w której jest sortowana według typu problemu, aby wyróżnić potencjalnych problemów. Etykietka narzędzia zawiera opis problemu.  
  
-   Rozmiar stosu. Liczba ta obejmuje elementy modelu DOM i obiekty, które dodaje aparat środowiska wykonawczego języka JavaScript do sterty JavaScript. Rozmiar sterty łącza do typów widoku migawki.  
  
-   Rozmiar sterty różnicowej. Ta wartość przedstawia różnicę między rozmiaru sterty bieżącej migawki oraz Rozmiar sterty poprzednią migawkę. Wartość jest następuje czerwona strzałka w przypadku braku wzrostu pamięci w górę lub zielona strzałka w dół, jeśli istnieje zmniejszenie pamięci. Jeśli rozmiar stosu nie zmieniła się od migawek, zostanie wyświetlony tekst **bez zmian** zamiast numeru. Dla migawki pierwszy, zostanie wyświetlony tekst **linii bazowej**. Łącza Rozmiar sterty różnicowej do typów Widok porównania migawki.  
  
-   Liczba obiektów. Ten licznik pokazuje tylko obiektów utworzonych w aplikacji i odfiltrowuje wbudowane obiekty utworzone przez środowisko uruchomieniowe JavaScript. Liczba obiektu łącza do typów widoku Szczegóły migawki.  
  
-   Liczba obiektów różnicowej. Pokazuje dwóch wartości: pierwsza wartość to liczba nowych obiektów dodanych od momentu poprzedniej migawki; a druga wartość jest liczba obiektów usuniętych od wcześniejszej migawki. Na przykład na ilustracji przedstawiono 1,859 obiekty zostały dodane, a 1,733 obiekty zostały usunięte, ponieważ migawki nr 1. Te informacje następuje czerwona strzałka w górę, jeśli liczba całkowita liczba obiektów wzrosło lub zielona strzałka w dół, jeśli ma ona zmniejszyć. Jeśli nie zmieniła się liczba obiektów, zostanie wyświetlony tekst **bez zmian** zamiast numeru. Dla migawki pierwszy, zostanie wyświetlony tekst **linii bazowej**. Łącza liczba różnicowej obiektu do widoku typy porównania migawki.  
  
-   Zrzut ekranu przedstawiający ekran w czasie wykonywania migawki.  
  
## <a name="view-snapshot-details"></a>Wyświetl szczegóły migawki  
 Szczegółowe informacje o wykorzystaniu pamięci dotyczące każdej migawki można wyświetlić w widoku Szczegóły migawki.  
  
 Widok podsumowania migawki wybierz łącze, aby wyświetlić szczegóły migawki. Na przykład łącze Rozmiar sterty otwiera migawki szczegóły z widokiem typów otwartych domyślnie.  
  
 Na ilustracji przedstawiono widok typy szczegółowo migawki, posortowane według rozmiaru zachowanego dane użycia pamięci.  
  
 ![Widok szczegółów migawki wyświetlanie potencjalnych problemów](../profiling/media/js_mem_snapshot_details.png "JS_Mem_Snapshot_Details")  
  
 W widoku szczegółów migawki można przejrzeć dane użycia pamięci przez typ, root lub dominatora, wybierając opcję z paska narzędzi:  
  
-   **Typy**. Przedstawia rozmiar i łączna liczba wystąpienia obiektów na stercie pogrupowane według typu obiektu. Domyślnie te są sortowane według liczby wystąpień.  
  
    > [!TIP]
    >  Zazwyczaj widoki różnicowego typów sterty obiektów są najbardziej przydatne widoków identyfikowanie przeciek pamięci; Widoki te zapewniają **zakres** filtr, aby ułatwić identyfikację lewej obiektów.  
  
-   **Elementy główne**. Pokazuje hierarchiczny widok obiektów z obiektów głównego za pomocą odwołania podrzędnego. Domyślnie węzły podrzędne są sortowane według rozmiaru zachowanego kolumny, z największych u góry.  
  
-   **Dominatorów**. Przedstawia listę obiektów na stercie wyłącznego odwołują się do innych obiektów. Dominatorów są sortowane według rozmiaru zachowanego.  
  
    > [!TIP]
    >  Po usunięciu dominatora z pamięci jest odzyskanie całej pamięci, który zachowuje obiektu. W przypadku kilku aplikacji widoku Dominatorów mogą ułatwić wyjaśnienia rozmiary zachowanych pamięci, ponieważ możesz przejrzeć cały obiekt ciąg odwołania.  
  
 Wszystkie trzy widoki Pokaż podobnych typów wartości, w tym:  
  
-   **Identyfikatory**. Nazwa, która najlepiej identyfikuje obiekt. Na przykład elementów HTML migawki wyświetlone szczegóły wartość atrybutu ID, jeśli jest on używany.  
  
-   **Typ**. Typ obiektu (na przykład elementu łącza HTML lub div element).  
  
-   **Rozmiar**. Rozmiar obiektu nie takich jak rozmiar wszystkie obiekty.  
  
-   **Zachowane rozmiar**. Rozmiar obiektu plus rozmiar wszystkich obiektów podrzędnych, które mają bez elementów nadrzędnych. Ze względów praktycznych to ilość pamięci przechowywane przez obiekt, więc w przypadku usunięcia obiektu odzyskać określoną ilością pamięci.  
  
-   **Liczba**. Liczba wystąpień obiektu. Ta wartość jest wyświetlana tylko w widoku typów.  
  
## <a name="view-a-snapshot-diff"></a>Wyświetlić diff migawki  
 Narzędzie JavaScript memory analyzer porównuje migawki względem poprzednią migawkę w widokach różnicowego migawki.  
  
 W widoku podsumowania migawki można wyświetlić szczegóły migawki różnicowej, wybierając rozmiar stosu różnicowej lub łącza liczba różnicowej obiektu po dwóch lub więcej migawki.  
  
 Można wyświetlić różnicowej informacji na temat typów certyfikatów głównych i dominatorów. Diff migawki zawiera informacje, takie jak obiekty, które zostały dodane do stosu między dwiema migawkami.  
  
 Na tej ilustracji przedstawiono widok typów w porównania migawki.  
  
 ![Migawki widoku różnic, wyświetlanie typów](../profiling/media/js_mem_snapshot_diff.png "JS_Mem_Snapshot_Diff")  
  
 W oknie porównania migawki widoków Dominatorów, typy i elementy główne są takie same jak w [wyświetlić szczegóły migawki](#view-snapshot-details) okna. Diff migawki przedstawia tej samej informacji jako szczegóły migawki, te wartości dodatkowe:  
  
-   **Różnica rozmiaru**. Różnica między rozmiar obiektu w bieżącej migawce i jego rozmiaru w poprzednią migawkę nie takich jak rozmiar wszelkie odwołania do obiektów.  
  
-   **Zachowane różnica rozmiaru**. Różnica między rozmiaru zachowanego obiektu w bieżącą migawką a jego rozmiaru zachowanego poprzednią migawkę. Rozmiaru zachowanego obejmuje rozmiar obiektów plus rozmiar wszystkich jego obiektów podrzędnych, które mają bez elementów nadrzędnych. Praktycznego punktu widzenia rozmiaru zachowanego to ilość pamięci przechowywane przez obiekt, więc w przypadku usunięcia obiektu odzyskać określoną ilością pamięci.  
  
 Aby filtrować różnicowej informacji między migawki, wybierz jedną z **zakres** filtrów w górnej części różnicowej widoków.  
  
-   **Obiekty pozostałe z migawki nr\<numer >**. Ten filtr zawiera różnic między obiektami dodawane do sterty i usuwane z sterty w porównaniu z migawką bazową i poprzednią migawkę. Na przykład, jeśli +205 zawiera podsumowanie migawki /-195 liczba obiektów, filtru zostanie wyświetlona dziesięć obiektów, które zostały dodane, ale nie zostaną usunięte.  
  
    > [!TIP]
    >  Aby wyświetlić najbardziej użyteczne informacje w tym filtrze, wykonaj czynności opisane w [izolować przeciek pamięci](#isolate-a-memory-leak).  
  
-   **Obiekty dodane między migawki nr\<numer > i #\<numer >**. Ten filtr zawiera wszystkie obiekty dodane do sterty z wcześniejszej migawki.  
  
-   **Wszystkie obiekty w migawce nr\<numer >**. To ustawienie filtru nie odfiltrować obiekty na stercie.  
  
 Do wyświetlenia odwołań do obiektów, które nie odpowiadają bieżącej **zakres** filtru, wybierz **Pokaż niezgodny odwołania** na liście ustawień ![upuszczania ustawienia&#45;pozycji listy w analizatorze pamięci ] (../profiling/media/js_mem_settings.png "JS_Mem_Settings") w prawym górnym rogu okienka. Jeśli to ustawienie zostanie włączone, niezgodny odwołania są wyświetlane szary tekst.  
  
> [!TIP]
>  Firma Microsoft zaleca, postępuj zgodnie z instrukcjami [izolować przeciek pamięci](#isolate-a-memory-leak) , a następnie użyj obiekty pozostałe **zakres** filtr, aby zidentyfikować obiekty, które są przeciek pamięci.  
  
## <a name="view-objects-by-dominator"></a>Wyświetl obiekty wg dominatora  
 W widokach typów i Dominatorów, można wybrać, czy chcesz wyświetlić obiekty, które zostało zwinięte do ich dominatorów (jest to domyślny widok w **Dominatorów** kartę). Po wybraniu tego widoku dominatorów tylko są wyświetlane w widoku najwyższego poziomu obiektów. (Obiekty, które są elementami podrzędnymi obiektów globalnych są ukryte w widoku najwyższego poziomu). W przypadku niektórych aplikacji to wyjaśnienia, obiekty, które powodują przeciek pamięci, zmniejszając szumu w danych.  
  
 Aby włączyć widok obiekty wg dominatora, wybierz **Zwiń w obiektach wg dominatora** przycisku. ![Składanie obiektów w ich dominatorów](../profiling/media/js_mem_fold_objects.png "JS_Mem_Fold_Objects")  
  
 Aby uzyskać więcej informacji dotyczących dominatorów, zobacz [wyświetlić szczegóły migawki](#view-snapshot-details).  
  
## <a name="filter-data-by-identifier"></a>Filtrowanie danych za pomocą identyfikatora  
 W widoku Dominatorów i typy można odfiltrować dane przez wyszukiwanie określonego identyfikatorów. Aby wyszukać identyfikatora, po prostu wpisz jego nazwę w **filtru identyfikator** polu tekstowym w prawym górnym rogu. Po rozpoczęciu wpisywania, identyfikatory, które nie zawierają wpisane znaki są odfiltrowywane.  
  
 Każdy widok ma własny filtr, więc filtru nie jest zachowywane po przełączeniu do innego widoku.  
  
## <a name="find-an-object-in-the-object-tree"></a>Znajdź obiektu drzewa obiektów  
 W widokach typy i Dominatorów można zobaczyć relację konkretnego obiektu do `Global` obiektu. Obiekty odblokowany dostęp do `Global` obiektu nie będą zbierane w pamięci. Możesz łatwo znaleźć znanego obiektu w widoku elementów głównych, bez wyszukiwania za pomocą `Global` drzewa obiektów. Aby to zrobić, otwórz menu skrótów dla obiekt w Dominatorów lub typu widoku, a następnie wybierz **Pokaż w widoku elementów głównych**.  
  
## <a name="view-shared-object-references"></a>Umożliwia wyświetlanie odwołań do udostępnionego obiektu  
 W widokach typy i Dominatorów dolnym okienku zawiera listy odwołania do obiektów, która zawiera odwołania do udostępnionego. Po wybraniu obiektu w górnym okienku na liście odwołania do obiektu zostaną wyświetlone wszystkie obiekty, które wskazują ten obiekt.  
  
> [!NOTE]
>  Odwołania cykliczne są wyświetlane z gwiazdki (*) i tooltip informacyjny i nie można rozwijać. W przeciwnym razie ich może uniemożliwiać przejście w górę drzewa odwołania i identyfikowania obiektów, które są zachowywania pamięci.  
  
 Jeśli chcesz, aby uzyskać dodatkową pomoc identyfikowania obiektów równoważnych, wybierz **Wyświetl identyfikatory obiektów** na liście ustawień ![upuszczania ustawienia&#45;pozycji listy w analizatorze pamięci](../profiling/media/js_mem_settings.png "JS_Mem_Settings ") w prawym górnym rogu w górnym okienku. Ta opcja powoduje wyświetlenie identyfikatory obiektów obok nazwy obiektów w **identyfikatory** listy (identyfikatory są wyświetlane we wszystkich widokach, nie tylko listy odwołań do obiektów). Obiekty, które mają ten sam identyfikator są udostępnione odwołań.  
  
 Na poniższej ilustracji przedstawiono listy odwołań do obiektów dla wybranego elementu z identyfikatorami wyświetlane.  
  
 ![Obiekt odwołania z identyfikatorami wyświetlanych](../profiling/media/js_mem_shared_refs.png "JS_Mem_Shared_Refs")  
  
## <a name="show-built-in-objects"></a>Pokaż obiekty wbudowane  
 Domyślnie w widokach Dominatorów i typy wyświetlane są tylko obiekty utworzone w aplikacji. Dzięki temu można odfiltrować niepotrzebne informacje i izolowania problemów związanych z aplikacji. Jednak czasami może być przydatne do wyświetlania wszystkich obiektów, które generuje środowiska wykonawczego języka JavaScript dla aplikacji.  
  
 Aby wyświetlić te obiekty, wybierz **Pokaż built-ins** na liście ustawień ![upuszczania ustawienia&#45;pozycji listy w analizatorze pamięci](../profiling/media/js_mem_settings.png "JS_Mem_Settings") w prawym górnym rogu okienka.  
  
## <a name="save-diagnostic-session-files"></a>Zapisywanie plików sesji diagnostycznej  
 Podsumowań diagnostycznych migawki i ich widoków szczegółów skojarzone są zapisywane jako. *diagsession* plików. **Eksplorator rozwiązań** Wyświetla poprzedniej sesji diagnostyki w folderze sesji diagnostyki. W **Eksploratora rozwiązań**, można otworzyć poprzedniej sesji lub usuń lub zmień nazwy plików.  
  
## <a name="associate-source-code-with-memory-usage-data"></a>Skojarz kodu źródłowego z danych użycia pamięci  
 Aby wyizolować części kodu, który ma problem pamięci, należy użyć następujących metod:  
  
- Poszukaj nazwy klas i identyfikatory elementów modelu DOM szczegółowe informacje i widoki różnicowej.  
  
- Wyszukaj wartości ciągu, szczegóły i różnicowe widoków, które mogą być skojarzone z kodu źródłowego.  
  
- Użyj [znaleźć obiektu drzewa obiektów](#find-an-object-in-the-object-tree) polecenie, aby podejść drzewa obiektów. Może to ułatwić do identyfikacji kodu skojarzonego źródła.  
  
- Dodawanie poleceń analizator pamięci do kodu źródłowego.  
  
 W kodzie źródłowym służy następujące polecenia:  
  
-   `console.takeHeapSnapshot` pobiera migawkę sterty w analizator pamięci JavaScript. To polecenie jest jednym z [polecenia konsoli JavaScript](../debugger/javascript-console-commands.md).  
  
-   `performance.mark` Ustawia znacznik użytkownika (odwrócony trójkąt) pojawi się w oś czasu wykresu pamięci w widoku podsumowania, gdy aplikacja jest uruchomiona. To polecenie pobiera jeden argument ciągu zawiera opis zdarzenia, który jest wyświetlany jako etykietka narzędzia na wykresie pamięci. Ten opis nie może przekraczać 100 znaków.  
  
> [!TIP]
>  Użyj `console.takeHeapSnapshot` celu przyspieszenia analizy, gdy powtarzające się scenariusze użycia pamięci.  
  
 Te polecenia Zgłoś wyjątek, jeśli je dodać do aplikacji i uruchamianie aplikacji poza analizator pamięci JavaScript. Można jednak sprawdzić, czy istnieje polecenia przed ich użyciem. (Polecenia nie istnieje na początku fazy uruchamiania sesji). Aby sprawdzić, czy można bezpiecznie wywołać `takeHeapSnapshot`, użyj tego kodu:  
  
```javascript  
if (console && console.takeHeapSnapshot) {  
    console.takeHeapSnapshot();  
}  
```  
  
 Aby sprawdzić, czy można bezpiecznie wywołać `performance.mark`, użyj tego kodu:  
  
```javascript  
if (performance && performance.mark) {  
    performance.mark("message_string");  
}  
  
```  
  
 W tym miejscu jest wykres pamięci z kilku znaków użytkownika i etykietkę narzędzia dla znaku aktualnie wybranego użytkownika, dla którego `performance.mark` argument ciągu ma ustawioną wartość "dane generowane":  
  
 ![Przy użyciu znaku profilu](../profiling/media/js_mem_performance_marks.png "JS_Mem_Performance_Marks")  
  
## <a name="tips-to-identify-memory-issues"></a>Wskazówek dotyczących identyfikowania problemy z pamięcią  
  
-   Zgodne z przepływem pracy opisanego w [izolować przeciek pamięci](#isolate-a-memory-leak) i użyj **obiekty pozostałe z migawki nr\<numer >** filtru w widoku różnic, aby zidentyfikować prawdopodobnie kandydatów do przecieki pamięci.  
  
-   Użyj [znaleźć obiektu drzewa obiektów](#find-an-object-in-the-object-tree) aby zobaczyć, których odwołań do obiektu w hierarchii pamięci. Widoku elementów głównych pokazuje, jak obiekt jest odblokowany dostęp do globalnego obiektu, który może uniemożliwić zbierane pamięci.  
  
-   Gdy przyczyny problemu pamięci trudno jest określić, użyj różnych widokach (takich jak Dominatorów i typy), aby wyszukać commonalities, szczególnie w celu identyfikowania jeden obiekt (lub kilka obiektów) który mogą zawierać odwołania do wielu innych obiektów, które są wyświetlane w Widok.  
  
-   Wyszukaj obiekty, które pozostają w pamięci mogą przypadkowo po użytkownikowi nawigację do nowej strony, który jest częstą przyczyną problemy z pamięcią. Na przykład:  
  
    -   Nieprawidłowe użycie [adresu URL. CreateObjectUrl](http://msdn.microsoft.com/library/windows/apps/hh453196.aspx) funkcja przyczyny tego problemu.  
  
    -   Niektóre obiekty mogą udostępniać `dispose` — metoda i zalecenia dotyczące użycia. Na przykład, należy wywołać `dispose` na [WinJS.Binding.List](http://msdn.microsoft.com/library/windows/apps/Hh700774.aspx) wywołanie listy `createFiltered` metody, a następnie opuścić stronę.  
  
    -   Może być konieczne usunięcie co najmniej jednego odbiornika zdarzeń. Aby uzyskać więcej informacji, zobacz [odbiorników zdarzeń DOM widoku](../debugger/view-dom-event-listeners.md).  
  
-   Obejrzyj to drugie część [ten film](http://channel9.msdn.com/Events/Build/2013/3-316) z konferencji 2013 kompilacji o analizator pamięci JavaScript.  
  
-   Odczyt [zarządzanie pamięcią w aplikacji platformy UWP](http://msdn.microsoft.com/magazine/jj651575.aspx).  
  
-   Należy rozważyć tymczasowo modyfikowania kodu do izolowania problemów. Na przykład możesz chcieć:  
  
    -   Analizator pamięci, należy użyć poleceń `console.takeSnapshot` i `performance.mark`. (Zobacz [skojarzyć kodu źródłowego z danych użycia pamięci](#associate-source-code-with-memory-usage-data).)  
  
         Aby wyizolować problemy, które nie izolować przez ręczne tworzenie migawki sterty można używać tych poleceń.  
  
    -   Utwórz obiekt testowy i śledzenia ją w widokach analizator pamięci JavaScript, takie jak wyświetlanie typów. Na przykład bardzo duży obiekt można dołączyć do innego obiektu, aby zobaczyć, czy określony obiekt lub element został zbierane pamięci.  