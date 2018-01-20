---
title: "Uruchom sesję debugowania dla aplikacji platformy uniwersalnej systemu Windows w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/04/2018
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
- vs.debug.installedapppackagelauncher
- vs.debug.error.wwahost_scriptdebuggingdisabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
caps.latest.revision: "20"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: uwp
ms.openlocfilehash: 718d24ab0f9fbb310d2482b63bc98dd139658330
ms.sourcegitcommit: 5d43e9590e2246084670b79269cc9d99124bb3df
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="start-a-debugging-session-for-a-uwp-app-in-visual-studio"></a>Uruchom sesję debugowania dla aplikacji platformy uniwersalnej systemu Windows w programie Visual Studio
  
 W tym temacie opisano, jak uruchomić sesję debugowania dla aplikacji platformy uniwersalnej systemu Windows w języku XAML i Visual C++, Visual C# lub Visual Basic i dla aplikacji platformy uniwersalnej systemu Windows zapisywane w kodzie HTML i JavaScript. Debugowanie aplikacji obejmuje zarówno Konfigurowanie sesji debugowania i wybierając sposób, aby uruchomić aplikację.  
  
##  <a name="BKMK_The_easy_way_to_start_debugging"></a>Łatwo można rozpocząć debugowania  
  
1.  Otwórz rozwiązanie aplikacji w programie Visual Studio.  
  
2.  Wybierz F5.  
  
 Visual Studio kompiluje i uruchamia aplikację w debugerze. Wykonanie kontynuowany do momentu osiągnięciu punktu przerwania, możesz ręcznie Wstrzymaj wykonywanie, wystąpi nieobsługiwany wyjątek, lub kończy się aplikacja.  
  
##  <a name="BKMK_Choose_the_build_configuration_options"></a>Opcje konfiguracji kompilacji  
  
1.   Z listy rozwijanej obok pozycji listy **Rozpocznij debugowanie** przycisk debugera **standardowe** narzędzi wybierz **debugowania**.  
  
2.  Z **platformy** listy wybierz do kompilacji dla platformy docelowej.  
  
##  <a name="BKMK_Choose_the_deployment_target"></a>Wybierz cel wdrożenia  
  
Można wdrażać i debugowania aplikacji platformy uniwersalnej systemu Windows, na komputerze programu Visual Studio, podłączonego urządzenia, symulator Visual Studio na komputerze lokalnym, urządzenie zdalne lub emulator. Wybierz cel wdrożenia z listy rozwijanej z prawej strony **platformy** docelowego debugera **standardowe** paska narzędzi.
  
![Wybierz cel wdrożenia](../debugger/media/vsrun_select_target_device.png)  
  
Wybierz jedną z następujących opcji:  
  
|||  
|-|-|  
|**Komputer lokalny**|Debugowanie aplikacji w bieżącej sesji na komputerze lokalnym.|  
|**Simulator**|Debugowanie aplikacji w symulatorze Visual Studio dla aplikacji platformy uniwersalnej systemu Windows. Symulator jest oknem pulpitu, które umożliwia debugowanie funkcji urządzeniami — takie jak gestów dotykowych i obracanie urządzeń — które mogą nie być dostępne na komputerze lokalnym. Ta opcja jest dostępna tylko jeśli aplikacji **Min platformy docelowej. Wersja** jest mniejsza niż system operacyjny na komputerze deweloperskim. Zobacz [uruchamianie aplikacji platformy UWP w symulatorze](../debugger/run-windows-store-apps-in-the-simulator.md).|  
|**Komputer zdalny**|Debugowanie aplikacji na urządzeniu, do którego jest podłączony do komputera lokalnego za pośrednictwem sieci intranet lub połączone bezpośrednio za pomocą kabla Ethernet. Aby debugować zdalnie, narzędzi Remote Tools for Visual Studio musi być zainstalowana i uruchomiona na urządzeniu zdalnym. Zobacz [aplikacji platformy uniwersalnej systemu Windows uruchom na komputerze zdalnym](../debugger/run-windows-store-apps-on-a-remote-machine.md).|  
|**Urządzenia**|Debugowanie aplikacji na urządzeniu połączenie USB. Urządzenie musi być odblokowany i ma ekranu odblokowane.|  
|**Mobile Emulator**|Rozruch z konfiguracją określoną w nazwie emulatora emulatora, wdrożyć aplikację i Rozpocznij debugowanie. Emulatory są dostępne tylko na komputerach z włączoną funkcją Hyper-V.|  

