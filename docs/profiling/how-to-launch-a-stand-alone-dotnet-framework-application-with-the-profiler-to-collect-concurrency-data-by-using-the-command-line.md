---
title: 'Porady: uruchamianie aplikacji autonomicznej .NET Framework z Profilerem do zbierania danych współbieżności przy użyciu wiersza polecenia | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 17a48848-bd3e-44ef-9971-e39836ff1df2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: a257a69abbe760709a197ab97e87bb6ab76b085b
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-launch-a-stand-alone-net-framework-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line"></a>Porady: uruchamianie aplikacji autonomicznej .NET Framework z profilera do zbierania danych współbieżności przy użyciu wiersza polecenia
W tym temacie opisano sposób użycia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzia wiersza polecenia narzędzi profilowania umożliwia uruchamianie aplikacji autonomicznej (klient) .NET Framework i zbieranie danych współbieżności procesów i wątków  
  
> [!NOTE]
>  Narzędzia wiersza polecenia narzędzi profilowania znajdują się w podkatalogu narzędzia \Team Tools\Performance [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] katalogu instalacyjnego. Na komputerach 64-bitowym zarówno w przypadku 64-bitowych, jak i 32-bitowe wersje narzędzia są dostępne. Za pomocą narzędzi wiersza polecenia profilera, możesz dodać ścieżkę narzędzia do zmiennej środowiskowej PATH w oknie wiersza polecenia lub dodać go do samo polecenie. Aby uzyskać więcej informacji, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Profiler jest dołączony do aplikacji, można wstrzymywać i wznawiać zbierania danych. Aby zakończyć sesję profilowania, profilera nie musi być dołączony do aplikacji i profilera muszą zostać jawnie wyłączone.  
  
## <a name="starting-the-application-with-the-profiler"></a>Uruchamianie aplikacji przy użyciu profilera  
 Można uruchomić aplikacji docelowej .NET Framework z profilera, umożliwia VSPerfClrEnv.exe ustaw zmienne profilowania .NET Framework. Następnie należy użyć narzędzia VSPerfCmd **/start** i **/uruchamianie** opcje do inicjowania profilera i uruchomić aplikację. Można określić **/start** i **/uruchamianie** i odpowiednie opcje w jednym wierszu polecenia. Można również dodać **/globaloff** opcję w wierszu polecenia, aby wstrzymać zbieranie danych po uruchomieniu aplikacji docelowej. Następnie należy użyć **/globalon** w osobnym wierszu polecenia można uruchomić zbierania danych.  
  
#### <a name="to-start-an-application-with-the-profiler"></a>Aby uruchomić aplikację przy użyciu profilera  
  
1.  Otwórz okno wiersza polecenia.  
  
