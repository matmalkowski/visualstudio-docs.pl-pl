---
title: Debugowanie wielu procesów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.programs
- vs.debug.processes.attaching
- vs.debug.activeprogram
- vs.debug.attaching
- vs.debug.attachedprocesses
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: bde37134-66af-4273-b02e-05b3370c31ab
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 08a089feceb6ba66791358096e3c4663df06494e
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="debug-multiple-processes"></a>Debugowanie wielu procesów
Poniżej przedstawiono sposób Rozpocznij debugowanie procesów, Przełącz między procesami, Podziel i kontynuować działanie, krokowo źródła, Zatrzymaj debugowanie i przerwanie lub odłączyć od procesów.  
  
##  <a name="BKMK_Configure_the_execution_behavior_of_multiple_processes"></a> Skonfiguruj sposób wykonywania wielu procesów  
 Domyślnie działa wiele procesów w debugerze, podziału, wykonywanie krok po kroku i poleceń debugera zatrzymywania zwykle wpływ na wszystkie procesy. Na przykład zawieszenia jednego procesu w punkcie przerwania wykonywania innych procesów również jest wstrzymana. Można zmienić to zachowanie domyślne, aby uzyskać większą kontrolę nad elementami docelowymi wykonywania poleceń.  
  
1.  Kliknij przycisk **Debuguj > Opcje i ustawienia**.  
  
