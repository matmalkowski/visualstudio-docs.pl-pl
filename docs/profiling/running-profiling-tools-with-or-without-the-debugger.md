---
title: "Uruchomione narzędzia profilowania z lub bez debuger | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3fcdccad-c1bd-4c67-bcec-bf33a8fb5d63
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 2507ec49129692914ba6d11e4f651d5895b49c8b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="running-profiling-tools-with-or-without-the-debugger"></a>Uruchomione narzędzia profilowania z lub bez debugera
Visual Studio teraz oferuje możliwość wyboru wydajności narzędzi, niektóre z nich (na przykład **użycie procesora CPU** i **użycie pamięci**) można uruchomić z lub bez debugera. Narzędzia non debugera wydajności są przeznaczone do uruchamiania na wersji konfiguracji, gdy debuger zintegrowane narzędzia są przeznaczone do uruchamiania na konfiguracji debugowania.  
  
## <a name="should-i-run-the-tool-with-or-without-the-debugger"></a>Narzędzie należy uruchomić z lub bez debugera?  
 Narzędzia zintegrowane debugera wydajności pozwalają dużo operacji wykonywanych przez narzędzia z systemem innym niż debuger nie może, na przykład ustawić punkty przerwania i sprawdzić wartości zmiennych. Narzędzia debugera nie zapewniają środowisko bliżej co widzi użytkowników wydanych aplikacji.  
  
 Oto kilka pytań, które mogą pomóc zdecydować, jakiego rodzaju narzędzie jest odpowiednia do własnych celów:  
  
1.  Problem podczas aplikacji został on opracowany lub został on został znaleziony w wydanej wersji?  
  
     Jeśli problem, który mamy do czynienia z został znaleziony podczas tworzenia, prawdopodobnie nie trzeba uruchomić narzędzia wydajności w kompilacji wydania. Jeśli został odnaleziony w wersji, należy odtworzyć problem z konfiguracją wersji i zdecyduj, czy debuger może pomóc w celu dokładniejszego zbadania.  
  
2.  Przetwarza problem spowodowany przez użycie Procesora CPU  
  
     Wiele problemów są z powodu problemów z wydajnością zewnętrznych, takich jak plik we/wy lub czasu odpowiedzi sieci, dlatego nie należy utworzyć różnica, czy uruchamianie narzędzi do oceny wydajności z lub bez debugera. W przypadku problemu z powodu wywołuje użycie Procesora CPU, różnica między konfiguracje wersji i debugowania mogą być znaczne i prawdopodobnie należy sprawdzić, czy problem istnieje w kompilacji wydania przed użyciem narzędzia zintegrowane debugera  
  
3.  Należy dokładnie mierzyć wydajność, czy dopuszczalny jest przybliżoną liczbę?  
  
     Debugowania braku kompilacje niektóre funkcje optymalizacji, które zapewniają kompilacjami wydania, na przykład ze śródwierszowaniem wywołania funkcji i stałych oczyszczania nieużywane kod ścieżki i zmiennych zapisywanie w sposób, który nie może być używana przez debuger. Debuger się zmienia się razy wydajności, ponieważ wykonywania pewnych operacji, które są niezbędne do debugowania (na przykład przechwytywaniu wyjątków i zdarzeń ładowania modułu). Numery wydajności w narzędziach zintegrowane debugera są mniej dokładne, bez uwzględnienia optymalizacje debugera, ale nadal mogą być przydatne w porównaniu z innych względnych pomiarów podczas debugowania. Numery wydajności w przypadku wersji konfiguracji przy użyciu narzędzi z systemem innym niż debugera są bardziej dokładne.
  
##  <a name="BKMK_Quick_start__Collect_diagnostic_data"></a>Zbieranie danych profilowania podczas debugowania  
 Poniższa sekcja zawiera debugowania lokalnego. Można znaleźć informacje o debugowaniu na urządzeniu lub debugowanie zdalne w kolejnych sekcjach.  
  
1.  Otwórz projekt chcesz debugować, następnie kliknij przycisk **Debug / Rozpocznij debugowanie** (lub **Start** na pasku narzędzi lub **F5**).  
  
2.  **Narzędzia diagnostyczne** okna pojawiają się automatycznie, jeśli wyłączono go. Aby wyświetlić okno ponownie, kliknij przycisk **Debug / Windows / Pokaż narzędzia diagnostyczne**.  
  
