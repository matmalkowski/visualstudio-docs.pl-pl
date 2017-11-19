---
title: "Uruchom sesję debugowania dla aplikacji platformy uniwersalnej systemu Windows w programie Visual Studio (VB, C#, C++ i XAML) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.IVCAppHostRemoteDebugPageObject.MachineName
- VC.Project.IVCAppHostRemoteDebugPageObject.BreakpointBehavior
- VC.Project.IVCAppHostLocalDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCAppHostTetheredDebugPageObject.DebuggerType
- VC.Project.IVCAppHostLocalDebugPageObject.BreakpointBehavior
- VC.Project.IVCAppHostRemoteDebugPageObject.LaunchApplication
- VC.Project.IVCAppHostRemoteDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCAppHostLocalDebugPageObject.DebuggerType
- VC.Project.IVCAppHostSimulatorDebugPageObject.DebuggerType
- ImmersiveProjects.Properties.Debug
- VC.Project.IVCAppHostTetheredDebugPageObject.LaunchApplication
- VC.Project.IVCAppHostSimulatorDebugPageObject.LaunchApplication
- VC.Project.IVCAppHostSimulatorDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCAppHostLocalDebugPageObject.LaunchApplication
- VC.Project.IVCAppHostLocalDebugPageObject.AllowLocalNetworkLoopback
- AppPackage.Properties.Debug
- VC.Project.IVCAppHostRemoteDebugPageObject.Authentication
- VC.Project.IVCAppHostRemoteDebugPageObject.DebuggerType
- VC.Project.IVCAppHostSimulatorDebugPageObject.BreakpointBehavior
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 66ec0e79-8261-4c19-a618-3fd1b3f71bbd
caps.latest.revision: "20"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c5c7cf9a5329e1b77d8669568434357deb2dd131
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/11/2017
---
# <a name="start-a-debugging-session-for-a-uwp-app-in-visual-studio-vb-c-c-and-xaml"></a>Uruchom sesję debugowania dla aplikacji platformy uniwersalnej systemu Windows w programie Visual Studio (VB, C#, C++ i XAML)
![Ma zastosowanie do systemu Windows i Windows Phone](../debugger/media/windows_and_phone_content.png "windows_and_phone_content")  
  
 W tym temacie opisano, jak uruchomić sesję debugowania dla aplikacji platformy uniwersalnej systemu Windows w języku XAML i Visual C++, Visual C# lub Visual Basic. Debugowanie aplikacji obejmuje zarówno Konfigurowanie sesji debugowania i wybierając sposób, aby uruchomić aplikację.  
  
> [!NOTE]
>  Dla aplikacji napisanych w JavaScript i HTML zobacz [uruchomić sesję debugowania (JavaScript)](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md).  
  
