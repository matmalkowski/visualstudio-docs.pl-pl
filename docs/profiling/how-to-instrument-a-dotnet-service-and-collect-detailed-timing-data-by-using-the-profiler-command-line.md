---
title: 'Porady: Instrumentacja usługi .NET i zbieranie szczegółowych danych o chronometrażu przy użyciu wiersza polecenia profilera | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: c7a5cbb2f411a6d1e2c01275e07da1ea7321488b
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2018
ms.locfileid: "34815967"
---
# <a name="how-to-instrument-a-net-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line"></a>Porady: Instrumentacja usługi .NET i zbieranie szczegółowych danych o chronometrażu przy użyciu wiersza polecenia profilera

W tym artykule opisano sposób użycia narzędzia wiersza polecenia programu Visual Studio Profiling Tools instrumentem [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] usługi i zbieranie szczegółowych danych o chronometrażu.

> [!NOTE]
> Jeśli usługi nie można uruchomić ponownie po uruchomieniu komputera nie może profilować usługi przy użyciu metody instrumentacji, takie usługi, który uruchamia tylko wtedy, gdy system operacyjny był uruchamiany.
>
> Narzędzia wiersza polecenia narzędzi profilowania znajdują się w *narzędzia \Team Tools\Performance* podkatalog [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] katalogu instalacyjnego. Na komputerach 64-bitowych zarówno 64-bitowe i 32-bitowe wersje narzędzia są dostępne. Za pomocą narzędzi wiersza polecenia profilera, możesz dodać ścieżkę narzędzia do zmiennej środowiskowej PATH w oknie wiersza polecenia lub dodać go do samo polecenie. Aby uzyskać więcej informacji, zobacz [Określ ścieżkę do narzędzia wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).
>
> Dodawanie danych o interakcji między warstwy do uruchomienia profilowania wymaga określonych procedur przy użyciu wiersza polecenia narzędzi profilowania. Zobacz [zbierania danych o interakcji między warstwy](../profiling/adding-tier-interaction-data-from-the-command-line.md).

Do zbierania danych o chronometrażu z [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] usługi przy użyciu metody instrumentacji, użyj [VSInstr.exe](../profiling/vsinstr.md) narzędzie do generowania instrumentowanej wersji składnika. Można następnie zamienić nieinstrumentowanego wersję usługi instrumentowaną wersję, upewniając się, że usługa jest skonfigurowana do uruchamiania ręcznego. Możesz użyć [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) narzędzia, aby zainicjować zmienne globalne profilowania środowiska, a następnie ponownie uruchom komputer-host. Następnie należy uruchomić profilera.

Gdy usługa jest uruchomiona, dane chronometrażu są zbierane automatycznie w pliku danych. Można wstrzymywać i wznawiać zbierania danych podczas sesji profilowania.

Aby zakończyć sesję profilowania, możesz wyłączyć usługę, a następnie jawnie Wyłącz profilera. W większości przypadków zaleca się czyszczenie profilowania zmienne środowiskowe z końcem sesji.

## <a name="start-the-application-with-the-profiler"></a>Uruchom aplikację przy użyciu profilera

1. Otwórz okno wiersza polecenia.

2. Użyj **VSInstr** narzędzie do generowania instrumentowaną wersję pliku binarnego usługi.

3. Zastąp instrumentowanej wersji oryginalnego pliku binarnego. W systemie Windows menedżera kontroli usług, upewnij się, że usługa uruchamiana ma ustawiony ręczny.

4. Inicjowanie [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] profilowania zmiennych środowiskowych. Wpisz:

     **VSPerfClrEnv /globaltraceon**

5. Uruchom ponownie komputer.

6. Otwórz okno wiersza polecenia.

