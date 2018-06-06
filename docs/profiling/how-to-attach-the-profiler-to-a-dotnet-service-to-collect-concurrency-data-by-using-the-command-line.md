---
title: 'Porady: dołączanie profilera do usługi .NET i zbieranie danych współbieżności przy użyciu wiersza polecenia | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: ffbdfe37-8325-44be-bd36-2c8aab2dec7b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 60f300f58c0cc9c06d8af64a4054b95306899f3a
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2018
ms.locfileid: "34815746"
---
# <a name="how-to-attach-the-profiler-to-a-net-service-to-collect-concurrency-data-by-using-the-command-line"></a>Porady: dołączanie profilera do usługi .NET i zbieranie danych współbieżności przy użyciu wiersza polecenia
W tym artykule opisano sposób użycia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzia profilowania wiersza polecenia narzędzia umożliwiające dołączanie profilera do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] usługi i zbieranie danych współbieżności procesów i wątków, przy użyciu metody próbkowania.  
  
> [!NOTE]
>  Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagane znaczących zmian w sposobie profilera Visual Studio zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows wymagają również nowe techniki kolekcji. Zobacz [narzędzi wydajności w przypadku aplikacji systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
> [!NOTE]
>  Narzędzia wiersza polecenia narzędzi profilowania znajdują się w *\Team Tools\Performance narzędzia* podkatalogu w katalogu instalacji programu Visual Studio. Na komputerach 64-bitowych zarówno 64-bitowe i 32-bitowe wersje narzędzia są dostępne. Za pomocą narzędzi wiersza polecenia profilera, możesz dodać ścieżkę narzędzia do zmiennej środowiskowej PATH w oknie wiersza polecenia lub dodać go do samo polecenie. Aby uzyskać więcej informacji, zobacz [Określ ścieżkę do narzędzia wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Zbieranie danych współbieżności, możesz dołączyć do procesu usługi profilera. Profiler jest dołączony do usługi, można wstrzymywać i wznawiać zbierania danych. Aby zakończyć sesję profilowania, profilera nie musi być dołączony do usługi i profilera muszą zostać jawnie wyłączone. W większości przypadków zaleca się czyszczenie profilowania zmienne środowiskowe z końcem sesji.  
  
## <a name="attach-the-profiler"></a>Dołączanie profilera  
  
#### <a name="to-attach-the-profiler-to-a-net-framework-service"></a>Aby dołączanie profilera do usługi .NET Framework  
  
1.  Zainstaluj usługę.  
  
2.  Otwórz okno poleceń.  
  
3.  Inicjowanie profilowania zmiennych środowiskowych. Wpisz:  
  
     [VSPerfClrEnv](../profiling/vsperfclrenv.md) **/globalsampleon** [**/samplelineoff**]  
  
    -   **/globalsampleon** umożliwia próbkowania.  
  
    -   **/samplelineoff** wyłącza przypisania zebranych danych do wierszy kodu określonego źródła. W przypadku wybrania tej opcji, danych jest przypisane tylko do funkcji.  
  
4.  Uruchom ponownie komputer.  
  
5.  Uruchom profilera. Wpisz:  
  
     [VSPerfCmd](../profiling/vsperfcmd.md) **/start:concurrency/Output:** `OutputFile` [`Options`]  
  
     [/Output](../profiling/output.md)**:** `OutputFile` jest wymagany w przypadku opcji **/start**. `OutputFile` Określa nazwę i lokalizację profilowania pliku danych (Vsp).  
  
     Można użyć dowolnego z następujących opcji z **/start** opcji.  
  
    > [!NOTE]
    >  **User** i **/crosssession** opcje są zwykle wymagane dla usług.  
  
    |Opcja|Opis|  
    |------------|-----------------|  
    |[/ User](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName`|Określa nazwę domeny i nazwę konta, który jest właścicielem PROFILOWANEGO procesu. Ta opcja jest wymagana tylko wtedy, gdy proces jest uruchomiony jako użytkownik innego niż zalogowanego użytkownika. Właściciel procesu jest wymieniony w **nazwy użytkownika** kolumny na **procesów** kartę Menedżera zadań systemu Windows.|  
    |[/crosssession](../profiling/crosssession.md)|Włącza profilowanie procesów w innych sesji. Ta opcja jest wymagana, jeśli usługa jest uruchomiona w innej sesji. Identyfikator jest wymieniony w sesji **identyfikator sesji** kolumny na **procesów** kartę Menedżera zadań systemu Windows. **/CS** może być określony jako skrót **/crosssession**.|  
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Określa licznik wydajności systemu Windows, które będą zbierane podczas profilowania.|  
    |[/automark](../profiling/automark.md) **:** `Interval`|Za pomocą **/wincounter** tylko. Określa liczbę milisekund między zdarzeniami kolekcji liczników wydajności systemu Windows. Domyślna to 500 ms.|  
    |[/Events](../profiling/events-vsperfcmd.md) **:** `Config`|Określa zdarzenia funkcji Śledzenie zdarzeń systemu Windows (), które mają być zbierane podczas profilowania. Zdarzenia ETW są gromadzone w oddzielnej (. *etl*) pliku.|  
  
6.  W razie potrzeby uruchom usługę.  
  
7.  Dołączanie profilera do usługi. Wpisz:  
  
     **VSPerfCmd / dołączyć:** `PID` [[/targetclr](../profiling/targetclr.md)**:**`Version`]  
  
    -   `PID` Określa identyfikator procesu lub proces nazwę usługi. Identyfikatory wszystkich procesów uruchomionych procesów można wyświetlić w Menedżerze zadań systemu Windows.  
  
    -   **targetclr:** `Version` Określa wersję środowisko uruchomieniowe języka wspólnego (CLR) do profilu po załadowaniu więcej niż jedną wersję środowiska uruchomieniowego w aplikacji. Opcjonalna.  
  
## <a name="control-data-collection"></a>Sterowanie zbieraniem danych  
 Gdy usługa jest uruchomiona, można kontrolować zbierania danych przez uruchamianie i zatrzymywanie przy zapisywaniu danych do pliku przy użyciu *VSPerfCmd.exe* opcje. Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonania programu, takie jak uruchamianie lub zamykanie aplikacji.  
  
#### <a name="to-start-and-stop-data-collection"></a>Aby uruchomić i zatrzymać zbieranie danych  
  
-   Następujące pary **VSPerfCmd** opcje uruchamiania i zatrzymywania zbierania danych. Określ opcję każdego w osobnym wierszu polecenia. Włączenie funkcji zbierania danych można włączać i wyłączać wiele razy.  
  
    |Opcja|Opis|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Uruchamia (**/globalon**) lub zatrzymania (**/globaloff**) zbierania danych dla wszystkich procesów.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Uruchamia (**/processon**) lub zatrzymania (**/processoff**) zbierania danych przez proces określony przez identyfikator procesu (`PID`).|  
    |**/ dołączyć:**{`PID`&#124;`ProcName`} [/ detach](../profiling/detach.md)[: {`PID`&#124;`ProcName`}]|**/ dołączyć** rozpoczyna zbieranie danych przez proces określony przez identyfikator procesu lub nazwy procesu. **/ detach** zatrzymuje zbieranie danych dla określonego procesu lub dla wszystkich procesów, jeśli nie określono określonego procesu.|  
  
-   Można również użyć **VSPerfCmd.exe**[/oznaczyć](../profiling/mark.md) opcję, aby wstawić znacznik profilowania do pliku danych. **/Oznaczyć** polecenie dodaje identyfikator sygnatury czasowej i opcjonalny zdefiniowane przez użytkownika ciąg tekstowy. Znaczniki można filtrować dane w widoków danych i raportów profilera. Następujące pary VSPerfCmd opcje uruchamiania i zatrzymywania zbierania danych. Określ każdej opcji na osobnym wiersza polecenia. Włączenie funkcji zbierania danych można włączać i wyłączać wiele razy.  
  
## <a name="end-the-profiling-session"></a>Kończenie sesji profilowania  
 Aby zakończyć sesję profilowania, profilera musi nie być zbierania danych. Można zatrzymać zbieranie danych z aplikacji profilowaniu metodą współbieżności, zatrzymując usługę lub wywołując **VSPerfCmd / detach** opcji. Następnie wywołaj **VSPerfCmd/shutdown** opcję, aby wyłączyć profilera i zamknij plik danych profilowania. **VSPerfClrEnv /globaloff** polecenie usuwa profilowania zmiennych środowiskowych, ale konfiguracja systemu nie zostanie zresetowana do ponownego uruchomienia komputera.  
  
#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania  
  
1.  Wykonaj jedną z następujących czynności, aby odłączyć profilera z aplikacji docelowej.  
  
    -   Zatrzymaj usługę.  
  
         —lub—  
  
    -   Typ **VSPerfCmd / detach.**  
  
2.  Zamknij profilera. Wpisz:  
  
     **VSPerfCmd**[zamknięcia](../profiling/shutdown.md)