##  <a name="BKMK_In_this_topic"></a>W tym temacie  
 [Łatwo można rozpocząć debugowania](#BKMK_The_easy_way_to_start_debugging)  
  
 [Konfigurowanie sesji debugowania](#BKMK_Configure_the_debugging_session)  
  
-   [Otwórz stronę właściwości debugowania dla projektu](#BKMK_Open_the_debugging_property_page_for_the_project)  
  
-   [Opcje konfiguracji kompilacji](#BKMK_Choose_the_build_configuration_options)  
  
-   [Wybierz cel wdrożenia](#BKMK_Choose_the_deployment_target)  
  
-   [Wybierz debuger do użycia](#BKMK_Choose_the_debugger_to_use)  
  
-   [(Opcjonalnie) Opóźnienie rozpoczynania sesji debugowania](#BKMK__Optional__Delay_starting_the_debug_session)  
  
-   [(Opcjonalnie) Wyłącz sprzężenia zwrotne sieci](#BKMK__Optional__Disable_network_loopbacks)  
  
-   [(Opcjonalnie) Zainstaluj ponownie aplikację po rozpoczęciu debugowania](#BKMK__Optional__Reinstall_the_app_when_you_start_debugging)  
  
-   [(Opcjonalnie) Wyłączyć wymaganie uwierzytelniania można uruchomić zdalnego debugera](#BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger)  
  
 [Uruchom sesję debugowania](#BKMK_Start_the_debugging_session)  
  
-   [Rozpocznij debugowanie (F5)](#BKMK_Start_debugging__F5_)  
  
-   [Rozpocznij debugowanie (F5), ale opóźnienie rozpoczęcia aplikacji](#BKMK_Start_debugging__F5__but_delay_the_app_start)  
  
-   [Uruchom zainstalowaną aplikację w debugerze](#BKMK_Start_an_installed_app_in_the_debugger)  
  
-   [Dołącz debuger do uruchomionej aplikacji](#BKMK_Attach_the_debugger_to_a_running_app_)  
  
    -   [Ustaw aplikację do uruchamiania w trybie debugowania](#BKMK_Set_the_app_to_run_in_debug_mode)  
  
    -   [Dołącz debuger](#BKMK_Attach_the_debugger)  
  
##  <a name="BKMK_The_easy_way_to_start_debugging"></a>Łatwo można rozpocząć debugowania  
  
1.  Otwórz rozwiązanie aplikacji w programie Visual Studio.  
  
2.  Wybierz F5.  
  
 Visual Studio kompiluje i uruchamia aplikację w debugerze. Wykonanie kontynuowany do momentu osiągnięciu punktu przerwania, ręcznie wstrzymaniu wykonywania, wystąpi wyjątek un obsłużony, lub kończy się aplikacja. Aby uzyskać więcej informacji, zobacz [nawigowanie po sesji debugowania (Xaml i C#)](../debugger/navigate-a-debugging-session-in-visual-studio-xaml-and-csharp.md) .  
  
##  <a name="BKMK_Configure_the_debugging_session"></a>Konfigurowanie sesji debugowania  
  
###  <a name="BKMK_Open_the_debugging_property_page_for_the_project"></a>Otwórz stronę właściwości debugowania dla projektu  
  
1.  W Eksploratorze rozwiązań wybierz projekt. W menu skrótów wybierz **właściwości**.  
  
2.  Wykonaj następujące czynności, aby otworzyć stronę właściwości debugowania dla projektu:  
  
    -   Dla aplikacji Visual C# i Visual Basic, wybierz **debugowania**.  
  
         ![K & 35; &#47; Strony właściwości debugowania projektu VB](../debugger/media/dbg_csvb_debugpropertypage.png "DBG_CsVb_DebugPropertyPage")  
  
    -   W przypadku aplikacji Visual C++, rozwiń węzeł **właściwości konfiguracji** węzeł, a następnie wybierz **debugowanie**.  
  
         ![& C &43; 43; Strony właściwości debugowania aplikacji platformy uniwersalnej systemu Windows](../debugger/media/dbg_cpp_debugpropertypage.png "DBG_CPP_DebugPropertyPage")  
  
###  <a name="BKMK_Choose_the_build_configuration_options"></a>Opcje konfiguracji kompilacji  
  
1.  Z **konfiguracji** wybierz **debugowania** lub **debugowania (aktywny)**.  
  
2.  Z **platformy** listy wybierz do kompilacji dla platformy docelowej. W większości przypadków **Any CPU** (**wszystkich platform** w programie Visual C++) jest najlepszym rozwiązaniem.  
  
###  <a name="BKMK_Choose_the_deployment_target"></a>Wybierz cel wdrożenia  
 ![Dotyczy tylko systemów Windows](../debugger/media/windows_only_content.png "windows_only_content")  
  
 Można wdrażać i debugowania aplikacji platformy uniwersalnej systemu Windows na komputerze programu Visual Studio, w symulatorze Visual Studio na komputerze lokalnym lub na urządzeniu zdalnym.  
  
-   W przypadku aplikacji C# i Visual Basic, wybierz lokalizację docelową z **urządzenie docelowe** listy na **debugowania** stronę właściwości projektu.  
  
-   W przypadku aplikacji C++, wybierz lokalizację docelową z **debugera, aby uruchomić** listy na **debugowanie** strony właściwości:  
  
 Wybierz jedną z następujących opcji:  
  
|||  
|-|-|  
|**Komputer lokalny**|Debugowanie aplikacji w bieżącej sesji na komputerze lokalnym. Zobacz [aplikacji platformy uniwersalnej systemu Windows uruchom na komputerze lokalnym](../debugger/run-windows-store-apps-on-the-local-machine.md).|  
|**Symulator**|Debugowanie aplikacji w symulatorze Visual Studio dla [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplikacji. Symulator jest oknem pulpitu, które umożliwia debugowanie funkcji urządzeniami — takie jak gestów dotykowych i obracanie urządzeń, które nie są dostępne na komputerze lokalnym. Zobacz [uruchamianie aplikacji platformy UWP w symulatorze](../debugger/run-windows-store-apps-in-the-simulator.md).|  
|**Komputer zdalny**|Debugowanie aplikacji na urządzeniu, do którego jest podłączony do komputera lokalnego za pośrednictwem sieci intranet lub połączone bezpośrednio za pomocą kabla Ethernet. Aby debugować zdalnie, Visual Studio Tools zdalnego musi być zainstalowana i uruchomiona na urządzeniu zdalnym. Zobacz [aplikacji platformy uniwersalnej systemu Windows uruchom na komputerze zdalnym](../debugger/run-windows-store-apps-on-a-remote-machine.md).|  
  
 Jeśli wybierzesz **maszyny zdalnej**, określ nazwę lub adres IP komputera zdalnego w jeden z następujących sposobów:  
  
-   Wprowadź nazwę lub adres IP komputera zdalnego.  
  
    -   W przypadku aplikacji C# i Visual Basic, wprowadź nazwę lub adres IP w **maszyny zdalnej** pole.  
  
    -   W przypadku aplikacji C++, wprowadź nazwę lub adres IP w **Nazwa maszyny** pole.  
  
-   Wybierz komputer zdalny z **wybierz połączenia zdalnego debugera** okno dialogowe.  
  
     Aby otworzyć okno dialogowe:  
  
    -   W przypadku aplikacji C# i Visual Basic wybierz **znaleźć**.  
  
    -   W przypadku aplikacji C++, wybierz strzałkę w dół w **Nazwa maszyny** polu i wybierz polecenie  **\<zlokalizuj... >**.  
  
     ![Wybierz okno dialogowe połączenia zdalnego debugera](../debugger/media/vsrun_selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")  
  
    > [!NOTE]
    >  **Wybierz połączenia zdalnego debugera** Wyświetla okno dialogowe maszyny, które znajdują się w lokalnej sieci podrzędnych i komputerów, które są podłączone bezpośrednio do komputera programu Visual Studio kabla Ethernet. Aby określić inny komputer, wprowadź nazwę w **Nazwa maszyny** pole.  
  
 ![Dotyczy tylko Windows Phone](../debugger/media/phone_only_content.png "phone_only_content")  
  
 Można wdrażać i debugowania aplikacji Windows Phone, na urządzeniu lub na jednym z emulatory phone Visual Studio. Wybierz urządzenie lub emulator z **urządzenie docelowe** listy.  
  
###  <a name="BKMK_Choose_the_debugger_to_use"></a>Wybierz debuger do użycia  
 Domyślnie program Visual Studio debuguje zarządzanym kodem w aplikacji C# i Visual Basic.  
  
 W przypadku aplikacji C# i Visual Basic można debugować zarówno zarządzanego i natywnego kodu C/C++ w aplikacji. Wybierz **Włącz debugowanie kodu niezarządzanego** pole wyboru, aby uwzględnić kod macierzysty w sesji debugowania.  
  
 Domyślnie program Visual Studio debuguje natywnego kodu w języku C++ aplikacji.  
  
 W przypadku aplikacji C++ można debugować określone typy kodu, które znajdują się w części aplikacji zamiast lub oprócz kodu natywnego. Określenie kodu do debugowania w **typ debugera** listy na **debugowanie** strony właściwości projektu aplikacji.  
  
 Wybierz jedną z tych debugery z **procesu aplikacji** listy:  
  
|||  
|-|-|  
|**Tylko skryptu**|Debugowanie kodu JavaScript w aplikacji. Kodu zarządzanego i natywnego kodu zostaną zignorowane.|  
|**Tylko kod natywny**|Debugowanie kodu natywnego C/C++ w aplikacji. Kodu zarządzanego i kodu JavaScript są ignorowane.|  
|**Tylko zarządzane**|Debugowanie zarządzanego kodu w aplikacji. Kod JavaScript i natywnego kodu C/C++ są ignorowane.|  
|**Mieszanego (kodu zarządzanego i natywnego)**|Debugowanie kodu C/C++ natywnego i zarządzanego kodu w aplikacji. Kod JavaScript jest ignorowana.|  
|**Tylko procesora GPU**|Debugowania natywnego kodu C++, który jest uruchamiany na procesor graficzny (GPU).|  
  
 ![Dotyczy tylko Windows Phone](../debugger/media/phone_only_content.png "phone_only_content")  
  
 Dla aplikacji Windows Phone, można także debugera do użycia dla procesów w tle z **proces zadania w tle**.  
  
###  <a name="BKMK__Optional__Delay_starting_the_debug_session"></a>(Opcjonalnie) Opóźnienie rozpoczynania sesji debugowania  
 Domyślnie program Visual Studio natychmiast uruchamia aplikację po rozpoczęciu debugowania. Można również uruchomić sesję debugowania, ale opóźnienie uruchomienia aplikacji. Po wybraniu tej opcji, po uruchomieniu z ekranu startowego lub kontrakt aktywacji lub po uruchomieniu przez inny proces lub metoda aplikacji została uruchomiona w debugerze. Jeśli chcesz debugować zadania w tle, gdy aplikacja nie jest uruchomiona, również opóźnić uruchomienie aplikacji.  
  
 Opóźnienia uruchomienia aplikacji, można:  
  
-   Dla aplikacji Visual C# i Visual Basic, wybierz **nie uruchamiaj, ale Debuguj kod przy rozpoczęciu** na **debugowania** strony właściwości.  
  
-   W przypadku aplikacji Visual C++, wybierz **tak** z **uruchamianie aplikacji** listy na **debugowanie** strony właściwości.  
  
###  <a name="BKMK__Optional__Disable_network_loopbacks"></a>(Opcjonalnie) Wyłącz sprzężenia zwrotne sieci  
 ![Dotyczy tylko systemów Windows](../debugger/media/windows_only_content.png "windows_only_content")  
  
 Ze względów bezpieczeństwa aplikacji platformy uniwersalnej systemu Windows, która jest zainstalowana w sposób standardowy jest niedozwolone do nawiązywania połączeń sieciowych do zainstalowania na urządzeniu. Domyślnie wdrożenie programu Visual Studio tworzy wyjątek od tej reguły dla wdrożonej aplikacji. To wykluczenie umożliwia przetestowanie procedur komunikacji na jednym komputerze. Przed wysłaniem aplikacji Microsoft Store należy przetestować aplikację bez zwolnienia.  
  
 Aby usunąć wykluczenia sprzężenia zwrotnego sieci:  
  
-   Dla aplikacji Visual C# i Visual Basic, wyczyść **Zezwalaj na sprzężenie zwrotne sieci** pole wyboru na **debugowania** strony właściwości.  
  
-   W przypadku aplikacji Visual C++, wybierz **nr** z **Zezwalaj na sprzężenie zwrotne sieci** listy na **debugowanie** strony właściwości.  
  
###  <a name="BKMK__Optional__Reinstall_the_app_when_you_start_debugging"></a>(Opcjonalnie) Zainstaluj ponownie aplikację po rozpoczęciu debugowania  
 Diagnozowanie problemów z instalacji i wstępnej konfiguracji aplikacji Visual C# lub Visual Basic, wybierz **Odinstaluj i ponownie zainstaluj Mój pakiet** na **debugowania** stronę właściwości i Utwórz ponownie oryginalna instalacja po rozpoczęciu debugowania. Ta opcja nie jest dostępne dla projektów Visual C++.  
  
###  <a name="BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger"></a>(Opcjonalnie) Wyłączyć wymaganie uwierzytelniania można uruchomić zdalnego debugera  
 ![Dotyczy tylko systemów Windows](../debugger/media/windows_only_content.png "windows_only_content")  
  
 Domyślnie musisz podać poświadczenia, aby uruchomić zdalnego debugera.  
  
> [!IMPORTANT]
>  Można uruchomić zdalnego debugera w trybie bez uwierzytelniania, ale ten tryb jest zalecane. Po uruchomieniu w tym trybie nie ma zabezpieczeń sieci. Wybierz tryb Bez uwierzytelniania tylko wtedy, gdy masz pewność, że sieć nie jest zagrożona przez złośliwe lub wrogie działania.  
  
 Aby usunąć wymaganie uwierzytelniania:  
  
1.  Dla aplikacji Visual C# i Visual Basic, wyczyść **uwierzytelnianie** pole wyboru na **debugowania** strony właściwości.  
  
2.  Dla aplikacji Visual C++, wybierz **nr** z **wymagają uwierzytelniania** listy na **debugowanie** strony właściwości.  
  
 [W tym temacie](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Start_the_debugging_session"></a>Uruchom sesję debugowania  
  
###  <a name="BKMK_Start_debugging__F5_"></a>Rozpocznij debugowanie (F5)  
 Po wybraniu **Rozpocznij debugowanie** (klawiatury: F5) na **debugowania** menu programu Visual Studio uruchamia aplikację w debugerze. Wykonanie kontynuowany do momentu osiągnięciu punktu przerwania, możesz ręcznie Wstrzymaj wykonywanie, wystąpi wyjątek, lub kończy się aplikacja.  
  
###  <a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a>Rozpocznij debugowanie (F5), ale opóźnienie rozpoczęcia aplikacji  
 Można skonfigurować aplikację do uruchamiania w trybie debugowania, ale należy ją uruchomić za pomocą metody innej niż debugera. Można na przykład, aby debugować uruchamiania aplikacji z Start menu lub debugowania proces w tle w aplikacji bez konieczności uruchamiania aplikacji. Aby opóźnić uruchomienie aplikacji, wykonaj następujące czynności:  
  
-   Na **debugowanie** strony właściwości aplikacji (**debugowania** w programie Visual C++)  
  
    -   Dla aplikacji Visual C# i Visual Basic, wybierz **nie uruchamiaj, ale Debuguj kod przy rozpoczęciu**.  
  
    -   W przypadku aplikacji Visual C++, wybierz **tak** z **uruchamianie aplikacji** listy.  
  
-   Wybierz **Rozpocznij debugowanie** na **debugowania** menu (klawiatury: F5).  
  
-   Uruchom aplikację z menu Start, kontrakt wykonywania lub za pomocą innej procedury.  
  
 Uruchamia aplikację w trybie debugowania. Wykonanie kontynuowany do momentu osiągnięciu punktu przerwania, możesz ręcznie Wstrzymaj wykonywanie, wystąpi nieobsługiwany wyjątek, lub kończy się aplikacja.  
  
 . Aby uzyskać więcej informacji o debugowaniu zadania w tle, zobacz [wyzwalacza wstrzymania, wznowienia i zdarzeń dla aplikacji platformy uniwersalnej systemu Windows w tle)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).  
  
###  <a name="BKMK_Start_an_installed_app_in_the_debugger"></a>Uruchom zainstalowaną aplikację w debugerze  
 Podczas rozpoczynania debugowania za pomocą F5, Visual Studio tworzy i wdraża aplikację, ustawia aplikacji do uruchamiania w trybie debugowania i następnie rozpoczyna się. Aby uruchomić aplikację, która jest już zainstalowana na urządzeniu, użyj okna dialogowego Debuguj zainstalowany pakiet aplikacji. Ta procedura jest przydatna, gdy chcesz debugować aplikację, która została zainstalowana ze Sklepu Windows lub, jeśli pliki źródłowe dla aplikacji, lecz nie ma projektu programu Visual Studio dla aplikacji. Na przykład może być systemu niestandardowej kompilacji, która nie korzysta z projektów Visual Studio lub rozwiązania.  
  
 Aplikację można zainstalować na urządzeniu lokalnym, lub można ją na urządzeniu zdalnym.  Możesz natychmiast uruchomić aplikację, lub możesz ustawić do uruchamiania w debugerze po uruchomieniu przez inny proces lub metody, takie jak z Start menu lub kontrakt aktywacji, można również ustawić aplikacji do uruchamiania w trybie debugowania, gdy chcesz debugować proces w tle bez uruchamiania aplikacji. Aby uzyskać więcej informacji, zobacz [wyzwalacza wstrzymania, wznowienia i zdarzeń dla aplikacji platformy uniwersalnej systemu Windows w tle)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).  
  
 Aby ustawić zainstalowaną aplikację do uruchamiania w trybie debugowania, wykonaj następujące czynności:  
  
> [!NOTE]
>  Aplikacja nie może być uruchomiona, po uruchomieniu tej procedury.  
  
1.  Na **debugowania** menu, wybierz **Debuguj zainstalowany pakiet aplikacji**  
  
2.  Z listy, wybierz jedną z następujących opcji:  
  
    |||  
    |-|-|  
    |**Komputer lokalny**|Debugowanie aplikacji w bieżącej sesji na komputerze lokalnym. Zobacz [aplikacji platformy uniwersalnej systemu Windows uruchom na komputerze lokalnym](../debugger/run-windows-store-apps-on-the-local-machine.md).|  
    |**Symulator**|Debugowanie aplikacji w symulatorze Visual Studio dla [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplikacji. Symulator jest oknem pulpitu, które umożliwia debugowanie funkcji urządzeniami — takie jak gestów dotykowych i obracanie urządzeń, które nie są dostępne na komputerze lokalnym. Zobacz [uruchamianie aplikacji platformy UWP w symulatorze](../debugger/run-windows-store-apps-in-the-simulator.md).|  
    |**Komputer zdalny**|Debugowanie aplikacji na urządzeniu, do którego jest podłączony do komputera lokalnego za pośrednictwem sieci intranet lub połączone bezpośrednio za pomocą kabla Ethernet. Aby debugować zdalnie, Visual Studio Tools zdalnego musi być zainstalowana i uruchomiona na urządzeniu zdalnym. Zobacz [aplikacji platformy uniwersalnej systemu Windows uruchom na komputerze zdalnym](../debugger/run-windows-store-apps-on-a-remote-machine.md).|  
  
3.  Wybierz aplikację z **zainstalowane pakiety aplikacji** listy.  
  
4.  Wybierz aparat debugowania do użycia z **Debuguj ten typ kodu** listy.  
  
5.  (Opcjonalnie). Wybierz **nie uruchamiaj, ale Debuguj kod przy rozpoczęciu** do debugowania aplikacji podczas jej uruchamiania za pomocą innej metody, lub Aby debugować proces w tle.  
  
 Po kliknięciu **Start**, aplikacja jest uruchomiona lub jest ustawiony na uruchomienie w trybie debugowania.  
  
###  <a name="BKMK_Attach_the_debugger_to_a_running_app_"></a>Dołącz debuger do uruchomionej aplikacji  
 Można dołączyć debugera do [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplikacji, musi Użyj Menedżera pakietów możliwością debugowania można ustawić aplikacji do uruchamiania w trybie debugowania. Możliwością debugowania Menedżera pakietów jest zainstalowany program Visual Studio Tools zdalnego.  
  
 Dołączanie debugera do aplikacji jest przydatne, gdy potrzebne do debugowania aplikacji już zainstalowany, takie jak aplikacja, która została zainstalowana z [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)]. Dołączanie jest wymagany, jeśli pliki źródłowe dla aplikacji, lecz nie ma projektu programu Visual Studio dla aplikacji. Na przykład może być systemu niestandardowej kompilacji, która nie korzysta z projektów Visual Studio lub rozwiązania.  
  
 Dołączanie debugera do aplikacji wymaga następujące kroki:  
  
1.  Ustaw aplikację do uruchamiania w trybie debugowania. Należy to zrobić, gdy aplikacja nie jest uruchomiona.  
  
2.  Uruchom aplikację. Aplikację można uruchomić z ekranu startowego, kontrakt wykonywania lub innej metody.  
  
3.  Dołącz debuger do uruchomionej aplikacji.  
  
####  <a name="BKMK_Set_the_app_to_run_in_debug_mode"></a>Ustaw aplikację do uruchamiania w trybie debugowania  
  
1.  Zainstaluj program Visual Studio Tools zdalnego na urządzeniu, na którym zainstalowano aplikację. Zobacz [Instalowanie narzędzi Remote Tools](http://msdn.microsoft.com/library/windows/apps/hh441469.aspx#BKMK_Installing_the_Remote_Tools).  
  
2.  Na ekranie startowym Wyszukaj `Debuggable Package Manager` , a następnie uruchom go.  
  
     Zostanie wyświetlone okno programu PowerShell, poprawnie skonfigurowany na potrzeby polecenia cmdlet AppxDebug.  
  
3.  Aby włączyć debugowanie aplikacji, należy określić identyfikator element PackageFullName aplikacji. Aby wyświetlić listę wszystkich aplikacji, które zawiera element PackageFullName, wpisz `Get-AppxPackage` w wierszu polecenia programu PowerShell.  
  
4.  W wierszu polecenia programu PowerShell wprowadź `Enable-AppxDebug` *Pełna_nazwa_pakietu* gdzie *Pełna_nazwa_pakietu* jest identyfikatorem element PackageFullName aplikacji.  
  
####  <a name="BKMK_Attach_the_debugger"></a>Dołącz debuger  
 Aby dołączyć debuger:  
  
1.  Na **debugowania** menu, wybierz **dołączyć do procesu**.  
  
     **Dołączyć do procesu** zostanie wyświetlone okno dialogowe.  
  
2.  Aby dołączyć do aplikacji na urządzeniu zdalnym, określ urządzenie zdalne w **kwalifikator** pole. Można:  
  
    -   Wprowadź nazwę w **kwalifikator** pole.  
  
    -   Wybierz strzałkę w dół w **kwalifikator** polu, a następnie wybierz urządzenie z listy urządzeń dołączonych do przed.  
  
    -   Wybierz **znaleźć** wybierz urządzenie z listy urządzeń w danej podsieci lokalnej.  
  
3.  Określ typ kodu, który chcesz debugować w **dołączyć do** pola.  
  
     Wybierz **wybierz** , a następnie wykonaj jedną z następujących czynności:  
  
    -   Wybierz **automatycznie Określ typ kodu do debugowania**  
  
    -   Wybierz **Debuguj te typy kodu** , a następnie wybierz co najmniej jeden typ z listy.  
  
4.  W **dostępne procesy** wybierz procesu aplikacji.  
  
5.  Wybierz **dołączyć**.  
  
 Visual Studio dołącza debuger do procesu. Wykonanie kontynuowany do momentu osiągnięciu punktu przerwania, możesz ręcznie Wstrzymaj wykonywanie, wystąpi nieobsługiwany wyjątek, lub kończy się aplikacja.  
  
 [W tym temacie](#BKMK_In_this_topic)  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji w programie Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)   
 [Nawigowanie po sesji debugowania (Xaml i C#)](../debugger/navigate-a-debugging-session-in-visual-studio-xaml-and-csharp.md)