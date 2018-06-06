---
title: 'Porady: uruchamianie aplikacji autonomicznej .NET Framework z Profilerem do zbierania danych pamięci przy użyciu wiersza polecenia | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 3bc53041-91b7-4ad0-8413-f8bf2c4b3f5e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 3d1cbc108bbe48377b34683436f4796ac377ef82
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2018
ms.locfileid: "34815512"
---
# <a name="how-to-launch-a-stand-alone-net-framework-application-with-the-profiler-to-collect-memory-data-by-using-the-command-line"></a>Porady: uruchamianie aplikacji autonomicznej .NET Framework z profilerem do zbierania danych pamięci przy użyciu wiersza polecenia
W tym temacie opisano sposób użycia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędziach profilowania narzędzia wiersza polecenia do uruchomienia aplikacji autonomicznej (klient) .NET Framework i zbieranie danych pamięci.  
  
 Sesja profilowania ma trzy części:  
  
-   Uruchamianie aplikacji przy użyciu profilera.  
  
-   Zbieranie danych profilowania.  
  
-   Kończenie sesji profilowania.  
  
> [!NOTE]
>  Narzędzia wiersza polecenia narzędzi profilowania znajdują się w *narzędzia \Team Tools\Performance* podkatalog [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] katalogu instalacyjnego. Na komputerach 64-bitowych zarówno 64-bitowe i 32-bitowe wersje narzędzia są dostępne. Za pomocą narzędzi wiersza polecenia profilera, możesz dodać ścieżkę narzędzia do zmiennej środowiskowej PATH w oknie wiersza polecenia lub dodać go do samo polecenie. Aby uzyskać więcej informacji, zobacz [Określ ścieżkę do narzędzia wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
## <a name="start-the-application-with-the-profiler"></a>Uruchom aplikację przy użyciu profilera  
 Do uruchamiania aplikacji docelowej przy użyciu profilera, użyj **VSPerfCmd.exe/start** i **/uruchamianie** opcje do inicjowania profilera i uruchomić aplikację. Można określić **/start** i **/uruchamianie** i odpowiednie opcje w jednym wierszu polecenia.  
  
 Można również dodać **/globaloff** opcje, aby zatrzymać zbieranie danych na początku aplikacji docelowej. Następnie należy użyć **/globalon** zacząć zbierać dane.  
  
#### <a name="to-start-an-application-by-using-the-profiler"></a>Aby uruchomić aplikację za pomocą profilera  
  
1.  Otwórz okno wiersza polecenia.  
  
2.  Uruchom profilera. Wpisz:  
  
     **/ OUTPUT /start:sample VSPerfCmd:** `OutputFile` [`Options`]  
  
    -   [/Start](../profiling/start.md)**: Przykładowe** opcji inicjowania profilera.  
  
    -   [/Output](../profiling/output.md)**:** `OutputFile` jest wymagany w przypadku opcji **/start**. `OutputFile` Określa nazwę i lokalizację profilowania pliku danych (Vsp).  
  
     Można użyć dowolnego z następujących opcji z **/start:sample** opcji.  
  
    |Opcja|Opis|  
    |------------|-----------------|  
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Określa licznik wydajności systemu Windows, które będą zbierane podczas profilowania.|  
    |[/automark](../profiling/automark.md) **:** `Interval`|Za pomocą **/wincounter** tylko. Określa liczbę milisekund między zdarzeniami kolekcji liczników wydajności systemu Windows. Domyślna to 500 ms.|  
  
3.  Uruchomienie aplikacji docelowej. Wpisz:  
  
     **VSPerfCmd**[/uruchamianie](../profiling/launch.md) **:** `appName` **/gc:**{**alokacji**&#124;**okres istnienia** }[`Options`]  
  
    -   [/Gc](../profiling/gc-vsperfcmd.md)**:** `Keyword` opcja jest wymagana w celu zbierania danych pamięci .NET Framework. Parametr — słowo kluczowe Określa, czy zbieranie danych alokacji pamięci lub zbieranie alokacji pamięci i danych o okresie istnienia obiektu.  
  
        |Słowo kluczowe|Opis|  
        |-------------|-----------------|  
        |**Alokacja**|Zbieraj tylko dane alokacji pamięci.|  
        |**Cykl życia**|Zbieranie alokacji pamięci i danych o okresie istnienia obiektu.|  
  
     Można użyć dowolnego z następujących opcji z **/uruchamianie** opcji.  
  
    |Opcja|Opis|  
    |------------|-----------------|  
    |[przełącznika/args](../profiling/args.md) **:** `Arguments`|Określa ciąg, który zawiera argumenty wiersza polecenia do przekazania do aplikacji docelowej.|  
    |[/ Console](../profiling/console.md)|Uruchamia aplikację wiersza polecenia docelowego w osobnym oknie.|  
    |[/Events](../profiling/events-vsperfcmd.md) **:** `Config`|Określa zdarzenia funkcji Śledzenie zdarzeń systemu Windows (), które mają być zbierane podczas profilowania. Zdarzenia ETW są gromadzone w pliku oddzielne (ETL).|  
    |[/targetclr](../profiling/targetclr.md) **:** `Version`|Określa wersję środowisko uruchomieniowe języka wspólnego (CLR) do profilu po załadowaniu więcej niż jedną wersję środowiska uruchomieniowego w aplikacji.|  
  
## <a name="control-data-collection"></a>Sterowanie zbieraniem danych  
 Po uruchomieniu aplikacji docelowej zbieranie danych można kontrolować przy uruchamianie i zatrzymywanie przy zapisywaniu danych do pliku przy użyciu *VSPerfCmd.exe* opcje. Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonania programu, takie jak uruchamianie lub zamykanie aplikacji.  
  
#### <a name="to-start-and-stop-data-collection"></a>Aby uruchomić i zatrzymać zbieranie danych  
  
-   Następujące pary opcje uruchamiania i zatrzymywania zbierania danych. Określ opcję każdego w osobnym wierszu polecenia. Włączenie funkcji zbierania danych można włączać i wyłączać wiele razy.  
  
    |Opcja|Opis|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Uruchamia (**/globalon**) lub zatrzymania (**/globaloff**) zbierania danych dla wszystkich procesów.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [processoff](../profiling/processon-and-processoff.md) **:** `PID`|Uruchamia (**/processon**) lub zatrzymania (**/processoff**) zbierania danych dla procesu, który jest określony przez identyfikator procesu (`PID`).|  
    |[/ dołączyć](../profiling/attach.md) **:** `PID` [/ detach](../profiling/detach.md)|**/ dołączyć** rozpoczyna zbieranie danych dla procesu, który jest określony przez `PID` (identyfikator procesu). **/ detach** zatrzymania zbierania danych dla wszystkich procesów.|  
  
-   Można również użyć **VSPerfCmd.exe**[/oznaczyć](../profiling/mark.md) opcję, aby wstawić znacznik profilowania do pliku danych. **/Oznaczyć** polecenie dodaje identyfikator sygnatury czasowej i opcjonalny zdefiniowane przez użytkownika ciąg tekstowy. Znaczniki może służyć do filtrowania danych.  
  
## <a name="end-the-profiling-session"></a>Kończenie sesji profilowania  
 Aby zakończyć sesję profilowania, profilera musi być odłączony od wszystkich procesów PROFILOWANEGO i profilera muszą zostać jawnie wyłączone. Można odłączyć profilera z aplikacji, która była profilowany przy użyciu metody próbkowania przez zamknięcie aplikacji, przez wywołanie **VSPerfCmd / detach** opcji. Następnie wywołaj **VSPerfCmd/shutdown** opcję, aby wyłączyć profilera i zamknij plik danych profilowania. **VSPerfClrEnv / Wyłącz** polecenie czyści profilowania zmiennych środowiskowych.  
  
#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania  
  
1.  Wykonaj jedną z poniższych czynności, aby odłączyć profilera z aplikacji docelowej:  
  
    -   Zamknij aplikacji docelowej.  
  
         —lub—  
  
    -   Typ **VSPerfCmd / detach**  
  
2.  Zamknij profilera. Wpisz:  
  
     **VSPerfCmd** [ /shutdown](../profiling/shutdown.md)  
  
## <a name="see-also"></a>Zobacz także  
 [Profil aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Widoki danych pamięci .NET](../profiling/dotnet-memory-data-views.md)