3.  Uruchom scenariusze, które mają być zbierane dane.  
  
     Podczas uruchamiania sesji, znajdują się informacje dotyczące zdarzeń, pamięci procesu i użycie procesora CPU.  
  
     Poniżej przedstawiono graficzne **narzędzia diagnostyczne** okna w Visual Studio 2015 Update 1:  
  
     ![DiagnosticTools &#45; Aktualizację1](../profiling/media/diagnostictools-update1.png "aktualizację1 DiagnosticTools")  
  
4.  Można wybrać, czy wyświetlane **użycie pamięci** lub **użycie procesora CPU** (lub obie) z **wybierz narzędzia** ustawienie na pasku narzędzi. Jeśli używasz programu Visual Studio Enterprise, można włączyć lub wyłączyć IntelliTrace w **narzędzia / Opcje / IntelliTrace**.  
  
5.  Sesja diagnostyczna kończy się po zatrzymaniu debugowania.  
  
 W programie Visual Studio 2015 Update 1 **narzędzia diagnostyczne** okna ułatwia dla można skupić się na zdarzenia planuje się.   Nazwy zdarzenia są wyświetlane z prefiksami kategorii (**gestu**, **dane wyjściowe programu**, **punktu przerwania**, **pliku** itp.), można szybko Przejrzyj listę dla danej kategorii lub pominąć kategorie, które nie zależy Ci.  
  
 Okno teraz zawiera pole wyszukiwania, dzięki czemu można znaleźć określony ciąg gdziekolwiek listy zdarzeń. Na przykład na poniższym rysunku przedstawiono wyniki wyszukiwania dla ciągu "Zainstaluj" zgodny czterech zdarzeń:  
  
 ![DiagnosticsEventSearch](../profiling/media/diagnosticseventsearch.png "DiagnosticsEventSearch")  
  
 Można również filtrować zdarzenia i widoku w oknie. W **filtru** listy rozwijanej, sprawdzić, czy lub usuń zaznaczenie pola wyboru określonych kategorii zdarzeń:. Nazwy kategorii są takie same jak nazwy prefiksu.  
  
 ![DiagnosticEventFilter](../profiling/media/diagnosticeventfilter.png "DiagnosticEventFilter")  
  
 Aby uzyskać więcej informacji, zobacz [wyszukiwanie i filtrowanie karcie zdarzeń w oknie narzędzia diagnostyczne](http://blogs.msdn.com/b/visualstudioalm/archive/2015/11/12/searching-and-filtering-the-events-tab-of-the-diagnostic-tools-window.aspx).  
  
## <a name="collect-profiling-data-without-debugging"></a>Zbieranie danych profilowania bez debugowania  
 Niektóre narzędzia profilowania wymagają uprawnień administratora do uruchomienia. Można uruchomić programu Visual Studio jako administrator lub użytkownik może uruchomić narzędzia jako administrator, podczas uruchamiania sesji diagnostycznej.  
  
1.  Otwórz projekt w programie Visual Studio.  
  
2.  Na **debugowania** menu, wybierz **profilera wydajności...** (Klawisz skrótu: Alt + F2).  
  
3.  Na stronie uruchamiania diagnostyki wybierz co najmniej jedno narzędzie do pracy w sesji. Wyświetlane są tylko narzędzia, które mają zastosowanie do projektu typu systemu operacyjnego i język programowania. Po wybraniu narzędzie diagnostyczne są wyłączone wybrane narzędzia, których nie można uruchomić w tej samej sesji diagnostycznej. Oto, jak może wyglądać wybranych aplikacji C# uniwersalnych systemu Windows:  
  
     ![Wybierz narzędzia diagnostyczne](../profiling/media/diag_selecttool.png "DIAG_SelectTool")  
  
4.  Aby uruchomić sesji diagnostycznej, kliknij przycisk **Start**.  
  
5.  Uruchom scenariusze, dla których chcesz zbierać dane.  
  
     Podczas uruchamiania sesji, niektóre narzędzia wyświetlane wykresy danych w czasie rzeczywistym na stronie uruchamiania narzędzia diagnostyczne.  
  
     ![Zebranie danych dotyczących wydajności i diagnostyki Zazn](../profiling/media/pdhub_collectdata.png "PDHUB_CollectData")  
  
6.  Aby zakończyć sesję diagnostyki, kliknij przycisk **zatrzymać zbieranie**.  
  
 Po zatrzymaniu zbierania danych w sesji diagnostycznej, analizy danych, a raport jest wyświetlany na stronie diagnostyki.  
  
 Można również otworzyć sesji .diagnostic zapisanej strony uruchamianie plików z listy ostatnio otwartą na narzędzia diagnostyczne.  
  
 ![Otwórz plik sesji diagnostyki zapisane](../profiling/media/pdhub_openexistingdiagsession.png "PDHUB_OpenExistingDiagSession")  
  
## <a name="the-profiling-report"></a>Raport profilowania  
 ![Raport narzędzi diagnostycznych](../profiling/media/diag_report.png "DIAG_Report")  
  
|||  
|-|-|  
|![Krok 1](../profiling/media/procguid_1.png "ProcGuid_1")|Na osi czasu są widoczne długość sesji profilowania, zdarzenia aktywacji cyklu życia aplikacji i znaczniki użytkownika.|  
|![Krok 2](../profiling/media/procguid_2.png "ProcGuid_2")|Raport można ograniczyć do części osi czasu, przeciągając niebieskie paski w celu wybrania regionu na osi czasu.|  
|![Krok 3](../profiling/media/procguid_3.png "ProcGuid_3")|Narzędzie wyświetla co najmniej jednego głównego wykresy. Jeśli sesja diagnostyki została utworzona z wielu narzędzi, zostaną wyświetlone wszystkie wykresy wzorca.|  
|![Krok 4](../profiling/media/procguid_4.png "ProcGuid_4")|Można zwijać i rozwijać poszczególnych wykresów.|  
|![Krok 5](../profiling/media/procguid_6.png "ProcGuid_6")|Jeśli dane zawierają informacje z różnych narzędzi, szczegóły dla tego narzędzia są zbierane na kartach.|  
|![Krok 6](../profiling/media/procguid_6a.png "ProcGuid_6a")|To narzędzie może mieć co najmniej jeden widok szczegółów. Widok są filtrowane według wybranego regionu osi czasu.|  
  
## <a name="setting-the-analysis-target-to-another-device"></a>Ustawienie docelowej analizy na innym urządzeniu  
 Oprócz uruchamiania aplikacji z projektu programu Visual Studio, można również uruchomić sesji diagnostycznych na alternatywnych obiektów docelowych. Na przykład możesz chcieć diagnozowanie problemów z wydajnością w wersji aplikacji zainstalowanej ze sklepu z aplikacjami systemu Windows.  
  
 ![Wybierz element docelowy analizy narzędzia diagnostyczne](../profiling/media/pdhub_chooseanalysistarget.png "PDHUB_ChooseAnalysisTarget")  
  
 Można uruchomić aplikacji, które są już zainstalowane na urządzeniu lub narzędzia diagnostyczne można dołączyć do niektórych aplikacji, które zostały już uruchomione. Po wybraniu **uruchamiania aplikacji** lub **zainstalowanych aplikacji**, wybierz aplikację z listy, który wykryje aplikacji w celu określonego wdrożenia.  
  
 ![Wybierz uruchomiona lub jest zainstalowana aplikacja diagnostyki](../profiling/media/pdhub_selectrunningapp.png "PDHUB_SelectRunningApp")  
  
 Po wybraniu **programu Internet Explorer**, podaj adres URL i można zmienić cel wdrożenia telefonu.  
  
 ![Podaj adres url do wyświetlenia w programie Internet Explorer](../profiling/media/pdhub_choosephoneanalysistarget.png "PDHUB_ChoosePhoneAnalysisTarget")  
  
## <a name="remote-debugging"></a>Debugowanie zdalne  
 Uruchomiona na zdalnym komputerze lub tablecie sesji diagnostycznej wymaga programu Visual Studio Tools zdalnego zainstalowana i uruchomiona w celu zdalnego. Dla aplikacji klasycznych, zobacz [zdalnego debugowania](../debugger/remote-debugging.md).  Dla aplikacji uniwersalnych systemu Windows, temacie [aplikacji platformy uniwersalnej systemu Windows uruchom na komputerze zdalnym](../debugger/run-windows-store-apps-on-a-remote-machine.md).  
  
## <a name="blog-posts-and-msdn-articles-from-the-diagnostics-development-team"></a>Wpisy na blogu i artykuły MSDN z zespół deweloperów diagnostyki  
 [MSDN Magazine: Analizowanie wydajności podczas debugowania w programie Visual Studio 2015](https://msdn.microsoft.com/en-us/magazine/dn973013.aspx)  
  
 [MSDN Magazine: Umożliwia szybsze diagnozowanie problemów IntelliTrace](https://msdn.microsoft.com/en-us/magazine/dn973014.aspx)  
  
 [Wpis w blogu: diagnozowanie przecieki programu obsługi zdarzeń za pomocą narzędzia użycia pamięci w programie Visual Studio 2015](http://blogs.msdn.com/b/visualstudioalm/archive/2015/04/29/diagnosing-event-handler-leaks-with-the-memory-usage-tool-in-visual-studio-2015.aspx)  
  
 [Wideo: Debugowanie historyczne przy użyciu funkcji IntelliTrace w programie Visual Studio Ultimate 2015](https://channel9.msdn.com/Events/Ignite/2015/BRK3716)  
  
 [Wideo: Debugowanie problemów z wydajnością przy użyciu programu Visual Studio 2015](https://channel9.msdn.com/Events/Build/2015/3-731)  
  
 [Wskazówek: Informacje o wydajności w ułatwia podczas debugowania w programie Visual Studio](http://blogs.msdn.com/b/visualstudioalm/archive/2014/08/18/perftips-performance-information-at-a-glance-while-debugging-with-visual-studio.aspx)  
  
 [Diagnostyczne narzędzia okna debugera programu Visual Studio 2015](http://blogs.msdn.com/b/visualstudioalm/archive/2015/01/16/diagnostic-tools-debugger-window-in-visual-studio-2015.aspx)  
  
 [IntelliTrace w Visual Studio Enterprise 2015](http://blogs.msdn.com/b/visualstudioalm/archive/2015/01/16/intellitrace-in-visual-studio-ultimate-2015.aspx)
