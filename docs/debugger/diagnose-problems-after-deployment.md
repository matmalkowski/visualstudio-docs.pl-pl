---
title: "Diagnozowanie problemów po wdrożeniu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 06/20/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a3463eab-a352-4d17-8551-adbaad526db0
caps.latest.revision: "60"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4f2dce73eab17d97779edec73c1c2c0c60690ac5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="diagnose-problems-after-deployment"></a>Diagnozowanie problemów po wdrożeniu
Aby zdiagnozować problemy w aplikacji sieci web ASP.NET po wdrożeniu przy użyciu funkcji IntelliTrace, obejmują informacje o kompilacji z Twojej wersji, aby umożliwić programowi Visual Studio automatycznie znaleźć poprawnych plików źródłowych i pliki symboli, które są wymagane do debugowania dziennika funkcji IntelliTrace.  

 Jeśli korzystasz z programu Microsoft Monitoring Agent do formantu IntelliTrace, należy skonfigurować konfigurowanie monitorowania wydajności aplikacji na serwerze sieci web. Rejestruje zdarzeń diagnostycznych, podczas gdy aplikacji działa i zapisuje zdarzenia do pliku dziennika funkcji IntelliTrace. Następnie można przejrzeć zdarzenia w Visual Studio Enterprise (ale nie Professional lub Community Edition), przejdź do kodu, w którym wystąpiło zdarzenie, przyjrzeć się zarejestrowane wartości w danym momencie i przenoszenie przodu lub do tyłu przez kod, który został uruchomiony. Po odnaleźć i rozwiązać ten problem, powtórz cykl w celu tworzenia, wersji i monitorować Twojej wersji, dlatego można rozwiązać potencjalne problemy w przyszłości wcześniej i szybsze.  

 ![Kod, kompilacji, wersji, monitorowanie, diagnozowanie, napraw](../debugger/media/ffr_cycle.png "FFR_Cycle")  

 **Potrzebne są:**  
  
-   Visual Studio 2017, Visual Studio 2015 lub Team Foundation Server 2017 r. 2015, 2013, 2012 lub 2010, aby skonfigurować kompilację  
  
-   Microsoft Monitoring Agent monitorowania aplikacji i rejestrowanie danych diagnostycznych  

-   Visual Studio Enterprise (ale nie w wersji Professional lub społeczności), aby przejrzeć dane diagnostyczne i debugowanie kodu przy użyciu funkcji IntelliTrace  

##  <a name="SetUpBuild"></a>Krok 1: Obejmują informacje o Twojej wersji kompilacji  
 Konfigurowanie procesu kompilacji do tworzenia manifestu kompilacji (plik BuildInfo.config) dla projektu sieci web i obejmują tego manifestu z Twojej wersji. Tego manifestu zawiera informacje dotyczące projektu kontroli źródła, a system kompilacji, które zostały użyte do utworzenia określonej kompilacji. Informacje te pomagają Visual Studio Znajdź pasujące źródło i symbole po otwarciu dziennika IntelliTrace, aby przejrzeć zarejestrowane zdarzenia.  