##  <a name="BKMK_Open_the_debugging_property_page_for_the_project"></a>Wybierz dodatkowe opcje debugowania  

Jeśli musisz skonfigurować dodatkowe opcje debugowania, otwórz stronę właściwości projektu.
  
1.  W Eksploratorze rozwiązań wybierz projekt. W menu skrótów wybierz **właściwości**.  
  
2.  Wykonaj następujące czynności, aby otworzyć stronę właściwości debugowania dla projektu:  
  
    -   Dla aplikacji Visual C# i Visual Basic, wybierz **debugowania**.  
  
         ![K & 35; &#47; Strony właściwości debugowania projektu VB](../debugger/media/dbg_csvb_debugpropertypage.png)  
  
    -   W przypadku aplikacji Visual C++ i JavaScript, rozwiń węzeł **właściwości konfiguracji** węzeł, a następnie wybierz **debugowanie**.  
  
         ![& C &43; 43; Strony właściwości debugowania aplikacji platformy uniwersalnej systemu Windows](../debugger/media/dbg_cpp_debugpropertypage.png)  

###  <a name="BKMK_Choose_the_debugger_to_use"></a>Wybierz debuger do użycia  
Domyślnie program Visual Studio debuguje zarządzanym kodem w aplikacji C# i Visual Basic. W przypadku aplikacji C# i Visual Basic można debugować zarówno zarządzanego i natywnego kodu C/C++ w aplikacji. W aplikacjach C++ Visual Studio debuguje kodu natywnego domyślnie. W aplikacjach JavaScript programu Visual Studio debuguje skryptu domyślnie. 
  
Dla aplikacji C++ i JavaScript można debugować określone typy kodu, które znajdują się w części aplikacji zamiast lub oprócz kodu natywnego. Określenie kodu do debugowania w **typ debugera** listy na **debugowanie** strony właściwości projektu aplikacji.  
  
Wybierz jedną z tych debugery z **procesu aplikacji** listy:  
  
|||  
|-|-|  
|**Tylko zarządzane**|Debugowanie zarządzanego kodu w aplikacji. Kod JavaScript i natywnego kodu C/C++ są ignorowane.|  
|**Tylko kod natywny**|Debugowanie kodu natywnego C/C++ w aplikacji. Kodu zarządzanego i kodu JavaScript są ignorowane.|  
|**Mieszanego (kodu zarządzanego i natywnego)**|Debugowanie kodu C/C++ natywnego i zarządzanego kodu w aplikacji. Kod JavaScript jest ignorowana. W projektach C++, ta opcja jest nazywany **(zarządzanego i natywnego)**.|  
|**Tylko skryptu**|Debugowanie kodu JavaScript w aplikacji. Kodu zarządzanego i natywnego kodu zostaną zignorowane.|  
|**Skrypt i natywne**|Debugowanie kodu C/C++ natywnego i kodu JavaScript w aplikacji. Kod zarządzany jest ignorowana. Dostępne w tylko dla projektów C++.|  
|**Tylko GPU (C++ AMP)**|Debugowania natywnego kodu C++, który jest uruchamiany na procesor graficzny (GPU). Dostępne w tylko dla projektów C++.|  

W aplikacji C# i Visual Basic, można również ustawić taki sam **debugera typu** wartości dla dowolnego zadania w tle, które są częścią projektu.
  
###  <a name="BKMK__Optional__Delay_starting_the_debug_session"></a>(Opcjonalnie) Opóźnienie rozpoczynania sesji debugowania  
 Domyślnie program Visual Studio natychmiast uruchamia aplikację po rozpoczęciu debugowania. Można również uruchomić sesję debugowania, ale opóźnienie uruchomienia aplikacji. Po wybraniu tej opcji, po uruchomieniu z ekranu startowego lub kontrakt aktywacji lub po uruchomieniu przez inny proces lub metoda aplikacji została uruchomiona w debugerze. Jeśli chcesz debugować zadania w tle, gdy aplikacja nie jest uruchomiona, również opóźnić uruchomienie aplikacji.  
  
 Opóźnienia uruchomienia aplikacji, można:  
  
-   Dla aplikacji Visual C# i Visual Basic, wybierz **nie uruchamiaj, ale Debuguj kod przy rozpoczęciu** na **debugowania** strony właściwości.  
  
-   W przypadku aplikacji Visual C++ i JavaScript, wybierz **nr** z **uruchamianie aplikacji** listy na **debugowanie** strony właściwości.  
  
###  <a name="BKMK__Optional__Disable_network_loopbacks"></a>(Opcjonalnie) Wyłącz sprzężenia zwrotne sieci  
  
 Ze względów bezpieczeństwa aplikacji platformy uniwersalnej systemu Windows, która jest zainstalowana w sposób standardowy jest niedozwolone do nawiązywania połączeń sieciowych do zainstalowania na urządzeniu. Domyślnie wdrożenie programu Visual Studio tworzy wyjątek od tej reguły dla wdrożonej aplikacji. To wykluczenie umożliwia przetestowanie procedur komunikacji na jednym komputerze. Przed wysłaniem aplikacji Microsoft Store należy przetestować aplikację bez zwolnienia.  
  
 Aby usunąć wykluczenia sprzężenia zwrotnego sieci:  
  
-   Dla aplikacji Visual C# i Visual Basic, wyczyść **Zezwalaj na sprzężenie zwrotne sieci lokalnej** pole wyboru na **debugowania** strony właściwości.  
  
-   W przypadku aplikacji Visual C++ i JavaScript, wybierz **nr** z **Zezwalaj lokalnego sprzężenia zwrotnego w sieci** listy na **debugowanie** strony właściwości.  
  
###  <a name="BKMK__Optional__Reinstall_the_app_when_you_start_debugging"></a>(Opcjonalnie) Zainstaluj ponownie aplikację po rozpoczęciu debugowania  
 Diagnozowanie problemów z instalacji i wstępnej konfiguracji aplikacji Visual C# lub Visual Basic, wybierz **Odinstaluj i ponownie zainstaluj Mój pakiet** na **debugowania** stronę właściwości i Utwórz ponownie oryginalna instalacja po rozpoczęciu debugowania. Ta opcja nie jest dostępne dla projektów Visual C++ i JavaScript.  
  
###  <a name="BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger"></a>(Opcjonalnie) Wyłączyć wymaganie uwierzytelniania można uruchomić zdalnego debugera  
  
 Domyślnie, należy podać poświadczenia do uruchamiania debugera zdalnego po wybraniu **maszyny zdalnej** jako cel wdrożenia.
  
> [!IMPORTANT]
>  Można uruchamiać bez uwierzytelniania zdalny debuger, ale ten tryb jest zalecane. Po uruchomieniu w tym trybie nie ma zabezpieczeń sieci. Bez uwierzytelniania należy wybrać tylko wtedy, gdy masz pewność, że sieć nie jest narażone złośliwego kodu lub szkodliwy ruch.  
  
 Aby usunąć wymaganie uwierzytelniania:  
  
1.  Dla aplikacji Visual C# i Visual Basic, wybierz **maszyny zdalnej** jako **urządzenie docelowe** na **debugowania** strony właściwości, a następnie ustawić **tryb uwierzytelniania**  do **Brak** lub **uniwersalnego (nieszyfrowanego protokołu)**.
  
2.  Dla aplikacji Visual C++ i JavaScript, wybierz **maszyny zdalnej** jako **urządzenie docelowe** na **debugowanie** strony właściwości, a następnie ustawić **wymagają Uwierzytelnianie** do **Brak** lub **uniwersalnego (nieszyfrowanego protokołu)**.  

    **Uniwersalny (nieszyfrowanego protokołu)** jest przeznaczona do użytku podczas wdrażania na urządzeniu zdalnym. Obecnie jest przeznaczony dla urządzenia IoT, urządzenia Xbox i urządzenia HoloLens, a także twórców aktualizacji lub nowszych komputerach. Uniwersalny (nieszyfrowanego protokołu) można używać tylko w sieciach zaufanych. Połączenie debugowania jest narażony na złośliwych użytkowników, którzy może przechwytywać i zmiany danych są przekazywane między opracowywania i komputer zdalny.  
  
##  <a name="BKMK_Start_the_debugging_session"></a>Uruchom sesję debugowania  
  
###  <a name="BKMK_Start_debugging__F5_"></a>Rozpocznij debugowanie (F5)  
 Po wybraniu **Rozpocznij debugowanie** (klawiatury: F5) na **debugowania** menu programu Visual Studio uruchamia aplikację w debugerze. Wykonanie kontynuowany do momentu osiągnięciu punktu przerwania, możesz ręcznie Wstrzymaj wykonywanie, wystąpi wyjątek, lub kończy się aplikacja.  
  
###  <a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a>Rozpocznij debugowanie (F5), ale opóźnienie rozpoczęcia aplikacji  
 Można skonfigurować aplikację do uruchamiania w trybie debugowania, ale należy ją uruchomić za pomocą metody innej niż debugera. Można na przykład, aby debugować uruchamiania aplikacji z Start menu lub debugowania proces w tle w aplikacji bez konieczności uruchamiania aplikacji. Aby opóźnić uruchomienie aplikacji, wykonaj następujące czynności:  
  
-   Na **debugowania** strony właściwości aplikacji (**debugowanie** w programie Visual C++ i JavaScript)  
  
    -   Dla aplikacji Visual C# i Visual Basic, wybierz **nie uruchamiaj, ale Debuguj kod przy rozpoczęciu**.  
  
    -   W przypadku aplikacji Visual C++ i JavaScript, wybierz **tak** z **uruchamianie aplikacji** listy.  
  
-   Wybierz **Rozpocznij debugowanie** na **debugowania** menu (klawiatury: F5).  
  
-   Uruchom aplikację z menu Start, kontrakt wykonywania lub za pomocą innej procedury.  
  
 Uruchamia aplikację w trybie debugowania. Wykonanie kontynuowany do momentu osiągnięciu punktu przerwania, możesz ręcznie Wstrzymaj wykonywanie, wystąpi nieobsługiwany wyjątek, lub kończy się aplikacja.  
  
 Aby uzyskać więcej informacji o debugowaniu zadania w tle, zobacz [wyzwalacza wstrzymania, wznowienia i zdarzeń dla aplikacji platformy uniwersalnej systemu Windows w tle)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).  
  
