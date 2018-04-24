---
title: 'Porady: Instrumentacja dynamicznie skompilowanej aplikacji ASP.NET Web i zbieranie danych o chronometrażu przy użyciu profilera przy użyciu wiersza polecenia | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 7c1f3073b1b3ebeb142805e5d34097c82e038e67
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line"></a>Porady: instrumentacja dynamicznie skompilowanej aplikacji sieci Web ASP.NET i zbieranie szczegółowych danych o chronometrażu przy użyciu wiersza polecenia profilera

W tym temacie opisano sposób użycia narzędzia wiersza polecenia programu Visual Studio Profiling Tools do zbierania danych o chronometrażu dla dynamicznie skompilowanej [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji za pomocą metoda profilowania instrumentacji.

> [!NOTE]
> Narzędzia wiersza polecenia narzędzi profilowania znajdują się w podkatalogu narzędzia \Team Tools\Performance [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] katalogu instalacyjnego. Na komputerach 64-bitowych zarówno 64-bitowe i 32-bitowe wersje narzędzia są dostępne. Za pomocą narzędzi wiersza polecenia profilera, możesz dodać ścieżkę narzędzia do zmiennej środowiskowej PATH w oknie wiersza polecenia lub dodać go do samo polecenie. Aby uzyskać więcej informacji, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).

