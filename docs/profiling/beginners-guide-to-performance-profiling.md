---
title: "Profilowanie wydajności aplikacji w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: H1Hack27Feb2017
ms.date: 02/27/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: get-started-article
f1_keywords:
- vs.performance.wizard.intropage
helpviewer_keywords:
- Profiling Tools, quick start
- Diagnostics Tools, CPU Usage
- CPU Usage
- Diagnostics Tools
ms.assetid: da2fbf8a-2d41-4654-a509-dd238532d25a
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: bacc4e9ebb0b0125b22089ec53a97248e9e1f4e9
ms.sourcegitcommit: 9e6ff74da1afd8bd2f0e69387ce81f2a74619182
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2018
---
# <a name="profile-application-performance-in-visual-studio"></a>Profilowanie wydajności aplikacji w programie Visual Studio
Visual Studio, narzędzia profilowania służy do analizowania problemów z wydajnością w aplikacji. Ta procedura przedstawia sposób użycia **użycie procesora CPU** kartę narzędzi diagnostycznych można uzyskać danych wydajności dla aplikacji. Narzędzia diagnostyczne są obsługiwane dla .NET development w Visual Studio, w tym aplikacji ASP.NET i programowania w języku macierzystym/C++.
  
Gdy wstrzymuje debugera, **użycie procesora CPU** narzędzie zbiera informacje o funkcjach, które są wykonywane w aplikacji. Narzędzie wyświetla listę funkcji, które zostały wykonywania pracy i umożliwia wykresu osi czasu, który można skupić się na poszczególnych segmentów sesji próbkowania.

Centrum diagnostyki oferuje wiele innych opcji do zarządzania sesję diagnostyczną. Jeśli **użycie procesora CPU** nie zapewnia dane, które chcesz dodać, [innych narzędzi do profilowania](../profiling/Profiling-Tools.md) zapewniają różne rodzaje informacji, które mogą być przydatne do Ciebie. W wielu przypadkach wąskie gardło aplikacji może być spowodowane przez inną niż Procesora, pamięci, renderowania interfejsu użytkownika lub czas żądania sieciowego. Centrum diagnostyki oferuje wiele innych opcji, aby rejestrować i analizować tego typu danych.

|         |         |
|---------|---------|
|  ![Ikona aparatu film wideo](../install/media/video-icon.png "obejrzeć film wideo")  |    [Obejrzyj film](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Profiling-with-Diagnostics-Tools-in-Visual-Studio-2017-daHnzMD6D_9211787171) przy użyciu narzędzia diagnostyczne, które pokazuje sposób Analiza użycia procesora CPU i analizowanie użycia pamięci. |

