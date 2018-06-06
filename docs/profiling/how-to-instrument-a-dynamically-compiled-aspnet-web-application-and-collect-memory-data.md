---
title: 'Porady: Instrumentacja dynamicznie skompilowanych ASP.NET sieci web aplikacji i zbieranie danych pamięci przy użyciu wiersza polecenia profilera | Dokumentacja firmy Microsoft'
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
ms.openlocfilehash: 6ef538ac7316375b14dcbd951d5cf89702cdde0e
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2018
ms.locfileid: "34815590"
---
# <a name="how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line"></a>Porady: Instrumentacja dynamicznie skompilowanej aplikacji sieci web ASP.NET i zbieranie danych pamięci przy użyciu wiersza polecenia profilera
W tym temacie opisano sposób użycia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] profilowanie wiersza polecenia narzędzi do gromadzenia szczegółowych .NET pamięci alokacji i obiekt okres istnienia danych dynamicznie skompilowanej [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci web przy użyciu metoda profilowania instrumentacji.  
  
> [!NOTE]
>  Narzędzia wiersza polecenia narzędzi profilowania znajdują się w *narzędzia \Team Tools\Performance* podkatalog [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] katalogu instalacyjnego. Na komputerach 64-bitowych zarówno 64-bitowe i 32-bitowe wersje narzędzia są dostępne. Za pomocą narzędzi wiersza polecenia profilera, możesz dodać ścieżkę narzędzia do zmiennej środowiskowej PATH w oknie wiersza polecenia lub dodać go do samo polecenie. Aby uzyskać więcej informacji, zobacz [Określ ścieżkę do narzędzia wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Do zbierania danych dotyczących wydajności z [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci web, możesz zmodyfikować *web.config* plik w aplikacji docelowej, aby włączyć [VSInstr.exe](../profiling/vsinstr.md) narzędzia Instrumentacja dynamicznie skompilowanej pliki aplikacji. Następnie należy użyć [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) narzędzie w celu skonfigurowania serwera obsługującego [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci Web i włączyć .NET pamięci profilowanie przez ustawienie zmiennych środowiskowych odpowiednie i uruchom ponownie komputer.  
  
 Aby zbierać dane, uruchom profilera, a następnie uruchom aplikacji docelowej. Profiler jest dołączony do aplikacji, można wstrzymywać i wznawiać zbierania danych. Po zebraniu danych, zamknij aplikację, Zamknij proces roboczy usług Internet Information Services (IIS) i następnie wyłącz profilera.  
  
 Po zakończeniu pracy profilowania przywrócić *web.config* plików i serwer sieci web do oryginalnego stanu.  
  
## <a name="configure-the-aspnet-web-application-and-the-web-server"></a>Konfigurowanie serwera sieci web i aplikacji sieci web ASP.NET  
  
#### <a name="to-configure-the-aspnet-web-application-and-the-web-server"></a>Aby skonfigurować serwer sieci web i aplikacji sieci web ASP.NET  

1.  Modyfikowanie *web.config* plik w aplikacji docelowej. Zobacz [porady: modyfikowanie plików web.config w celu Instrumentacja i profilowania dynamicznie skompilowanych aplikacji sieci web ASP.NET](../profiling/how-to-modify-web-config-files-to-instrument-dynamically-compiled-aspnet-apps.md).  
  
2.  Otwórz okno wiersza polecenia na komputerze, który jest hostem aplikacji sieci web.  
  
3.  Inicjowanie profilowania zmiennych środowiskowych. Wpisz:  
  
     **VSPerfClrEnv /globaltracegc**  
  
     —lub—  
  
     **VSPerfClrEnv /globaltracegclife**  
  
    -   **/globaltracegc** umożliwia zbieranie danych alokacji pamięci.  
  
    -   **/globaltracegclife** umożliwia zbieranie danych alokacji pamięci oraz danych o okresie istnienia obiektu.  
  
4.  Uruchom ponownie komputer.  
  
## <a name="run-the-profiling-session"></a>Uruchom sesję profilowania  
  
#### <a name="to-profile-the-aspnet-web-application"></a>Do profilu aplikacji sieci web ASP.NET  
  
1.  Uruchom profilera. Wpisz:  
  
     **VSPerfCmd** [/start](../profiling/start.md) **: śledzenia** [/output](../profiling/output.md) **:** `OutputFile` [`Options`]  
  
    -   **/Start:trace** opcji inicjowania profilera.  
  
    -   **/Output:** `OutputFile` jest wymagany w przypadku opcji **/start**. `OutputFile` Określa nazwę i lokalizację danych profilowania (. *Vsp*) pliku.  
  
     Można użyć dowolnego z następujących opcji z **/start:trace** opcji.  
  
    > [!NOTE]
    >  **User** i **/crosssession** opcje są zwykle wymagane dla aplikacji ASP.NET.  
  
    |Opcja|Opis|  
    |------------|-----------------|  
    |[/ User](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName`|Określa nazwę domeny i opcjonalną konta, który jest właścicielem [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] proces roboczy. Ta opcja jest wymagana, jeśli proces jest uruchomiony jako użytkownik innego niż zalogowanego użytkownika. Nazwa jest wyświetlana w **nazwy użytkownika** kolumny na **procesów** kartę Menedżera zadań systemu Windows.|  
    |[/crosssession](../profiling/crosssession.md)|Włącza profilowanie procesów w innych sesji. Ta opcja jest wymagana, jeśli aplikacja jest uruchomiona w innej sesji. Identyfikator jest wymieniony w sesji **identyfikator sesji** kolumny na **procesów** kartę Menedżera zadań systemu Windows. **/CS** może być określony jako skrót **/crosssession**.|  
    |[/globaloff](../profiling/globalon-and-globaloff.md)|Uruchamia, który wstrzymana profilera ze zbierania danych. Użyj [/globalon](../profiling/globalon-and-globaloff.md) wznowienie profilowania.|  
    |[/ licznika](../profiling/counter.md) **:** `Config`|Zbiera informacje o wydajności procesora licznika określone w `Config`. Informacje o liczniku jest dodawany do danych zbieranych na każdym zdarzeniu profilowania.|  
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Określa licznik wydajności systemu Windows, które będą zbierane podczas profilowania.|  
    |[/automark](../profiling/automark.md) **:** `Interval`|Za pomocą **/wincounter** tylko. Określa liczbę milisekund między zdarzeniami kolekcji liczników wydajności systemu Windows. Domyślna to 500 ms.|  
    |[/Events](../profiling/events-vsperfcmd.md) **:** `Config`|Określa zdarzenia funkcji Śledzenie zdarzeń systemu Windows (), które mają być zbierane podczas profilowania. Zdarzenia ETW są gromadzone w oddzielnej (. *etl*) pliku.|  
  
2.  Uruchom [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci web w typowy sposób.  
  
## <a name="control-data-collection"></a>Sterowanie zbieraniem danych  
 Po uruchomieniu aplikacji docelowej zbieranie danych można kontrolować przy uruchamianie i zatrzymywanie zapisywanie danych w pliku danych profilera przy użyciu *VSPerfCmd.exe* opcje. Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonania programu, takie jak uruchamianie lub zamykanie aplikacji.  
  
#### <a name="to-start-and-stop-data-collection"></a>Aby uruchomić i zatrzymać zbieranie danych  
  
-   Następujące pary opcje uruchamiania i zatrzymywania zbierania danych. Określ opcję każdego w osobnym wierszu polecenia. Włączenie funkcji zbierania danych można włączać i wyłączać wiele razy.  
  
    |Opcja|Opis|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Uruchamia (**/globalon**) lub zatrzymania (**/globaloff**) zbierania danych dla wszystkich procesów.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Uruchamia (**/processon**) lub zatrzymania (**/processoff**) zbierania danych przez proces określony przez identyfikator procesu (`PID`).|  
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|Uruchamia (**/threadon**) lub zatrzymania (**/threadoff**) zbierania danych dla wątku określony przez identyfikator wątku (`TID`).|  
  
-   Można również użyć **VSPerfCmd.exe**[/oznaczyć](../profiling/mark.md) opcję, aby wstawić znacznik profilowania do pliku danych. **/Oznaczyć** polecenie dodaje identyfikator sygnatury czasowej i opcjonalny zdefiniowane przez użytkownika ciąg tekstowy. Znaczniki można filtrować dane w widoków danych i raportów profilera.  
  
## <a name="end-the-profiling-session"></a>Kończenie sesji profilowania  
 Aby zakończyć sesję profilowania, Zamknij element docelowy [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci web, Zatrzymaj Internet Information Services (IIS) do zatrzymania PROFILOWANEGO procesu, a następnie zamknij profilera. Następnie uruchom ponownie usługi IIS.  
  
#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania  
  
1.  Zamknij [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci web.  
  
2.  Zamknij [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] proces roboczy resetując Internet Information Services (IIS). Wpisz:  
  
     **Polecenie IISReset/Stop**  
  
3.  Zamknij profilera. Wpisz:  
  
     **VSPerfCmd**  [ /shutdown](../profiling/shutdown.md)  
  
4.  Uruchom ponownie usługi IIS. Wpisz:  
  
     **Polecenie IISReset/Start**  
  
## <a name="restore-the-application-and-computer-configuration"></a>Przywróć konfigurację aplikacji i komputera  
 Po ukończeniu wszystkich profilowania, Zastąp *web.config* , wyczyść profilowania zmiennych środowiskowych, a następnie ponownie uruchom komputer, aby przywrócić serwer i [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji do oryginalnego stanu.  
  
#### <a name="to-restore-the-application-and-computer-configuration"></a>Aby przywrócić konfigurację aplikacji i komputera  
  
1.  Zastąp *web.config* plik z kopią oryginalnego pliku.  
  
2.  (Opcjonalnie). Wyczyść profilowania zmiennych środowiskowych. Wpisz:  
  
     **VSPerfCmd /globaloff**  
  
3.  Uruchom ponownie komputer.  
  
## <a name="see-also"></a>Zobacz także  
 [Aplikacje sieci web ASP.NET profilu](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Widoki danych pamięci .NET](../profiling/dotnet-memory-data-views.md)
