---
title: 'Porady: dołączanie profilera do aplikacji autonomicznej .NET Framework do zbierania danych współbieżności przy użyciu wiersza polecenia | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: fdd41576-797e-4312-8520-fee7bb767e4a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: f727e2a06fa2e5798de84c7b6ee6d97bfb2a4558
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2018
ms.locfileid: "34815288"
---
# <a name="how-to-attach-the-profiler-to-a-net-framework-stand-alone-application-to-collect-concurrency-data-by-using-the-command-line"></a>Porady: dołączanie profilera do aplikacji autonomicznej .NET Framework do zbierania danych współbieżności przy użyciu wiersza polecenia
W tym artykule opisano sposób użycia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzia wiersza polecenia narzędzi profilowania umożliwia dołączanie profilera do uruchomionej aplikacji autonomicznej (klient) .NET Framework i zbieranie danych współbieżności procesie i wątku.  
  
> [!NOTE]
>  Narzędzia wiersza polecenia narzędzi profilowania znajdują się w *narzędzia \Team Tools\Performance* podkatalog [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] katalogu instalacyjnego. Na komputerach 64-bitowych zarówno 64-bitowe i 32-bitowe wersje narzędzia są dostępne. Za pomocą narzędzi wiersza polecenia profilera, możesz dodać ścieżkę narzędzia do zmiennej środowiskowej PATH w oknie wiersza polecenia lub dodać go do samo polecenie. Aby uzyskać więcej informacji, zobacz [Określ ścieżkę do narzędzia wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Profiler jest dołączony do aplikacji, można wstrzymywać i wznawiać zbierania danych. Aby zakończyć sesję profilowania, profilera nie musi być dołączony do aplikacji i profilera muszą zostać jawnie wyłączone.  
  
## <a name="attach-the-profiler"></a>Dołączanie profilera  
  
#### <a name="to-attach-the-profiler-to-a-running-net-framework-application"></a>Aby dołączanie profilera do uruchomionej aplikacji .NET Framework  
  
1.  Otwórz okno wiersza polecenia.  
  
2.  Uruchom profilera. Wpisz:  
  
     [VSPerfCmd](../profiling/vsperfcmd.md) **/start:concurrency/Output:** `OutputFile` [`Options`]  
  
     [/Output](../profiling/output.md)**:** `OutputFile` jest wymagany w przypadku opcji **/start**. `OutputFile` Określa nazwę i lokalizację profilowania pliku danych (Vsp).  
  
     Można użyć dowolnego z następujących opcji z **/start:concurrency** opcji.  
  
    |Opcja|Opis|  
    |------------|-----------------|  
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Określa licznik wydajności systemu Windows, które będą zbierane podczas profilowania.|  
    |[/automark](../profiling/automark.md) **:** `Interval`|Za pomocą **/wincounter** tylko. Określa liczbę milisekund między zdarzeniami kolekcji liczników wydajności systemu Windows. Domyślna to 500 ms.|  
    |[/Events](../profiling/events-vsperfcmd.md) **:** `Config`|Określa zdarzenia funkcji Śledzenie zdarzeń systemu Windows (), które mają być zbierane podczas profilowania. Zdarzenia ETW są gromadzone w pliku oddzielne (ETL).|  
  
3.  Uruchomienie aplikacji docelowej w typowy sposób.  
  
4.  Dołączanie profilera do aplikacji docelowej. Wpisz:  
  
     **VSPerfCmd / dołączyć:** `PID` [**/lineoff**] [**/targetclr:**`Version`]  
  
    -   `PID` Określa identyfikator procesu aplikacji docelowej. Identyfikatory wszystkich procesów uruchomionych procesów można wyświetlić w Menedżerze zadań systemu Windows.  
  
    -   [/lineoff](../profiling/lineoff.md) wyłącza zbieranie danych numeru wiersza.  
  
    -   [/targetclr](../profiling/targetclr.md) **:** `Version` Określa wersję środowisko uruchomieniowe języka wspólnego (CLR) do profilu po załadowaniu więcej niż jedną wersję środowiska uruchomieniowego w aplikacji. Opcjonalna.  
  
## <a name="control-data-collection"></a>Sterowanie zbieraniem danych  
 Po uruchomieniu aplikacji docelowej zbieranie danych można kontrolować przy uruchamianie i zatrzymywanie przy zapisywaniu danych do pliku przy użyciu *VSPerfCmd.exe* opcje. Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonania programu, takie jak uruchamianie lub zamykanie aplikacji.  
  
#### <a name="to-start-and-stop-data-collection"></a>Aby uruchomić i zatrzymać zbieranie danych  
  
-   Następujące pary *VSPerfCmd.exe* opcje uruchamiania i zatrzymywania zbierania danych. Określ każdej opcji na osobnym wiersza polecenia. Włączenie funkcji zbierania danych można włączać i wyłączać wiele razy.  
  
    |Opcja|Opis|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Uruchamia (**/globalon**) lub zatrzymania (**/globaloff**) zbierania danych dla wszystkich procesów.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Uruchamia (**/processon**) lub zatrzymania (**/processoff**) zbierania danych przez proces określony przez identyfikator procesu (`PID`).|  
    |[/ dołączyć](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [/ detach](../profiling/detach.md)[**:**{`PID`&#124;`ProcName`}]|**/ dołączyć** rozpoczyna zbieranie danych przez proces określony przez identyfikator procesu (`PID`) lub nazwa procesu (Nazwa_procedury). **/ detach** zatrzymuje zbieranie danych dla określonego procesu lub dla wszystkich procesów, jeśli nie określono określonego procesu.|  
  
## <a name="end-the-profiling-session"></a>Kończenie sesji profilowania  
 Aby zakończyć sesję profilowania, profilera musi nie być zbierania danych. Można zatrzymać zbieranie danych z aplikacji profilowane metodą współbieżności przez zamknięcie aplikacji lub wywoływania **VSPerfCmd / detach** opcji. Następnie wywołaj **VSPerfCmd/shutdown** opcję, aby wyłączyć profilera i zamknij plik danych profilowania. **VSPerfClrEnv / Wyłącz** polecenie czyści profilowania zmiennych środowiskowych.  
  
#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania  
  
1.  Wykonaj jedną z następujących czynności, aby odłączyć profilera z aplikacji docelowej.  
  
    -   Typ **VSPerfCmd / detach**  
  
         —lub—  
  
    -   Zamknij aplikacji docelowej.  
  
2.  Zamknij profilera. Wpisz:  
  
     VSPerfCmd [ /shutdown](../profiling/shutdown.md)