W tym temacie omówiono Analiza użycia procesora CPU w normalnym przepływie pracy debugowania. Użycie procesora CPU można analizować również bez istnieje debuger dołączony lub wybierając uruchomionej aplikacji — Aby uzyskać więcej informacji, zobacz [zbierania danych profilowania bez debugowania](../profiling/running-profiling-tools-with-or-without-the-debugger.md#collect-profiling-data-without-debugging) w [uruchomienie narzędzia z lub bez debugeraprofilowania](../profiling/running-profiling-tools-with-or-without-the-debugger.md).
  
##  <a name="BKMK_Quick_start__Collect_diagnostic_data"></a>Krok 1: Zbieranie danych profilowania 
  
1.  Otwórz projekt, który ma być debugowania w programie Visual Studio i ustaw punkt przerwania w aplikacji w momencie, gdy chcesz sprawdzić użycie procesora CPU.

2.  Ustaw drugiego punktu przerwania na końcu funkcji lub regionu, kodu, który chcesz przeanalizować.

    > [!TIP]
    > Ustawiając dwa punkty przerwania, można ograniczyć zbieranie danych do części kodu, który chcesz przeanalizować.
  
3.  **Narzędzia diagnostyczne** okna pojawiają się automatycznie, jeśli wyłączono go. Aby wyświetlić okno ponownie, kliknij przycisk **Debug / Windows / Pokaż narzędzia diagnostyczne**.

4.  Można wybrać, czy wyświetlane **użycie procesora CPU**, [użycie pamięci](../profiling/Memory-Usage.md), i/lub z **wybierz narzędzia** ustawienie na pasku narzędzi. Jeśli używasz programu Visual Studio Enterprise, można również włączyć lub wyłączyć IntelliTrace w **narzędzia / Opcje / IntelliTrace**.

     ![Pokaż narzędzia diagnostyczne](../profiling/media/DiagToolsSelectTool.png "DiagToolsSelectTool")

     Firma Microsoft będzie głównie można spojrzenie na wykorzystanie procesora CPU, upewnij się, że **użycie procesora CPU** jest włączona (jest ona włączona domyślnie).

5.  Kliknij przycisk **Debug / Rozpocznij debugowanie** (lub **Start** na pasku narzędzi lub **F5**).

     Po zakończeniu ładowania aplikacji zostanie wyświetlony widok podsumowania narzędzi diagnostycznych.

     ![Karta Podsumowanie narzędzi diagnostycznych](../profiling/media/DiagToolsSummaryTab.png "DiagToolsSummaryTab")

     Aby uzyskać więcej informacji na temat zdarzeń, zobacz [wyszukiwanie i filtrowanie karcie zdarzeń w oknie narzędzia diagnostyczne](http://blogs.msdn.com/b/visualstudioalm/archive/2015/11/12/searching-and-filtering-the-events-tab-of-the-diagnostic-tools-window.aspx)

6.  Uruchom scenariusz, który spowoduje, że pierwszy punkt przerwania do trafiony.

7.  Gdy debuger jest wstrzymana, włącz opcję zbierania danych użycia procesora CPU, a następnie otwórz **użycie procesora CPU** kartę.

     ![Narzędzia diagnostyki Włącz profilowanie procesora CPU](../profiling/media/DiagToolsEnableCPUProfiling.png "DiagToolsEnableCPUProfiling")

     Po wybraniu **rekord Procesora profilu**, Visual Studio rozpocznie się rejestrowanie funkcji i jak długo podjęte w celu wykonania. Zebrane dane można przeglądać tylko wtedy, gdy aplikacja jest zatrzymywane w punkcie przerwania.

8.  Naciśnij klawisz F5, aby uruchomić aplikację na drugi punkt przerwania.

     Teraz masz teraz dane dotyczące wydajności aplikacji specjalnie dla regionu kodu, który uruchamia między dwoma punktami przerwań.

9.  Wybierz region interesują Cię analizowanie na osi czasu Procesora (musi to być region, który zawiera dane profilowania).

     ![Narzędzia diagnostyki wybranie Segment czasu](../profiling/media/DiagToolsSelectTimeSegment.png "DiagToolsSelectTimeSegment")

     Profiler rozpoczyna przygotowywania danych wątku. Poczekaj na jego zakończenie.

     ![Przygotowywanie wątków narzędzi diagnostycznych](../profiling/media/DiagToolsPreparingThreads.png "DiagToolsPreparingThreads")
  
     Użycie procesora CPU narzędzie wyświetla raport w **użycie procesora CPU** kartę.
  
     ![Diagnostyka narzędzia użycie procesora CPU kartę](../profiling/media/DiagToolsCPUUsageTab.png "DiagToolsCPUUsageTab")

     W tym momencie można rozpocząć do analizowania danych.

## <a name="Step2"></a>Krok 2: Analizowanie danych użycia procesora CPU

Zalecamy rozpocząć analizowanie danych, sprawdzając listę funkcji zgodnie z użycia procesora CPU, identyfikowanie funkcji, które robią najbardziej pracy i następnie biorąc bliższe spojrzenie na każdym z nich.

1. Na liście funkcji badania funkcji, które robią większość pracy.

    ![Diagnostyka narzędzia użycie procesora CPU funkcja listy](../profiling/media/DiagToolsCPUUsageFunctionList.png "DiagToolsCPUUsageFunctionList")

    > [!TIP]
    > Funkcje są wymienione w kolejności, począwszy od tych czynności najbardziej pracy (nie są one w kolejności wywołania). Dzięki temu można szybko zidentyfikować najdłuższym funkcje uruchomione.

2. Na liście funkcji dwukrotnie kliknij jedną z funkcji aplikacji, które jest w sposób pracy.

    Po dwukrotnym kliknięciu funkcja **wywołujący/wywoływany** widok zostanie otwarty w okienku po lewej stronie. 

    ![Widok wywoływany obiekt wywołujący narzędzi diagnostycznych](../profiling/media/DiagToolsCallerCallee.png "DiagToolsCallerCallee")

    W tym widoku wybranej funkcji zostaną wyświetlone w nagłówku, a w **bieżącej funkcji** okno (w tym przykładzie GetNumber). Funkcji, które wywołały bieżącą funkcję jest wyświetlany po lewej stronie w obszarze **podczas wywoływania funkcji**, a wszystkie funkcje wywoływane przez bieżącą funkcję są wyświetlane w **funkcji o nazwie** pole po prawej stronie. (Wybierz albo pola, aby zmienić bieżącą funkcję).

    Ten widok przedstawia łączny czas (ms) i odsetek ogólną aplikacji czasu podejmujący funkcja do wykonania działania.
    **Treść funkcji** również przedstawia łączną ilość czasu (i wartość procentowa czasu) w treści funkcji bez czasu poświęcony na wywołanie i wywołać funkcji. (W tym przykładzie ms 3713 poza 3729 zostały spędzony w treści funkcji, a pozostałe 16 ms zostały spędzony w kodzie zewnętrznych wywoływanych przez tę funkcję).

    > [!TIP]
    > Wysokiej wartości w **treści funkcji** może wskazywać wąskie gardło w samej funkcji.

3. Jeśli chcesz zobaczyć wyższego poziomu widoku pokazującego kolejność są funkcje wywołane, wybierz pozycję **drzewa wywołań** z listy rozwijanej w górnej części okienka.
 
    Poszczególnych numerowane obszar na ilustracji odnosi się do kroku w procedurze.
  
    ![Narzędzia diagnostyki drzewie wywołań](../profiling/media/DiagToolsCallTree.png "DiagToolsCallTree")
  
|||
|-|-|
|![Krok 1](../profiling/media/ProcGuid_1.png "ProcGuid_1")|Węzeł najwyższego poziomu w drzewach wywołania użycia procesora CPU jest pseudo-węzłem|  
|![Krok 2](../profiling/media/ProcGuid_2.png "ProcGuid_2")|W przypadku większości aplikacji gdy [Pokaż kod zewnętrzny](#BKMK_External_Code) opcja zostanie wyłączona, węzeł drugiego poziomu **[kod zewnętrzny]** węzła, który zawiera kod systemu i platformy, który uruchamiania i zatrzymywania aplikacji rysuje interfejsu użytkownika, Steruje planowania wątków i innymi usługami niskiego poziomu do aplikacji.|  
|![Krok 3](../profiling/media/ProcGuid_3.png "ProcGuid_3")|Element podrzędny węzła drugiego poziomu są metody kodu użytkownika i procedur asynchroniczne, które wywołuje lub utworzony przez system drugiego poziomu i kod framework.|
|![Krok 4](../profiling/media/ProcGuid_4.png "ProcGuid_4")|Węzły podrzędne metody zawierają dane tylko w przypadku wywołania metody nadrzędnej. Gdy **Pokaż kod zewnętrzny** jest wyłączona, metody aplikacja może również zawierać **[kod zewnętrzny]** węzła.|

Poniżej przedstawiono więcej informacji na temat wartości kolumn:

- **Łączna liczba procesorów** wskazuje ilość pracy została wykonana przez funkcję i wszystkie funkcje wywoływane przez go. Wysoka łączne wartości Procesora wskaż funkcje, które są najbardziej kosztownych ogólne.
  
- **Samodzielna Procesora** wskazuje ilość pracy została wykonana przez kod w treści funkcji, z wyłączeniem pracy wykonanej przez funkcje, które zostały wywołane przez nią. Wysoka **Procesora samoobsługowego** wartości może wskazywać wąskie gardło w samej funkcji.

- **Moduły** nazwę modułu zawierającego funkcję lub liczba modułów zawierających funkcje w węźle [kod zewnętrzny].

## <a name="BKMK_External_Code"></a>Widok kodu zewnętrznego

Funkcje w systemie i składników struktury są zewnętrznego kodu napisanego wykonywanych przez kod. Kod zewnętrzny obejmują funkcje, które start i Zatrzymaj aplikację, Rysuj interfejsu użytkownika, kontroli wątków i podaj inne niskiego poziomu usług do aplikacji. W większości przypadków będzie zainteresowana kod zewnętrzny, i dlatego narzędzia użycie procesora CPU zbiera funkcji zewnętrznych metody użytkownika do jednego **[kod zewnętrzny]** węzła.
  
Wyświetlanie ścieżek wywołań zewnętrznego kodu, należy wybrać **Pokaż kod zewnętrzny** z **filtrowanie widoku** listy, a następnie wybierz pozycję **Zastosuj**.  
  
![Wybierz Widok filtrów, a następnie wyświetlić kod zewnętrzny](../profiling/media/DiagToolsShowExternalCode.png "DiagToolsShowExternalCode")  
  
Należy pamiętać, że wiele łańcuchów wywołanie kodu zewnętrznego głęboko zagnieżdżone, tak, aby szerokość kolumny nazwy funkcji może być dłuższa niż szerokość wyświetlania wszystkich oprócz największy monitorów komputera. W takim przypadku funkcja nazwy są wyświetlane jako **[...]** .
  
Użyj pola wyszukiwania można znaleźć węzła, którego szukasz, a następnie przełącz do widoku danych za pomocą paska przewijania w poziomie.

> [!TIP]
> Jeśli profil zewnętrznego kodu, który wywołuje funkcje systemu Windows, należy upewnić się, czy masz najnowsze pliki PDB. Bez tych plików widoków raportu spowoduje wyświetlenie listy nazw funkcji systemu Windows, które są trudne do zrozumienia i są one niezrozumiałe. Aby uzyskać więcej informacji o sposobie upewnij się, że pliki potrzebne, zobacz [Określ symboli (.pdb) i plików źródłowych w debugerze](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).
  
## <a name="see-also"></a>Zobacz też  
 [Użycie pamięci](../profiling/memory-usage.md)  
 [Użycie procesora CPU](../profiling/cpu-usage.md)  
 [Profilowanie w programie Visual Studio](../profiling/index.md)  
 [Przegląd funkcji profilowania](../profiling/profiling-feature-tour.md)