2.  Na **debugowanie**, **ogólne** wyczyść **Przerwij wszystkie procesy w przypadku przerwania jednego procesu** pole wyboru.  
  
 ![Powrót do początku](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [zawartości](#BKMK_Contents)  
  
##  <a name="BKMK_Find_the_source_and_symbol___pdb__files"></a> Znajdowanie symboli i źródłowych plików (.pdb)  
 Aby kod źródłowy procesu, debuger musi mieć dostęp do plików źródłowych i pliki symboli procesu. Zobacz [Określ symboli (.pdb) i pliki źródłowe](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
 Jeśli nie masz dostępu do plików dla procesu, można nawigować przy użyciu okna dezasemblacji. Zobacz [porady: Korzystanie z okna dezasemblacji](../debugger/how-to-use-the-disassembly-window.md)  
  
 ![Powrót do początku](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [zawartości](#BKMK_Contents)  
  
##  <a name="BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger"></a> Uruchamiać wiele procesów w rozwiązaniu programu VS, dołączyć do procesu, automatyczne uruchamianie procesu w debugerze  
  
-   [Rozpocznij debugowanie wielu procesów w rozwiązaniu Visual Studio](#BKMK_Start_debugging_multiple_processes_in_a_Visual_Studio_solution)  
  
-   [Zmień projekt startowy](#BKMK_Change_the_startup_project)  
  
-   [Uruchom określonego projektu w rozwiązaniu](#BKMK_Start_a_specific_project_in_a_solution)  
  
-   [Uruchom wielu projektów w rozwiązaniu](#BKMK_Start_multiple_projects_in_a_solution)  
  
-   [Dołączanie do procesu](#BKMK_Attach_to_a_process)  
  
-   [Automatyczne uruchamianie procesu w debugerze](#BKMK_Automatically_start_an_process_in_the_debugger)  
  
> [!NOTE]
>  Debuger nie automatycznie dołączyć do procesu podrzędnego, który jest uruchamiany w debugowanym procesie, nawet jeśli projekt podrzędnych w tym samym rozwiązaniu. Debugowanie procesu podrzędnego:  
>   
>  -   Dołączanie do procesu podrzędnego, po jego uruchomieniu.  
>   
>      —lub—  
> -   Konfigurowanie systemu Windows, aby automatycznie uruchomić procesu podrzędnego w nowym wystąpieniu debugera.  
  
###  <a name="BKMK_Start_debugging_multiple_processes_in_a_Visual_Studio_solution"></a> Rozpocznij debugowanie wielu procesów w rozwiązaniu Visual Studio  
 Jeśli masz więcej niż jednego projektu w rozwiązaniu Visual Studio, która może działać niezależnie (projektów, które działały w osobnych procesach), można wybrać, które projekty uruchomieniu debugera.  
  
 ![Zmiana typu uruchamiania dla projektu](../debugger/media/dbg_execution_startmultipleprojects.png "DBG_Execution_StartMultipleProjects")  
  
####  <a name="BKMK_Change_the_startup_project"></a> Zmień projekt startowy  
 Aby zmienić projekt startowy rozwiązania, wybierz projekt w Eksploratorze rozwiązań, a następnie wybierz pozycję **Ustaw jako projekt startowy** z menu kontekstowego.  
  
####  <a name="BKMK_Start_a_specific_project_in_a_solution"></a> Uruchom określonego projektu w rozwiązaniu  
 Aby uruchomić projekt do rozwiązania bez zmieniania domyślny projekt startowy, wybierz projekt w Eksploratorze rozwiązań, a następnie wybierz pozycję **debugowania** z menu kontekstowego. Można wybrać **Start nowe wystąpienie** lub **krok do nowego wystąpienia**.  
  
 ![Powrót do początku](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [uruchamiać wiele procesów w rozwiązaniu programu VS, dołączyć do procesu, automatyczne uruchamianie procesu w debugerze](../debugger/debug-multiple-processes.md#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
 ![Powrót do początku](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [zawartości](#BKMK_Contents)  
  
####  <a name="BKMK_Start_multiple_projects_in_a_solution"></a> Uruchom wielu projektów w rozwiązaniu  
  
1.  Wybierz rozwiązanie w Eksploratorze rozwiązań, a następnie wybierz pozycję **właściwości** w menu kontekstowym.  
  
2.  Wybierz **wspólne właściwości**, **projekt startowy** na **właściwości** okno dialogowe.  
  
3.  Dla każdego projektu, który chcesz zmienić, wybierz **Start**, **uruchomienie bez debugowania**, lub **Brak**.  
  
 ![Powrót do początku](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [uruchamiać wiele procesów w rozwiązaniu programu VS, dołączyć do procesu, automatyczne uruchamianie procesu w debugerze](../debugger/debug-multiple-processes.md#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
 ![Powrót do początku](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [zawartości](#BKMK_Contents)  
  
###  <a name="BKMK_Attach_to_a_process"></a> Dołączanie do procesu  
 Debuger może również do *dołączyć* programy są uruchomione w procesach poza Visual Studio, w tym programy, które są uruchomione na urządzeniu zdalnym. Po dołączeniu do programu można używać debugera wykonywania poleceń, sprawdź stan programu i itd. Możliwość kontroli program może być ograniczona, w zależności od tego, czy program został skompilowany bez informacji o debugowaniu i czy masz dostęp do kodu źródłowego i czy kompilatora JIT środowiska uruchomieniowego języka wspólnego służy do śledzenia informacji o debugowaniu.  
  
 Zobacz [dołączyć do uruchamiania procesów](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md) Aby uzyskać więcej informacji.  
  
 **Dołączanie do procesu, który działa na komputerze lokalnym**  
  
 Kliknij przycisk **Debuguj > dołączyć do procesu**. Na **dołączyć do procesu** oknie dialogowym Wybierz proces z **dostępne procesy** listy, a następnie wybierz pozycję **Attach**.  
  
 ![Okno dialogowe procesu dołączania do](../debugger/media/dbg_attachtoprocessdlg.png "DBG_AttachToProcessDlg")  
  
 ![Powrót do początku](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [zawartości](#BKMK_Contents)  
  
###  <a name="BKMK_Automatically_start_an_process_in_the_debugger"></a> Automatyczne uruchamianie procesu w debugerze  
 Czasami może być konieczne debugowania kodu uruchamiania programu, który jest uruchamiana przez inny proces. Przykłady obejmują usługi i działania niestandardowego Instalatora. W tych scenariuszach możesz mieć uruchamiania debugera i dołączać automatycznie podczas uruchamiania aplikacji.  
  
1.  Uruchom Edytor rejestru (**regedit.exe**).  
  
2.  Przejdź do **HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\Image File Execution Options** folderu.  
  
3.  Wybierz folder do aplikacji, którą chcesz uruchomić w debugerze.  
  
     Jeśli nazwa aplikacji nie jest wymieniony jako folder podrzędny, wybierz **Image File Execution Options** , a następnie wybierz **nowy**, **klucza** w menu kontekstowym. Wybierz nowy klucz, wybierz **zmienić** menu skrótów, a następnie wprowadź nazwę aplikacji.  
  
4.  W menu kontekstowym w folderze aplikacji wybierz **nowy**, **wartość ciągu**.  
  
5.  Zmień nazwę nowej wartości z **nową wartość** do `debugger`.  
  
6.  W menu kontekstowym pozycji debugera, wybierz **Modyfikuj**.  
  
7.  W oknie dialogowym Edytowanie ciągu, wpisz `vsjitdebugger.exe` w **dane wartości** pole.  
  
     ![Ciąg, okno dialogowe Edytowanie](../debugger/media/dbg_execution_automaticstart_editstringdlg.png "DBG_Execution_AutomaticStart_EditStringDlg")  
  
 ![Automatyczne debugera Rozpocznij wprowadzanie w regedit.exe](../debugger/media/dbg_execution_automaticstart_result.png "DBG_Execution_AutomaticStart_Result")  
  
 ![Powrót do początku](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [zawartości](#BKMK_Contents)  
  
##  <a name="BKMK_Switch_processes__break_and_continue_execution__step_through_source"></a> Przełącz procesów, przerwanie i kontynuować działanie, kroków źródła  
  
-   [Przełączanie między procesami](#BKMK_Switch_between_processes)  
  
-   [Przerwij, kroku i kontynuować poleceń](#BKMK_Break__step__and_continue_commands)  
  
###  <a name="BKMK_Switch_between_processes"></a> Przełączanie między procesami  
 Możesz dołączyć do wielu procesów podczas debugowania, ale tylko jeden proces jest aktywny w debugerze w danym momencie. Można ustawić aktywne lub *bieżącego* procesów w pasku narzędzi debugowania lokalizacji lub **procesów** okna. Aby przełączyć między procesami, oba procesy musi być w trybie przerwania.  
  
 **Można ustawić bieżącego procesu**  
  
-   Na pasku narzędzi debugowania lokalizacji wybierz **procesu** Aby wyświetlić **procesu** pola listy. Wybierz proces, który chcesz wyznaczyć jako bieżącego procesu.  
  
     ![Przełączanie między procesami](../debugger/media/dbg_execution_switchbetweenmodules.png "DBG_Execution_SwitchBetweenModules")  
  
     Jeśli **debugowania lokalizacji** narzędzi nie jest widoczny, wybierz polecenie **narzędzia**, **Dostosuj**. Na **paski narzędzi** , wybierz pozycję **debugowania lokalizacji**.  
  
-   Otwórz **procesów** okna (skrót **Ctrl + Alt + Z**), Znajdź proces, który chcesz ustawić jako bieżący proces i kliknij ją dwukrotnie.  
  
     ![Okno procesów](../debugger/media/dbg_processeswindow.png "DBG_ProcessesWindow")  
  
     Bieżący proces jest oznaczona przez żółta strzałka.  
  
 Przełączanie do projektu ustawia ją bieżący proces do celów debugowania. Wszystkie okna debugera, które możesz wyświetlać wyświetli stan dla bieżącego procesu, a tylko bieżący proces wpływają na wszystkie polecenia wykonywania krokowego.  
  
 ![Powrót do początku](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [przełącznika procesów, przerwanie i kontynuować działanie, kroków źródła](../debugger/debug-multiple-processes.md#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
 ![Powrót do początku](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [zawartości](#BKMK_Contents)  
  
###  <a name="BKMK_Break__step__and_continue_commands"></a> Przerwij, kroku i kontynuować poleceń  
  
> [!NOTE]
>  Domyślnie podziału, kontynuować i poleceń debugera krok wpływają na wszystkie procesy, które są debugowane. Aby zmienić to zachowanie, zobacz [skonfigurować sposób wykonywania wielu procesów](#BKMK_Configure_the_execution_behavior_of_multiple_processes)  
  
||||  
|-|-|-|  
|**polecenie**|**Przerwij wszystkie procesy w przypadku przerwania jednego procesu**<br /><br /> Checked (ustawienie domyślne)|**Przerwij wszystkie procesy w przypadku przerwania jednego procesu**<br /><br /> Wyczyszczone|  
|**Debugowanie** menu:<br /><br /> -   **Przerwij wszystkie**|Przerwij wszystkie procesy.|Przerwij wszystkie procesy.|  
|**Debugowanie** menu:<br /><br /> -   **Kontynuuj**|Wznawianie wszystkich procesów.|Wznawianie wszystkich procesów wstrzymane.|  
|**Debugowanie** menu:<br /><br /> -   **Wkrocz**<br />-   **Przekrocz**<br />-   **Wyjdź**|Wszystkie procesy są uruchamiane podczas bieżącej kroki tej procedury.<br /><br /> Następnie Przerwij wszystkie procesy.|Bieżący kroki tej procedury.<br /><br /> Wznawia zawieszone procesy.<br /><br /> Nadal uruchomione procesy.|  
|**Debugowanie** menu:<br /><br /> -   **Krok do bieżącego procesu**<br />-   **Przekrocz nad bieżącego procesu**<br />-   **Wyjdź z bieżącego procesu**|Brak|Bieżący kroki tej procedury.<br /><br /> Inne procesy Obsługa stanu istniejącego (wstrzymany lub systemem).|  
|Okno źródła<br /><br /> -   **Punkt przerwania**|Przerwij wszystkie procesy.|Tylko źródła okna podziału procesu.|  
|Menu kontekstowe okna źródła:<br /><br /> -   **Uruchom do kursora**<br /><br /> Okno źródła musi być w bieżącym procesie.|Wszystkie procesy uruchamiane podczas procesu okna źródła następnie podziały i uruchamia do kursora.<br /><br /> Następnie przerwać inne procesy.|Uruchamia proces okna źródła do kursora.<br /><br /> Inne procesy Obsługa stanu istniejącego (wstrzymany lub systemem).|  
|**Procesy** menu kontekstowe okna:<br /><br /> -   **Proces podziału**|Brak|Wybrany proces podziału.<br /><br /> Inne procesy Obsługa stanu istniejącego (wstrzymany lub systemem).|  
|**Procesy** menu kontekstowe okna:<br /><br /> -   **Kontynuuj proces**|Brak|Wznawia wybrany proces.<br /><br /> Inne procesy Obsługa stanu istniejącego (wstrzymany lub systemem).|  
  
 ![Powrót do początku](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [przełącznika procesów, przerwanie i kontynuować działanie, kroków źródła](../debugger/debug-multiple-processes.md#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
 ![Powrót do początku](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [zawartości](#BKMK_Contents)  
  
##  <a name="BKMK_Stop_debugging__terminate_or_detach_from_processes"></a> Zatrzymaj debugowanie, przerwanie lub odłączyć od procesów  
  
-   [Zatrzymaj, przerwanie i odłączyć poleceń](#BKMK_Stop__terminate__and_detach_commands)  
  
 Domyślnie po wybraniu **debugowania**, **Zatrzymaj debugowanie** wiele procesów są otwarte w debugerze, debuger przerywa lub odłącza od wszystkich procesów w zależności od tego, jak proces został otwarty w Debuger:  
  
-   Jeśli bieżący proces został uruchomiony w debugerze, ten proces zostanie zakończony.  
  
-   Jeśli Debuger jest dołączony do bieżącego procesu, debuger odłączenie od procesu i pozostawia uruchamianie procesu.  
  
 Na przykład jeśli uruchomić debugowanie procesu z rozwiązania Visual Studio, Dołącz do innego procesu, który jest już uruchomiona, a następnie wybierz **Zatrzymaj debugowanie**, sesji debugowania kończy proces, który został uruchomiony w programie Visual Studio zostanie zakończony, gdy proces, który można dołączyć pozostaje uruchomiona. Aby kontrolować sposób, który należy zatrzymać debugowanie, można użyć poniższych procedur.  
  
> [!NOTE]
>  **Przerwij wszystkie procesy w przypadku przerwania jednego procesu** opcji nie wpływa na zatrzymanie debugowania lub przerywanie i odłączanie od procesów.  
  
 **Aby zmienić Zatrzymaj debugowanie wpływ poszczególnych procesów**  
  
-   Otwórz **procesów** okna (skrót **Ctrl + Alt + Z**). Wybierz proces, a następnie zaznacz lub wyczyść **odłączyć po zatrzymaniu debugowania** pole wyboru.  
  
###  <a name="BKMK_Stop__terminate__and_detach_commands"></a> Zatrzymaj, przerwanie i odłączyć poleceń  
  
|||  
|-|-|  
|**polecenie**|**Opis**|  
|**Debugowanie** menu:<br /><br /> -   **Zatrzymaj debugowanie**|Chyba, że zachowanie zmieni się przez **procesów** okna **odłączyć podczas debugowania zatrzymuje** opcji:<br /><br /> 1.  Procesy uruchomione przez debuger są zakończone.<br />2.  Procesy dołączone są odłączone z debugera.|  
|**Debugowanie** menu:<br /><br /> -   **Zakończ wszystkie**|Wszystkie procesy zostały zakończone.|  
|**Debugowanie** menu:<br /><br /> -   **Odłącz wszystkich**|Debuger odłącza od wszystkich procesów.|  
|**Procesy** menu kontekstowe okna:<br /><br /> -   **Odłączanie procesu**|Debuger odłączenie od wybranego procesu.<br /><br /> Inne procesy Obsługa stanu istniejącego (wstrzymany lub systemem).|  
|**Procesy** menu kontekstowe okna:<br /><br /> -   **Zakończenie procesu**|Wybrany proces zostanie zakończony.<br /><br /> Inne procesy Obsługa stanu istniejącego (wstrzymany lub systemem).|  
|**Procesy** menu kontekstowe okna:<br /><br /> -   **Odłącz podczas debugowania zatrzymuje**|Włącza zachowanie **debugowania**, **Zatrzymaj debugowanie** dla wybranego procesu:<br /><br /> -Zaznaczone: Debuger odłączenie od procesu.<br />-Wyczyszczone: Proces jest zakończony.|  
  
 ![Powrót do początku](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [zatrzymać debugowanie, przerwanie lub odłączyć od procesów](../debugger/debug-multiple-processes.md#BKMK_Stop_debugging__terminate_or_detach_from_processes)  
  
 ![Powrót do początku](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [zawartości](#BKMK_Contents)  
  
## <a name="see-also"></a>Zobacz też  
 [Określ symboli (.pdb) i pliki źródłowe](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Dołączanie do uruchomionego procesu](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Nawigowanie po kodzie za pomocą debugera](../debugger/navigating-through-code-with-the-debugger.md)   
 [Just-In-Time Debugging](../debugger/just-in-time-debugging-in-visual-studio.md)   
 [Debuguj aplikacje wielowątkowe](../debugger/debug-multithreaded-applications-in-visual-studio.md)