###  <a name="AutomatedBuild"></a>Tworzenie manifestu kompilacji dla kompilacji zautomatyzowanych za pomocą programu Team Foundation Server  

 Wykonaj następujące kroki, czy używasz kontroli wersji Team Foundation lub Git.
  
 **Krok 2:** [krok 2: wersji aplikacji](#DeployRelease)  
  
 Wykonaj następujące kroki, czy używasz kontroli wersji Team Foundation lub Git.  
 
 ####  <a name="TFS2017"></a>Team Foundation Server 2017

 Skonfiguruj definicję kompilacji, aby dodać lokalizacje źródłowe, kompilacji i symboli do manifestu kompilacji (plik BuildInfo.config). Team Foundation Build automatycznie tworzy ten plik i umieszczenie go w folderze wyjściowym projektu.
  
1.  Jeśli masz już definicję kompilacji, przy użyciu szablonu platformy ASP.NET Core (.NET Framework), możesz albo [edytować definicję kompilacji lub Utwórz nową definicję kompilacji.](http://msdn.microsoft.com/Library/1c2eca2d-9a65-477e-9b23-0678ff7882ee)
  
     ![Wyświetl definicję w TFS 2017 kompilacji](../debugger/media/ffr_tfs2017viewbuilddefinition.png "FFR_TFS2013ViewBuildDefinition")
  
2.  W przypadku utworzenia nowego szablonu, wybierz szablon platformy ASP.NET Core (platforma .NET). 
  
     ![Wybierz szablon procesu kompilacji &#45; TFS 2017](../debugger/media/ffr_tfs2017buildprocesstemplate.png "FFR_TFS2013BuildProcessTemplate")  
  
3.  Określanie lokalizacji zapisu pliku symboli (PDB), dzięki czemu źródła jest indeksowana automatycznie.  
  
     Jeśli używasz szablonu niestandardowego, upewnij się, że szablon ma działanie do indeksowania źródła. Określ, gdzie chcesz zapisać pliki symboli argument MSBuild będzie później dodać.
  
     ![Ustawianie ścieżki symboli w definicji kompilacji TFS 2017](../debugger/media/ffr_tfs2017builddefsymbolspath.png "FFR_TFS2013BuildDefSymbolsPath")  
  
     Aby uzyskać więcej informacji o symbolach, zobacz [publikowania danych symbol](http://msdn.microsoft.com/Library/bd6977ca-e30a-491a-a153-671d81222ce6).  
  
4.  Dodaj ten argument MSBuild, aby objąć lokalizacje TFS i symbole kompilacji pliku manifestu:  
  
     **/p:IncludeServerNameInBuildInfo = true**  
  
     Każdy, kto może uzyskiwać dostęp do serwera sieci web jest widoczny te lokalizacje w manifeście kompilacji. Upewnij się, że serwer źródłowy jest zabezpieczone.
  
6.  Uruchom nową kompilację.  

####  <a name="TFS2013"></a>Team Foundation Server 2013  
 Skonfiguruj definicję kompilacji, aby dodać lokalizacje źródłowe, kompilacji i symboli do manifestu kompilacji (plik BuildInfo.config). Team Foundation Build automatycznie tworzy ten plik i umieszczenie go w folderze wyjściowym projektu.  

1.  [Edytuj definicję kompilacji lub Utwórz nową definicję kompilacji.](http://msdn.microsoft.com/Library/1c2eca2d-9a65-477e-9b23-0678ff7882ee)  

     ![Wyświetl definicję w TFS 2013 kompilacji](../debugger/media/ffr_tfs2013viewbuilddefinition.png "FFR_TFS2013ViewBuildDefinition")  

2.  Wybierz szablon domyślny (TfvcTemplate.12.xaml) lub własny szablon niestandardowy.  

     ![Wybierz szablon procesu kompilacji &#45; TFS 2013](../debugger/media/ffr_tfs2013buildprocesstemplate.png "FFR_TFS2013BuildProcessTemplate")  

3.  Określanie lokalizacji zapisu pliku symboli (PDB), dzięki czemu źródła jest indeksowana automatycznie.  

     Jeśli używasz szablonu niestandardowego, upewnij się, że szablon ma działanie do indeksowania źródła. Określ, gdzie chcesz zapisać pliki symboli argument MSBuild będzie później dodać.  

     ![Ustawianie ścieżki symboli w definicji kompilacji TFS 2013](../debugger/media/ffr_tfs2013builddefsymbolspath.png "FFR_TFS2013BuildDefSymbolsPath")  

     Aby uzyskać więcej informacji o symbolach, zobacz [publikowania danych symbol](http://msdn.microsoft.com/Library/bd6977ca-e30a-491a-a153-671d81222ce6).  

4.  Dodaj ten argument MSBuild, aby objąć lokalizacje TFS i symbole kompilacji pliku manifestu:  

     **/p:IncludeServerNameInBuildInfo = true**  
  
     Każdy, kto może uzyskiwać dostęp do serwera sieci web jest widoczny te lokalizacje w manifeście kompilacji. Upewnij się, że serwer źródłowy jest zabezpieczone.

5.  Jeśli używasz szablonu niestandardowego, Dodaj ten argument MSBuild Określanie lokalizacji zapisu pliku symboli:  
  
     **/p:BuildSymbolStorePath =**\<*ścieżka do symboli*>  
  
     ![Zawierają informacje o serwerze kompilacji w kompilacji def TFS 2013](../debugger/media/ffr_tfs2013builddefincludeserverinfo.png "FFR_TFS2013BuildDefIncludeServerInfo")  
  
     Dodaj też te linie do pliku projektu sieci Web (.csproj, .vbproj):  
  
    ```  
    <!-- Import the targets file. Change the folder location as necessary. -->  
       <Import Project=""$(MSBuildExtensionsPath)\Microsoft\VisualStudio\v$(VisualStudioVersion)\BuildInfo\Microsoft.VisualStudio.ReleaseManagement.BuildInfo.targets" />  
  
    ```  

     Każdy, kto może uzyskiwać dostęp do serwera sieci web jest widoczny te lokalizacje w manifeście kompilacji. Upewnij się, że serwer źródłowy jest zabezpieczone.  

6.  Uruchom nową kompilację.  

 **Krok 2:** [krok 2: wersji aplikacji](#DeployRelease)  

####  <a name="TFS2012_2010"></a>Team Foundation Server 2012 lub 2010  
 Wykonaj następujące kroki, aby automatycznie utworzyć manifestu kompilacji (plik BuildInfo.config) dla projektu i umieścić plik w folderze wyjściowym projektu. Plik jest wyświetlany jako "*ProjectName*. BuildInfo.config"w folderze wyjściowym, ale jest zmieniona"BuildInfo.config"w folderze wdrożenia po opublikowaniu aplikacji.  

1.  Zainstalowanie programu Visual Studio 2013 (dowolna wersja) na serwerze kompilacji Team Foundation.  

2.  W definicji kompilacji określ miejsce zapisania symboli tak, aby Twoje źródło było indeksowane automatycznie.  

     Jeśli używasz szablonu niestandardowego, upewnij się, że szablon ma działanie do indeksowania źródła.  

3.  Dodaj następujące argumenty MSBuild do swojej definicji kompilacji:  

    -   **/p:VisualStudioVersion = 12.0**  

    -   **/p:MSBuildAssemblyVersion = 12.0**  

    -   **/TV:12.0**  

    -   **/p:IncludeServerNameInBuildInfo = true**  

    -   **/p:BuildSymbolStorePath =**\<*ścieżka do symboli*>  

4.  Uruchom nową kompilację.  

 **Krok 2:** [krok 2: wersji aplikacji](#DeployRelease)  

###  <a name="ManualBuild"></a>Tworzenie manifestu kompilacji dla kompilacji ręcznej przy użyciu programu Visual Studio  
 Wykonaj następujące kroki, aby automatycznie utworzyć manifestu kompilacji (plik BuildInfo.config) dla projektu i umieścić plik w folderze wyjściowym projektu. Plik jest wyświetlany jako "*ProjectName*. BuildInfo.config"w folderze wyjściowym, ale jest zmieniona"BuildInfo.config"w folderze wdrożenia po opublikowaniu aplikacji.  

1.  W **Eksploratora rozwiązań**, zwolnienie projektu sieci web.  

2.  Otwórz plik projektu (.csproj, .vbproj). Dodaj następujące wiersze:  

    ```xml  
    <!-- **************************************************** -->  
    <!-- Build info -->  
    <PropertyGroup>  
       <!-- Generate the BuildInfo.config file -->  
       <GenerateBuildInfoConfigFile>True</GenerateBuildInfoConfigFile>  
       <!-- Include server name in build info -->   
       <IncludeServerNameInBuildInfo>True</IncludeServerNameInBuildInfo>   
       <!-- Include the symbols path so Visual Studio can find the matching deployed code when you start debugging. -->  
       <BuildSymbolStorePath><path to symbols></BuildSymbolStorePath>  
    </PropertyGroup>  
    <!-- **************************************************** -->  
    ```  

3.  Zaewidencjonuj zaktualizowany plik projektu.  

4.  Uruchom nową kompilację.  

 **Krok 2:** [krok 2: wersji aplikacji](#DeployRelease)  

###  <a name="MSBuild"></a>Tworzenie manifestu kompilacji dla kompilacji ręcznej przy użyciu narzędzia MSBuild.exe  
 Dodaj te argumenty kompilacji podczas uruchamiania kompilacji:  

 **/p:GenerateBuildInfoConfigFile = true**  

 **/p:IncludeServerNameInBuildInfo = true**  

 **/p:BuildSymbolStorePath =**\<*ścieżka do symboli*>  

##  <a name="DeployRelease"></a>Krok 2: Wersji aplikacji  
 Jeśli używasz [pakietu Web.Deploy](http://msdn.microsoft.com/library/dd394698.aspx) utworzony przez procesu kompilacji, aby wdrożyć aplikację, manifest kompilacji zostanie automatycznie zmieniona na "*ProjectName*. BuildInfo.config"do"BuildInfo.config"i jest umieszczany w tym samym folderze z pliku Web.config aplikacji na serwerze sieci web.  

 Jeśli używasz innych metod do wdrożenia aplikacji, upewnij się, że manifest kompilacji jest zmieniana ze "*ProjectName*. BuildInfo.config"do"BuildInfo.config"i jest umieszczany w tym samym folderze z pliku Web.config aplikacji na serwerze sieci web.  

## <a name="step-3-monitor-your-app"></a>Krok 3: Monitorowanie aplikacji  
 Konfigurowanie monitorowania wydajności aplikacji na serwerze sieci web tak, aby monitorować aplikację do problemów, rejestrowania zdarzeń diagnostycznych i zapisać zdarzeń do pliku dziennika funkcji IntelliTrace. Zobacz [monitorować Twojej wersji dla problemów z wdrażaniem](../debugger/using-the-intellitrace-stand-alone-collector.md).  

##  <a name="InvestigateEvents"></a>Krok 4: Znajdziesz problem  
 Visual Studio Enterprise należy na komputerze dewelopera lub innym komputerze, aby przejrzeć zarejestrowane zdarzenia i debugowanie kodu przy użyciu funkcji IntelliTrace. Można również użyć narzędzi, takich jak CodeLens, mapy debugera i mapy kodu, aby zdiagnozować problem.  

### <a name="open-the-intellitrace-log-and-matching-solution"></a>Otwieranie dziennika IntelliTrace i pasującego rozwiązania  

1.  Otwórz dziennika IntelliTrace (.iTrace plik) z programu Visual Studio Enterprise. Lub po prostu kliknij dwukrotnie plik, jeśli masz program Visual Studio Enterprise na tym samym komputerze.  

2.  Wybierz **Otwórz rozwiązanie** z programu Visual Studio automatycznie otworzyć pasującego rozwiązania lub projektu, jeśli projekt nie został skompilowany jako część rozwiązania. [Pytanie: dziennika funkcji IntelliTrace brakuje informacji o Moje wdrożonej aplikacji. Dlaczego to możliwe? Co należy zrobić?](#InvalidConfigFile)  

     Visual Studio automatycznie półki wszystkie oczekujące zmiany, po otwarciu pasującego rozwiązania lub projektu. Aby uzyskać więcej informacji na temat tego zestawu na półce, Szukaj w **dane wyjściowe** okna lub **Team Explorer**.  

     Przed wprowadzeniem jakichkolwiek zmian, upewnij się, że masz prawidłowego źródła. Jeśli używasz rozgałęzianie, może wystąpić sytuacja, w gałęzi innej niż gdzie Visual Studio znajduje dopasowywania źródła, takich jak gałąź wersji.  

     ![Otwórz rozwiązanie z dziennika IntelliTrace](../debugger/media/ffr_itsummarypageopensolution.png "FFR_ITSummaryPageOpenSolution")  

     Jeśli masz istniejący obszar roboczy zamapowane do tego rozwiązania lub projektu programu Visual Studio wybiera ten obszar roboczy, aby umieścić źródła znalezionym.  

     ![Otwórz z kontroli źródła do obszaru roboczego zamapowanych](../debugger/media/ffr_openprojectfromsourcecontrol_mapped.png "FFR_OpenProjectFromSourceControl_Mapped")  

     W przeciwnym wypadku wybierz inny lub utwórz nowy obszar roboczy. Program Visual Studio będzie mapować całą gałąź do tego obszaru roboczego.  

     ![& Otwórz z kontroli źródła 45; Utwórz nowy obszar roboczy](../debugger/media/ffr_openprojectfromsourcecontrol_createnewworkspace.png "FFR_OpenProjectFromSourceControl_CreateNewWorkspace")  

     Aby utworzyć obszaru roboczego z określonego mapowania lub nazwy, która nie jest nazwą komputera, wybierz **Zarządzaj**.  

     [Pytanie: Dlaczego Visual Studio mówi się, że nie kwalifikuje się Moje wybranego obszaru roboczego?](#IneligibleWorkspace)  

     [Pytanie: Dlaczego nie można kontynuować do momentu I wybierz kolekcję zespołu lub innej kolekcji?](#ChooseTeamProject)  

### <a name="diagnose-a-performance-problem"></a>Diagnozowanie problemów z wydajnością  

1.  W obszarze **naruszeń wydajności**, przejrzyj zdarzenia zarejestrowane wydajności, łączny czas wykonywania i innych informacji o zdarzeniu. Następnie zagłęb się w metody, które zostały wywołane podczas zdarzenia dotyczącego wydajności.  

     ![Wyświetl szczegóły zdarzeń dotyczących wydajności](../debugger/media/ffr_itsummarypageperformance.png "FFR_ITSummaryPagePerformance")  

     Możesz także po prostu dwukrotnie kliknąć zdarzenie.  

2.  Na stronie zdarzeń przejrzyj czasy wykonania dla tych wywołań. Odszukaj spowalniające wywołanie w drzewie wykonywania.  

     Najwolniejsze wywołania pojawiają się we własnej sekcji w przypadku wielu wywołań, zagnieżdżonych lub innych.  

     Rozwiń to wywołanie, aby przejrzeć wszelkie zagnieżdżone wywołania i wartości, które zostały zarejestrowane w danym momencie. Następnie rozpocznij debugowanie z tego wywołania.  

     ![Rozpocznij debugowanie z wywołania metody](../debugger/media/ffr_itsummarypageperformancemethodscalled.png "FFR_ITSummaryPagePerformanceMethodsCalled")  

     Można też po prostu dwukrotnie kliknąć wywołanie.  

     Jeśli metoda ta jest w kodzie aplikacji, program Visual Studio przechodzi do tej metody.  

     ![Przejdź do kodu aplikacji ze zdarzenia wydajności](../debugger/media/ffr_itsummarypageperformancegotocode.png "FFR_ITSummaryPagePerformanceGoToCode")  

     Teraz można przeglądać inne zarejestrowane wartości stosu wywołań kroków opisanych w kodzie, lub użyj **IntelliTrace** okna [przechodzenie wstecz lub do przodu "w czasie" między innymi metodami](../debugger/intellitrace.md) które zostały wywołane podczas To zdarzenie wydajności. [Co to jest tych pozostałych zdarzeń i informacji w dzienniku funkcji IntelliTrace? ](../debugger/using-saved-intellitrace-data.md) [Co można zrobić w tym miejscu?](#WhatElse) [Więcej informacji na temat zdarzeń wydajności?](http://blogs.msdn.com/b/visualstudioalm/archive/2013/09/20/performance-details-in-intellitrace.aspx)  

### <a name="diagnose-an-exception"></a>Diagnozowanie wyjątku  

1.  W obszarze **wyjątku**, przejrzeć zdarzenia zarejestrowane wyjątków, ich typów, wiadomości, i gdy wystąpiły wyjątki. Aby poznać więcej szczegółów związanych z kodem, rozpocznij debugowanie od ostatniego zdarzenia w grupie wyjątków.  

     ![Rozpocznij debugowanie z zdarzenie wyjątku](../debugger/media/ffr_itsummarypageexception.png "FFR_ITSummaryPageException")  

     Możesz także po prostu dwukrotnie kliknąć zdarzenie.  

     Jeśli wystąpił wyjątek w kodzie aplikacji, program Visual Studio przechodzi do tego miejsca.  

     ![Przejdź do kodu aplikacji z zdarzenie wyjątku](../debugger/media/ffr_itsummarypageexceptiongotocode.png "FFR_ITSummaryPageExceptionGoToCode")  

     Teraz można przejrzeć inne zarejestrowane wartości, stos wywołań, lub użyj **IntelliTrace** okna [przechodzenie wstecz lub do przodu "w czasie" między inne zarejestrowane zdarzenia](../debugger/intellitrace.md), kodu powiązanego i rejestrowane w wartości te punkty w czasie. [Co to jest tych pozostałych zdarzeń i informacji w dzienniku funkcji IntelliTrace?](../debugger/using-saved-intellitrace-data.md)  

###  <a name="WhatElse"></a>Co można zrobić, w tym miejscu?  

-   [Uzyskaj więcej informacji o tym kodzie](../ide/find-code-changes-and-other-history-with-codelens.md). Można znaleźć odniesienia do tego kodu, historii zmian, powiązanych usterek, elementy robocze, przeglądy kodu lub testów jednostkowych, - all bez opuszczania edytora - użyj wskaźników CodeLens w edytorze.  

     ![CodeLens &#45; Wyświetlanie odwołania do tego kodu](../debugger/media/ffr_itsummarypageperformancecodelensreferences.png "FFR_ITSummaryPagePerformanceCodeLensReferences")  

     ![CodeLens &#45; Wyświetl historię zmian przez ten kod](../debugger/media/ffr_itsummarypageperformancecodelensauthors.png "FFR_ITSummaryPagePerformanceCodeLensAuthors")  

-   [Mapowanie Twoje miejsce w kodzie podczas debugowania kodu.](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md) Aby wizualnie śledzić metody, które zostały wywołane podczas sesji debugowania, mapuj stos wywołań.  

     ![Mapowanie stosu wywołań podczas debugowania](../debugger/media/ffr_itsummarypageperformancedebuggermap.png "FFR_ITSummaryPagePerformanceDebuggerMap")  

###  <a name="FAQ"></a>FUNKCJA PYTANIA I ODPOWIEDZI  

####  <a name="WhyInclude"></a>Pytanie: Dlaczego zawierają informacje o projekcie, kontroli źródła, kompilacji i symbole z mojej wersji?  
 Visual Studio wykorzystuje te informacje można znaleźć rozwiązania zgodnego i źródła dla wersji, który próbujesz debugować. Po otwarciu dziennika funkcji IntelliTrace i wybierz zdarzenie, aby rozpocząć debugowanie, Visual Studio będzie korzystać symboli można znaleźć i wyświetlić kod którym wystąpiło zdarzenie. Można przyjrzeć się wartości, które zostały zarejestrowane i Przenieś przodu lub do tyłu przez wykonanie kodu.  

 Jeśli używasz programu TFS, a tych informacji nie jest w manifeście kompilacji (plik BuildInfo.config), programu Visual Studio wyszukuje zgodne źródło i symbole z aktualnie połączonych TFS. Jeśli program Visual Studio nie może znaleźć poprawne TFS lub zgodne źródło, zostanie wyświetlony monit o wybranie innego TFS.  

####  <a name="InvalidConfigFile"></a>Pytanie: dziennika funkcji IntelliTrace brakuje informacji o Moje wdrożonej aplikacji. Dlaczego to możliwe? Co mam zrobić?  
 Taka sytuacja może wystąpić podczas wdrażania na komputerze projektowym lub nie masz połączenia do programu TFS podczas wdrażania.  

1.  Przejdź do folderu wdrożenia projektu.  

2.  Znajdź i Otwórz plik manifestu kompilacji (plik BuildInfo.config).  

3.  Upewnij się, że plik zawiera wymagane informacje:  

-   **ProjectName**  

     Nazwa projektu programu Visual Studio. Na przykład:  

    ```  
    <ProjectName>FabrikamFiber.Extranet.Web</ProjectName>  
    ```  

-   **SourceControl**  

-   Informacje o systemie kontroli źródła i te wymaganych właściwości:  

    -   **TFS**  

        -   **ProjectCollectionUri**: identyfikator URI serwera Team Foundation Server i project kolekcji  

        -   **ProjectItemSpec**: ścieżka do pliku projektu aplikacji (pliku .csproj lub .vbproj)  

        -   **ProjectVersionSpec**: wersji dla projektu  

         Na przykład:  

        ```  
        <SourceControl type="TFS">  
           <TfsSourceControl>  
              <ProjectCollectionUri>http://fabrikamfiber:8080/tfs/FabrikamFiber</ProjectCollectionUri>  
              <ProjectItemSpec>$/WorkInProgress/FabrikamFiber/FabrikamFiber.CallCenter/FabrikamFiber.Web/FabrikamFiber.Web.csproj</ProjectItemSpec>  
              <ProjectVersionSpec>LFabrikamFiber_BuildAndPublish_20130813@$/WorkInProgress</ProjectVersionSpec>  
           </TfsSourceControl>  
        </SourceControl>  
        ```  

    -   **Git**  

        -   **GitSourceControl**: lokalizacja **GitSourceControl** schematu  

        -   **RepositoryUrl**: identyfikator URI dla serwera Team Foundation Server, kolekcji projektów i repozytorium Git  

        -   **ProjectPath**: ścieżka do pliku projektu aplikacji (pliku .csproj lub .vbproj)  

        -   **CommitId**: identyfikator do Twojego zatwierdzenia  

         Na przykład:  

        ```  
        <SourceControl type="Git">   
           <GitSourceControl xmlns="http://schemas.microsoft.com/visualstudio/deploymentevent_git/2013/09">  
              <RepositoryUrl>http://gittf:8080/tfs/defaultcollection/_git/FabrikamFiber</RepositoryUrl>  
              <ProjectPath>/FabrikamFiber.CallCenter/FabrikamFiber.Web/FabrikamFiber.Web.csproj</ProjectPath>  
              <CommitId>50662c96502dddaae5cd5ced962d9f14ec5bc64d</CommitId>  
           </GitSourceControl>  
        </SourceControl>  
        ```  

-   **Kompilacja**  

     Informacje o systemie kompilacji albo `"TeamBuild"` lub `"MSBuild"`, a te wymaganych właściwości:  

    -   **BuildLabel** (dla TeamBuild): Nazwa kompilacji i numeru. Etykieta jest również używane jako nazwa zdarzenia wdrożenia. Aby uzyskać więcej informacji na temat numerów kompilacji, zobacz [Użyj kompilacji z liczb, aby zapewnić łatwy do rozpoznania nazwy do ukończonych kompilacji](http://msdn.microsoft.com/Library/1f302e9d-4b0a-40b5-8009-b69ca6f988c3).  

    -   **SymbolPath** (zalecane): Lista identyfikatorów URI dla lokalizacji symboli (plik PDB) rozdzielane średnikami. Te identyfikatory URI mogą być adresy URL lub UNC. Ułatwia dla programu Visual Studio można znaleźć zgodnego symboli, które zapewniają pomoc podczas debugowania.  

    -   **BuildReportUrl** (dla TeamBuild): Lokalizacja raportu kompilacji w programie TFS  

    -   **Identyfikatora BuildId** (dla TeamBuild): identyfikator URI dla kompilacji szczegółowych informacji w programie TFS. Ten identyfikator URI jest również używane jako identyfikator zdarzenia wdrożenia. To musi id musi być unikatowa, jeśli nie używasz TeamBuild.  

    -   **BuiltSolution**: ścieżka do pliku rozwiązania tego Visual Studio będzie korzystać można znaleźć i otworzyć rozwiązanie zgodne. To jest zawartość **SolutionPath** właściwości programu MsBuild.  

     Na przykład:  

    -   **TFS**  

        ```  
        <Build type="TeamBuild">  
           <MsBuild>  
              <BuildLabel kind="label">FabrikamFiber_BuildAndPublish_20130813.1</BuildLabel>  
              <SymbolPath>\\fabrikamfiber\FabrikamFiber.CallCenter\Symbols</SymbolPath>  
              <BuildReportUrl kind="informative, url" url="http://fabrikamfiber:8080/tfs/FabrikamFiber/_releasePipeline/FindRelease?buildUri=fabrikamfiber%3a%2f%2f%2fBuild%2fBuild%2f448">Build Report Url</BuildReportUrl>  
              <BuildId kind="id">1c4444d2-518d-4673-a590-dce2773c7744,fabrikamfiber:///Build/Build/448</BuildId>  
              <BuiltSolution>$/WorkInProgress/FabrikamFiber/FabrikamFiber.CallCenter/FabrikamFiber.CallCenter.sln</BuiltSolution>  
           </MsBuild>  
        </Build>  
        ```  

    -   **Git**  

        ```  
        <Build type="MSBuild">   
           <MSBuild>  
              <SymbolPath>\\gittf\FabrikamFiber.CallCenter\Symbols</SymbolPath>  
              <BuiltSolution>/FabrikamFiber.CallCenter/FabrikamFiber.CallCenter.sln</BuiltSolution>  
           </MSBuild>  
        </Build>  
        ```  

####  <a name="IneligibleWorkspace"></a>Pytanie: Dlaczego Visual Studio mówi się, że nie kwalifikuje się Moje wybranego obszaru roboczego?  
 **Odpowiedź:** wybranego obszaru roboczego nie ma żadnych mapowań między folderu kontroli źródła i folder lokalny. Aby utworzyć mapowanie dla tego obszaru roboczego, wybierz **Zarządzaj**. W przeciwnym wypadku wybierz już zmapowany obszar roboczy lub utwórz nowy.  

 ![Otwórz z kontroli źródła z nie zamapowanego obszarem roboczym](../debugger/media/ffr_openprojectfromsourcecontrol_notmapped.png "FFR_OpenProjectFromSourceControl_NotMapped")  

####  <a name="ChooseTeamProject"></a>Pytanie: Dlaczego nie można kontynuować do momentu I wybierz kolekcję zespołu lub innej kolekcji?  
 **Odpowiedź:** taka sytuacja może wystąpić dla żadnej z następujących powodów:  

-   Program Visual Studio nie jest połączony z TFS.  

     ![& Otwórz z kontroli źródła 45; niepodłączone](../debugger/media/ffr_openprojectfromsourcecontrol_notconnected.png "FFR_OpenProjectFromSourceControl_NotConnected")  

-   Program Visual Studio nie znalazł rozwiązania lub projektu w obecnej kolekcji zespołu.  

     Podczas kompilacji pliku manifestu (\<*ProjectName*>. BuildInfo.config) nie określa, gdzie Visual Studio można znaleźć zgodnego źródła, Visual Studio będzie korzystać z aktualnie połączonych TFS można znaleźć zgodnego rozwiązanie lub projekt. Jeśli Twoja bieżąca kolekcja zespołu nie ma pasującego źródła, program Visual Studio monituje o połączenie z inną kolekcją zespołu.  

-   Program Visual Studio nie znaleźć rozwiązania lub projektu w kolekcji określone przez plik manifestu kompilacji (\<*ProjectName*>. BuildInfo.config).  

     Określony TFS może już nie mieć pasującego źródła lub może już nawet nie istnieć, być może dlatego, że nastąpiła migracja do nowego TFS. Jeśli określone wystąpienie programu TFS nie istnieje, w programie Visual Studio może upłynąć limit czasu po około minucie, a następnie pojawi się monit o podłączenie do innej kolekcji. Aby kontynuować, należy połączyć się z właściwym serwerem TFS.  

     ![& Otwórz z kontroli źródła 45; Migracja](../debugger/media/ffr_openprojectfromsourcecontrol_migrated.png "FFR_OpenProjectFromSourceControl_Migrated")  

####  <a name="WhatWorkspace"></a>Pytanie: co to jest obszar roboczy?  
 **A:** Twojego [obszaru roboczego jest przechowywana kopia źródła](http://msdn.microsoft.com/Library/1d7f6ed8-ec7c-48f8-86da-9aea55a90d5a) , mogą tworzyć i przetestować go oddzielnie przed wyboru w pracy. Jeśli nie masz jeszcze obszaru roboczego, który jest specjalnie zmapowany na znalezione rozwiązania lub projekt, program Visual Studio wyświetli monit, aby wybrać dostępny obszar roboczy lub utworzyć nowy obszar roboczy z nazwą komputera jako domyślną nazwą obszaru roboczego.  

####  <a name="UntrustedSymbols"></a>Pytanie: Dlaczego uzyskać ten komunikat o niezaufanych symbole?  
 ![Debugowanie przy użyciu ścieżki symboli niezaufanych? ] (../debugger/media/ffr_ituntrustedsymbolpaths.png "FFR_ITUntrustedSymbolPaths")  

 **Odpowiedź:** ten komunikat jest wyświetlany, gdy ścieżki symboli w pliku manifestu kompilacji (\<*ProjectName*>. BuildInfo.config) nie jest uwzględniony na liście zaufanych symbol ścieżek. Możesz dodać ścieżkę do listy ścieżek symboli w opcjach debugera.
