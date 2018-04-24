---
title: 'Porady: Instrumentacja dla platformy .NET usługi i zbieranie danych pamięci przy użyciu wiersza polecenia profilera | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 2fa072fc-05fe-4420-99c0-51d2ea3ac4ce
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 03c676100487acb7aff9cb28071192ff6b04ed29
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-instrument-a-net-framework-service-and-collect-memory-data-by-using-the-profiler-command-line"></a>Porady: instrumentacja usługi .NET Framework i zbieranie danych pamięci przy użyciu wiersza polecenia profilera
W tym temacie opisano sposób użycia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzia wiersza polecenia narzędzi profilowania instrumentem [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] usługi i zbieranie danych użycia pamięci. Można zbierać dane alokacji pamięci lub zebrać alokacji pamięci i danych o okresie istnienia obiektu.  
  
> [!NOTE]
>  Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagane znaczących zmian w sposobie profilera Visual Studio zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows wymagają również nowe techniki kolekcji. Zobacz [narzędzi wydajności w przypadku aplikacji systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
> [!NOTE]
>  Jeśli usługi nie można uruchomić ponownie po uruchomieniu komputera nie może profilować usługi przy użyciu metody instrumentacji, takie usługi, które uruchamiane podczas uruchamiania systemu operacyjnego.  
>   
>  Narzędzia wiersza polecenia narzędzi profilowania znajdują się w podkatalogu narzędzia \Team Tools\Performance [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] katalogu instalacyjnego. Na komputerach 64-bitowym zarówno w przypadku 64-bitowych, jak i 32-bitowe wersje narzędzia są dostępne. Za pomocą narzędzi wiersza polecenia profilera, możesz dodać ścieżkę narzędzia do zmiennej środowiskowej PATH w oknie wiersza polecenia lub dodać go do samo polecenie. Aby uzyskać więcej informacji, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
## <a name="starting-the-profiling-session"></a>Rozpoczynanie sesji profilowania  
 Do zbierania danych dotyczących wydajności z [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] usługi, użyj [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) narzędzia, aby zainicjować zmienne środowiskowe odpowiednie i [VSInstr.exe](../profiling/vsinstr.md) narzędzia do tworzenia Instrumentacją kopia pliku binarnego.  
  
 Aby skonfigurować go na potrzeby profilowania, należy ponownie uruchomić komputer obsługujący usługę. Można również uruchomić usługę ręcznie z Menedżera kontroli usług. Następnie uruchom profilera, a następnie uruchom [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] usługi.  
  
 Po wykonaniu składników instrumentowanych pamięci dane są zbierane automatycznie w pliku danych. Można wstrzymywać i wznawiać zbierania danych podczas sesji profilowania.  
  
 Aby zakończyć sesję profilowania, zamknąć usługę i jawnie zamknięty profilera. W większości przypadków zaleca się czyszczenie profilowania zmienne środowiskowe z końcem sesji.  
  
#### <a name="to-begin-profiling-a-net-framework-service"></a>Aby rozpocząć profilowanie usługi .NET Framework  
  
1.  Otwórz okno wiersza polecenia.  
  
2.  Użyj **VSInstr** narzędzie do generowania instrumentowaną wersję pliku binarnego usługi.  
  
3.  Użyj Menedżera sterowania usługami zastąpić instrumentowanej wersji oryginalnego pliku binarnego. Upewnij się, że usługa uruchamiana ma ustawiony ręczny.  
  
4.  Inicjowanie profilowania zmiennych środowiskowych. Wpisz:  
  
     **VSPerfClrEnv** {**/globaltracegc** &#124; **/globaltracegclife**}  
  
    -   **/globaltracegc** i **/globaltracegclife** włączyć opcję zbierania danych okres istnienia alokacji i obiektu pamięci.  
  
        |Opcja|Opis|  
        |------------|-----------------|  
        |**/globaltracegc**|Zbiera tylko dane alokacji pamięci.|  
        |**/globaltracegclife**|Zbiera dane okresu istnienia alokacji i obiektu pamięci.|  
  
5.  Uruchom ponownie komputer.  
  
6.  Otwórz okno wiersza polecenia.  
  
7.  Uruchom profilera. Wpisz:  
  
     **VSPerfCmd**[/start](../profiling/start.md) **: śledzenia**[/output](../profiling/output.md) **:** `OutputFile` [`Options`]      
  
    -   **/Start: rywalizacji** opcji inicjowania profilera.  
  
    -   **/Output:** `OutputFile` jest wymagany w przypadku opcji **/start**. `OutputFile` Określa nazwę i lokalizację profilowania pliku danych (Vsp).  
  
     Można użyć dowolnego z następujących opcji z **/start:sample** opcji.  
  
    > [!NOTE]
    >  **User** i **/crosssession** opcje są zwykle wymagane dla usług.  
  
    |Opcja|Opis|  
    |------------|-----------------|  
    |[/ User](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName`|Określa nazwę domeny i użytkownika konta, który jest właścicielem proces roboczy programu ASP.NET. Ta opcja jest wymagana, jeśli proces jest uruchomiony jako użytkownik innego niż zalogowanego użytkownika. Właściciel procesu znajduje się w kolumnie Nazwa użytkownika na karcie Procesy Menedżera zadań systemu Windows.|  
    |[/crosssession](../profiling/crosssession.md)|Włącza profilowanie procesów w innych sesji logowania. Ta opcja jest wymagana, jeśli aplikacja ASP.NET działa w innej sesji. Identyfikator sesji jest wymieniony w kolumnie Identyfikator sesji, na karcie Procesy Menedżera zadań systemu Windows. **/CS** może być określony jako skrót **/crosssession**.|  
    |[/waitstart](../profiling/waitstart.md)[**:**`Interval`]|Określa liczbę sekund oczekiwania profilera zainicjować przed zwraca błąd. Jeśli `Interval` nie zostanie określony, profilera oczekiwania przez czas nieokreślony. Domyślnie **/start** natychmiast kończy pracę.|  
    |[/globaloff](../profiling/globalon-and-globaloff.md)|Do uruchomienia profilera ze zbierania danych wstrzymana, Dodaj **/globaloff** opcji w celu **/start** wiersza polecenia. Użyj **/globalon** wznowienie profilowania.|  
    |[/ licznika](../profiling/counter.md) **:** `Config`|Zbiera informacje o wydajności procesora licznika określony w konfiguracji. Informacje o liczniku jest dodawany do danych zbieranych na każdym zdarzeniu profilowania.|  
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Określa licznik wydajności systemu Windows, które będą zbierane podczas profilowania.|  
    |[/automark](../profiling/automark.md) **:** `Interval`|Za pomocą **/wincounter** tylko. Określa liczbę milisekund między zdarzeniami kolekcji liczników wydajności systemu Windows. Domyślna to 500 ms.|  
    |[/Events](../profiling/events-vsperfcmd.md) **:** `Config`|Określa zdarzenia funkcji Śledzenie zdarzeń systemu Windows (), które mają być zbierane podczas profilowania. Zdarzenia ETW są gromadzone w pliku oddzielne (ETL).|  
  
8.  W razie potrzeby uruchom usługę.  
  
9. Dołączanie profilera do usługi. Wpisz:  
  
     **VSPerfCmd / dołączyć:**`PID`&#124;`ProcessName`  
  
    -   Określ identyfikator procesu lub proces nazwę usługi. Można wyświetlić nazwy wszystkich uruchomionych procesów i identyfikatorów procesów w Menedżerze zadań systemu Windows.  
  
## <a name="controlling-data-collection"></a>Kontrolowanie zbierania danych  
 Gdy usługa jest uruchomiona, można kontrolować zbierania danych przez uruchamianie i zatrzymywanie przy zapisywaniu danych do pliku z **VSPerfCmd.exe** opcje. Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonania programu, takie jak uruchamianie lub zamykanie aplikacji.  
  
#### <a name="to-start-and-stop-data-collection"></a>Aby uruchomić i zatrzymać zbieranie danych  
  
-   Następujące pary **VSPerfCmd** opcje uruchamiania i zatrzymywania zbierania danych. Określ opcję każdego w osobnym wierszu polecenia. Włączenie funkcji zbierania danych można włączać i wyłączać wiele razy.  
  
    |Opcja|Opis|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Uruchamia (**/globalon**) lub zatrzymania (**/globaloff**) zbierania danych dla wszystkich procesów.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Uruchamia (**/processon**) lub zatrzymania (**/processoff**) zbierania danych przez proces określony przez identyfikator procesu (`PID`).|  
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|Uruchamia (**/threadon**) lub zatrzymania (**/threadoff**) zbierania danych dla wątku określony przez identyfikator wątku (`TID`).|  
  
## <a name="ending-the-profiling-session"></a>Kończenie sesji profilowania  
 Aby zakończyć sesję profilowania, zamknij aplikację, która jest uruchomiony składnik instrumentowanych Zacznij **VSPerfCmd** [/shutdown](../profiling/shutdown.md) opcję, aby wyłączyć profilera i zamknij plik danych profilowania. **VSPerfClrEnv /globaloff** polecenie czyści profilowania zmiennych środowiskowych.  
  
#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania  
  
1.  Zatrzymaj usługę z Menedżera kontroli usług.  
  
2.  Zamknij profilera. Wpisz:  
  
     **VSPerfCmd/shutdown**  
  
3.  Po ukończeniu wszystkich profilowania, wyczyść profilowania zmiennych środowiskowych. Wpisz:  
  
     **VSPerfClrEnv /globaloff**  
  
     Zastąp oryginalny instrumentowanych modułu. Jeśli to konieczne, należy ponownie skonfigurować typ uruchomienia usługi.  
  
4.  Uruchom ponownie komputer.  
  
## <a name="see-also"></a>Zobacz też  
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)   
 [Widoki danych pamięci .NET](../profiling/dotnet-memory-data-views.md)