---
title: "Uruchom sesję debugowania dla aplikacji platformy uniwersalnej systemu Windows w programie Visual Studio (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.debug.installedapppackagelauncher
- vs.debug.error.wwahost_scriptdebuggingdisabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: fb91203f-2cf4-44d3-8ed9-93bc5aaa50b8
caps.latest.revision: "24"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: uwp
ms.openlocfilehash: b92f2f5ac10f917257e58443ab2161a164f39b28
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="start-a-debugging-session-for-uwp-apps-in-visual-studio-javascript"></a>Uruchom sesję debugowania dla aplikacji platformy uniwersalnej systemu Windows w programie Visual Studio (JavaScript)
![Ma zastosowanie do systemu Windows i Windows Phone](../debugger/media/windows_and_phone_content.png "windows_and_phone_content")  
  
 W tym temacie opisano, jak uruchomić sesję debugowania dla aplikacji platformy uniwersalnej systemu Windows w JavaScript i HTML5. Można uruchomić debugowania jednym naciśnięciem klawisza lub można skonfigurować sesję debugowania dla konkretnych scenariuszy, a następnie wybierz sposób, aby uruchomić aplikację.  
  
> [!NOTE]
>  Dla aplikacji napisanych w języku XAML i Visual C#, Visual C++ lub Visual Basic, zobacz [rozpocząć sesję debugowania: (VB, C#, C++ i XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)  
  
