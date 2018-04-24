---
title: 'Porady: dołączanie profilera do aplikacji sieci Web ASP.NET w celu zbierania danych pamięci przy użyciu wiersza polecenia | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: d608f85a-41ae-4ca7-85e6-b96624dbc83c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: e45eb3e1ac874343de5a3076a62b89e541f20d75
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line"></a>Porady: dołączanie profilera do aplikacji sieci Web ASP.NET w celu zbierania danych pamięci przy użyciu wiersza polecenia
W tym temacie opisano sposób użycia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzia profilowania wiersza polecenia narzędzia umożliwiające dołączanie profilera do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] sieci Web aplikacji i zbieranie danych dotyczących liczby i rozmiaru alokacji pamięci .NET Framework. Może również zbierać dane dotyczące okresu istnienia obiektów pamięci .NET Framework.  
  
> [!NOTE]
>  Narzędzia wiersza polecenia narzędzi profilowania znajdują się w podkatalogu narzędzia \Team Tools\Performance [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] katalogu instalacyjnego. Na komputerach 64-bitowych zarówno 64-bitowe i 32-bitowe wersje narzędzia są dostępne. Za pomocą narzędzi wiersza polecenia profilera, możesz dodać ścieżkę narzędzia do zmiennej środowiskowej PATH w oknie wiersza polecenia lub dodać go do samo polecenie. Aby uzyskać więcej informacji, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Do zbierania danych dotyczących wydajności z [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci Web, należy użyć [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) narzędzia, aby zainicjować zmienne środowiskowe odpowiednie na komputerze, który jest hostem [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci Web. Należy ponownie uruchomić komputer, aby skonfigurować serwer sieci Web do profilowania.  
  
 Następnie należy użyć [VSPerfCmd.exe](../profiling/vsperfcmd.md) narzędzia dołączanie profilera do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] proces roboczy, który jest hostem witryny sieci Web. Gdy profiler jest dołączony do aplikacji, można wstrzymywać i wznawiać zbierania danych.  
  
 Aby zakończyć sesję profilowania, profilera nie musi być dołączony do aplikacji i profilera muszą zostać jawnie wyłączone. W większości przypadków zaleca się czyszczenie profilowania zmienne środowiskowe z końcem sesji.  
  
## <a name="attaching-the-profiler"></a>Dołączanie profilera  
  
#### <a name="to-attach-the-profiler-to-an-aspnet-web-application"></a>Aby dołączanie profilera do aplikacji sieci Web ASP.NET  
  
1.  Otwórz okno wiersza polecenia.  
  
2.  Inicjowanie profilowania zmiennych środowiskowych. Wpisz:  
  
     **VSPerfClrEnv** {**/globalsamplegc** &#124; **/globalsamplegclife**} [**/samplelineoff**]  
  
    -   Opcje **/globalsamplegc** i **/globalsamplegclife** Określ typ pamięci dane do zebrania.  
  
         Określ jeden i tylko jeden z następujących opcji.  
  
        |Opcja|Opis|  
        |------------|-----------------|  
        |**/globalsamplegc**|Umożliwia zbieranie danych alokacji pamięci.|  
        |**/globalsamplegclife**|Umożliwia zbieranie danych o okresie istnienia obiektu i danych alokacji pamięci.|  
  
    -   Opcja **/samplelineoff** wyłącza przypisania zebranych danych do wierszy kodu określonego źródła. Jeśli ta opcja jest określony, dane są przypisane na poziomie funkcji.  
  
3.  Uruchom ponownie komputer, aby ustawić dla nowej konfiguracji środowiska.  
  
4.  Otwórz okno wiersza polecenia. Jeśli to konieczne, należy ustawić profilera zmiennej środowiska ścieżki.  
  
5.  Uruchom profilera. Wpisz:  
  
     **VSPerfCmd**[/start](../profiling/start.md) **: Przykładowe**[/output](../profiling/output.md) **:** `OutputFile` [`Options`]      
  
    -   **/Start:sample** opcji inicjowania profilera.  
  
    -   **/Output:** `OutputFile` jest wymagany w przypadku opcji **/start**. `OutputFile` Określa nazwę i lokalizację profilowania pliku danych (Vsp).  
  
     Można użyć dowolnego z następujących opcji z **/start:sample** opcji.  
  
    > [!NOTE]
    >  **User** i **/crosssession** opcje są zwykle wymagane dla aplikacji ASP.NET.  
  
    |Opcja|Opis|  
    |------------|-----------------|  
    |[/ User](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName`|Określa nazwę domeny i użytkownika konta, który jest właścicielem proces roboczy programu ASP.NET. Ta opcja jest wymagana, jeśli proces jest uruchomiony jako użytkownik innego niż zalogowanego użytkownika. Właściciel procesu znajduje się w kolumnie Nazwa użytkownika na karcie Procesy Menedżera zadań systemu Windows.|  
    |[/crosssession](../profiling/crosssession.md)|Włącza profilowanie procesów w innych sesji logowania. Ta opcja jest wymagana, jeśli aplikacja ASP.NET działa w innej sesji. Identyfikator sesji jest wyświetlane w kolumnie Identyfikator sesji, na karcie Procesy Menedżera zadań systemu Windows. **/CS** może być określony jako skrót **/crosssession**.|  
    |[/waitstart](../profiling/waitstart.md) [**:**`Interval`]|Określa liczbę sekund oczekiwania profilera zainicjować przed zwraca błąd. Jeśli `Interval` nie zostanie określony, profilera oczekiwania przez czas nieokreślony. Domyślnie **/start** natychmiast kończy pracę.|  
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Określa licznik wydajności systemu Windows, które będą zbierane podczas profilowania.|  
    |[/automark](../profiling/automark.md) **:** `Interval`|Za pomocą **/wincounter** tylko. Określa liczbę milisekund między zdarzeniami kolekcji liczników wydajności systemu Windows. Domyślna to 500 ms.|  
    |[/Events](../profiling/events-vsperfcmd.md) **:** `Config`|Określa zdarzenia funkcji Śledzenie zdarzeń systemu Windows (), które mają być zbierane podczas profilowania. Zdarzenia ETW są gromadzone w pliku oddzielne (ETL).|  
  
6.  Uruchom [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci Web w typowy sposób.  
  
7.  Dołączanie profilera do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] proces roboczy. Wpisz:  
  
     **VSPerfCmd**[/ dołączyć](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [[/targetclr](../profiling/targetclr.md)**:**`Version`]    
  
    -   Identyfikator procesu `(PID)` Określa identyfikator procesu lub nazwy procesu [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] proces roboczy. Identyfikatory wszystkich procesów uruchomionych procesów można wyświetlić w Menedżerze zadań systemu Windows.  
  
    -   **/targetclr:** `Version` Określa wersję środowisko uruchomieniowe języka wspólnego (CLR) do profilu po załadowaniu więcej niż jedną wersję środowiska uruchomieniowego w aplikacji.  
  
## <a name="controlling-data-collection"></a>Kontrolowanie zbierania danych  
 Gdy aplikacja jest uruchomiona, można kontrolować zbierania danych przez uruchamianie i zatrzymywanie zapisywanie danych w pliku danych profilera przy użyciu **VSPerfCmd.exe** opcje. Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonania programu, takie jak uruchamianie lub zamykanie aplikacji.  
  
#### <a name="to-start-and-stop-data-collection"></a>Aby uruchomić i zatrzymać zbieranie danych  
  
-   Następujące pary **VSPerfCmd** opcje uruchamiania i zatrzymywania zbierania danych. Określ opcję każdego w osobnym wierszu polecenia. Włączenie funkcji zbierania danych można włączać i wyłączać wiele razy.  
  
    |Opcja|Opis|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Uruchamia (**/globalon**) lub zatrzymania (**/globaloff**) zbierania danych dla wszystkich procesów.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Uruchamia (**/processon**) lub zatrzymania (**/processoff**) zbierania danych przez proces określony przez `PID`.|  
    |**/ dołączyć:**{`PID`&#124;`ProcName`} [/ detach](../profiling/detach.md)[**:**{`PID`&#124;:`ProcName`}]|**/ dołączyć** rozpoczyna zbieranie danych dla procesu, który jest określony przez identyfikator procesu lub nazwy procesu. **/ detach** zatrzymuje zbieranie danych dla określonego procesu lub dla wszystkich procesów, jeśli nie określono określonego procesu.|  
  
## <a name="ending-the-profiling-session"></a>Kończenie sesji profilowania  
 Aby zakończyć sesję profilowania, profiler musi zostać odłączone od aplikacji sieci Web. Można zatrzymać zbieranie danych z aplikacji, która jest profilowane za pomocą metody pobierania próbek przez ponowne uruchomienie [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] procesu roboczego proces lub przez wywołanie metody **VSPerfCmd / detach** opcji. Następnie wywołaj **VSPerfCmd** [/shutdown](../profiling/shutdown.md) opcję, aby wyłączyć profilera i zamknij plik danych profilowania. **VSPerfClrEnv /globaloff** polecenie usuwa profilowania zmiennych środowiskowych, ale konfiguracja systemu nie zostanie zresetowana do ponownego uruchomienia komputera.  
  
#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania  
  
1.  Wykonaj jedną z poniższych czynności, aby odłączyć profilera z aplikacji docelowej:  
  
    -   Typ **VSPerfCmd** [/ detach](../profiling/detach.md)  
  
         —lub—  
  
    -   Zamknij [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] proces roboczy. Wpisz:  
  
     **Polecenie IISReset/Stop**  
  
2.  Zamknij profilera. Wpisz:  
  
     **VSPerfCmd/shutdown**  
  
3.  (Opcjonalnie) Wyczyść profilowania zmiennych środowiskowych. Wpisz:  
  
     **VSPerfCmd /globaloff**  
  
4.  Uruchom ponownie komputer. Jeśli to konieczne, uruchom ponownie usługi Internet Information Services (IIS). Wpisz:  
  
     **Polecenie IISReset/Start**  
  
## <a name="see-also"></a>Zobacz też  
 [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Widoki danych pamięci .NET](../profiling/dotnet-memory-data-views.md)