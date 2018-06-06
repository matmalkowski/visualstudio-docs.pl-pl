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
ms.openlocfilehash: b69e67bce9623c9b5b7a6fc943ace0f08ce2d7da
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2018
ms.locfileid: "34815246"
---
# <a name="how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line"></a>Porady: Instrumentacja dynamicznie skompilowanej aplikacji sieci web ASP.NET i zbieranie szczegółowych danych o chronometrażu przy użyciu profilera przy użyciu wiersza polecenia

W tym artykule opisano sposób użycia narzędzia wiersza polecenia programu Visual Studio Profiling Tools do zbierania danych o chronometrażu dla dynamicznie skompilowanej [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji za pomocą metoda profilowania instrumentacji.

> [!NOTE]
> Narzędzia wiersza polecenia narzędzi profilowania znajdują się w *narzędzia \Team Tools\Performance* podkatalog [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] katalogu instalacyjnego. Na komputerach 64-bitowych zarówno 64-bitowe i 32-bitowe wersje narzędzia są dostępne. Za pomocą narzędzi wiersza polecenia profilera, możesz dodać ścieżkę narzędzia do zmiennej środowiskowej PATH w oknie wiersza polecenia lub dodać go do samo polecenie. Aby uzyskać więcej informacji, zobacz [Określ ścieżkę do narzędzia wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).

Do zbierania danych dotyczących wydajności z [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci web, możesz zmodyfikować *web.config* plik w aplikacji docelowej, aby włączyć [VSInstr.exe](../profiling/vsinstr.md) narzędzia Instrumentacja dynamicznie skompilowanej pliki aplikacji. Następnie należy użyć [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) narzędzia, aby ustawić zmienne środowiskowe odpowiednie na serwerze sieci web, aby włączyć profilowanie, a następnie ponownie uruchom komputer.

Uruchom profilera, a następnie uruchom aplikacji docelowej. Profiler jest dołączony do aplikacji, można wstrzymywać i wznawiać zbierania danych. Po zakończeniu profilowania, zamknij aplikację, Zamknij proces roboczy usług Internet Information Services (IIS) i następnie wyłącz profilera. Po zakończeniu pracy profilowania przywrócić *web.config* plików i serwer sieci Web do oryginalnego stanu.

## <a name="configure-the-aspnet-web-application-and-the-web-server"></a>Konfigurowanie serwera sieci web i aplikacji sieci web ASP.NET

1. Modyfikowanie *web.config* plik w aplikacji docelowej. Zobacz [porady: modyfikowanie plików web.config w celu Instrumentacja i profilowania dynamicznie skompilowanych aplikacji sieci web ASP.NET](../profiling/how-to-modify-web-config-files-to-instrument-dynamically-compiled-aspnet-apps.md).

2. Otwórz okno wiersza polecenia.

3. Inicjowanie profilowania zmiennych środowiskowych. Wpisz:

     **VSPerfClrEnv /globaltraceon**

    - **/globaltraceon** Włącza profilowanie przy użyciu metody instrumentacji.

4. Uruchom ponownie komputer.

## <a name="run-the-profiling-session"></a>Uruchom sesję profilowania

1. Otwórz okno wiersza polecenia.

2. Uruchom profilera. Wpisz:

     **VSPerfCmd**[/start](../profiling/start.md) **: śledzenia**[/output](../profiling/output.md) **:** `OutputFile` [`Options`]

    - **/Start:trace** opcji inicjowania profilera.

    - **/Output:** `OutputFile` jest wymagany w przypadku opcji **/start**. `OutputFile` Określa nazwę i lokalizację danych profilowania (. *Vsp*) pliku.

     Można użyć dowolnego z następujących opcji z **/start:trace** opcji.

    > [!NOTE]
    > **User** i **/crosssession** opcje są zwykle wymagane dla aplikacji ASP.NET.

    |Opcja|Opis|
    |------------|-----------------|
    |[/ User](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName`|Określa nazwę domeny i użytkownika konta, który jest właścicielem proces roboczy programu ASP.NET. Ta opcja jest wymagana, jeśli proces jest uruchomiony jako użytkownik innego niż zalogowanego użytkownika. Właściciel procesu jest wymieniony w **nazwy użytkownika** kolumny na **procesów** kartę Menedżera zadań systemu Windows.|
    |[/crosssession](../profiling/crosssession.md)|Włącza profilowanie procesów w innych sesji logowania. Ta opcja jest wymagana, jeśli aplikacja ASP.NET działa w innej sesji. Identyfikator sesji jest wymieniony w **identyfikator sesji** kolumny na **procesów** kartę Menedżera zadań systemu Windows. **/CS** może być określony jako skrót **/crosssession**.|
    |[/globaloff](../profiling/globalon-and-globaloff.md)|Uruchamia, który wstrzymana profilera ze zbierania danych. Użyj [/globalon](../profiling/globalon-and-globaloff.md) wznowienie profilowania.|
    |[/ licznika](../profiling/counter.md) **:** `Config`|Zbiera informacje licznika wydajności procesora, określonego w `Config`. Informacje o liczniku jest dodawany do danych, które są zbierane w każdym zdarzeniu profilowania.|
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Określa licznik wydajności systemu Windows, które będą zbierane podczas profilowania.|
    |[/automark](../profiling/automark.md) **:** `Interval`|Za pomocą **/wincounter** tylko. Określa liczbę milisekund między zdarzeniami kolekcji liczników wydajności systemu Windows. Domyślna to 500 ms.|
    |[/Events](../profiling/events-vsperfcmd.md) **:** `Config`|Określa zdarzenia funkcji Śledzenie zdarzeń systemu Windows (), które mają być zbierane podczas profilowania. Zdarzenia ETW są gromadzone w oddzielnej (. *etl*) pliku.|

3. Uruchom [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci web w typowy sposób.

## <a name="control-data-collection"></a>Sterowanie zbieraniem danych

Po uruchomieniu aplikacji docelowej zbieranie danych można kontrolować przy uruchamianie i zatrzymywanie zapisywanie danych w pliku danych profilera przy użyciu *VSPerfCmd.exe* opcje. Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonania programu, takie jak uruchamianie lub zamykanie aplikacji.

- Następujące pary opcje uruchamiania i zatrzymywania zbierania danych. Określ opcję każdego w osobnym wierszu polecenia. Włączenie funkcji zbierania danych można włączać i wyłączać wiele razy.

    |Opcja|Opis|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Uruchamia (**/globalon**) lub zatrzymania (**/globaloff**) zbierania danych dla wszystkich procesów.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Uruchamia (**/processon**) lub zatrzymania (**/processoff**) zbierania danych przez proces określony przez identyfikator procesu (`PID`).|
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|Uruchamia (**/threadon**) lub zatrzymania (**/threadoff**) zbierania danych dla wątku określony przez identyfikator wątku (`TID`).|

- Można również użyć **VSPerfCmd.exe**[/oznaczyć](../profiling/mark.md) opcję, aby wstawić znacznik profilowania do pliku danych. **/Oznaczyć** polecenie dodaje identyfikator sygnatury czasowej i opcjonalny zdefiniowane przez użytkownika ciąg tekstowy. Znaczniki można filtrować dane w widoków danych i raportów profilera.

## <a name="end-the-profiling-session"></a>Kończenie sesji profilowania

Aby zakończyć sesję profilowania, Zamknij element docelowy [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci web, resetowanie usług IIS, aby zatrzymać proces PROFILOWANEGO, a następnie zamknij profilera.

1. Zamknij [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci web.

2. Zamknij [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] proces roboczy resetując Internet Information Services (IIS). Wpisz:

     **Polecenie IISReset/Stop**

3. Zamknij profilera. Wpisz:

     **VSPerfCmd** [ /shutdown](../profiling/shutdown.md)

4. Uruchom ponownie usługi IIS. Wpisz:

     **Polecenie IISReset/Start**

## <a name="restore-the-application-and-computer-configuration"></a>Przywróć konfigurację aplikacji i komputera

Po ukończeniu wszystkich profilowania, Zastąp *web.config* , wyczyść profilowania zmiennych środowiskowych, a następnie ponownie uruchom komputer można przywrócić aplikacji i serwerze stanów, które znajdowały się przed rozpoczęciem profilowania.

1. Zastąp *web.config* plik z kopią oryginalnego pliku.

2. Wyczyść profilowania zmiennych środowiskowych. Wpisz:

     **VSPerfCmd /globaloff**

3. Uruchom ponownie komputer.

## <a name="see-also"></a>Zobacz także

[Aplikacje sieci web ASP.NET profilu](../profiling/command-line-profiling-of-aspnet-web-applications.md)  
[Widok danych metody Instrumentacji](../profiling/instrumentation-method-data-views.md)