###  <a name="BKMK_Start_an_installed_app_in_the_debugger"></a>Uruchom zainstalowaną aplikację w debugerze  
Podczas rozpoczynania debugowania za pomocą F5, Visual Studio tworzy i wdraża aplikację, ustawia aplikacji do uruchamiania w trybie debugowania i następnie rozpoczyna się. Aby uruchomić aplikację, która jest już zainstalowana na urządzeniu, należy użyć **Debuguj zainstalowany pakiet aplikacji** okno dialogowe. Ta procedura jest przydatne, należy do debugowania aplikacji, która została zainstalowana z Microsoft Store lub jeśli pliki źródłowe dla aplikacji, lecz nie ma projektu programu Visual Studio dla aplikacji. Na przykład może być systemu niestandardowej kompilacji, która nie korzysta z projektów Visual Studio lub rozwiązania.  
  
Aplikację można zainstalować na urządzeniu lokalnym, lub można ją na urządzeniu zdalnym.  Możesz natychmiast uruchomić aplikację, lub możesz ustawić do uruchamiania w debugerze po uruchomieniu przez inny proces lub metody, takie jak z Start menu lub kontrakt aktywacji, można również ustawić aplikacji do uruchamiania w trybie debugowania, gdy chcesz debugować proces w tle bez uruchamiania aplikacji. Aby uzyskać więcej informacji, zobacz [wyzwalacza wstrzymania, wznowienia i zdarzeń dla aplikacji platformy uniwersalnej systemu Windows w tle)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).  
  