Aby zbierać dane dotyczące wydajności z [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci Web, można zmodyfikować pliku web.config aplikacji docelowej, aby włączyć [VSInstr.exe](../profiling/vsinstr.md) narzędzia Instrumentacja dynamicznie skompilowanej aplikacji plików. Następnie należy użyć [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) narzędzia, aby ustawić zmienne środowiskowe odpowiednie na serwerze sieci Web, aby włączyć profilowanie, a następnie ponownie uruchom komputer.

Uruchom profilera, a następnie uruchom aplikacji docelowej. Profiler jest dołączony do aplikacji, można wstrzymywać i wznawiać zbierania danych. Po zakończeniu profilowania, zamknij aplikację, Zamknij proces roboczy usług Internet Information Services (IIS) i następnie wyłącz profilera. Po zakończeniu pracy profilowania przywracania pliku web.config i serwer sieci Web do oryginalnego stanu.

## <a name="configuring-the-aspnet-web-application-and-the-web-server"></a>Konfigurowanie aplikacji sieci Web ASP.NET i serwera sieci Web

1. Modyfikowanie pliku web.config aplikacji docelowej. Zobacz [porady: modyfikowanie plików Web.Config w celu Instrumentowania i profilowania dynamicznie skompilowanych aplikacji sieci Web ASP.NET](../profiling/how-to-modify-web-config-files-to-instrument-and-profile-dynamically-compiled-aspnet-web-applications.md).

2. Otwórz okno wiersza polecenia.

3. Inicjowanie profilowania zmiennych środowiskowych. Wpisz:

     **VSPerfClrEnv /globaltraceon**

    - **/globaltraceon** Włącza profilowanie przy użyciu metody instrumentacji.

4. Uruchom ponownie komputer.

## <a name="running-the-profiling-session"></a>Uruchomiona sesja profilowania

1. Otwórz okno wiersza polecenia.

2. Uruchom profilera. Wpisz:

     **VSPerfCmd**[/start](../profiling/start.md) **: śledzenia**[/output](../profiling/output.md) **:** `OutputFile` [`Options`]    

    - **/Start:trace** opcji inicjowania profilera.

    - **/Output:** `OutputFile` jest wymagany w przypadku opcji **/start**. `OutputFile` Określa nazwę i lokalizację profilowania pliku danych (Vsp).

     Można użyć dowolnego z następujących opcji z **/start:trace** opcji.

    > [!NOTE]
    > **User** i **/crosssession** opcje są zwykle wymagane dla aplikacji ASP.NET.

    |Opcja|Opis|
    |------------|-----------------|
    |[/ User](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName`|Określa nazwę domeny i użytkownika konta, który jest właścicielem proces roboczy programu ASP.NET. Ta opcja jest wymagana, jeśli proces jest uruchomiony jako użytkownik innego niż zalogowanego użytkownika. Właściciel procesu znajduje się w kolumnie Nazwa użytkownika na karcie Procesy Menedżera zadań systemu Windows.|
    |[/crosssession](../profiling/crosssession.md)|Włącza profilowanie procesów w innych sesji logowania. Ta opcja jest wymagana, jeśli aplikacja ASP.NET działa w innej sesji. Identyfikator sesji jest wymienione w kolumnie Identyfikator sesji, na karcie Procesy Menedżera zadań systemu Windows. **/CS** może być określony jako skrót **/crosssession**.|
    |[/globaloff](../profiling/globalon-and-globaloff.md)|Uruchamia, który wstrzymana profilera ze zbierania danych. Użyj [/globalon](../profiling/globalon-and-globaloff.md) wznowienie profilowania.|
    |[/ licznika](../profiling/counter.md) **:** `Config`|Zbiera informacje licznika wydajności procesora, określonego w `Config`. Informacje o liczniku jest dodawany do danych, które są zbierane w każdym zdarzeniu profilowania.|
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Określa licznik wydajności systemu Windows, które będą zbierane podczas profilowania.|
    |[/automark](../profiling/automark.md) **:** `Interval`|Za pomocą **/wincounter** tylko. Określa liczbę milisekund między zdarzeniami kolekcji liczników wydajności systemu Windows. Domyślna to 500 ms.|
    |[/Events](../profiling/events-vsperfcmd.md) **:** `Config`|Określa zdarzenia funkcji Śledzenie zdarzeń systemu Windows (), które mają być zbierane podczas profilowania. Zdarzenia ETW są gromadzone w pliku oddzielne (ETL).|

3. Uruchom [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci Web w typowy sposób.

## <a name="controlling-data-collection"></a>Kontrolowanie zbierania danych

Po uruchomieniu aplikacji docelowej zbieranie danych można kontrolować przy uruchamianie i zatrzymywanie zapisywanie danych w pliku danych profilera przy użyciu **VSPerfCmd.exe** opcje. Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonania programu, takie jak uruchamianie lub zamykanie aplikacji.

- Następujące pary opcje uruchamiania i zatrzymywania zbierania danych. Określ opcję każdego w osobnym wierszu polecenia. Włączenie funkcji zbierania danych można włączać i wyłączać wiele razy.

    |Opcja|Opis|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Uruchamia (**/globalon**) lub zatrzymania (**/globaloff**) zbierania danych dla wszystkich procesów.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Uruchamia (**/processon**) lub zatrzymania (**/processoff**) zbierania danych przez proces określony przez identyfikator procesu (`PID`).|
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|Uruchamia (**/threadon**) lub zatrzymania (**/threadoff**) zbierania danych dla wątku określony przez identyfikator wątku (`TID`).|

- Można również użyć **VSPerfCmd.exe**[/oznaczyć](../profiling/mark.md) opcję, aby wstawić znacznik profilowania do pliku danych. **/Oznaczyć** polecenie dodaje identyfikator sygnatury czasowej i opcjonalny zdefiniowane przez użytkownika ciąg tekstowy. Znaczniki można filtrować dane w widoków danych i raportów profilera.

## <a name="ending-the-profiling-session"></a>Kończenie sesji profilowania

Aby zakończyć sesję profilowania, Zamknij element docelowy [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci Web, resetowanie usług IIS, aby zatrzymać proces PROFILOWANEGO, a następnie zamknij profilera.

1. Zamknij [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci Web.

2. Zamknij [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] proces roboczy resetując Internet Information Services (IIS). Wpisz:

     **Polecenie IISReset/Stop**

3. Zamknij profilera. Wpisz:

     **VSPerfCmd** [ /shutdown](../profiling/shutdown.md)

4. Uruchom ponownie usługi IIS. Wpisz:

     **Polecenie IISReset/Start**

## <a name="restoring-the-application-and-computer-configuration"></a>Przywracanie konfiguracji aplikacji i komputera

Po ukończeniu wszystkich profilowania, Zastąp plik web.config, wyczyść profilowania zmienne środowiskowe i uruchomienie komputera w celu przywrócenia aplikacji i serwerze stanów, które znajdowały się przed rozpoczęciem profilowania.

1. Zastąp plik web.config kopia oryginalnego pliku.

2. Wyczyść profilowania zmiennych środowiskowych. Wpisz:

     **VSPerfCmd /globaloff**

3. Uruchom ponownie komputer.

## <a name="see-also"></a>Zobacz także

[Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)  
[Widoki danych metody instrumentacji](../profiling/instrumentation-method-data-views.md)