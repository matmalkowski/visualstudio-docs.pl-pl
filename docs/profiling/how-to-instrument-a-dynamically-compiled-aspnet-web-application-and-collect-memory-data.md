---
title: 'Porady: Instrumentacja dynamicznie skompilowanej sieci Web ASP.NET aplikacji i zbieranie danych pamięci przy użyciu wiersza polecenia profilera | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 2cdd9903-39db-47e8-93dd-5e6a21bc3435
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 498eef4bac0a3f12735eccea2a15a5f4ab5975eb
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line"></a>Porady: instrumentacja dynamicznie skompilowanej aplikacji sieci Web ASP.NET i zbieranie danych pamięci przy użyciu wiersza polecenia profilera
W tym temacie opisano sposób użycia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] profilowanie wiersza polecenia narzędzi do gromadzenia szczegółowych .NET pamięci alokacji i obiekt okres istnienia danych dynamicznie skompilowanej [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci Web przy użyciu metoda profilowania instrumentacji.  
  
> [!NOTE]
>  Narzędzia wiersza polecenia narzędzi profilowania znajdują się w podkatalogu narzędzia \Team Tools\Performance [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] katalogu instalacyjnego. Na komputerach 64-bitowym zarówno w przypadku 64-bitowych, jak i 32-bitowe wersje narzędzia są dostępne. Za pomocą narzędzi wiersza polecenia profilera, możesz dodać ścieżkę narzędzia do zmiennej środowiskowej PATH w oknie wiersza polecenia lub dodać go do samo polecenie. Aby uzyskać więcej informacji, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Aby zbierać dane dotyczące wydajności z [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci Web, można zmodyfikować pliku web.config aplikacji docelowej, aby włączyć [VSInstr.exe](../profiling/vsinstr.md) narzędzia Instrumentacja dynamicznie skompilowanej aplikacji plików. Następnie należy użyć [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) narzędzie w celu skonfigurowania serwera obsługującego [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci Web i włączyć .NET pamięci profilowanie przez ustawienie zmiennych środowiskowych odpowiednie i uruchom ponownie komputer.  
  
 Aby zbierać dane, uruchom profilera, a następnie uruchom aplikacji docelowej. Profiler jest dołączony do aplikacji, można wstrzymywać i wznawiać zbierania danych. Po zebraniu danych, zamknij aplikację, Zamknij proces roboczy usług Internet Information Services (IIS) i następnie wyłącz profilera.  
  
 Po zakończeniu pracy profilowania przywracania pliku web.config i serwer sieci Web do oryginalnego stanu.  
  
## <a name="configuring-the-aspnet-web-application-and-the-web-server"></a>Konfigurowanie aplikacji sieci Web ASP.NET i serwera sieci Web  
  
#### <a name="to-configure-the-aspnet-web-application-and-the-web-server"></a>Aby skonfigurować serwer sieci Web i aplikacji sieci Web ASP.NET  
  
1.  Modyfikowanie pliku web.config aplikacji docelowej. Zobacz [porady: modyfikowanie plików Web.Config w celu Instrumentowania i profilowania dynamicznie skompilowanych aplikacji sieci Web ASP.NET](../profiling/how-to-modify-web-config-files-to-instrument-and-profile-dynamically-compiled-aspnet-web-applications.md).  
  
2.  Otwórz okno wiersza polecenia na komputerze, który jest hostem aplikacji sieci Web.  
  
3.  Inicjowanie profilowania zmiennych środowiskowych. Wpisz:  
  
     **VSPerfClrEnv /globaltracegc**  
  
     —lub—  
  
     **VSPerfClrEnv /globaltracegclife**  
  
    -   **/globaltracegc** umożliwia zbieranie danych alokacji pamięci.  
  
    -   **/globaltracegclife** umożliwia zbieranie danych alokacji pamięci oraz danych o okresie istnienia obiektu.  
  
4.  Uruchom ponownie komputer.  
  
## <a name="running-the-profiling-session"></a>Uruchomiona sesja profilowania  
  
#### <a name="to-profile-the-aspnet-web-application"></a>Do profilu aplikacji sieci Web ASP.NET  
  
1.  Uruchom profilera. Wpisz:  
  
     **VSPerfCmd** [/start](../profiling/start.md) **: śledzenia** [/output](../profiling/output.md) **:** `OutputFile` [`Options`]  
  
    -   **/Start:trace** opcji inicjowania profilera.  
  
    -   **/Output:** `OutputFile` jest wymagany w przypadku opcji **/start**. `OutputFile` Określa nazwę i lokalizację profilowania pliku danych (Vsp).  
  
     Można użyć dowolnego z następujących opcji z **/start:trace** opcji.  
  
    > [!NOTE]
    >  **User** i **/crosssession** opcje są zwykle wymagane dla aplikacji ASP.NET.  
  
    |Opcja|Opis|  
    |------------|-----------------|  
    |[/ User](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName`|Określa nazwę domeny i opcjonalną konta, który jest właścicielem [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] proces roboczy. Ta opcja jest wymagana, jeśli proces jest uruchomiony jako użytkownik innego niż zalogowanego użytkownika. Nazwa jest wyświetlana w kolumnie Nazwa użytkownika na karcie Procesy Menedżera zadań systemu Windows.|  
    |[/crosssession](../profiling/crosssession.md)|Włącza profilowanie procesów w innych sesji. Ta opcja jest wymagana, jeśli aplikacja jest uruchomiona w innej sesji. Identyfikator sesji jest wymieniony w kolumnie Identyfikator sesji, na karcie Procesy Menedżera zadań systemu Windows. **/CS** może być określony jako skrót **/crosssession**.|  
    |[/globaloff](../profiling/globalon-and-globaloff.md)|Uruchamia, który wstrzymana profilera ze zbierania danych. Użyj [/globalon](../profiling/globalon-and-globaloff.md) wznowienie profilowania.|  
    |[/ licznika](../profiling/counter.md) **:** `Config`|Zbiera informacje o wydajności procesora licznika określone w `Config`. Informacje o liczniku jest dodawany do danych zbieranych na każdym zdarzeniu profilowania.|  
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Określa licznik wydajności systemu Windows, które będą zbierane podczas profilowania.|  
    |[/automark](../profiling/automark.md) **:** `Interval`|Za pomocą **/wincounter** tylko. Określa liczbę milisekund między zdarzeniami kolekcji liczników wydajności systemu Windows. Domyślna to 500 ms.|  
    |[/Events](../profiling/events-vsperfcmd.md) **:** `Config`|Określa zdarzenia funkcji Śledzenie zdarzeń systemu Windows (), które mają być zbierane podczas profilowania. Zdarzenia ETW są gromadzone w pliku oddzielne (ETL).|  
  
2.  Uruchom [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci Web w typowy sposób.  
  
## <a name="controlling-data-collection"></a>Kontrolowanie zbierania danych  
 Po uruchomieniu aplikacji docelowej zbieranie danych można kontrolować przy uruchamianie i zatrzymywanie zapisywanie danych w pliku danych profilera przy użyciu **VSPerfCmd.exe** opcje. Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonania programu, takie jak uruchamianie lub zamykanie aplikacji.  
  
#### <a name="to-start-and-stop-data-collection"></a>Aby uruchomić i zatrzymać zbieranie danych  
  
-   Następujące pary opcje uruchamiania i zatrzymywania zbierania danych. Określ opcję każdego w osobnym wierszu polecenia. Włączenie funkcji zbierania danych można włączać i wyłączać wiele razy.  
  
    |Opcja|Opis|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Uruchamia (**/globalon**) lub zatrzymania (**/globaloff**) zbierania danych dla wszystkich procesów.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Uruchamia (**/processon**) lub zatrzymania (**/processoff**) zbierania danych przez proces określony przez identyfikator procesu (`PID`).|  
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|Uruchamia (**/threadon**) lub zatrzymania (**/threadoff**) zbierania danych dla wątku określony przez identyfikator wątku (`TID`).|  
  
-   Można również użyć **VSPerfCmd.exe**[/oznaczyć](../profiling/mark.md) opcję, aby wstawić znacznik profilowania do pliku danych. **/Oznaczyć** polecenie dodaje identyfikator sygnatury czasowej i opcjonalny zdefiniowane przez użytkownika ciąg tekstowy. Znaczniki można filtrować dane w widoków danych i raportów profilera.  
  
## <a name="ending-the-profiling-session"></a>Kończenie sesji profilowania  
 Aby zakończyć sesję profilowania, Zamknij element docelowy [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci Web, Zatrzymaj Internet Information Services (IIS) do zatrzymania PROFILOWANEGO procesu, a następnie zamknij profilera. Następnie uruchom ponownie usługi IIS.  
  
#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania  
  
1.  Zamknij [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci Web.  
  
2.  Zamknij [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] proces roboczy resetując Internet Information Services (IIS). Wpisz:  
  
     **Polecenie IISReset/Stop**  
  
3.  Zamknij profilera. Wpisz:  
  
     **VSPerfCmd**  [ /shutdown](../profiling/shutdown.md)  
  
4.  Uruchom ponownie usługi IIS. Wpisz:  
  
     **Polecenie IISReset/Start**  
  
## <a name="restoring-the-application-and-computer-configuration"></a>Przywracanie aplikacji i konfiguracji komputera  
 Po ukończeniu wszystkich profilowania, Zastąp plik web.config, wyczyść profilowania zmiennych środowiskowych, a następnie uruchom ponownie komputer, aby przywrócić serwer i [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji do oryginalnego stanu.  
  
#### <a name="to-restore-the-application-and-computer-configuration"></a>Aby przywrócić konfigurację aplikacji i komputera  
  
1.  Zastąp plik web.config kopia oryginalnego pliku.  
  
2.  (Opcjonalnie). Wyczyść profilowania zmiennych środowiskowych. Wpisz:  
  
     **VSPerfCmd /globaloff**  
  
3.  Uruchom ponownie komputer.  
  
## <a name="see-also"></a>Zobacz też  
 [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Widoki danych pamięci .NET](../profiling/dotnet-memory-data-views.md)