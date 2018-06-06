---
title: 'Porady: dołączanie profilera do usługi natywnej i zbieranie danych współbieżności przy użyciu wiersza polecenia | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 283a1ee1-b43e-4daf-95ae-1311925a42a8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 0ed87be79445e9a51160292a768407ee19f71bb0
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2018
ms.locfileid: "34766604"
---
# <a name="how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line"></a>Porady: dołączanie profilera do usługi natywnej i zbieranie danych współbieżności przy użyciu wiersza polecenia
W tym artykule opisano sposób użycia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzia profilowania wiersza polecenia narzędzia umożliwiające dołączanie profilera do natywnego (C/C++), usługi i zbieranie danych współbieżności procesie i wątku przy użyciu metody pobierania próbek.  
  
> [!NOTE]
>  Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagane znaczących zmian w sposobie profilera Visual Studio zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows wymagają również nowe techniki kolekcji. Zobacz [narzędzi wydajności w przypadku aplikacji systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
> [!NOTE]
>  Narzędzia wiersza polecenia narzędzi profilowania znajdują się w *\Team Tools\Performance narzędzia* podkatalogu w katalogu instalacji programu Visual Studio. Na komputerach 64-bitowych zarówno 64-bitowe i 32-bitowe wersje narzędzia są dostępne. Aby użyć profilera w wierszu polecenia, należy dodać ścieżkę do narzędzia do zmiennej środowiskowej PATH z **wiersza polecenia** okna lub samo polecenie. Aby uzyskać więcej informacji, zobacz [Określ ścieżkę do narzędzia wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Profiler jest dołączony do usługi, można wstrzymywać i wznawiać zbierania danych. Aby zakończyć sesję profilowania, profilera nie musi być dołączony do usługi, a profilera muszą zostać jawnie wyłączone.  
  
## <a name="attach-the-profiler"></a>Dołączanie profilera  
 Dołączanie profilera do usługi natywnej, należy użyć **VSPerfCmd/start** i **/ dołączyć** opcje inicjowania profilera i dołączenie go do aplikacji docelowej. Można określić **/start** i **/ dołączyć** i odpowiednie opcje w jednym wierszu polecenia. Można również dodać **/globaloff** opcję, aby wstrzymać zbieranie danych na początku aplikacji docelowej. Następnie należy użyć **/globalon** do rozpoczęcia zbierania danych.  
  
#### <a name="to-attach-the-profiler-to-a-native-service"></a>Aby dołączanie profilera do usługi natywnej  
  
1.  Jeśli usługa nie jest uruchomiona, uruchom usługę.  
  
2.  Uruchom profilera, wpisując następujące polecenie w wierszu polecenia:  
  
     [VSPerfCmd](../profiling/vsperfcmd.md) **/start:concurrency/Output:** `OutputFile` [`Options`]  
  
    -   [/Output](../profiling/output.md)**:** `OutputFile` jest wymagany w przypadku opcji **/start**. `OutputFile` Określa nazwę i lokalizację profilowania pliku danych (Vsp).  
  
     Każda opcja, można użyć w poniższej tabeli z **/start** opcji.  
  
    > [!NOTE]
    >  Większość usług wymagają **User** i **/crosssession** opcji.  
  
    |Opcja|Opis|  
    |------------|-----------------|  
    |[/ User](../profiling/user-vsperfcmd.md) **:**[`Domain\`]`UserName`|Określa opcjonalne domenę i nazwę użytkownika konta, aby uzyskać dostęp do profilera.|  
    |[/crosssession](../profiling/crosssession.md)|Włącza profilowanie procesów w innych sesji logowania.|  
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Określa licznik wydajności systemu Windows, które będą zbierane podczas profilowania.|  
    |[/automark](../profiling/automark.md) **:** `Interval`|Za pomocą **/wincounter** tylko. Określa liczbę milisekund między zdarzeniami kolekcji liczników wydajności systemu Windows. Wartość domyślna to 500.|  
    |[/Events](../profiling/events-vsperfcmd.md) **:** `Config`|Określa zdarzenia funkcji Śledzenie zdarzeń systemu Windows (), które mają być zbierane podczas profilowania. Zdarzenia ETW są gromadzone w pliku oddzielne (ETL).|  
  
3.  Dołączanie profilera do usługi, wpisując następujące polecenie w wierszu polecenia:  
  
     **VSPerfCmd / dołączyć:** `PID`  
  
     `PID` Określa identyfikator procesu lub nazwy procesu aplikacji docelowej. Identyfikatory wszystkich procesów uruchomionych procesów można wyświetlić w Menedżerze zadań systemu Windows.  
  
## <a name="control-data-collection"></a>Sterowanie zbieraniem danych  
 Po uruchomieniu aplikacji docelowej zbieranie danych można kontrolować przy uruchamianie i zatrzymywanie przy zapisywaniu danych do pliku z *VSPerfCmd.exe* opcje. Przez kontrolowanie zbierania danych może zbierać dane dotyczące określonych części wykonania programu, takie jak uruchamianie lub zamykanie aplikacji.  
  
#### <a name="to-start-and-stop-data-collection"></a>Aby uruchomić i zatrzymać zbieranie danych  
  
-   Pary opcje w poniższej tabeli uruchomić i zatrzymać zbieranie danych. Określ opcję każdego w osobnym wierszu polecenia. Włączenie funkcji zbierania danych można włączać i wyłączać wiele razy.  
  
    |Opcja|Opis|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Uruchamia (**/globalon**) lub zatrzymania (**/globaloff**) zbierania danych dla wszystkich procesów.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Uruchamia (**/processon**) lub zatrzymania (**/processoff**) zbierania danych przez proces który identyfikator procesu (`PID`) określa.|  
    |[/ dołączyć](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [/ detach](../profiling/detach.md)[**:**{`PID`&#124;`ProcName`}]|**/ dołączyć** rozpoczyna zbieranie danych przez proces który identyfikator procesu (`PID`) lub nazwa procesu (*Nazwa_procedury*) określa. **/ detach** zatrzymuje zbieranie danych dla określonego procesu lub dla wszystkich procesów, jeśli jest określony żaden proces.|  
  
## <a name="end-the-profiling-session"></a>Kończenie sesji profilowania  
 Aby zakończyć sesję profilowania, profilera musi nie być zbierania danych. Można zatrzymać zbieranie danych z usługi natywnej, który jest poddawany profilowaniu metodą współbieżności, zatrzymując usługę lub za pomocą **VSPerfCmd / detach** opcji. Następnie wywołaj **VSPerfCmd/shutdown** opcję, aby wyłączyć profilera i zamknij plik danych profilowania.  
  
#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania  
  
1.  Odłączanie profilera z aplikacji docelowej, zatrzymując usługę lub wpisując następujące polecenie w wierszu polecenia:  
  
     Typ **VSPerfCmd / detach**  
  
2.  Zamknij profilera, wpisując następujące polecenie w wierszu polecenia:  
  
     **VSPerfCmd** [ /shutdown](../profiling/shutdown.md)