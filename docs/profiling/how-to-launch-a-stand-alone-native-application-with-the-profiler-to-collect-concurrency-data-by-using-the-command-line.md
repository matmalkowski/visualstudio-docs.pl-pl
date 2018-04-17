---
title: 'Porady: uruchamianie autonomicznej aplikacji natywnej z Profilerem do zbierania danych współbieżności przy użyciu wiersza polecenia | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
ms.assetid: e5aed651-afed-4b70-9a7e-1a6032cc614f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: a71d7b656dc56d1bb92916d4b35f5fae39e05b77
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-launch-a-stand-alone-native-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line"></a>Porady: uruchamianie aplikacji natywnej z profilerem do zbierania danych współbieżności przy użyciu wiersza polecenia
W tym temacie opisano sposób użycia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędziach profilowania narzędzia wiersza polecenia do uruchomienia aplikacji natywnej autonomicznej (klient) i zbierania danych współbieżności procesie i wątku.  
  
 Sesja profilowania zawiera następujące części:  
  
-   Uruchamianie aplikacji przy użyciu profilera  
  
-   Kontrolowanie zbierania danych  
  
-   Kończenie sesji profilowania  
  
> [!NOTE]
>  Narzędzia wiersza polecenia narzędzi profilowania znajdują się w podkatalogu narzędzia \Team Tools\Performance [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] katalogu instalacyjnego. Na komputerach 64-bitowych zarówno 64-bitowe i 32-bitowe wersje narzędzia są dostępne. Aby użyć profilera w wierszu polecenia, należy dodać ścieżkę do narzędzia do zmiennej środowiskowej PATH z **wiersza polecenia** okna lub dodaj je do samo polecenie. Aby uzyskać więcej informacji, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
## <a name="starting-the-application-with-the-profiler"></a>Uruchamianie aplikacji przy użyciu profilera  
 Aby rozpocząć aplikacji docelowej profilera, należy użyć [VSPerfCmd.exe](../profiling/vsperfcmd.md)**/start** i **/uruchamianie** opcje do inicjowania profilera i uruchomić aplikację. Można określić **/start** i **/uruchamianie** i odpowiednie opcje. Można również dodać **/globaloff** opcję, aby wstrzymać zbieranie danych na początku aplikacji docelowej. Następnie należy użyć **/globalon** do rozpoczęcia zbierania danych.  
  
#### <a name="to-start-an-application-with-the-profiler"></a>Aby uruchomić aplikację przy użyciu profilera  
  
1.  W wierszu polecenia wpisz następujące polecenie:  
  
     [VSPerfCmd](../profiling/vsperfcmd.md) **/start:concurrency/Output:** `OutputFile` [`Options`]  
  
     [/Output](../profiling/output.md)**:** `OutputFile` jest wymagany w przypadku opcji **/start**. `OutputFile` Określa nazwę i lokalizację profilowania pliku danych (Vsp).  
  
     Można użyć tych opcjach w poniższej tabeli z **/start:concurrency** opcji.  
  
    |Opcja|Opis|  
    |------------|-----------------|  
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Określa licznik wydajności systemu Windows, które będą zbierane podczas profilowania.|  
    |[/automark](../profiling/automark.md) **:** `Interval`|Za pomocą **/wincounter** tylko. Określa liczbę milisekund między zdarzeniami kolekcji liczników wydajności systemu Windows. Wartość domyślna to 500.|  
    |[/Events](../profiling/events-vsperfcmd.md) **:** `Config`|Określa zdarzenia funkcji Śledzenie zdarzeń systemu Windows (), które mają być zbierane podczas profilowania. Zdarzenia ETW są gromadzone w pliku oddzielne (ETL).|  
  
2.  Uruchom aplikację docelowym, wpisując:  
  
     **VSPerfCmd**[/uruchamianie](../profiling/launch.md) **:** `AppName` [`Options`]    
  
     Można użyć tych opcjach w poniższej tabeli z **/uruchamianie** opcji.  
  
    |Opcja|Opis|  
    |------------|-----------------|  
    |[przełącznika/args](../profiling/args.md) **:** `Arguments`|Określa ciąg, który zawiera argumenty wiersza polecenia do przekazania do aplikacji docelowej.|  
    |[/ Console](../profiling/console.md)|Uruchamia aplikację wiersza polecenia docelowego w osobnym oknie.|  
    |[/targetclr](../profiling/targetclr.md) **:** `CLRVersion`|Określa wersję środowisko uruchomieniowe języka wspólnego (CLR) do profilowania, jeśli więcej niż jedną wersję środowiska CLR ładowania aplikacji.|  
  
## <a name="controlling-data-collection"></a>Kontrolowanie zbierania danych  
 Aplikacja docelowa jest uruchomiona, można kontrolować zbierania danych przez uruchamianie i zatrzymywanie przy zapisywaniu danych do pliku z opcjami VSPerfCmd.exe. Przez kontrolowanie zbierania danych może zbierać dane dotyczące określonych części wykonania programu, takie jak uruchamianie lub zamykanie aplikacji.  
  
#### <a name="to-start-and-stop-data-collection"></a>Aby uruchomić i zatrzymać zbieranie danych  
  
-   Pary opcje w poniższej tabeli uruchomić i zatrzymać zbieranie danych. Określ opcję każdego w osobnym wierszu polecenia. Włączenie funkcji zbierania danych można włączać i wyłączać wiele razy.  
  
    |Opcja|Opis|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Uruchamia (**/globalon**) lub zatrzymania (**/globaloff**) zbierania danych dla wszystkich procesów.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Uruchamia (**/processon**) lub zatrzymania (**/processoff**) zbierania danych przez proces który identyfikator procesu (`PID`) określa.|  
    |[/ dołączyć](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [/ detach](../profiling/detach.md)[**:**{`PID`&#124;`ProcName`}]|**/ dołączyć** rozpoczyna zbieranie danych przez proces który identyfikator procesu (`PID`) lub nazwa procesu (*Nazwa_procedury*) określa. **/ detach** zatrzymuje zbieranie danych dla określonego procesu lub dla wszystkich procesów, jeśli jest określony żaden proces.|  
  
-   Można również użyć **VSPerfCmd.exe**[/oznaczyć](../profiling/mark.md) opcję, aby wstawić znacznik profilowania do pliku danych. **/Oznaczyć** polecenie dodaje identyfikator sygnatury czasowej i opcjonalny zdefiniowane przez użytkownika ciąg tekstowy. Znaczniki można filtrować dane w widoków danych i raportów profilera.  
  
## <a name="ending-the-profiling-session"></a>Kończenie sesji profilowania  
 Aby zakończyć sesję profilowania, profilera musi nie być zbierania danych. Można zatrzymać zbieranie danych współbieżności, zamykając profilowana aplikacja lub wywołując **VSPerfCmd / detach** opcji. Następnie wywołaj **VSPerfCmd/shutdown** opcję, aby wyłączyć profilera i zamknij plik danych profilowania.  
  
#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania  
  
1.  Odłączanie profilera z aplikacji docelowej, jej zamknięcie lub wpisując następujące polecenie w wierszu polecenia:  
  
     **VSPerfCmd / detach**  
  
2.  Zamknij profilera, wpisując następujące polecenie w wierszu polecenia:  
  
     **VSPerfCmd** [ /shutdown](../profiling/shutdown.md)