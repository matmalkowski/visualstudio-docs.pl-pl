---
title: 'Porady: dołączanie profilera do autonomicznej aplikacji natywnej i zbieranie statystyk aplikacji przy użyciu wiersza polecenia | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: df44fe42-281b-4398-b3fc-277b62ae41f1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: c9ef8415aaa9a5004528841c2fc9c466a8374459
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-attach-the-profiler-to-a-native-stand-alone-application-and-collect-application-statistics-by-using-the-command-line"></a>Porady: dołączanie profilera do autonomicznej aplikacji natywnej i zbieranie statystyk aplikacji przy użyciu wiersza polecenia
W tym temacie opisano sposób użycia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzia wiersza polecenia narzędzi profilowania dołączanie profilera do aplikacji autonomicznej uruchomiona natywnego (klient) i zbieranie statystyk wydajności za pomocą metody pobierania próbek.  
  
> [!NOTE]
>  Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagane znaczących zmian w sposobie profilera Visual Studio zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows wymagają również nowe techniki kolekcji. Zobacz [narzędzi wydajności w przypadku aplikacji systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
> [!NOTE]
>  Narzędzia wiersza polecenia narzędzi profilowania znajdują się w podkatalogu narzędzia \Team Tools\Performance [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] katalogu instalacyjnego. Na komputerach 64-bitowych zarówno 64-bitowe i 32-bitowe wersje narzędzia są dostępne. Za pomocą narzędzi wiersza polecenia profilera, możesz dodać ścieżkę narzędzia do zmiennej środowiskowej PATH w oknie wiersza polecenia lub dodać go do samo polecenie. Aby uzyskać więcej informacji, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Gdy profiler jest dołączony do aplikacji, można wstrzymywać i wznawiać zbierania danych. Aby zakończyć sesję profilowania, profilera nie musi być dołączony do aplikacji i profilera muszą zostać jawnie wyłączone.  
  
## <a name="attach-the-profiler"></a>Dołączanie profilera  
 Dołączanie profilera do aplikacji docelowej przy użyciu profilera, należy użyć **VSPerfCmd/start** i **/ dołączyć** opcje inicjowania profilera i Dołącz do aplikacji docelowej. Można określić **/start** i **/ dołączyć** i odpowiednie opcje w jednym wierszu polecenia. Można również dodać **/globaloff** opcję, aby wstrzymać zbieranie danych na początku aplikacji docelowej. Następnie należy użyć **/globalon** zacząć zbierać dane.  
  
#### <a name="to-attach-the-profiler-to-a-running-net-framework-application"></a>Aby dołączanie profilera do uruchomionej aplikacji .NET Framework  
  
1.  Otwórz okno wiersza polecenia.  
  
2.  Uruchom profilera. Wpisz:  
  
     **/ OUTPUT /start:sample VSPerfCmd:** `OutputFile` [`Options`]  
  
    -   [/Start](../profiling/start.md)**: Przykładowe** opcji inicjowania profilera.  
  
    -   [/Output](../profiling/output.md)**:** `OutputFile` jest wymagany w przypadku opcji **/start**. `OutputFile` Określa nazwę i lokalizację profilowania pliku danych (Vsp).  
  
     Można użyć dowolnego z następujących opcji z **/start:sample** opcji.  
  
    |Opcja|Opis|  
    |------------|-----------------|  
    |[/ User](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName`|Określa nazwę domeny i nazwę konta, który jest właścicielem PROFILOWANEGO procesu. Ta opcja jest wymagana tylko wtedy, gdy proces jest uruchomiony jako użytkownik innego niż zalogowanego użytkownika. Właściciel procesu znajduje się w kolumnie Nazwa użytkownika na karcie Procesy Menedżera zadań systemu Windows.|  
    |[/crosssession](../profiling/crosssession.md)|Włącza profilowanie procesów w innych sesji. Ta opcja jest wymagana, jeśli aplikacja ASP.NET działa w innej sesji. Identyfikator sesji jest wyświetlane w kolumnie Identyfikator sesji, na karcie Procesy Menedżera zadań systemu Windows. **/CS** może być określony jako skrót **/crosssession**.|  
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Określa licznik wydajności systemu Windows, które będą zbierane podczas profilowania.|  
    |[/automark](../profiling/automark.md) **:** `Interval`|Za pomocą **/wincounter** tylko. Określa liczbę milisekund między zdarzeniami kolekcji liczników wydajności systemu Windows. Domyślna to 500 ms.|  
    |[/Events](../profiling/events-vsperfcmd.md) **:** `Config`|Określa zdarzenia funkcji Śledzenie zdarzeń systemu Windows (), które mają być zbierane podczas profilowania. Zdarzenia ETW są gromadzone w pliku oddzielne (ETL).|  
  
3.  Dołączanie profilera do aplikacji docelowej. Wpisz:  
  
     **VSPerfCmd**[/ dołączyć](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [`Sample Event`]    
  
     `PID` Określa identyfikator procesu aplikacji docelowej. `ProcessName` Określa nazwę procesu. Należy pamiętać, że jeśli określisz `ProcessName` i działa wiele procesów, które mają taką samą nazwę, są nieprzewidywalne wyniki. Identyfikatory wszystkich procesów uruchomionych procesów można wyświetlić w Menedżerze zadań systemu Windows.  
  
     Domyślnie wydajności, dane są pobierane co zegara procesora nie zostało zatrzymane 10 000 000 cykle. Jest to około 100 razy co sekundę 1GH procesora. Można określić jedną z następujących opcji, aby zmienić interwał cyklu zegara lub określić zdarzenia różnych próbkowania.  
  
    |Zdarzenie próbkowania|Opis|  
    |------------------|-----------------|  
    |[/ Timer](../profiling/timer.md) **:** `Interval`|Powoduje interwał próbkowania liczby cykli zegara nie zostało zatrzymane, które są określone przez `Interval`.|  
    |[PF](../profiling/pf.md)[**:**`Interval`]|Zmiany zdarzenie próbkowania błędów strony. Jeśli `Interval` jest określony, ustawia liczbę błędów stron między próbkami. Domyślna to 10.|  
    |[sys](../profiling/sys-vsperfcmd.md) [**:**`Interval`]|Zdarzenie próbkowania wywołań systemowych zmiany z procesu jądra systemu operacyjnego (syscalls). Jeśli `Interval` jest określony, ustawia liczbę wywołań między próbkami. Domyślna to 10.|  
    |[/ licznika](../profiling/counter.md) **:** `Config`|Zmiany zdarzenie próbkowania i interwał licznika wydajności procesora i interwał, który jest określony w `Config`.|  
  
## <a name="controlling-data-collection"></a>Kontrolowanie zbierania danych  
 Uruchomionej aplikacji docelowej, można użyć opcji VSPerfCmd.exe go uruchamiać i zatrzymywać przy zapisywaniu danych w pliku danych profilera. Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonania programu, takie jak uruchamianie lub zamykanie aplikacji.  
  
#### <a name="to-start-and-stop-data-collection"></a>Aby uruchomić i zatrzymać zbieranie danych  
  
-   Następujące pary **VSPerfCmd** opcje uruchamiania i zatrzymywania zbierania danych. Określ opcję każdego w osobnym wierszu polecenia. Włączenie funkcji zbierania danych można włączać i wyłączać wiele razy.  
  
    |Opcja|Opis|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Uruchamia (**/globalon**) lub zatrzymania (**/globaloff**) zbierania danych dla wszystkich procesów.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Uruchamia (**/processon**) lub zatrzymania (**/processoff**) zbierania danych dla procesu, który jest określony przez `PID`.|  
    |[/ dołączyć](../profiling/attach.md) **:** `PID` [/ detach](../profiling/detach.md)|**/ dołączyć** rozpoczyna zbieranie danych przez proces określony przez `PID`. **/ detach** zatrzymania zbierania danych dla wszystkich procesów.|  
  
## <a name="ending-the-profiling-session"></a>Kończenie sesji profilowania  
 Aby zakończyć sesję profilowania, profilera musi być odłączony od wszystkich procesów PROFILOWANEGO i profilera muszą zostać jawnie wyłączone. Można odłączyć profilera z aplikacji, która była profilowany przy użyciu metody próbkowania przez zamknięcie aplikacji, przez wywołanie **VSPerfCmd / detach** opcji. Następnie wywołaj **VSPerfCmd/shutdown** opcję, aby wyłączyć profilera i zamknij plik danych profilowania. **VSPerfClrEnv / Wyłącz** polecenie czyści profilowania zmiennych środowiskowych.  
  
#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania  
  
1.  Wykonaj jedną z poniższych czynności, aby odłączyć profilera z aplikacji docelowej.  
  
    -   Typ **VSPerfCmd / detach**  
  
         —lub—  
  
    -   Zamknij aplikacji docelowej.  
  
2.  Zamknij profilera. Wpisz:  
  
     **VSPerfCmd** [ /shutdown](../profiling/shutdown.md)  
  
3.  (Opcjonalnie) Wyczyść profilowania zmiennych środowiskowych. Wpisz:  
  
     **VSPerfClrEnv / Wyłącz**  
  
## <a name="see-also"></a>Zobacz też  
 [Profilowanie aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Widok danych metody próbkowania](../profiling/profiler-sampling-method-data-views.md)