Aby uruchomić zainstalowaną aplikację w debugerze, wybierz **debugowania**, następnie **innych celów debugowania**, a następnie **Debuguj zainstalowany pakiet aplikacji**. Aby uzyskać dodatkowe instrukcje, zobacz [debugowania pakietu aplikacji zainstalowanych](../debugger/debug-installed-app-package.md).

###  <a name="BKMK_Attach_the_debugger_to_a_running_app_"></a>Dołącz debuger do uruchomionej aplikacji platformy uniwersalnej systemu Windows  

Aby debugować uruchomionej aplikacji platformy uniwersalnej systemu Windows, należy wybrać **debugowania**, następnie **innych celów debugowania**, a następnie **Debuguj zainstalowany pakiet aplikacji**. Aby uzyskać dodatkowe instrukcje, zobacz [debugowania pakietu aplikacji zainstalowanych](../debugger/debug-installed-app-package.md).
  
###  <a name="BKMK_Attach_the_debugger_to_a_running_app_"></a>Dołącz debuger do uruchomionej aplikacji systemu Windows 8.x
 Można dołączyć debugera do [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplikacji, musi Użyj Menedżera pakietów możliwością debugowania można ustawić aplikacji do uruchamiania w trybie debugowania. Możliwością debugowania Menedżera pakietów jest instalowany z narzędzi Remote Tools for Visual Studio.  
  
 Dołączanie debugera do aplikacji jest przydatne, gdy potrzebne do debugowania aplikacji już zainstalowany, takie jak aplikacja, która została zainstalowana z [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)]. Dołączanie jest wymagany, jeśli pliki źródłowe dla aplikacji, lecz nie ma projektu programu Visual Studio dla aplikacji. Na przykład może być systemu niestandardowej kompilacji, która nie korzysta z projektów Visual Studio lub rozwiązania.  
  
 Dołączanie debugera do aplikacji wymaga następujące kroki:  
  
