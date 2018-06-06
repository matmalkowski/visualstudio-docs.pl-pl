---
title: 'Porady: Instrumentacja statycznie skompilowanej sieci Web ASP.NET aplikacji i zbieranie danych pamięci przy użyciu wiersza polecenia profilera | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: ea1dcb7c-1dc3-49ff-9418-8795b5b3d3bc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a1081f0f0f1cc261179192520108e49f5cf4aaa5
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2018
ms.locfileid: "34815759"
---
# <a name="how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line"></a>Porady: Instrumentacja statycznie skompilowanej aplikacji sieci web ASP.NET i zbieranie danych pamięci przy użyciu wiersza polecenia profilera
W tym artykule opisano sposób użycia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzia wiersza polecenia narzędzi profilowania do Instrumentacja wstępnie skompilowanym [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] składników sieci web lub witryny sieci web i zbieranie alokacji pamięci .NET, okres istnienia obiektów i szczegółowych danych o chronometrażu.  
  
> [!NOTE]
>  Narzędzia wiersza polecenia narzędzi profilowania znajdują się w *narzędzia \Team Tools\Performance* podkatalog [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] katalogu instalacyjnego. Na komputerach 64-bitowych zarówno 64-bitowe i 32-bitowe wersje narzędzia są dostępne. Za pomocą narzędzi wiersza polecenia profilera, możesz dodać ścieżkę narzędzia do zmiennej środowiskowej PATH w oknie wiersza polecenia lub dodać go do samo polecenie. Aby uzyskać więcej informacji, zobacz [Określ ścieżkę do narzędzia wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Aby zbierać dane z [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] składników sieci Web przy użyciu metody instrumentacji, użyj [VSInstr.exe](../profiling/vsinstr.md) narzędzie do generowania instrumentowanej wersji składnika. Na komputerze, który obsługuje składnika wersja nieinstrumentowanego składnika Zamień instrumentowaną wersję. Następnie należy użyć [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) narzędzia, aby zainicjować zmienne globalne profilowania środowiska i uruchom ponownie komputer-host. Następnie należy uruchomić profilera.  
  
 Po wykonaniu składników instrumentowanych danych o chronometrażu są zbierane automatycznie w pliku danych. Można wstrzymywać i wznawiać zbierania danych podczas sesji profilowania.  
  
 Aby zakończyć sesję profilowania, Zamknij [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] procesu roboczego, który hostuje składnik, a następnie jawnie Wyłącz profilera. W większości przypadków zaleca się czyszczenie profilowania zmienne środowiskowe z końcem sesji.  
  
## <a name="start-to-profile"></a>Rozpocznij profilu  
  
#### <a name="to-instrument-an-aspnet-web-component-and-start-profiling"></a>Instrumentacja składników sieci Web ASP.NET i Rozpocznij profilowanie  
  
1.  Użyj **VSInstr** narzędzie do generowania instrumentowanej wersji aplikacji docelowej. Jeśli to konieczne, Zamień instrumentowanych danych binarnych plików binarnych aplikacji na komputerze hosta platformy ASP.NET.  
  
2.  Otwórz okno wiersza polecenia  
  
3.  Inicjowanie .NET profilowania zmiennych środowiskowych. W oknie wiersza polecenia wpisz:  
  
     **VSPerfClrEnv /globaltracegc**  
  
     —lub—  
  
     **VSPerfClrEnv /globaltracegclife**  
  
    -   **/globaltracegc** zbiera alokacji pamięci .NET i danych o chronometrażu.  
  
    -   **/globaltracegclife** alokacji pamięci .NET zbiera, okres istnienia obiektów i szczegółowych danych o chronometrażu.  
  
4.  Uruchom ponownie komputer.  
  
5.  Otwórz okno wiersza polecenia.  
  
6.  Uruchom profilera. W oknie wiersza polecenia wpisz:  
  
     **/ OUTPUT /start:trace VSPerfCmd:** `OutputFile` [`Options`]  
  
    -   [/Start](../profiling/start.md)**: śledzenia** opcji inicjowania profilera.  
  
    -   [/Output](../profiling/output.md)**:** `OutputFile` jest wymagany w przypadku opcji **/start**. `OutputFile` Określa nazwę i lokalizację profilowania pliku danych (Vsp).  
  
     Można użyć dowolnego z następujących opcji z **/start:trace** opcji.  
  
    > [!NOTE]
    >  **User** i **/crosssession** opcje są zwykle wymagane dla aplikacji ASP.NET.  
  
    |Opcja|Opis|  
    |------------|-----------------|  
    |[/ User](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName`|Określa opcjonalne domenę i nazwę użytkownika konta, do której należy proces roboczy programu ASP.NET. Ta opcja jest wymagana, jeśli proces jest uruchomiony jako użytkownik, który różni się od zalogowanego użytkownika. Nazwa jest wyświetlana w **nazwy użytkownika** kolumny na **procesów** kartę Menedżera zadań systemu Windows.|  
    |[/crosssession](../profiling/crosssession.md)|Włącza profilowanie procesów w innych sesji. Ta opcja jest wymagana, jeśli aplikacja jest uruchomiona w innej sesji. Identyfikator sesji jest wymieniony w kolumnie Identyfikator sesji na **procesów** kartę Menedżera zadań systemu Windows. **/CS** może być określony jako skrót **/crosssession**.|  
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Określa licznik wydajności systemu Windows, które będą zbierane podczas profilowania.|  
    |[/automark](../profiling/automark.md) **:** `Interval`|Za pomocą **/wincounter** tylko. Określa liczbę milisekund między zdarzeniami kolekcji liczników wydajności systemu Windows. Domyślna to 500 ms.|  
    |[/Events](../profiling/events-vsperfcmd.md) **:** `Config`|Określa zdarzenia funkcji Śledzenie zdarzeń systemu Windows (), które mają być zbierane podczas profilowania. Zdarzenia ETW są gromadzone w pliku oddzielne (ETL).|  
    |[/globaloff](../profiling/globalon-and-globaloff.md)|Do uruchomienia profilera ze zbierania danych wstrzymana, Dodaj **/globaloff** opcji w celu **/start** wiersza polecenia. Użyj **/globalon** wznowienie profilowania.|  
  
7.  Otwórz witrynę sieci web, którą zawiera składnik instrumentowanych.  
  
## <a name="control-data-collection"></a>Sterowanie zbieraniem danych  
 Po uruchomieniu aplikacji docelowej zbieranie danych można kontrolować przy uruchamianie i zatrzymywanie przy zapisywaniu danych do pliku przy użyciu *VSPerfCmd.exe* opcje. Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonania programu, takie jak uruchamianie lub zamykanie aplikacji.  
  
#### <a name="to-start-and-stop-data-collection"></a>Aby uruchomić i zatrzymać zbieranie danych  
  
-   Następujące pary opcje uruchamiania i zatrzymywania zbierania danych. Określ opcję każdego w osobnym wierszu polecenia. Włączenie funkcji zbierania danych można włączać i wyłączać wiele razy.  
  
    |Opcja|Opis|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Uruchamia (**/globalon**) lub zatrzymania (**/globaloff**) zbierania danych dla wszystkich procesów.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Uruchamia (**/processon**) lub zatrzymania (**/processoff**) zbierania danych przez proces określony przez identyfikator procesu (`PID`).|  
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|Uruchamia (**/threadon**) lub zatrzymania (**/threadoff**) zbierania danych dla wątku określony przez identyfikator wątku (`TID`).|  
  
## <a name="end-the-profiling-session"></a>Kończenie sesji profilowania  
 Aby zakończyć sesję profilowania, Zamknij [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci web, a następnie użyj Internet Information Services (IIS) **IISReset** polecenie, aby zamknąć [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] proces roboczy. Wywołanie **VSPerfCmd** [/shutdown](../profiling/shutdown.md) opcję, aby wyłączyć profilera i zamknij plik danych profilowania. **VSPerfClrEnv /globaloff** polecenie czyści profilowania zmiennych środowiskowych. Należy ponownie uruchomić komputer, aby nowe ustawienia środowiska do zastosowania.  
  
#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania  
  
1.  Zamknij [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci web.  
  
2.  Zamknij [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] proces roboczy. Wpisz:  
  
     **Polecenie IISReset/Stop**  
  
3.  Zamknij profilera. Wpisz:  
  
     **VSPerfCmd/shutdown**  
  
4.  (Opcjonalnie). Wyczyść profilowania zmiennych środowiskowych. Wpisz:  
  
     **VSPerfCmd /globaloff**  
  
5.  Uruchom ponownie komputer. Jeśli to konieczne, uruchom ponownie usługi IIS. Wpisz:  
  
     **Polecenie IISReset/Start**  
  
## <a name="see-also"></a>Zobacz także  
 [Aplikacje sieci web ASP.NET profilu](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Widoki danych pamięci .NET](../profiling/dotnet-memory-data-views.md)