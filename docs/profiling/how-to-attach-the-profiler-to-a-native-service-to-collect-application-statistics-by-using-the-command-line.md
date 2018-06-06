---
title: 'Porady: dołączanie profilera do usługi natywnej i zbieranie statystyk aplikacji przy użyciu wiersza polecenia | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: f783817f-77a0-4eb8-985b-ec3b77eadc42
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 5c40350019d0878893568977df6db88c30fdc734
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2018
ms.locfileid: "34764859"
---
# <a name="how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line"></a>Porady: dołączanie profilera do usługi natywnej i zbieranie statystyk aplikacji przy użyciu wiersza polecenia
W tym artykule opisano sposób użycia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzia wiersza polecenia narzędzi profilowania dołączanie profilera do usługi natywnej i zbieranie statystyk wydajności za pomocą metody pobierania próbek.  
  
> [!NOTE]
>  Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagane znaczących zmian w sposobie profilera Visual Studio zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows wymagają również nowe techniki kolekcji. Zobacz [narzędzi wydajności w przypadku aplikacji systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
> [!NOTE]
>  Narzędzia wiersza polecenia narzędzi profilowania znajdują się w *narzędzia \Team Tools\Performance* podkatalog [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] katalogu instalacyjnego. Na komputerach 64-bitowych zarówno 64-bitowe i 32-bitowe wersje narzędzia są dostępne. Za pomocą narzędzi wiersza polecenia profilera, możesz dodać ścieżkę narzędzia do zmiennej środowiskowej PATH w oknie wiersza polecenia lub dodać go do samo polecenie. Aby uzyskać więcej informacji, zobacz [Określ ścieżkę do narzędzia wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Profiler jest dołączony do usługi, można wstrzymywać i wznawiać zbierania danych.  
  
 Aby zakończyć sesję profilowania, profilera musi być odłączony od usługi i profilera muszą zostać jawnie wyłączone.  
  
## <a name="start-the-application-with-the-profiler"></a>Uruchom aplikację przy użyciu profilera  
 Dołączanie profilera do usługi natywnej, należy użyć **VSPerfCmd.exe**[/start](../profiling/start.md) i [/ dołączyć](../profiling/attach.md) opcje inicjowania profilera i dołączenie go do aplikacji docelowej. Można określić **/start** i **/ dołączyć** i odpowiednie opcje w jednym wierszu polecenia. Można również dodać [/globaloff](../profiling/globalon-and-globaloff.md) opcję, aby wstrzymać zbieranie danych na początku aplikacji docelowej. Następnie można użyć [/globalon](../profiling/globalon-and-globaloff.md) do rozpoczęcia zbierania danych.  
  
#### <a name="to-attach-the-profiler-to-a-native-service"></a>Aby dołączanie profilera do usługi natywnej  
  
1.  W razie potrzeby uruchom usługę.  
  
2.  Otwórz okno wiersza polecenia.  
  
3.  Uruchom profilera. Wpisz:  
  
     **VSPerfCmd /start:sample**[/output](../profiling/output.md) **:** `OutputFile` [`Options`]  
  
    -   **/Start:sample** opcji inicjowania profilera.  
  
    -   **/Output:** `OutputFile` jest wymagany w przypadku opcji **/start**. `OutputFile` Określa nazwę i lokalizację danych profilowania (. *Vsp*) pliku.  
  
     Można użyć dowolnego z następujących opcji z **/start:sample** opcji.  
  
    > [!NOTE]
    >  **User** i **/crosssession** opcje są zwykle wymagane dla usług.  
  
    |Opcja|Opis|  
    |------------|-----------------|  
    |[/ User](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName`|Określa nazwę domeny i nazwę konta, który jest właścicielem PROFILOWANEGO procesu. Ta opcja jest wymagana tylko wtedy, gdy proces jest uruchomiony jako użytkownik innego niż zalogowanego użytkownika. Właściciel procesu znajduje się w kolumnie Nazwa użytkownika na karcie Procesy Menedżera zadań systemu Windows.|  
    |[/crosssession](../profiling/crosssession.md)|Włącza profilowanie procesów w innych sesji. Ta opcja jest wymagana, jeśli aplikacja jest uruchomiona w innej sesji. Identyfikator sesji jest wymieniony w kolumnie Identyfikator sesji, na karcie Procesy Menedżera zadań systemu Windows. **/CS** może być określony jako skrót **/crosssession**.|  
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Określa licznik wydajności systemu Windows, które będą zbierane podczas profilowania.|  
    |[/automark](../profiling/automark.md) **:** `Interval`|Za pomocą **/wincounter** tylko. Określa liczbę milisekund między zdarzeniami kolekcji liczników wydajności systemu Windows. Domyślna to 500 ms.|  
    |[/Events](../profiling/events-vsperfcmd.md) **:** `Config`|Określa zdarzenia funkcji Śledzenie zdarzeń systemu Windows (), które mają być zbierane podczas profilowania. Zdarzenia ETW są gromadzone w pliku oddzielne (ETL).|  
  
4.  Dołączanie profilera do usługi. Wpisz:  
  
     **VSPerfCmd / dołączyć:** `PID` [`Sample Event`]  
  
     `PID` Określa identyfikator procesu aplikacji docelowej. Identyfikatory wszystkich procesów uruchomionych procesów można wyświetlić w Menedżerze zadań systemu Windows.  
  
     Domyślnie wydajności, dane są pobierane co zegara procesora nie zostało zatrzymane 10 000 000 cykle. Jest to mniej więcej co 10 sekund na procesorze 1GH. Można określić jedną z następujących opcji, aby zmienić interwał cyklu zegara lub określić zdarzenia różnych próbkowania.  
  
    |Zdarzenie próbkowania|Opis|  
    |------------------|-----------------|  
    |[/ Timer](../profiling/timer.md) **:** `Interval`|Zmiany liczby cykli zegara nie zostało zatrzymane, określony przez interwał próbkowania `Interval`.|  
    |[PF](../profiling/pf.md)[**:**`Interval`]|Zmiany zdarzenie próbkowania błędów strony. Jeśli `Interval` jest określony, ustawia liczbę błędów stron między próbkami. Domyślna to 10.|  
    |[sys](../profiling/sys-vsperfcmd.md) [**:**`Interval`]|Zdarzenie próbkowania wywołań systemowych zmiany z procesu jądra systemu operacyjnego (syscalls). Jeśli `Interval` jest określony, ustawia liczbę wywołań między próbkami. Domyślna to 10.|  
    |[/ licznika](../profiling/counter.md) **:** `Config`|Zmiany zdarzenie próbkowania i interwał licznika wydajności procesora i interwał określony we `Config`.|  
  
## <a name="control-data-collection"></a>Sterowanie zbieraniem danych  
 Po uruchomieniu aplikacji docelowej można użyć *VSPerfCmd.exe* opcji, aby uruchomić i zatrzymać przy zapisywaniu danych w pliku danych profilera. Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonania programu, takie jak uruchamianie lub zamykanie aplikacji.  
  
#### <a name="to-start-and-stop-data-collection"></a>Aby uruchomić i zatrzymać zbieranie danych  
  
-   Następujące pary **VSPerfCmd** opcje uruchamiania i zatrzymywania zbierania danych. Określ opcję każdego w osobnym wierszu polecenia. Włączenie funkcji zbierania danych można włączać i wyłączać wiele razy.  
  
    |Opcja|Opis|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Uruchamia (**/globalon**) lub zatrzymania (**/globaloff**) zbierania danych dla wszystkich procesów.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Uruchamia (**/processon**) lub zatrzymania (**/processoff**) zbierania danych przez proces określony przez identyfikator procesu (`PID`).|  
    |**/ dołączyć:** {`PID`&#124;`ProcName`} [/ detach](../profiling/detach.md)[: {`PID`&#124;`ProcName`}]|**/ dołączyć** rozpoczyna zbieranie danych przez proces określony przez identyfikator procesu lub nazwy procesu. **/ detach** zatrzymuje zbieranie danych dla określonego procesu lub dla wszystkich procesów, jeśli nie określono procesu.|  
  
## <a name="end-the-profiling-session"></a>Kończenie sesji profilowania  
 Aby zakończyć sesję profilowania, profilera musi być odłączony od usługi i następnie jawnie zamknięty. Można odłączyć usługi natywnej i który jest poddawany profilowaniu za pomocą metody pobierania próbek, zatrzymując usługę lub poprzez wywołanie **VSPerfCmd / detach** opcji. Następnie wywołaj **VSPerfCmd** [/shutdown](../profiling/shutdown.md) opcję, aby wyłączyć profilera i zamknij plik danych profilowania.  
  
#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania  
  
1.  Wykonaj jedną z następujących czynności, aby odłączyć profilera z aplikacji docelowej:  
  
    -   Zatrzymaj usługę.  
  
         —lub—  
  
    -   Typ **VSPerfCmd / detach**  
  
2.  Zamknij profilera. Wpisz:  
  
     **VSPerfCmd/shutdown**  
  
## <a name="see-also"></a>Zobacz także  
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)   
 [Widok danych metody próbkowania](../profiling/profiler-sampling-method-data-views.md)