2.  Uruchom profilera. Wpisz:  
  
     [VSPerfCmd](../profiling/vsperfcmd.md) **/start:concurrency**[**,**{**ResourceOnly**&#124;**ThreadOnly**}] **/ dane wyjściowe:** `OutputFile` [`Options`]  
  
    -   [/Start](../profiling/start.md) opcji inicjowania profilera.  
  
        |||  
        |-|-|  
        |**/Start:CONCURRENCY**|Umożliwia zbieranie zarówno rywalizacji i danych wykonanie wątku.|  
        |**/Start:CONCURRENCY, resourceonly**|Umożliwia zbieranie tylko danych kontencji zasobów.|  
        |**/Start:CONCURRENCY, threadonly**|Umożliwia zbieranie danych o tylko wykonanie wątku.|  
  
    -   [/Output](../profiling/output.md)**:** `OutputFile` jest wymagany w przypadku opcji **/start**. `OutputFile` Określa nazwę i lokalizację profilowania pliku danych (Vsp).  
  
     Można użyć dowolnego z następujących opcji z **/start:concurrency** opcji.  
  
    |Opcja|Opis|  
    |------------|-----------------|  
    |[/ User](../profiling/user-vsperfcmd.md) **:**[`domain\`]`username`|Określa opcjonalne domenę i nazwę użytkownika konta, aby uzyskać dostęp do profilera.|  
    |[/crosssession](../profiling/crosssession.md)|Włącza profilowanie procesów w innych sesji logowania.|  
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Określa licznik wydajności systemu Windows, które będą zbierane podczas profilowania.|  
    |[/automark](../profiling/automark.md) **:** `Interval`|Za pomocą **/wincounter** tylko. Określa liczbę milisekund między zdarzeniami kolekcji liczników wydajności systemu Windows. Domyślna to 500 ms.|  
    |[/Events](../profiling/events-vsperfcmd.md) **:** `Config`|Określa zdarzenia funkcji Śledzenie zdarzeń systemu Windows (), które mają być zbierane podczas profilowania. Zdarzenia ETW są gromadzone w pliku oddzielne (ETL).|  
  
3.  Uruchomienie aplikacji docelowej. Wpisz:  
  
     **VSPerfCmd**[/uruchamianie](../profiling/launch.md) **:** `AppName` [`Options`] [`Sample Event`]    
  
     Można użyć dowolnego z następujących opcji z **/uruchamianie** opcji.  
  
    |Opcja|Opis|  
    |------------|-----------------|  
    |[przełącznika/args](../profiling/args.md) **:** `Arguments`|Określa ciąg, który zawiera argumenty wiersza polecenia do przekazania do aplikacji docelowej.|  
    |[/ Console](../profiling/console.md)|Uruchamia aplikację wiersza polecenia docelowego w osobnym oknie.|  
    |[/targetclr](../profiling/targetclr.md) **:** `Version`|Określa wersję środowisko uruchomieniowe języka wspólnego (CLR) do profilu po załadowaniu więcej niż jedną wersję środowiska uruchomieniowego w aplikacji.|  
  
## <a name="controlling-data-collection"></a>Kontrolowanie zbierania danych  
 Aplikacja docelowa jest uruchomiona, można kontrolować zbierania danych przez uruchamianie i zatrzymywanie przy zapisywaniu danych do pliku przy użyciu opcji VSPerfCmd.exe. Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonania programu, takie jak uruchamianie lub zamykanie aplikacji.  
  
#### <a name="to-start-and-stop-data-collection"></a>Aby uruchomić i zatrzymać zbieranie danych  
  
1.  Następujące pary VSPerfCmd.exe opcje uruchamiania i zatrzymywania zbierania danych. Określ każdej opcji na osobnym wiersza polecenia. Włączenie funkcji zbierania danych można włączać i wyłączać wiele razy.  
  
    |Opcja|Opis|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Uruchamia (**/globalon**) lub zatrzymania (**/globaloff**) zbierania danych dla wszystkich procesów.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Uruchamia (**/processon**) lub zatrzymania (**/processoff**) zbierania danych przez proces określony przez identyfikator procesu (`PID`).|  
    |[/ dołączyć](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [/ detach](../profiling/detach.md)[**:**{`PID`&#124;`ProcName`}]|**/ dołączyć** rozpoczyna zbieranie danych przez proces określony przez identyfikator procesu (`PID`) lub nazwa procesu (Nazwa_procedury). **/ detach** zatrzymuje zbieranie danych dla określonego procesu lub dla wszystkich procesów, jeśli nie określono określonego procesu.|  
  
## <a name="ending-the-profiling-session"></a>Kończenie sesji profilowania  
 Aby zakończyć sesję profilowania, profilera musi nie być zbierania danych. Można zatrzymać zbieranie danych współbieżności, zamykając profilowana aplikacja lub wywołując **VSPerfCmd / detach** opcji. Następnie wywołaj **VSPerfCmd/shutdown** opcję, aby wyłączyć profilera i zamknij plik danych profilowania. **VSPerfClrEnv / Wyłącz** polecenie czyści profilowania zmiennych środowiskowych.  
  
#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania  
  
1.  Wykonaj jedną z następujących czynności, aby odłączyć profilera z aplikacji docelowej.  
  
    -   Zamknij aplikacji docelowej.  
  
         —lub—  
  
    -   Typ **VSPerfCmd / detach**  
  
2.  Zamknij profilera  
  
     **VSPerfCmd** [ /shutdown](../profiling/shutdown.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Zbieranie danych współbieżności](../profiling/collecting-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)