1.  Ustaw aplikację do uruchamiania w trybie debugowania. Należy to zrobić, gdy aplikacja nie jest uruchomiona.  
  
2.  Uruchom aplikację. Aplikację można uruchomić z ekranu startowego, kontrakt wykonywania lub innej metody.  
  
3.  Dołącz debuger do uruchomionej aplikacji.  
  
####  <a name="BKMK_Set_the_app_to_run_in_debug_mode"></a>Ustaw aplikację do uruchamiania w trybie debugowania  
  
1.  Instalowanie narzędzi Remote Tools dla programu Visual Studio na urządzeniu, na którym zainstalowano aplikację. Zobacz [Instalowanie narzędzi remote tools](../debugger/remote-debugging.md).  
  
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

    > [!NOTE]
    >  W odróżnieniu od innych typów aplikacji JavaScript aplikacje uruchomione w wystąpienia procesu wwahost.exe. Jeśli z innych aplikacji JavaScript po dołączeniu do aplikacji, należy znać identyfikatora procesu liczbowych (PID) wwahost.exe aplikacji działającej w.  
    >   
    >  Zamknij wszystkie inne aplikacje JavaScript jest najprostszym sposobem, aby rozwiązać ten problem. W przeciwnym razie można otworzyć Menedżera zadań systemu Windows, aby uruchomić aplikację i zanotuj identyfikatorów procesów wwahost.exe. Po określeniu procesu, aby dołączyć do w **dostępne procesy** okno dialogowe wwahost.exe aplikacji będą mieć identyfikator, który jest inny niż te, które zostały wymienione.  
  
5.  Wybierz **dołączyć**.  
  
 Visual Studio dołącza debuger do procesu. Wykonanie kontynuowany do momentu osiągnięciu punktu przerwania, możesz ręcznie Wstrzymaj wykonywanie, wystąpi nieobsługiwany wyjątek, lub kończy się aplikacja.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji w programie Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)   