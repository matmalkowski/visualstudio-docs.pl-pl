---
title: "Za pomocą autonomicznego modułu zbierającego IntelliTrace | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.historicaldebug.collectdataoutsideVS
helpviewer_keywords: IntelliTrace, debugging applications in production
ms.assetid: 1bde9807-8219-4a2a-a440-ac5ee5178159
caps.latest.revision: "105"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 04b627e1f3188a4e7e938f9446251b5be80b87e6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="using-the-intellitrace-stand-alone-collector"></a>Korzystanie z autonomicznego modułu zbierającego funkcji IntelliTrace
**Autonomiczny moduł zbierający IntelliTrace** pozwala na zbieranie danych diagnostycznych funkcji IntelliTrace dla aplikacji na serwerach produkcyjnych lub w innych środowiskach bez instalowania programu Visual Studio na komputerze docelowym i bez zmiany docelowe środowiska systemu. Autonomiczny moduł zbierający IntelliTrace działa w przypadku aplikacji sieci web programu SharePoint, WPF i formularze systemu Windows. Po zakończeniu zbierania danych po prostu usuń moduł zbierający, aby go odinstalować.  
  
 Obejrzyj IntelliTrace w działaniu: [zbierania i analizowania danych funkcji IntelliTrace w środowisku produkcyjnym w celu debugowania (wideo z witryny Channel 9)](http://go.microsoft.com/fwlink/?LinkID=251851)  
  
> [!NOTE]
>  Może również zbierać te same dane funkcji IntelliTrace dla sieci web i aplikacji SharePoint uruchomionych na komputerach zdalnych przy użyciu **programu Microsoft Monitoring Agent** w **śledzenia** tryb.  
>   
>  Zdarzenia związane z wydajnością w danych funkcji IntelliTrace można zbierać, uruchamiając agenta **Monitor** tryb. **Monitor** trybu ma mniej niż negatywny wpływ na wydajność **śledzenia** tryb lub **autonomiczny moduł zbierający IntelliTrace**. Po zainstalowaniu programu Microsoft Monitoring Agent polecenia alter środowiska systemu docelowego. Zobacz [przy użyciu programu Microsoft Monitoring Agent](../debugger/using-the-microsoft-monitoring-agent.md).  
  
 **Wymagania**  
  
-   .NET framework 3.5, 4 lub 4.5  
  
-   Visual Studio Enterprise (ale nie Professional lub Community Edition) na komputerze dewelopera lub inny komputer można otworzyć .iTrace, pliki  
  
    > [!NOTE]
    >  Upewnij się zapisać symbolu (.pdb), pliki. Aby debugować przy użyciu funkcji IntelliTrace i wykonywać krokowo kodu, musi mieć pasujące pliki źródłowe i symboli plików. Zobacz [diagnozowanie problemów po wdrożeniu](../debugger/diagnose-problems-after-deployment.md).  
  
 **FAQ**  
  
-   [Jakie aplikacje działają z modułu zbierającego?](#WhatApps)  
  
-   [Jak rozpocząć pracę?](#GetStarted)  
  
-   [Jak uzyskać większość danych bez spowolnieniem Moja aplikacja](#Minimizing)  
  
-   [Else gdzie można uzyskać danych funkcji IntelliTrace?](#WhereElse)  
  
##  <a name="WhatApps"></a>Jakie aplikacje działają z modułu zbierającego?  
  
-   Aplikacje sieci Web platformy ASP.NET hostowane na Internet Information Services (IIS) w wersji 7.0, 7.5 i 8.0  
  
-   Aplikacje programu SharePoint 2010 oraz SharePoint 2013  
  
-   Windows Presentation Foundation (WPF) i Windows formularzy aplikacji.  
  
##  <a name="GetStarted"></a>Jak rozpocząć pracę?  
  
1.  [Instalowanie modułu zbierającego](#BKMK_Install_the_IntelliTrace_Stand_Alone_Collector)  
  
2.  [Ustawianie uprawnień do katalogu modułu zbierającego](#ConfigurePermissionsRunningCollector)  
  
3.  [Zainstaluj polecenia cmdlet programu IntelliTrace PowerShell do zbierania danych dla aplikacji sieci Web lub aplikacji SharePoint](#BKMK_Set_up_the_IntelliTrace_PowerShell_commandlets)  
  
4.  [Ustawianie uprawnień do katalogu pliku .iTrace](#BKMK_Create_and_Configure_a_Log_File_Directory)  
  
5.  [Zbieranie danych z aplikacji sieci Web lub aplikacji programu SharePoint](#BKMK_Collect_Data_from_IIS_Application_Pools)  
  
     —lub—  
  
     [Zbieranie danych z zarządzanej aplikacji](#BKMK_Collect_Data_from_Executables)  
  
6.  [Otwórz plik .iTrace w Visual Studio Enterprise](#BKMK_View_IntelliTrace_Log_Files)  
  
##  <a name="BKMK_Install_the_IntelliTrace_Stand_Alone_Collector"></a>Instalowanie modułu zbierającego  
  
1.  Na serwerze aplikacji, Utwórz katalog modułu zbierającego, na przykład: **C:\IntelliTraceCollector**  
  
2.  Pobierz moduł zbierający z Microsoft Download Center lub z folderu instalacyjnego programu Visual Studio 2013 Update 3. [Moduł zbierający IntelliTrace dla programu Visual Studio 2013 z aktualizacją 4](https://www.microsoft.com/en-us/download/details.aspx?id=44909)::  
  
    -   **Centrum pobierania Microsoft**:  
  
        1.  Obok pozycji **IntelliTraceCollector.exe**, wybierz **Pobierz**.  
  
        2.  Na przykład zapisać IntelliTraceCollector.exe do katalogu modułu zbierającego: **C:\IntelliTraceCollector**  
  
        3.  Uruchom IntelliTraceCollector.exe. Spowoduje to wyodrębnienie plików IntelliTraceCollection.cab.  
  
         \-lub -  
  
    -   **Folder instalacyjny usługi Visual Studio**:  
  
        1.  Skopiuj IntelliTraceCollection.cab z następującym folderze:  
  
             **.. \Microsoft 12.0\Common7\IDE\CommonExtensions\Microsoft\IntelliTrace\12.0.0 programu visual Studio**  
  
        2.  Na przykład umieścić IntelliTraceCollection.cab w katalogu modułów zbierających: **C:\IntelliTraceCollector**  
  
3.  Rozwiń IntelliTraceCollection.cab:  
  
    1.  Na serwerze aplikacji Otwórz okno wiersza polecenia z uprawnieniami administratora.  
  
    2.  Przejdź do katalogu modułu zbierającego, na przykład: **C:\IntelliTraceCollector**  
  
    3.  Użyj **rozwiń** polecenia, w tym okresie (**.**) na końcu, aby rozwinąć IntelliTraceCollection.cab:  
  
         `expand  /f:* IntelliTraceCollection.cab .`  
  
        > [!NOTE]
        >  Okres (**.**) zachowuje podfolderów, które zawierają planów zlokalizowanych kolekcji.  
  
##  <a name="ConfigurePermissionsRunningCollector"></a>Ustawianie uprawnień do katalogu modułu zbierającego  
  
1.  Na serwerze aplikacji Otwórz okno wiersza polecenia z uprawnieniami administratora.  
  
2.  Użyj okna **icacls** polecenie, aby podać serwer pełne uprawnienia administratora do katalogu modułu zbierającego. Na przykład:  
  
     `icacls "C:\IntelliTraceCollector" /grant "` *\<Domain\AdministratorID >*`":F`  
  
3.  Gromadzenie danych dla aplikacji sieci Web lub aplikacji programu SharePoint:  
  
    1.  Nadaj osoba, która uruchomi poleceń cmdlet programu IntelliTrace PowerShell pełnych uprawnień do katalogu modułu zbierającego.  
  
         Na przykład:  
  
         `icacls "C:\IntelliTraceCollector" /grant "` *\<Domena\identyfikator_użytkownika >*`":F`  
  
    2.  Udzielić tej puli aplikacji dla aplikacji sieci Web lub aplikacji programu SharePoint, Odczyt i wykonywanie uprawnień do katalogu modułu zbierającego.  
  
         Na przykład:  
  
        -   Dla aplikacji sieci Web w **DefaultAppPool** puli aplikacji:  
  
             `icacls "C:\IntelliTraceCollector" /grant "IIS APPPOOL\DefaultAppPool":RX`  
  
        -   Dla aplikacji programu SharePoint w **SharePoint — 80** puli aplikacji:  
  
             `icacls "C:\IntelliTraceCollector" /grant "IIS APPPOOL\SharePoint - 80":RX`  
  
##  <a name="BKMK_Set_up_the_IntelliTrace_PowerShell_commandlets"></a>Zainstaluj polecenia cmdlet programu IntelliTrace PowerShell do zbierania danych dla aplikacji sieci Web lub aplikacji SharePoint  
  
1.  Na serwerze aplikacji upewnij się, czy środowisko PowerShell jest włączona. W większości wersji systemu Windows Server, można dodać tę funkcję w **Menedżera serwera** narzędzie administracyjne.  
  
     ![Dodawanie programu PowerShell przy użyciu Menedżera serwera](../debugger/media/intellitrace_servermanager_addpowershell.png "INTELLITRACE_ServerManager_AddPowerShell")  
  
2.  Zainstaluj polecenia cmdlet programu IntelliTrace PowerShell.  
  
    1.  Otwórz okno poleceń programu PowerShell jako administrator.  
  
        1.  Wybierz **Start**, **wszystkie programy**, **Akcesoria**, **programu Windows PowerShell**.  
  
        2.  Wybierz jedną z następujących czynności:  
  
            -   W 64-bitowych systemach operacyjnych, otwórz menu skrótów **programu Windows PowerShell**. Wybierz **Uruchom jako administrator**.  
  
            -   W 32-bitowych systemach operacyjnych, otwórz menu skrótów **programu Windows PowerShell (x86)**. Wybierz **Uruchom jako administrator**.  
  
    2.  W oknie polecenia programu PowerShell, użyj **Import-Module** polecenie, aby zaimportować **Microsoft.VisualStudio.IntelliTrace.PowerShell.dll**.  
  
         Na przykład:  
  
         `Import-Module "C:\IntelliTraceCollector\Microsoft.VisualStudio.IntelliTrace.PowerShell.dll"`  
  
##  <a name="BKMK_Create_and_Configure_a_Log_File_Directory"></a>Ustawianie uprawnień do katalogu pliku .iTrace  
  
1.  Na serwerze aplikacji, Utwórz katalog pliku .iTrace, na przykład: **C:\IntelliTraceLogFiles**  
  
    > [!NOTE]
    >  -   Aby uniknąć spowolnieniem aplikacji, wybierz lokalizację na lokalnym dysku o dużej szybkości, który nie jest bardzo aktywny.  
    > -   .ITrace, pliki i pliki modułu zbierającego można umieścić w tym samym miejscu. Jednak jeśli masz aplikację sieci Web lub aplikacji programu SharePoint, upewnij się, że jest to miejsce poza katalogiem, która obsługuje aplikację.  
  
    > [!IMPORTANT]
    >  -   Katalog pliku .iTrace należy ograniczyć tylko do tych tożsamości, które należy skontaktować się z modułu zbierającego. Plik .iTrace mogą zawierać poufne informacje, takie jak dane od użytkowników, baz danych, innych lokalizacji źródłowej i parametry połączenia, ponieważ IntelliTrace można rejestrować wszystkie dane przesyłane do metody parametrów lub zwracanych wartości.  
    > -   Upewnij się, że tych osób, które można otworzyć .iTrace, pliki mają uprawnienia do wyświetlania danych poufnych. Udostępnianie plików .iTrace, należy zachować ostrożność. Czy inne osoby muszą mieć dostęp, skopiuj pliki do bezpiecznej lokalizacji udostępnionej.  
  
2.  Dla aplikacji sieci Web lub aplikacji programu SharePoint nadaj jej puli aplikacji pełnych uprawnień do katalogu pliku .iTrace. Można użyć Windows **icacls** polecenie lub użyj Eksploratora Windows (lub Eksploratora plików).  
  
     Na przykład:  
  
    -   Aby skonfigurować uprawnienia z systemu Windows **icacls** polecenia:  
  
        -   Dla aplikacji sieci Web w **DefaultAppPool** puli aplikacji:  
  
             `icacls "C:\IntelliTraceLogFiles" /grant "IIS APPPOOL\DefaultAppPool":F`  
  
        -   Dla aplikacji programu SharePoint w **SharePoint — 80** puli aplikacji:  
  
             `icacls "C:\IntelliTraceLogFiles" /grant "IIS APPPOOL\SharePoint - 80":F`  
  
         —lub—  
  
    -   Aby skonfigurować uprawnienia z Eksploratora Windows (lub Eksploratora plików):  
  
        1.  Otwórz **właściwości** katalogu pliku .iTrace.  
  
        2.  Na **zabezpieczeń** , wybierz pozycję **Edytuj**, **Dodaj**.  
  
        3.  Upewnij się, że **podmiotów zabezpieczeń** pojawia się w **wybierz ten typ obiektu** pole. Jeśli nie ma, wybierz **typy obiektów** ją dodać.  
  
        4.  Upewnij się, że komputera lokalnego jest wyświetlany w **z tej lokalizacji** pole. Jeśli nie ma, wybierz **lokalizacje** je zmienić.  
  
        5.  W **wprowadź nazwy obiektów do wybrania** pozycję Dodaj pulę aplikacji dla aplikacji sieci Web lub aplikacji programu SharePoint.  
  
        6.  Wybierz **Sprawdź nazwy** do rozpoznania nazwy. Wybierz **OK**.  
  
        7.  Upewnij się, że pula aplikacji ma **Pełna kontrola**.  
  
##  <a name="BKMK_Collect_Data_from_IIS_Application_Pools"></a>Zbieranie danych z aplikacji sieci Web lub aplikacji programu SharePoint  
  
1.  Aby rozpocząć, zbieranie danych, Otwórz okno poleceń programu PowerShell jako administrator, a następnie uruchom to polecenie:  
  
     `Start-IntelliTraceCollection``"`  *\<ApplicationPool >* `"`  *\<PathToCollectionPlan >*  *\< FullPathToITraceFileDirectory >*  
  
    > [!IMPORTANT]
    >  Po uruchomieniu tego polecenia, wpisz **Y** potwierdzenie uruchomienia zbierania danych.  
  
     Na przykład, aby zbierać dane z aplikacji programu SharePoint w **SharePoint — 80** puli aplikacji:  
  
     `Start-IntelliTraceCollection "SharePoint - 80" "C:\IntelliTraceCollector\collection_plan.ASP.NET.default.xml" "C:\IntelliTraceLogFiles"`  
  
    |||  
    |-|-|  
    |*Puli aplikacji*|Nazwa puli aplikacji, w którym aplikacja jest uruchomiona|  
    |*PathToCollectionPlan*|Ścieżka do planu kolekcji, plik XML, który konfiguruje ustawienia dla modułu zbierającego.<br /><br /> Można określić plan, który jest dostarczany z modułu zbierającego. Następujących planów roboczych dla aplikacji sieci Web i aplikacji programu SharePoint:<br /><br /> -collection_plan.ASP.NET.default.xml<br />     Zbiera tylko zdarzenia funkcji IntelliTrace i zdarzeń programu SharePoint, w tym wyjątki, wywołania bazy danych i żądań serwera sieci Web.<br />-collection_plan.ASP.NET.trace.xml<br />     Zbiera liczbę wywołań funkcji i wszystkich danych w collection_plan.ASP.NET.default.xml. Ten plan jest dobry szczegółowych analiz, ale może spowolnić więcej niż collection_plan.ASP.NET.default.xml aplikacji.<br /><br /> Aby uniknąć spowolnieniem aplikacji, należy dostosować te plany lub utworzyć własny plan. Bezpieczeństwo należy umieścić wszystkie niestandardowe plany w bezpiecznej lokalizacji jako pliki modułu zbierającego. Zobacz [tworzenie i dostosowywanie planów kolekcji funkcji IntelliTrace](http://go.microsoft.com/fwlink/?LinkId=227871) i [jak uzyskać najbardziej danych bez spowolnieniem mojej aplikacji?](#Minimizing) **Uwaga:** domyślnie maksymalny rozmiar pliku .iTrace wynosi 100 MB. W przypadku pliku .iTrace osiągnie ten limit, moduł zbierający usuwa wpisy najwcześniejszą pliku do zapewnienia miejsca dla nowszej wpisów. Aby zmienić ten limit, należy edytować planu kolekcji `MaximumLogFileSize` atrybutu. <br /><br /> *Gdzie można znaleźć zlokalizowane wersje te plany kolekcji?*<br /><br /> Zlokalizowane planów można znaleźć w podfolderach modułu zbierającego.|  
    |*FullPathToITraceFileDirectory*|Pełna ścieżka do katalogu pliku .iTrace. **Uwaga dotycząca zabezpieczeń:** Podaj pełną ścieżkę, a nie ścieżkę względną.|  
  
     Moduł zbierający dołącza do puli aplikacji i uruchamia zbieranie danych.  
  
     *W tym momencie można otworzyć pliku .iTrace?* Nie, plik jest zablokowany podczas zbierania danych.  
  
2.  Odtwórz problem.  
  
3.  Aby utworzyć migawkę pliku .iTrace, należy użyć następującej składni:  
  
     `Checkpoint-IntelliTraceCollection``"`  *\<ApplicationPool >*`"`  
  
4.  Aby sprawdzić stan kolekcji, należy użyć następującej składni:  
  
     `Get-IntelliTraceCollectionStatus`  
  
5.  Aby zatrzymać zbieranie danych, należy użyć następującej składni:  
  
     `Stop-IntelliTraceCollection``"`  *\<ApplicationPool >*`"`  
  
    > [!IMPORTANT]
    >  Po uruchomieniu tego polecenia, wpisz **Y** aby upewnić się, że chcesz zatrzymać zbieranie danych. W przeciwnym razie moduł zbierający może kontynuować zbieranie danych, iTrace plik pozostanie zablokowane lub plik nie może zawierać żadnych użytecznych danych.  
  
6.  [Otwórz plik .iTrace w Visual Studio Enterprise](#BKMK_View_IntelliTrace_Log_Files)  
  
##  <a name="BKMK_Collect_Data_from_Executables"></a>Zbieranie danych z zarządzanej aplikacji  
  
1.  Aby uruchomić aplikację i zbierać dane w tym samym czasie, należy użyć następującej składni:  
  
     *\<FullPathToIntelliTraceCollectorExecutable >* `\IntelliTraceSC.exe launch /cp:`  *\<PathToCollectionPlan >* `/f:`  *\< FullPathToITraceFileDirectoryAndFileName >*  *\<PathToAppExecutableFileAndFileName >*  
  
     Na przykład, aby zbierać dane z aplikacji o nazwie **moja_aplikacja**:  
  
     `C:IntelliTraceCollectorIntelliTraceSC.exe launch /cp:"C:IntelliTraceCollectorcollection_plan.ASP.NET.default.xml" /f:"C:IntelliTraceLogFilesMyApp.itrace" "C:MyAppMyApp.exe"`  
  
    |||  
    |-|-|  
    |*FullPathToIntelliTraceCollectorExecutable*|Pełna ścieżka do pliku wykonywalnego, zbierający IntelliTraceSC.exe|  
    |*PathToCollectionPlan*|Ścieżka do planu kolekcji, plik XML, który konfiguruje ustawienia dla modułu zbierającego.<br /><br /> Można określić plan, który jest dostarczany z modułu zbierającego. Następujących planów pracę zarządzanych aplikacjach:<br /><br /> -collection_plan.ASP.NET.default.xml<br />     Zbiera tylko zdarzenia IntelliTrace, w tym wyjątki, wywołania bazy danych i żądań serwera sieci Web.<br />-collection_plan.ASP.NET.trace.xml<br />     Zbiera liczbę wywołań funkcji i wszystkich danych w collection_plan.ASP.NET.default.xml. Ten plan jest dobry szczegółowych analiz, ale może spowolnić więcej niż collection_plan.ASP.NET.default.xml aplikacji.<br /><br /> Aby uniknąć spowolnieniem aplikacji, należy dostosować te plany lub utworzyć własny plan. Bezpieczeństwo należy umieścić wszystkie niestandardowe plany w bezpiecznej lokalizacji jako pliki modułu zbierającego. Zobacz [tworzenie i dostosowywanie planów kolekcji funkcji IntelliTrace](http://go.microsoft.com/fwlink/?LinkId=227871) i [jak uzyskać najbardziej danych bez spowolnieniem mojej aplikacji?](#Minimizing) **Uwaga:** domyślnie maksymalny rozmiar pliku .iTrace wynosi 100 MB. W przypadku pliku .iTrace osiągnie ten limit, moduł zbierający usuwa wpisy najwcześniejszą pliku do zapewnienia miejsca dla nowszej wpisów. Aby zmienić ten limit, należy edytować planu kolekcji `MaximumLogFileSize` atrybutu. <br /><br /> *Gdzie można znaleźć zlokalizowane wersje te plany kolekcji?*<br /><br /> Zlokalizowane planów można znaleźć w podfolderach modułu zbierającego.|  
    |*FullPathToITraceFileDirectoryAndFileName*|Pełna ścieżka do katalogu pliku .iTrace i nazwę pliku .iTrace **.itrace** rozszerzenia. **Uwaga dotycząca zabezpieczeń:** Podaj pełną ścieżkę, a nie ścieżkę względną.|  
    |*PathToAppExecutableFileAndFileName*|Ścieżka i nazwa pliku zarządzanych aplikacji|  
  
2.  Zatrzymaj zbieranie danych przez zakończenie działania aplikacji.  
  
3.  [Otwórz plik .iTrace w Visual Studio Enterprise](#BKMK_View_IntelliTrace_Log_Files)  
  
##  <a name="BKMK_View_IntelliTrace_Log_Files"></a>Otwórz plik .iTrace w Visual Studio Enterprise  
  
> [!NOTE]
>  Aby debugować przy użyciu funkcji IntelliTrace i wykonywać krokowo kodu, musi mieć pasujące pliki źródłowe i symboli plików. Zobacz [diagnozowanie problemów po wdrożeniu](../debugger/diagnose-problems-after-deployment.md).  
  
1.  Przenoszenie pliku .iTrace lub skopiuj go do komputera za pomocą programu Visual Studio Enterprise (ale nie Professional lub Community Edition).  
  
2.  Kliknij dwukrotnie plik .iTrace poza programem Visual Studio lub Otwórz plik w programie Visual Studio.  
  
     Visual Studio zawiera **Podsumowanie funkcji IntelliTrace** strony. W większości sekcjach, można przejrzeć zdarzenia lub innych elementów, wybierz element i rozpocząć debugowanie przy użyciu funkcji IntelliTrace w punkcie gdzie i kiedy wystąpiło zdarzenie. Zobacz [Using zapisywane są dane funkcji IntelliTrace](../debugger/using-saved-intellitrace-data.md).  
  
    > [!NOTE]
    >  Aby debugować przy użyciu funkcji IntelliTrace i wykonywać krokowo kodu, musi mieć pasujące pliki źródłowe i symboli plików na komputerze deweloperskim. Zobacz [diagnozowanie problemów po wdrożeniu](../debugger/diagnose-problems-after-deployment.md).  
  
##  <a name="Minimizing"></a>Jak uzyskać większość danych bez spowolnieniem mojej aplikacji?  
 IntelliTrace można zbierać duże ilości danych, więc wpływ na wydajność aplikacji zależy od danych, która zbiera dane funkcji IntelliTrace i rodzaj analizę kodu. Zobacz [optymalizacji zbierania danych funkcji IntelliTrace na serwerach produkcyjnych](http://go.microsoft.com/fwlink/?LinkId=255233).  
  
 Oto niektóre sposoby uzyskania większość danych bez spowolnieniem aplikacji:  
  
-   Uruchom moduł zbierający tylko, jeśli uważasz, że występuje problem lub odtworzyć problem.  
  
     Rozpocznij zbieranie, odtworzenia problemu, a następnie zatrzymać zbieranie. Otwórz plik .iTrace w Visual Studio Enterprise i sprawdź, czy dane. Zobacz [Otwórz plik .iTrace w Visual Studio Enterprise](#BKMK_View_IntelliTrace_Log_Files).  
  
-   Dla aplikacji sieci Web i aplikacji programu SharePoint moduł zbierający rejestruje dane dla każdej aplikacji, które współużytkują określoną pulę aplikacji. Może to spowolnić dowolnej aplikacji, który współużytkuje tej samej puli aplikacji, nawet jeśli moduły do tylko jednej aplikacji można określić tylko w planie kolekcji.  
  
     Aby zapobiec sytuacji, w której moduł zbierający spowolnieniem inne aplikacje, host każdej aplikacji w odrębnej puli aplikacji.  
  
-   Przejrzyj zdarzenia w planie zbierania, dla którego IntelliTrace służy do zbierania danych. Edycji planu kolekcji można wyłączyć zdarzenia, które nie są istotne lub nie Cię interesują.  
  
     Aby wyłączyć zdarzenia, ustaw `enabled` atrybutu dla `<DiagnosticEventSpecification>` elementu `false`:  
  
     `<DiagnosticEventSpecification enabled="false">`  
  
     Jeśli `enabled` atrybut nie istnieje, zdarzenie jest aktywne.  
  
     *Jak to poprawić wydajność?*  
  
    -   Można zmniejszyć czas uruchamiania, wyłączając zdarzenia, które nie są odpowiednie do aplikacji. Na przykład Wyłącz zdarzeń przepływu pracy systemu Windows dla aplikacji, które nie używają przepływu pracy systemu Windows.  
  
    -   Może poprawić wydajność zarówno uruchamiania i środowiska uruchomieniowego, wyłączając zdarzeń rejestru dla aplikacji, które uzyskują dostęp do rejestru, ale nie pokazuj problemy z ustawień rejestru.  
  
-   Przejrzyj modułów w planie zbierania, dla którego IntelliTrace służy do zbierania danych. Edycji planu kolekcji w celu uwzględnienia tylko moduły interesujące:  
  
    1.  Otwórz planu kolekcji. Znajdź `<ModuleList>` elementu.  
  
    2.  W `<ModuleList>`ustaw `isExclusionList` atrybutu `false`.  
  
    3.  Użyj `<Name>` elementu, aby określić poszczególnych modułów z jedną z następujących: Nazwa pliku, wartość ciągu, aby uwzględnić każdy moduł, którego nazwa zawiera ciąg lub klucza publicznego.  
  
     Na przykład aby zbierać dane z właśnie głównego modułu sieci Web aplikacji sieci Web Fiber firmy Fabrikam, należy utworzyć listę podobne do następującego:  
  
    ```xml  
    <ModuleList isExclusionList="false">  
       <Name>FabrikamFiber.Web.dll</Name>  
    </ModuleList>  
  
    ```  
  
     Aby zbierać dane z dowolnego modułu, którego nazwa zawiera "Fabrikam", należy utworzyć listę podobne do następującego:  
  
    ```xml  
    <ModuleList isExclusionList="false">  
       <Name>Fabrikam</Name>  
    </ModuleList>  
  
    ```  
  
     Aby zbierać dane z modułów, określając ich tokeny klucza publicznego, Utwórz listę podobne do następującego:  
  
    ```xml  
    <ModuleList isExclusionList="false">  
       <Name>PublicKeyToken:B77A5C561934E089</Name>  
       <Name>PublicKeyToken:B03F5F7F11D50A3A</Name>  
       <Name>PublicKeyToken:31BF3856AD364E35</Name>  
       <Name>PublicKeyToken:89845DCD8080CC91</Name>  
       <Name>PublicKeyToken:71E9BCE111E9429C</Name>  
    </ModuleList>  
  
    ```  
  
     *Jak to poprawić wydajność?*  
  
     Zmniejsza to ilość informacji o wywołaniu metody i innych danych instrumentacji, służący do zbierania danych funkcji IntelliTrace uruchamia i uruchomieniu aplikacji. Dane te umożliwiają:  
  
    -   Po zebraniu danych wykonywać krokowo kodu.  
  
    -   Sprawdź, czy wartości przekazanych do i zwracany z wywołania funkcji.  
  
     *Dlaczego nie wyklucza zamiast modułów?*  
  
     Domyślnie planów kolekcji wykluczyć modułów ustawiając `isExclusionList` atrybutu `true`. Jednak z wyłączeniem modułów może nadal powodować zbieranie danych z modułów, które nie spełniają kryteria listy, a nie interesujące, takie jak moduły innych firm lub open source.  
  
-   *Znajduje wszystkie dane funkcji IntelliTrace nie zbieraj?*  
  
     Tak, aby zmniejszyć wpływ na wydajność, IntelliTrace ogranicza zbierania danych do wartości typów pierwotnych danych przekazany do i zwrócony z metody i wartości typów pierwotnych danych w polach najwyższego poziomu obiektów przekazany do i zwrócony z metody.  
  
     Na przykład, załóżmy, że masz `AlterEmployee` podpis metody, który akceptuje całkowitą `id` i `Employee` obiektu `oldemployee`:  
  
     `public Employee AlterEmployee(int id, Employee oldemployee)`  
  
     `Employee` Typ ma następujące atrybuty: `Id`, `Name`, i `HomeAddress`. Istnieje relacja skojarzenia między `Employee` i `Address` typu.  
  
     ![Relacja między pracowników i adres](../debugger/media/employeeaddressrelationship.png "EmployeeAddressRelationship")  
  
     Moduł zbierający rejestruje wartości `id`, `Employee.Id`, `Employee.Name` i `Employee` obiektu zwróconego z `AlterEmployee` metody. Jednak moduł zbierający nie zapisuje informacje o `Address` innych obiektów niż czy miał wartość null lub nie. Moduł zbierający również nie zapisuje dane dotyczące zmiennych lokalnych w `AlterEmployee` metody tylko innych metod tych zmiennych lokalnych jako parametry, w którym są rejestrowane jako parametry metody.  
  
##  <a name="WhereElse"></a>Else gdzie można uzyskać danych funkcji IntelliTrace?  
  
-   W programie Visual Studio Enterprise sesję debugowania funkcji IntelliTrace, zobacz temat [funkcji IntelliTrace](../debugger/intellitrace-features.md).  
  
-   Z sesji testowania w programie Microsoft Test Manager, zobacz [porady: zbieranie danych IntelliTrace pomocy debugowania trudnych problemów](http://msdn.microsoft.com/Library/02b6716f-569e-4961-938a-e790a0c74b5c).  
  
## <a name="where-can-i-get-more-information"></a>Gdzie można uzyskać więcej informacji?  
 [Przy użyciu zapisanych danych funkcji IntelliTrace](../debugger/using-saved-intellitrace-data.md)  
  
 [IntelliTrace](../debugger/intellitrace.md)  
  
### <a name="blogs"></a>Blogi  
 [Zdalnie przy użyciu funkcji IntelliTrace autonomiczny moduł zbierający](http://go.microsoft.com/fwlink/?LinkId=262277)  
  
 [Tworzenie i dostosowywanie planów kolekcji funkcji IntelliTrace](http://go.microsoft.com/fwlink/?LinkId=227871)  
  
 [Optymalizacja zbieranie danych IntelliTrace na serwerach produkcyjnych](http://go.microsoft.com/fwlink/?LinkId=255233)  
  
 [Visual Studio ALM i TFS blogu](http://go.microsoft.com/fwlink/?LinkID=201340)  
  
### <a name="forums"></a>Fora  
 [Debuger programu Visual Studio](http://go.microsoft.com/fwlink/?LinkId=262263)  
  
### <a name="videos"></a>Wideo  
 [Channel 9 wideo: zbierania i analizowania danych funkcji IntelliTrace](http://go.microsoft.com/fwlink/?LinkID=251851)