7. Uruchom profilera. Wpisz:

     **/ OUTPUT /start:trace VSPerfCmd:** `OutputFile` [`Options`]

    - [/Start](../profiling/start.md)**: śledzenia** opcji inicjowania profilera.

    - [/Output](../profiling/output.md)**:** `OutputFile` jest wymagany w przypadku opcji **/start**. `OutputFile` Określa nazwę i lokalizację danych profilowania (. *Vsp*) pliku.

     Można zastosować dowolną z następujących opcji z **/start:trace** opcji.

    > [!NOTE]
    > **User** i **/crosssession** opcje są zwykle wymagane dla usług profilowania.

    |Opcja|Opis|
    |------------|-----------------|
    |[/ User](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName`|Określa nazwę domeny i nazwę konta, który jest właścicielem PROFILOWANEGO procesu. Ta opcja jest wymagana tylko wtedy, gdy proces jest uruchomiony jako użytkownik innego niż zalogowanego użytkownika. Właściciel procesu jest wymieniony w **nazwy użytkownika** kolumny na **procesów** kartę Menedżera zadań systemu Windows.|
    |[/crosssession](../profiling/crosssession.md)|Włącza profilowanie procesów w innych sesji. Ta opcja jest wymagana, jeśli aplikacja jest uruchomiona w innej sesji. Identyfikator jest wymieniony w sesji **identyfikator sesji** kolumny na **procesów** kartę Menedżera zadań systemu Windows. **/CS** może być określony jako skrót **/crosssession**.|
    |[/waitstart](../profiling/waitstart.md)[**:**`Interval`]|Określa liczbę sekund oczekiwania profilera zainicjować przed zwraca błąd. Jeśli `Interval` nie zostanie określony, profilera oczekiwania przez czas nieokreślony. Domyślnie **/start** natychmiast kończy pracę.|
    |[/globaloff](../profiling/globalon-and-globaloff.md)|Do uruchomienia profilera ze zbierania danych wstrzymana, Dodaj **/globaloff** opcji w celu **/start** wiersza polecenia. Użyj **/globalon** wznowienie profilowania.|
    |[/ licznika](../profiling/counter.md) **:** `Config`|Zbiera informacje o wydajności procesora licznika określony w konfiguracji. Informacje o liczniku jest dodawany do danych zbieranych na każdym zdarzeniu profilowania.|
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Określa licznik wydajności systemu Windows, które będą zbierane podczas profilowania.|
    |[/automark](../profiling/automark.md) **:** `Interval`|Za pomocą **/wincounter** tylko. Określa liczbę milisekund między zdarzeniami kolekcji liczników wydajności systemu Windows. Domyślna to 500 ms.|
    |[/Events](../profiling/events-vsperfcmd.md) **:** `Config`|Określa zdarzenia funkcji Śledzenie zdarzeń systemu Windows (), które mają być zbierane podczas profilowania. Zdarzenia ETW są gromadzone w oddzielnej (. *etl*) pliku.|

8. Uruchom usługę z Menedżera kontroli usług systemu Windows.

## <a name="control-data-collection"></a>Sterowanie zbieraniem danych

Gdy usługa jest uruchomiona, można użyć *VSPerfCmd.exe* opcji, aby uruchomić i zatrzymać przy zapisywaniu danych w pliku danych profilera. Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonania programu, takie jak uruchamianie lub zamykanie usługi.

- Następujące pary **VSPerfCmd** opcje uruchamiania i zatrzymywania zbierania danych. Określ opcję każdego w osobnym wierszu polecenia. Włączenie funkcji zbierania danych można włączać i wyłączać wiele razy.

    |Opcja|Opis|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Uruchamia (**/globalon**) lub zatrzymania (**/globaloff**) zbierania danych dla wszystkich procesów.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Uruchamia (**/processon**) lub zatrzymania (**/processoff**) zbierania danych przez proces określony przez identyfikator procesu (`PID`).|
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|Uruchamia (**/threadon**) lub zatrzymania (**/threadoff**) zbierania danych dla wątku określony przez identyfikator wątku (`TID`).|

## <a name="end-the-profiling-session"></a>Kończenie sesji profilowania

Aby zakończyć sesję profilowania, Zatrzymaj usługę działa instrumentowanych składnik, a następnie wywołać **VSPerfCmd** [/shutdown](../profiling/shutdown.md) opcję, aby wyłączyć profilera i zamknij plik danych profilowania. **VSPerfClrEnv /globaloff** polecenie czyści profilowania zmiennych środowiskowych.

Należy ponownie uruchomić komputer, aby nowe ustawienia środowiska do zastosowania.

1. Zatrzymaj usługę z Menedżera kontroli usług.

2. Zamknij profilera. Wpisz:

     **VSPerfCmd/shutdown**

3. Po ukończeniu wszystkich profilowania, wyczyść profilowania zmiennych środowiskowych. Wpisz:

     **VSPerfClrEnv /globaloff**

4. Zastąp oryginalny instrumentowanych modułu. Jeśli to konieczne, należy ponownie skonfigurować typ uruchomienia usługi.

5. Uruchom ponownie komputer.

## <a name="see-also"></a>Zobacz także

[Usługi profilowania](../profiling/command-line-profiling-of-services.md)  
[Widok danych metody Instrumentacji](../profiling/instrumentation-method-data-views.md)
