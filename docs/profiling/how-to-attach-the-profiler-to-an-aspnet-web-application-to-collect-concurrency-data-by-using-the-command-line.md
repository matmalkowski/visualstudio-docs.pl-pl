---
title: 'Porady: dołączanie profilera do aplikacji sieci Web ASP.NET w celu zbierania danych współbieżności przy użyciu wiersza polecenia | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 0e215fdd-55f8-43ef-9534-06542eefe223
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 56a3daa0f20a62c8b7410ba5b339179fbf9c5521
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-concurrency-data-by-using-the-command-line"></a>Porady: dołączanie profilera do aplikacji sieci Web ASP.NET w celu zbierania danych współbieżności użyciu wiersza polecenia
W tym temacie opisano sposób użycia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzia wiersza polecenia narzędzi profilowania umożliwia dołączanie profilera do aplikacji ASP.NET i zbieranie danych współbieżności procesie i wątku.  
  
 Narzędzia wiersza polecenia narzędzi profilowania znajdują się w podkatalogu narzędzia \Team Tools\Performance katalogu instalacyjnego programu Visual Studio. Na komputerach 64-bitowych zarówno 64-bitowe i 32-bitowe wersje narzędzia są dostępne. Aby użyć profilera w wierszu polecenia, należy dodać ścieżkę do narzędzia do zmiennej środowiskowej PATH z **wiersza polecenia** okna lub dodaj je do samo polecenie. Aby uzyskać więcej informacji, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Zbieranie danych współbieżności, dołączanie profilera do procesu roboczego programu ASP.NET, który jest hostem witryny sieci Web. Profiler jest dołączony do aplikacji, można wstrzymywać i wznawiać zbierania danych. Aby zakończyć sesję profilowania, profilera nie musi być dołączony do aplikacji i profilera muszą zostać jawnie wyłączone. W większości przypadków należy wyczyścić profilowania zmienne środowiskowe z końcem sesji.  
  
## <a name="attaching-the-profiler"></a>Dołączanie profilera  
  
#### <a name="to-attach-the-profiler-to-a-aspnet-application"></a>Aby dołączanie profilera do aplikacji ASP.NET  
  
1.  Uruchom profilera, wpisując następujące polecenie:  
  
     [VSPerfCmd](../profiling/vsperfcmd.md) **/start:concurrency/Output:** `OutputFile` [`Options`]  
  
    -   [/Start](../profiling/start.md) opcji inicjowania profilera do zbierania danych kontencji zasobów.  
  
    -   [/Output](../profiling/output.md)**:** `OutputFile` jest wymagany w przypadku opcji **/start**. `OutputFile` Określa nazwę i lokalizację profilowania pliku danych (Vsp).  
  
     Każda opcja, można użyć w poniższej tabeli z **/start** opcji.  
  
    |Opcja|Opis|  
    |------------|-----------------|  
    |[/ User](../profiling/user-vsperfcmd.md) **:**[`Domain\`]`UserName`|Określa opcjonalne domenę i nazwę użytkownika konta, aby uzyskać dostęp do profilera.|  
    |[/crosssession](../profiling/crosssession.md)|Włącza profilowanie procesów w innych sesji logowania.|  
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Określa licznik wydajności systemu Windows, które będą zbierane podczas profilowania.|  
    |[/automark](../profiling/automark.md) **:** `Interval`|Za pomocą **/wincounter** tylko. Określa liczbę milisekund między zdarzeniami kolekcji liczników wydajności systemu Windows. Wartość domyślna to 500.|  
    |[/Events](../profiling/events-vsperfcmd.md) **:** `Config`|Określa zdarzenia funkcji Śledzenie zdarzeń systemu Windows (), które mają być zbierane podczas profilowania. Zdarzenia ETW są gromadzone w pliku oddzielne (ETL).|  
  
2.  Uruchamianie aplikacji platformy ASP.NET w typowy sposób.  
  
3.  Dołączanie profilera do procesu roboczego ASP.NET, wpisując następujące polecenie:**VSPerfCmd / dołączyć:** `PID` [**/targetclr:**`Version`]  
  
    -   `PID` Określa identyfikator lub nazwa procesu roboczego ASP.NET. Identyfikatory wszystkich procesów uruchomionych procesów można wyświetlić w Menedżerze zadań systemu Windows.  
  
    -   [/targetclr](../profiling/targetclr.md) **:** `Version` Określa wersję środowisko uruchomieniowe języka wspólnego (CLR) do profilu po załadowaniu więcej niż jedną wersję środowiska uruchomieniowego w aplikacji. Ten parametr jest opcjonalny.  
  
## <a name="controlling-data-collection"></a>Kontrolowanie zbierania danych  
 Gdy aplikacja jest uruchomiona, można kontrolować zbierania danych przez uruchamianie i zatrzymywanie przy zapisywaniu danych do pliku przy użyciu opcji VSPerfCmd.exe. Przez kontrolowanie zbierania danych może zbierać dane dotyczące określonych części wykonania programu, takie jak uruchamianie lub zamykanie aplikacji.  
  
#### <a name="to-start-and-stop-data-collection"></a>Aby uruchomić i zatrzymać zbieranie danych  
  
-   Pary opcje narzędzia VSPerfCmd w poniższej tabeli uruchomić i zatrzymać zbieranie danych. Określ opcję każdego w osobnym wierszu polecenia. Włączenie funkcji zbierania danych można włączać i wyłączać wiele razy.  
  
    |Opcja|Opis|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Uruchamia (**/globalon**) lub zatrzymania (**/globaloff**) zbierania danych dla wszystkich procesów.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [processoff](../profiling/processon-and-processoff.md) **:**  `PID`|Uruchamia (**/processon**) lub zatrzymania (**/processoff**) zbierania danych przez proces który identyfikator procesu (`PID`) określa.|  
    |[/ dołączyć](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [/ detach](../profiling/detach.md)[**:**{`PID`&#124;`ProcName`}]|**/ dołączyć** rozpoczyna zbieranie danych przez proces który identyfikator procesu (`PID`) lub nazwa procesu (*Nazwa_procedury*) określa. **/ detach** zatrzymuje zbieranie danych dla określonego procesu lub dla wszystkich procesów, jeśli jest określony żaden proces.|  
  
## <a name="ending-the-profiling-session"></a>Kończenie sesji profilowania  
 Aby zakończyć sesję profilowania, profilera musi nie być zbierania danych. Można zatrzymać zbieranie danych z aplikacji, która jest profilowane metodą współbieżności przez ponowne uruchomienie procesu roboczego ASP.NET lub za pomocą **VSPerfCmd / detach** opcji. Następnie wywołaj **VSPerfCmd/shutdown** opcję, aby wyłączyć profilera i zamknij plik danych profilowania. **VSPerfClrEnv /globaloff** polecenie usuwa profilowania zmiennych środowiskowych, ale konfiguracja systemu nie zostanie zresetowana do ponownego uruchomienia komputera.  
  
#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania  
  
1.  Odłączanie profilera z aplikacji docelowej, jej zamknięcie lub wpisując następujące polecenie w wierszu polecenia:  
  
     **VSPerfCmd / detach**  
  
2.  Zamknij profilera, wpisując następujące polecenie w wierszu polecenia:  
  
     **VSPerfCmd** [ /shutdown](../profiling/shutdown.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Szybkie profilowanie za pomocą VSPerfASPNETCmd witryny sieci Web](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)