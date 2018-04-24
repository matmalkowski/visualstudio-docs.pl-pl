---
title: 'Porady: Instrumentowanie składnika autonomicznego .NET Framework i zbieranie danych o chronometrażu przy użyciu profilera z wiersza polecenia | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: b7dcc27b-45c6-4302-9552-6fa5b1e94b56
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 728f5b78e5a86c19ac709784a3a186b7a65cdd64
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-instrument-a-stand-alone-net-framework-component-and-collect-timing-data-with-the-profiler-from-the-command-line"></a>Porady: instrumentowanie składnika autonomicznego .NET Framework i zbieranie danych o chronometrażu przy użyciu profilera z wiersza polecenia
W tym temacie opisano sposób użycia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzia wiersza polecenia narzędzi profilowania składników .NET Framework, takich jak plik .exe lub .dll Instrumentacja i zbieranie szczegółowych danych o chronometrażu.  
  
> [!NOTE]
>  Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagane znaczących zmian w sposobie profilera Visual Studio zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows wymagają również nowe techniki kolekcji. Zobacz [narzędzi wydajności w przypadku aplikacji systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
>   
>  Narzędzia wiersza polecenia narzędzi profilowania znajdują się w podkatalogu narzędzia \Team Tools\Performance [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] katalogu instalacyjnego. Na komputerach 64-bitowych zarówno 64-bitowe i 32-bitowe wersje narzędzia są dostępne. Za pomocą narzędzi wiersza polecenia profilera, możesz dodać ścieżkę narzędzia do zmiennej środowiskowej PATH w oknie wiersza polecenia lub dodać go do samo polecenie. Aby uzyskać więcej informacji, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
>   
>  Dodawanie danych o interakcji między warstwy do uruchomienia profilowania wymaga określonych procedur przy użyciu wiersza polecenia narzędzia profilowania. Zobacz [zbierania danych o interakcji między warstwy](../profiling/adding-tier-interaction-data-from-the-command-line.md).  
  
 Zbieranie szczegółowych danych o chronometrażu ze składnikiem .NET Framework przy użyciu metody instrumentacji, należy użyć [VSInstr.exe](../profiling/vsinstr.md) narzędzie do generowania instrumentowanej wersji składnika i [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) narzędzia, aby zainicjować profilowania zmiennych środowiskowych. Następnie należy uruchomić profilera.  
  
 Po wykonaniu składników instrumentowanych danych o chronometrażu są zbierane automatycznie w pliku danych. Można wstrzymywać i wznawiać zbierania danych podczas sesji profilowania.  
  
 Aby zakończyć sesję profilowania, zamknij aplikacji docelowej i jawnie zamknięty profilera. W większości przypadków zaleca się czyszczenie profilowania zmienne środowiskowe z końcem sesji.  
  
## <a name="starting-the-profiling-session"></a>Rozpoczynanie sesji profilowania  
  
#### <a name="to-start-profiling-by-using-the-instrumentation-method"></a>Do uruchomienia profilowania przy użyciu metody Instrumentacji  
  
1.  Otwórz okno wiersza polecenia. W razie potrzeby dodaj katalogu narzędzi programu profiler do Twojej zmiennej środowiskowej PATH. Ścieżka instalacji nie zostanie dodany.  
  
2.  Użyj **VSInstr** narzędzie do generowania instrumentowanej wersji aplikacji docelowej.  
  
3.  Inicjowanie programu .NET Framework — profilowanie zmiennych środowiskowych. Wpisz:  
  
     **VSPerfClrEnv /traceon**  
  
4.  Uruchom profilera. Wpisz:  
  
     **/ OUTPUT /start:trace VSPerfCmd:** `OutputFile` [`Options`]  
  
    -   [/Start](../profiling/start.md)**: śledzenia** opcji inicjowania profilera.  
  
    -   [/Output](../profiling/output.md)**:** `OutputFile` jest wymagany w przypadku opcji **/start**. `OutputFile` Określa nazwę i lokalizację profilowania pliku danych (Vsp).  
  
     Można zastosować dowolną z następujących opcji z **/start:trace** opcji.  
  
    |Opcja|Opis|  
    |------------|-----------------|  
    |[/ User](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName`|Określa nazwę domeny i nazwę konta, który jest właścicielem PROFILOWANEGO procesu. Ta opcja jest wymagana tylko wtedy, gdy proces jest uruchomiony jako użytkownik innego niż zalogowanego użytkownika. Właściciel procesu znajduje się w kolumnie Nazwa użytkownika na karcie Procesy Menedżera zadań systemu Windows.|  
    |[/crosssession](../profiling/crosssession.md)|Włącza profilowanie procesów w innych sesji. Ta opcja jest wymagana, jeśli aplikacja ASP.NET działa w innej sesji. Identyfikator sesji jest wyświetlane w kolumnie Identyfikator sesji, na karcie Procesy Menedżera zadań systemu Windows. **/CS** może być określony jako skrót **/crosssession**.|  
    |[/globaloff](../profiling/globalon-and-globaloff.md)|Uruchamia, który wstrzymana profilera ze zbierania danych. Użyj [/globalon](../profiling/globalon-and-globaloff.md) wznowienie profilowania.|  
    |[/ licznika](../profiling/counter.md) **:** `Config`|Zbiera informacje licznika wydajności procesora, określonego w `Config`. Informacje o liczniku jest dodawany do danych, które są zbierane w każdym zdarzeniu profilowania.|  
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Określa licznik wydajności systemu Windows, które będą zbierane podczas profilowania.|  
    |[/automark](../profiling/automark.md) **:** `Interval`|Za pomocą **/wincounter** tylko. Określa liczbę milisekund między zdarzeniami kolekcji liczników wydajności systemu Windows. Domyślna to 500 ms.|  
    |[/Events](../profiling/events-vsperfcmd.md) **:** `Config`|Określa zdarzenia funkcji Śledzenie zdarzeń systemu Windows (), które mają być zbierane podczas profilowania. Zdarzenia ETW są gromadzone w pliku oddzielne (ETL).|  
  
5.  W oknie wiersza polecenia, należy uruchomić w aplikacji docelowej.  
  
## <a name="controlling-data-collection"></a>Kontrolowanie zbierania danych  
 Po uruchomieniu aplikacji docelowej zbieranie danych można kontrolować przy uruchamianie i zatrzymywanie zapisywanie danych w pliku danych profilera przy użyciu **VSPerfCmd.exe** opcje. Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonania programu, takie jak uruchamianie lub zamykanie aplikacji.  
  
#### <a name="to-start-and-stop-data-collection"></a>Aby uruchomić i zatrzymać zbieranie danych  
  
-   Następujące pary opcje uruchamiania i zatrzymywania zbierania danych. Określ opcję każdego w osobnym wierszu polecenia. Włączenie funkcji zbierania danych można włączać i wyłączać wiele razy.  
  
    |Opcja|Opis|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Uruchamia (**/globalon**) lub zatrzymania (**/globaloff**) zbierania danych dla wszystkich procesów.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Uruchamia (**/processon**) lub zatrzymania (**/processoff**) zbierania danych przez proces określony przez identyfikator procesu (`PID`).|  
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|Uruchamia (**/threadon**) lub zatrzymania (**/threadoff**) zbierania danych dla wątku określony przez identyfikator wątku (`TID`).|  
  
## <a name="ending-the-profiling-session"></a>Kończenie sesji profilowania  
 Aby zakończyć sesję profilowania, zamknij aplikację, która jest uruchomiony składnik Instrumentacją. Wywołanie **VSPerfCmd** [/shutdown](../profiling/shutdown.md) opcję, aby wyłączyć profilera i zamknij plik danych profilowania. **VSPerfClrEnv / Wyłącz** polecenie czyści profilowania zmiennych środowiskowych.  
  
#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania  
  
1.  Zamknij aplikacji docelowej.  
  
2.  Zamknij profilera. Wpisz:  
  
     **VSPerfCmd/shutdown**  
  
3.  (Opcjonalnie) Wyczyść profilowania zmiennych środowiskowych. Wpisz:  
  
     **VSPerfClrEnv / Wyłącz**  
  
## <a name="see-also"></a>Zobacz też  
 [Profilowanie aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Widoki danych metody instrumentacji](../profiling/instrumentation-method-data-views.md)