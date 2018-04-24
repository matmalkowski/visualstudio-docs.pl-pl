---
title: 'Porady: dołączanie profilera do aplikacji sieci Web ASP.NET w celu zbierania statystyk aplikacji przy użyciu wiersza polecenia | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 3725ddbe-ce91-4469-991e-8c5ed048c618
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: a916e1d3410957a3f03c82436dee6f84bd57726b
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line"></a>Porady: dołączanie profilera do aplikacji sieci Web ASP.NET w celu zbierania statystyk aplikacji przy użyciu wiersza polecenia
W tym temacie opisano sposób użycia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzia wiersza polecenia narzędzi profilowania dołączanie profilera do aplikacji sieci Web ASP.NET i zbieranie statystyk wydajności za pomocą metody pobierania próbek.  
  
> [!NOTE]
>  Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagane znaczących zmian w sposobie profilera Visual Studio zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows wymagają również nowe techniki kolekcji. Zobacz [narzędzi wydajności w przypadku aplikacji systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
>   
>  Dodawanie danych o interakcji między warstwy do uruchomienia profilowania wymaga określonych procedur przy użyciu wiersza polecenia narzędzia profilowania. Zobacz [zbierania danych o interakcji między warstwy](../profiling/adding-tier-interaction-data-from-the-command-line.md).  
>   
>  Narzędzia wiersza polecenia narzędzi profilowania znajdują się w podkatalogu narzędzia \Team Tools\Performance [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] katalogu instalacyjnego. Na komputerach 64-bitowych zarówno 64-bitowe i 32-bitowe wersje narzędzia są dostępne. Za pomocą narzędzi wiersza polecenia profilera, możesz dodać ścieżkę narzędzia do zmiennej środowiskowej PATH w oknie wiersza polecenia lub dodać go do samo polecenie. Aby uzyskać więcej informacji, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Do zbierania danych wydajności z aplikacji sieci Web ASP.NET, należy zainicjować zmienne środowisko i komputer, który jest hostem aplikacji sieci Web ASP.NET, należy ponownie skonfigurować serwer sieci Web do profilowania.  
  
 Następnie możesz dołączanie profilera do procesu roboczego programu ASP.NET, który jest hostem witryny sieci Web. Gdy profiler jest dołączony do aplikacji, można wstrzymywać i wznawiać zbierania danych.  
  
 Aby zakończyć sesję profilowania, profilera musi zostać odłączony od profilowana aplikacja i profilera muszą zostać jawnie wyłączone. W większości przypadków zaleca się czyszczenie profilowania zmienne środowiskowe z końcem sesji.  
  
## <a name="starting-the-profiler-and-attaching-to-an-aspnet-web-application"></a>Uruchamianie profilera i dołączanie do aplikacji sieci Web ASP.NET  
  
#### <a name="to-attach-the-profiler-to-an-aspnet-web-application"></a>Aby dołączanie profilera do aplikacji sieci Web ASP.NET  
  
1.  Otwórz okno wiersza polecenia.  
  
2.  Inicjowanie profilowania zmiennych środowiskowych. Wpisz:  
  
     **VSPerfClrEnv /globalsampleon** [**/samplelineoff**]  
  
    -   **/globalsampleon** umożliwia próbkowania.  
  
    -   **/samplelineoff** wyłącza przypisania zebranych danych do wierszy kodu określonego źródła. W przypadku wybrania tej opcji, danych jest przypisane tylko do funkcji.  
  
3.  Uruchom ponownie komputer.  
  
4.  Uruchom profilera. Typ:**VSPerfCmd** [/start](../profiling/start.md)**: Przykładowe** [/output](../profiling/output.md)**:**`OutputFile`[`Options`]  
  
    -   **/Start:sample** opcji inicjowania profilera.  
  
    -   **/Output:** `OutputFile` jest wymagany w przypadku opcji **/start**. `OutputFile` Określa nazwę i lokalizację profilowania pliku danych (Vsp).  
  
     Można zastosować dowolną z następujących opcji z **/start:sample** opcji.  
  
    > [!NOTE]
    >  **User** i **/crosssession** opcje są zwykle wymagane dla aplikacji ASP.NET.  
  
    |Opcja|Opis|  
    |------------|-----------------|  
    |[/ User](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName`|Określa nazwę domeny i użytkownika konta, który jest właścicielem proces roboczy programu ASP.NET. Ta opcja jest wymagana, jeśli proces jest uruchomiony jako użytkownik innego niż zalogowanego użytkownika. Właściciel procesu znajduje się w kolumnie Nazwa użytkownika na karcie Procesy Menedżera zadań systemu Windows.|  
    |[/crosssession](../profiling/crosssession.md)|Włącza profilowanie procesów w innych sesji logowania. Ta opcja jest wymagana, jeśli aplikacja ASP.NET działa w innej sesji. Identyfikator sesji jest wyświetlane w kolumnie Identyfikator sesji, na karcie Procesy Menedżera zadań systemu Windows. **/CS** może być określony jako skrót **/crosssession**.|  
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Określa licznik wydajności systemu Windows, które będą zbierane podczas profilowania.|  
    |[/automark](../profiling/automark.md) **:** `Interval`|Za pomocą **/wincounter** tylko. Określa liczbę milisekund między zdarzeniami kolekcji liczników wydajności systemu Windows. Domyślna to 500 ms.|  
    |[/Events](../profiling/events-vsperfcmd.md) **:** `Config`|Określa zdarzenia funkcji Śledzenie zdarzeń systemu Windows (), które mają być zbierane podczas profilowania. Zdarzenia ETW są gromadzone w pliku oddzielne (ETL).|  
  
5.  Uruchom aplikację sieci Web ASP.NET w typowy sposób.  
  
6.  Dołączanie profilera do procesu roboczego programu ASP.NET. Typ:**VSPerfCmd** [/ dołączyć](../profiling/attach.md)**:**{`PID`&#124;`ProcName`} [`Sample Event`] [[/targetclr](../profiling/targetclr.md) **:**`Version`]  
  
    -   `PID` Określa identyfikator procesu procesu roboczego ASP.NET; `ProcName` Określa nazwę procesu roboczego. Można wyświetlić nazwy wszystkich uruchomionych procesów i identyfikatorów procesów w Menedżerze zadań systemu Windows.  
  
    -   Domyślnie wydajności, dane są pobierane co zegara procesora nie zostało zatrzymane 10 000 000 cykle. Jest to około 100 razy w ciągu sekundy na procesor 1GH. Można określić jedną z następujących **VSPerfCmd** opcje, aby zmienić interwał cyklu zegara lub określić zdarzenia różnych próbkowania.  
  
    |Zdarzenie próbkowania|Opis|  
    |------------------|-----------------|  
    |[/ Timer](../profiling/timer.md) **:** `Interval`|Powoduje interwał próbkowania liczby cykli zegara nie zostało zatrzymane, które są określone przez `Interval`.|  
    |[PF](../profiling/pf.md)[**:**`Interval`]|Zmiany zdarzenie próbkowania błędów strony. Jeśli `Interval` jest określony, ustawia liczbę błędów stron między próbkami. Domyślna to 10.|  
    |[sys](../profiling/sys-vsperfcmd.md)[`:``Interval`]|Zdarzenie próbkowania wywołań systemowych zmiany z procesu jądra systemu operacyjnego (syscalls). Jeśli `Interval` jest określony, ustawia liczbę wywołań między próbkami. Domyślna to 10.|  
    |[/ licznika](../profiling/counter.md) **:** `Config`|Zmiany zdarzenie próbkowania i interwał licznika wydajności procesora i interwał, w którym są określone w `Config`.|  
    |[/targetclr](../profiling/targetclr.md) **:** `Version`|Określa wersję środowisko uruchomieniowe języka wspólnego (CLR) do profilu po załadowaniu więcej niż jedną wersję środowiska uruchomieniowego w aplikacji.|  
  
    -   **targetclr:** `Version` Określa wersję środowiska CLR do profilowania po załadowaniu więcej niż jedną wersję środowiska uruchomieniowego w aplikacji. Opcjonalna.  
  
## <a name="controlling-data-collection"></a>Kontrolowanie zbierania danych  
 Gdy aplikacja jest uruchomiona, można kontrolować zbierania danych przez uruchamianie i zatrzymywanie przy zapisywaniu danych do pliku przy użyciu **VSPerfCmd.exe** opcje. Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonania programu, takie jak uruchamianie lub zamykanie aplikacji.  
  
#### <a name="to-start-and-stop-data-collection"></a>Aby uruchomić i zatrzymać zbieranie danych  
  
-   Następujące pary **VSPerfCmd** opcje uruchamiania i zatrzymywania zbierania danych. Określ opcję każdego w osobnym wierszu polecenia. Włączenie funkcji zbierania danych można włączać i wyłączać wiele razy.  
  
    |Opcja|Opis|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Uruchamia (**/globalon**) lub zatrzymania (**/globaloff**) zbierania danych dla wszystkich procesów.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` **/processoff:** `PID`|Uruchamia (**/processon**) lub zatrzymania (**/processoff**) zbierania danych dla procesu, który jest określony przez `PID`.|  
    |[/ dołączyć](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [/ detach](../profiling/detach.md)[**:**{`PID`&#124;`ProcName`}]|**/ dołączyć** rozpoczyna zbieranie danych przez proces określony przez `PID` lub nazwa procesu (Nazwa_procedury). **/ detach** zatrzymuje zbieranie danych dla określonego procesu lub dla wszystkich procesów, jeśli nie określono określonego procesu.|  
  
## <a name="ending-the-profiling-session"></a>Kończenie sesji profilowania  
 Aby zakończyć sesję profilowania, Zamknij [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci Web, a następnie użyj Internet Information Services (IIS) **IISReset** polecenie, aby zamknąć [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] proces roboczy. Wywołanie **VSPerfCmd** [/shutdown](../profiling/shutdown.md) opcję, aby wyłączyć profilera i zamknij plik danych profilowania.  
  
 **VSPerfClrEnv /globaloff** polecenie czyści profilowania zmiennych środowiskowych. Należy ponownie uruchomić komputer, aby nowe ustawienia środowiska do zastosowania.  
  
 **VSPerfClrEnv /globaloff** polecenie usuwa profilowania zmiennych środowiskowych, ale konfiguracja systemu nie zostanie zresetowana do ponownego uruchomienia komputera.  
  
#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania  
  
1.  Wykonaj jedną z następujących czynności, aby odłączyć profilera z aplikacji docelowej:  
  
    -   Typ **VSPerfCmd / detach**  
  
         —lub—  
  
    -   Zamknij [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] proces roboczy.  
  
2.  Zamknij profilera. Typ:**VSPerfCmd**  [ /shutdown](../profiling/shutdown.md)  
  
3.  (Opcjonalnie) Wyczyść profilowania zmiennych środowiskowych. Wpisz:  
  
     **VSPerfCmd /globaloff**  
  
4.  Uruchom ponownie komputer.  
  
## <a name="see-also"></a>Zobacz też  
 [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Widok danych metody próbkowania](../profiling/profiler-sampling-method-data-views.md)