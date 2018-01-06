---
title: "Porady: uruchamianie aplikacji autonomicznej z Profilerem i zbieranie statystyk aplikacji przy użyciu wiersza polecenia | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52dcee2b-f178-4a76-bddc-e36c50bfcb78
caps.latest.revision: "37"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 7840b2a28d5d2aff350af7c86f19332c7b8dd087
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-launch-a-stand-alone-application-with-the-profiler-and-collect-application-statistics-by-using-the-command-line"></a>Porady: uruchamianie aplikacji autonomicznej z profilerem i zbieranie statystyk aplikacji przy użyciu wiersza polecenia
W tym temacie opisano sposób użycia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędziach profilowania narzędzia wiersza polecenia do uruchomienia aplikacji autonomicznej (klient) i zbieranie statystyk wydajności za pomocą metody pobierania próbek.  
  
> [!NOTE]
>  Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagane znaczących zmian w sposobie profilera Visual Studio zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows wymagają również nowe techniki kolekcji. Zobacz [narzędzi wydajności w przypadku aplikacji systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
>   
>  Dodawanie danych o interakcji między warstwy do uruchomienia profilowania wymaga określonych procedur przy użyciu wiersza polecenia narzędzia profilowania. Zobacz [zbierania danych o interakcji między warstwy](../profiling/adding-tier-interaction-data-from-the-command-line.md)  
  
 Za pomocą narzędzi wiersza polecenia profilera, możesz dodać ścieżkę do zmiennej środowiskowej PATH w oknie wiersza polecenia lub dodać go do samo polecenie. Na maszynie, w którym jest zainstalowany program Visual Studio z okna polecenia programu Visual Studio można uruchomić narzędzi profilowania.  
  
1.  Jeśli używasz narzędzia profilowania maszyny, na których program Visual Studio jest zainstalowany zestawy okno poleceń programu Visual Studio prawidłowe ścieżki. Na **narzędzia** menu, wybierz **wiersza polecenia VS**  
  
> [!NOTE]
>  Narzędzia wiersza polecenia narzędzi profilowania znajdują się w podkatalogu narzędzia \Team Tools\Performance katalogu instalacyjnego programu Visual Studio. Na komputerach 64-bitowych zarówno 64-bitowe i 32-bitowe wersje narzędzia są dostępne. Za pomocą narzędzi wiersza polecenia profilera, możesz dodać ścieżkę do zmiennej środowiskowej PATH w oknie wiersza polecenia lub dodać go do samo polecenie. Aby uzyskać więcej informacji, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
## <a name="starting-the-application-with-the-profiler"></a>Uruchamianie aplikacji przy użyciu profilera  
 Do uruchamiania aplikacji docelowej przy użyciu profilera, użyj narzędzia VSPerfCmd **/start** i **/uruchamianie** opcje do inicjowania profilera i uruchomić aplikację. Można określić **/start** i **/uruchamianie** i odpowiednie opcje w jednym wierszu polecenia.  
  
 Można również dodać **/globaloff** opcję, aby wstrzymać zbieranie danych na początku aplikacji docelowej. Następnie należy użyć **/globalon** zacząć zbierać dane.  
  
#### <a name="to-start-an-application-by-using-the-profiler"></a>Aby uruchomić aplikację za pomocą profilera  
  
1.  Otwórz okno wiersza polecenia.  
  
2.  Uruchom profilera. Wpisz:  
  
     **/ OUTPUT /start:sample VSPerfCmd:** `OutputFile` [`Options`]  
  
    -   [/Start](../profiling/start.md)**: Przykładowe** opcji inicjowania profilera.  
  
    -   [/Output](../profiling/output.md)**:** `OutputFile` jest wymagany w przypadku opcji **/start**. `OutputFile`Określa nazwę i lokalizację profilowania pliku danych (Vsp).  
  
     Można użyć dowolnego z następujących opcji z **/start:sample** opcji.  
  
    |Opcja|Opis|  
    |------------|-----------------|  
    |[/wincounter](../profiling/wincounter.md) **:**`WinCounterPath`|Określa licznik wydajności systemu Windows, które będą zbierane podczas profilowania.|  
    |[/automark](../profiling/automark.md) **:**`Interval`|Za pomocą **/wincounter** tylko. Określa liczbę milisekund między zdarzeniami kolekcji liczników wydajności systemu Windows. Domyślna to 500 ms.|  
    |[/Events](../profiling/events-vsperfcmd.md) **:**`Config`|Określa zdarzenia funkcji Śledzenie zdarzeń systemu Windows (), które mają być zbierane podczas profilowania. Zdarzenia ETW są gromadzone w pliku oddzielne (ETL).|  
  
3.  Uruchomienie aplikacji docelowej. Typ:**VSPerfCmd przełącznik/Launch:** `appName` [`Options`] [`Sample Event`]  
  
     Można użyć co najmniej jeden z następujących opcji z **/uruchamianie** opcji.  
  
    |Opcja|Opis|  
    |------------|-----------------|  
    |[przełącznika/args](../profiling/args.md) **:**`Arguments`|Określa ciąg, który zawiera argumenty wiersza polecenia do przekazania do aplikacji docelowej.|  
    |[/ Console](../profiling/console.md)|Uruchamia aplikację wiersza polecenia docelowego w osobnym oknie.|  
  
     Domyślnie wydajności, dane są pobierane co zegara procesora nie zostało zatrzymane 10 000 000 cykle. Jest to około jednej godziny co 10 sekund na procesor 1GHz. Można określić jedną z następujących opcji, aby zmienić interwał cyklu zegara lub określić zdarzenia różnych próbkowania.  
  
    |Zdarzenie próbkowania|Opis|  
    |------------------|-----------------|  
    |[/ Timer](../profiling/timer.md) **:**`Interval`|Powoduje interwał próbkowania liczby cykli zegara nie zostało zatrzymane, które są określone przez `Interval`.|  
    |[PF](../profiling/pf.md)[**:**`Interval`]|Zmiany zdarzenie próbkowania błędów strony. Jeśli `Interval` jest określony, ustawia liczbę błędów stron między próbkami. Domyślna to 10.|  
    |[sys](../profiling/sys-vsperfcmd.md)[**:**`Interval`]|Zdarzenie próbkowania wywołań systemowych zmiany z procesu jądra systemu operacyjnego (syscalls). Jeśli `Interval` jest określony, ustawia liczbę wywołań między próbkami. Domyślna to 10.|  
    |[/ licznika](../profiling/counter.md) **:**`Config`|Zmiany zdarzenie próbkowania i interwał licznika wydajności procesora i interwał, w którym są określone w `Config`.|  
  
## <a name="controlling-data-collection"></a>Kontrolowanie zbierania danych  
 Po uruchomieniu aplikacji docelowej zbieranie danych można kontrolować przy uruchamianie i zatrzymywanie zapisywanie danych w pliku danych profilera przy użyciu **VSPerfCmd.exe** opcje. Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonania programu, takie jak uruchamianie lub zamykanie aplikacji.  
  
#### <a name="to-start-and-stop-data-collection"></a>Aby uruchomić i zatrzymać zbieranie danych  
  
-   Następujące pary opcje uruchamiania i zatrzymywania zbierania danych. Określ opcję każdego w osobnym wierszu polecenia. Włączenie funkcji zbierania danych można włączać i wyłączać wiele razy.  
  
    |Opcja|Opis|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Uruchamia (**/globalon**) lub zatrzymania (**/globaloff**) zbierania danych dla wszystkich procesów.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**  `PID`|Uruchamia (**/processon**) lub zatrzymania (**/processoff**) zbierania danych przez proces określony przez identyfikator procesu (`PID`).|  
    |[/ dołączyć](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [/ detach](../profiling/detach.md)[**:**{`PID`&#124;`ProcName`}]|**/ dołączyć** rozpoczyna zbieranie danych przez proces określony przez `PID` lub nazwa procesu (Nazwa_procedury). **/ detach** zatrzymuje zbieranie danych dla określonego procesu lub dla wszystkich procesów, jeśli nie określono określonego procesu.|  
  
## <a name="ending-the-profiling-session"></a>Kończenie sesji profilowania  
 Aby zakończyć sesję profilowania, profilera nie może być dołączone do dowolnego PROFILOWANEGO procesu i profilera muszą zostać jawnie wyłączone. Można odłączyć profilera z aplikacji, która była profilowany przy użyciu metody próbkowania przez zamknięcie aplikacji, przez wywołanie **VSPerfCmd / detach** opcji. Następnie wywołaj **VSPerfCmd/shutdown** opcję, aby wyłączyć profilera i zamknij plik danych profilowania. **VSPerfClrEnv / Wyłącz** polecenie czyści profilowania zmiennych środowiskowych.  
  
#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania  
  
1.  Wykonaj jedną z poniższych czynności, aby odłączyć profilera z aplikacji docelowej:  
  
    -   Zamknij aplikacji docelowej.  
  
         —lub—  
  
    -   Typ **VSPerfCmd / detach**  
  
2.  Zamknij profilera. Wpisz:  
  
     **VSPerfCmd** [ /shutdown  ](../profiling/shutdown.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Profilowanie aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Widok danych metody próbkowania](../profiling/profiler-sampling-method-data-views.md)