##  <a name="BKMK_In_this_topic"></a>W tym temacie  
 [W tym temacie](#BKMK_In_this_topic)  
  
 [Łatwo można rozpocząć debugowania](#BKMK_The_easy_way_to_start_debugging)  
  
 [Konfigurowanie sesji debugowania](#BKMK_Configure_the_debugging_session)  
  
-   [Otwórz stronę właściwości debugowania dla projektu](#BKMK_Open_the_debugging_property_page_for_the_project)  
  
-   [Opcje konfiguracji kompilacji](#BKMK_Choose_the_build_configuration_options)  
  
-   [Wybierz cel wdrożenia](#BKMK_Choose_the_deployment_target)  
  
-   [Wybierz debuger do użycia](#BKMK_Choose_the_debugger_to_use)  
  
-   [(Opcjonalnie) Opóźnienie uruchamianie aplikacji podczas sesji debugowania](#BKMK__Optional__Delay_starting_app_in_the_debug_session)  
  
-   [(Opcjonalnie) Wyłącz sprzężenia zwrotne sieci](#BKMK__Optional__Disable_network_loopbacks)  
  
 [Uruchom sesję debugowania](#BKMK_Start_the_debugging_session)  
  
-   [Rozpocznij debugowanie (F5)](#BKMK_Start_debugging__F5_)  
  
-   [Rozpocznij debugowanie (F5), ale opóźnienie rozpoczęcia aplikacji](#BKMK_Start_debugging__F5__but_delay_the_app_start)  
  
 [Uruchom zainstalowaną aplikację w debugerze](#BKMK_Start_an_installed_app_in_the_debugger)  
  
 [Dołącz debuger do uruchomionej aplikacji](#BKMK_Attach_the_debugger_to_a_running_app_)  
  
-   [Ustaw aplikację do uruchamiania w trybie debugowania](#BKMK_Set_the_app_to_run_in_debug_mode)  
  
-   [Dołącz debuger](#BKMK_Attach_the_debugger)  
  
##  <a name="BKMK_The_easy_way_to_start_debugging"></a>Łatwo można rozpocząć debugowania  
 ![Dotyczy tylko systemów Windows](../debugger/media/windows_only_content.png "windows_only_content")  
  
1.  Otwórz rozwiązanie aplikacji w programie Visual Studio.  
  
2.  Jeśli rozwiązanie zawiera wiele projektów, upewnij się, że projekt, który chcesz debugować projektu rozruchu. W Eksploruj rozwiązanie, wybierz projekt, a następnie wybierz pozycję **Ustaw jako projekt startowy** z menu kontekstowego.  
  
3.  Naciśnij F5.  
  
 ![Dotyczy tylko Windows Phone](../debugger/media/phone_only_content.png "phone_only_content")  
  
 Visual Studio kompiluje i uruchamia aplikację w debugerze. Wykonanie kontynuowany do momentu osiągnięciu punktu przerwania, możesz ręcznie Wstrzymaj wykonywanie, wystąpi nieobsługiwany wyjątek, lub kończy się aplikacja. Aby uzyskać więcej informacji, zobacz [Szybki Start: debugowanie kodu HTML i CSS](../debugger/quickstart-debug-html-and-css.md).  
  
##  <a name="BKMK_Configure_the_debugging_session"></a>Konfigurowanie sesji debugowania  
 Ponieważ skrypt nie jest skompilowany, nie stosuj ustawienia konfiguracji i platformy kompilacji. Jeśli debugujesz C++ lub zarządzanego składnika, ustawić **konfiguracji** do **debugowania** i platform docelowych z **konfiguracji** okna dialogowego.  
  
###  <a name="BKMK_Open_the_debugging_property_page_for_the_project"></a>Otwórz stronę właściwości debugowania dla projektu  
  
1.  W Eksploratorze rozwiązań wybierz projekt. W menu skrótów wybierz **właściwości**.  
  
2.  Rozwiń węzeł **właściwości konfiguracji** węzeł, a następnie wybierz **debugowanie**.  
  
###  <a name="BKMK_Choose_the_build_configuration_options"></a>Opcje konfiguracji kompilacji  
  
1.  Z **konfiguracji** wybierz **debugowania** lub **debugowania (aktywny)**.  
  
2.  Z **platformy** listy wybierz do kompilacji dla platformy docelowej. W większości przypadków **Any CPU** jest najlepszym rozwiązaniem.  
  
###  <a name="BKMK_Choose_the_deployment_target"></a>Wybierz cel wdrożenia  
 Można wdrażać i debugowanie aplikacji na maszynie programu Visual Studio w symulatorze Visual Studio na komputerze lokalnym lub na komputerze zdalnym. Wybierz lokalizację docelową z **debugera, aby uruchomić** listy na **debugowanie** stronę właściwości projektu.  
  
 ![Dotyczy tylko systemów Windows](../debugger/media/windows_only_content.png "windows_only_content")  
  
 Dla aplikacji platformy uniwersalnej systemu Windows, wybierz jedną z tych opcji z **urządzenie docelowe** listy:  
  
|||  
|-|-|  
|**Komputer lokalny**|Debugowanie aplikacji w bieżącej sesji na komputerze lokalnym. Zobacz [aplikacji platformy uniwersalnej systemu Windows uruchom na komputerze lokalnym](../debugger/run-windows-store-apps-on-the-local-machine.md).|  
|**Symulator**|Debugowanie aplikacji w symulatorze Visual Studio dla [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplikacji. Symulator jest oknem pulpitu, które umożliwia debugowanie funkcji urządzeniami — takie jak gestów dotykowych i obracanie urządzeń, które nie są dostępne na komputerze lokalnym. Zobacz [uruchamianie aplikacji platformy UWP w symulatorze](../debugger/run-windows-store-apps-in-the-simulator.md).|  
|**Komputer zdalny**|Debugowanie aplikacji na urządzeniu, do którego jest podłączony do komputera lokalnego za pośrednictwem sieci intranet lub połączone bezpośrednio za pomocą kabla Ethernet. Aby debugować zdalnie, Visual Studio Tools zdalnego musi być zainstalowana i uruchomiona na urządzeniu zdalnym. Zobacz [aplikacji platformy uniwersalnej systemu Windows uruchom na komputerze zdalnym](../debugger/run-windows-store-apps-on-a-remote-machine.md).|  
  
 Jeśli wybierzesz **maszyny zdalnej**, określ nazwę lub adres IP komputera zdalnego w jeden z następujących sposobów:  
  
-   Wprowadź nazwę lub adres IP komputera zdalnego w **Nazwa maszyny** pole.  
  
-   Wybierz strzałkę w dół w **Nazwa maszyny** polu i wybierz polecenie  **\<zlokalizuj... >**. Następnie wybierz komputer zdalny z **wybierz połączenia zdalnego debugera** okno dialogowe.  
  
     ![Wybierz połączenie zdalnego debugera](../debugger/media/vsrun_pro_selectremotedebuggerdlg.png "VSRUN_PRO_SelectRemoteDebuggerDlg")  
  
    > [!NOTE]
    >  Okno dialogowe Wybieranie połączenia zdalnego debugera wyświetla maszyny, które znajdują się w lokalnej sieci podrzędnych i komputerów, które są podłączone bezpośrednio do komputera programu Visual Studio kabla Ethernet. Aby określić inny komputer, wprowadź nazwę w **Nazwa maszyny** pole.  
  
 ![Dotyczy tylko Windows Phone](../debugger/media/phone_only_content.png "phone_only_content")  
  
 Dla aplikacji Windows Phone, wybierz **urządzenia** lub jednego z emulatorów z **urządzenie docelowe** listy.  
  
###  <a name="BKMK_Choose_the_debugger_to_use"></a>Wybierz debuger do użycia  
 Domyślnie debuger dołącza do kodu JavaScript w aplikacji. Istnieje możliwość debugowanie natywnych języka C++ i kod zarządzany składników aplikacji zamiast kodu JavaScript. Określenie kodu do debugowania w **typ debugera** listy na **debugowanie** strony właściwości projektu aplikacji.  
  
 Wybierz jedną z tych debugery z **typ debugera** listy:  
  
|||  
|-|-|  
|**Tylko skryptu**|Debugowanie kodu JavaScript w aplikacji. Kodu zarządzanego i natywnego kodu zostaną zignorowane.|  
|**Tylko kod natywny**|Debugowanie kodu natywnego C/C++ w aplikacji. Kodu zarządzanego i kodu JavaScript są ignorowane.|  
|**Natywny ze skryptem**|Debugowanie kodu natywnego języka C++ i kodu JavaScript w aplikacji.|  
|**Tylko zarządzane**|Debugowanie zarządzanego kodu w aplikacji. Kod JavaScript i natywnego kodu C/C++ są ignorowane.|  
|**Mieszanego (kodu zarządzanego i natywnego)**|Debugowanie kodu C/C++ natywnego i zarządzanego kodu w aplikacji. Kod JavaScript jest ignorowana.|  
  
###  <a name="BKMK__Optional__Delay_starting_app_in_the_debug_session"></a>(Opcjonalnie) Opóźnienie uruchamianie aplikacji podczas sesji debugowania  
 Domyślnie program Visual Studio natychmiast uruchamia aplikację po rozpoczęciu debugowania. Można również uruchomić sesję debugowania, ale opóźnienie uruchomienia aplikacji. Aplikacja jest uruchamiana w debugerze, po uruchomieniu z Start menu lub kontrakt aktywacji lub po uruchomieniu przez inny proces lub metody. Umożliwia także opóźnienia uruchomienia debugowania zdarzenia tło w aplikacji, który ma nastąpić, gdy aplikacja nie jest uruchomiona.  
  
 Możesz określić, czy można opóźnić uruchomienie aplikacji w **uruchamianie aplikacji** listy na **debugowanie** strony właściwości projektu aplikacji. Wybierz jedną z następujących opcji:  
  
-   Wybierz **nr** opóźnienia uruchomienia aplikacji.  
  
-   Wybierz **tak** Aby natychmiast uruchomić aplikację.  
  
###  <a name="BKMK__Optional__Disable_network_loopbacks"></a>(Opcjonalnie) Wyłącz sprzężenia zwrotne sieci  
 ![Dotyczy tylko systemów Windows](../debugger/media/windows_only_content.png "windows_only_content")  
  
 Ze względów bezpieczeństwa aplikacji platformy uniwersalnej systemu Windows, która jest zainstalowana w sposób standardowy jest niedozwolone do nawiązywania połączeń sieciowych do zainstalowania na urządzeniu. Domyślnie wdrożenie programu Visual Studio tworzy wyjątek od tej reguły dla wdrożonej aplikacji. To wykluczenie umożliwia przetestowanie procedur komunikacji na jednym komputerze. Przed wysłaniem aplikacji Microsoft Store należy przetestować aplikację bez zwolnienia.  
  
 Aby usunąć wykluczenia sprzężenia zwrotnego sieci, wybierz **nr** z **Zezwalaj na sprzężenie zwrotne sieci** listy na **debugowanie** strony właściwości.  
  
##  <a name="BKMK_Start_the_debugging_session"></a>Uruchom sesję debugowania  
  
###  <a name="BKMK_Start_debugging__F5_"></a>Rozpocznij debugowanie (F5)  
 Po wybraniu **Rozpocznij debugowanie** na **debugowania** menu (klawiatury: F5), programu Visual Studio uruchamia aplikację w debugerze. Wykonanie kontynuowany do momentu osiągnięciu punktu przerwania, możesz ręcznie Wstrzymaj wykonywanie, wystąpi nieobsługiwany wyjątek, lub kończy się aplikacja.  
  
###  <a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a>Rozpocznij debugowanie (F5), ale opóźnienie rozpoczęcia aplikacji  
 Można skonfigurować aplikację do uruchamiania w trybie debugowania, ale pozwól mu można uruchomić za pomocą metody innej niż debugera. Można na przykład, aby debugować uruchamiania aplikacji z Start menu lub debugowania proces w tle w aplikacji bez konieczności uruchamiania aplikacji. Aby opóźnić uruchomienie aplikacji, wykonaj następujące czynności:  
  
1.  Na **debugowania** strony aplikacji wybierz pozycję Właściwości projektu **nr** z **uruchamianie aplikacji** listy.  
  
2.  Wybierz **Rozpocznij debugowanie** na **debugowania** menu (klawiatury: F5).  
  
3.  Uruchom aplikację z menu Start, kontrakt wykonywania lub za pomocą innej procedury.  
  
 Uruchamia aplikację w trybie debugowania. Wykonanie kontynuowany do momentu osiągnięciu punktu przerwania, możesz ręcznie Wstrzymaj wykonywanie, wystąpi nieobsługiwany wyjątek, lub kończy się aplikacja.  
  
 . Aby uzyskać więcej informacji o debugowaniu zadania w tle, zobacz [wyzwalacza wstrzymania, wznowienia i zdarzeń dla aplikacji platformy uniwersalnej systemu Windows w tle)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).  
  
##  <a name="BKMK_Start_an_installed_app_in_the_debugger"></a>Uruchom zainstalowaną aplikację w debugerze  
 Podczas rozpoczynania debugowania za pomocą F5, Visual Studio tworzy i wdraża aplikację, ustawia aplikacji do uruchamiania w trybie debugowania i następnie rozpoczyna się. Aby uruchomić aplikację, która jest już zainstalowana na urządzeniu, użyj okna dialogowego Debuguj zainstalowany pakiet aplikacji. Ta procedura jest przydatna, gdy chcesz debugować aplikację, która została zainstalowana ze Sklepu Windows lub, jeśli pliki źródłowe dla aplikacji, lecz nie ma projektu programu Visual Studio dla aplikacji. Na przykład może być systemu niestandardowej kompilacji, która nie korzysta z projektów Visual Studio lub rozwiązania.  
  
 Aplikację można zainstalować na urządzeniu lokalnym, lub można ją na urządzeniu zdalnym.  Możesz natychmiast uruchomić aplikację, lub możesz ustawić do uruchamiania w debugerze po uruchomieniu przez inny proces lub metody, takie jak z Start menu lub kontrakt aktywacji, można również ustawić aplikacji do uruchamiania w trybie debugowania, gdy chcesz debugować proces w tle bez uruchamiania aplikacji. Aby uzyskać więcej informacji, zobacz [wyzwalacza wstrzymania, wznowienia i zdarzeń dla aplikacji platformy uniwersalnej systemu Windows w tle)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).  
  
 Aby ustawić zainstalowaną aplikację do uruchamiania w trybie debugowania, wykonaj następujące czynności:  
  
> [!NOTE]
>  Aplikacja nie może być uruchomiona, po uruchomieniu tej procedury.  
  
1.  Na **debugowania** menu, wybierz **Debuguj zainstalowany pakiet aplikacji**.  
  
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
  
##  <a name="BKMK_Attach_the_debugger_to_a_running_app_"></a>Dołącz debuger do uruchomionej aplikacji  
 Można dołączyć debugera do [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplikacji, musi Użyj Menedżera pakietów możliwością debugowania można ustawić aplikacji do uruchamiania w trybie debugowania. Możliwością debugowania Menedżera pakietów jest zainstalowany program Visual Studio Tools zdalnego.  
  
 Dołączanie debugera do aplikacji przydaje się, gdy musisz debugować aplikację już zainstalowany, takie jak aplikacja, która została zainstalowana z systemu Windows są przechowywane. Dołączanie jest wymagany, jeśli pliki źródłowe dla aplikacji, lecz nie ma projektu programu Visual Studio dla aplikacji. Na przykład może być systemu niestandardowej kompilacji, która nie korzysta z projektów Visual Studio lub rozwiązania.  
  
 Aby dołączyć do aplikacji:  
  
1.  Ustaw aplikację do uruchamiania w trybie debugowania. Należy to zrobić, gdy aplikacja nie jest uruchomiona.  
  
2.  Uruchom aplikację. Aplikację można uruchomić z Start menu, kontrakt wykonywania lub innej metody.  
  
3.  Dołącz debuger do uruchomionej aplikacji.  
  
###  <a name="BKMK_Set_the_app_to_run_in_debug_mode"></a>Ustaw aplikację do uruchamiania w trybie debugowania  
  
1.  Zainstaluj program Visual Studio Tools zdalnego na urządzeniu, na którym zainstalowano aplikację. Zobacz [Instalowanie narzędzi remote tools](http://msdn.microsoft.com/library/windows/apps/hh441469.aspx#BKMK_Installing_the_Remote_Tools).  
  
2.  W Start menu, wyszukaj `Debuggable Package Manager` , a następnie uruchom go.  
  
     Zostanie wyświetlone okno programu PowerShell, poprawnie skonfigurowany na potrzeby polecenia cmdlet AppxDebug.  
  
3.  Aby włączyć debugowanie aplikacji, należy określić identyfikator element PackageFullName aplikacji. Aby wyświetlić listę wszystkich aplikacji, które zawiera element PackageFullName, wpisz `Get-AppxPackage` w wierszu polecenia programu PowerShell.  
  
4.  W wierszu polecenia programu PowerShell wprowadź `Enable-AppxDebug` *Pełna_nazwa_pakietu* gdzie *Pełna_nazwa_pakietu* jest identyfikatorem element PackageFullName aplikacji.  
  
###  <a name="BKMK_Attach_the_debugger"></a>Dołącz debuger  
  
> [!TIP]
>  Uruchom aplikacji JavaScript w wystąpieniu procesu wwahost.exe. Jeśli z innych aplikacji JavaScript po dołączeniu do aplikacji, należy znać identyfikatora procesu liczbowych (PID) wwahost.exe aplikacji działającej w.  
>   
>  Zamknij wszystkie inne aplikacje JavaScript jest najprostszym sposobem, aby rozwiązać ten problem. W przeciwnym razie można otworzyć Menedżera zadań systemu Windows, aby uruchomić aplikację i zanotuj identyfikatorów procesów wwahost.exe. Po określeniu procesu, aby dołączyć do w **dostępne procesy** okno dialogowe wwahost.exe aplikacji będą mieć identyfikator, który jest inny niż te, które zostały wymienione.  
  
 Aby dołączyć debuger:  
  
1.  Na **debugowania** menu, wybierz **dołączyć do procesu**.  
  
     **Dołączyć do procesu** zostanie wyświetlone okno dialogowe.  
  
2.  Aby dołączyć do aplikacji na urządzeniu zdalnym, określ urządzenie zdalne w **kwalifikator** pole. Można:  
  
    -   Wprowadź nazwę w **kwalifikator** pole.  
  
    -   Wybierz strzałkę w dół w **kwalifikator** polu i wybierz urządzenie z listy urządzeń dołączonych do przed.  
  
    -   Wybierz **znaleźć** wybrać urządzenie z listy urządzeń w danej podsieci lokalnej.  
  
3.  Określ typ kodu, który chcesz debugować w **dołączyć do** pola.  
  
     Wybierz **wybierz** , a następnie wykonaj jedną z następujących czynności:  
  
    -   Wybierz **automatycznie Określ typ kodu do debugowania**.  
  
    -   Wybierz **Debuguj te typy kodu** , a następnie wybierz co najmniej jeden typ z listy.  
  
4.  W **dostępne procesy** listy, wybierz odpowiedni **wwahost.exe** procesu. Użyj **tytuł** kolumny do identyfikowania Twojej aplikacji.  
  
5.  Wybierz **dołączyć**.  
  
 Visual Studio dołącza debuger do procesu. Wykonanie kontynuowany do momentu osiągnięciu punktu przerwania, możesz ręcznie Wstrzymaj wykonywanie, wystąpi nieobsługiwany wyjątek, lub kończy się aplikacja.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrola wykonywania podczas sesji debugowania (JavaScript)](../debugger/control-execution-of-a-store-app-in-a-visual-studio-debug-session-for-windows-store-apps-javascript.md)   
 [Szybki Start: Debugowanie kodu HTML i CSS](../debugger/quickstart-debug-html-and-css.md)   
 [Wyzwalanie wstrzymania, wznowienia i zdarzeń dla aplikacji platformy uniwersalnej systemu Windows w tle)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)   
 [Debugowanie aplikacji w programie Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)