---
title: "Porady: dołączanie profilera do usługi .NET w celu zbierania statystyk aplikacji przy użyciu wiersza polecenia | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a0046c47-26c8-4bec-96a0-81da05e5104a
caps.latest.revision: "28"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a639c9401498f168834947d9ec9c3bd238010e13
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/11/2017
---
# <a name="how-to-attach-the-profiler-to-a-net-service-to-collect-application-statistics-by-using-the-command-line"></a>Porady: dołączanie profilera do usługi .NET w celu zbierania statystyk aplikacji przy użyciu wiersza polecenia
W tym temacie opisano sposób użycia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzia wiersza polecenia narzędzi profilowania do dołączenia profilera .NET Framework usługi i zbieranie statystyk wydajności za pomocą metody pobierania próbek.  
  
> [!NOTE]
>  Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagane znaczących zmian w sposobie profilera Visual Studio zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows wymagają również nowe techniki kolekcji. Zobacz [narzędzi wydajności w przypadku aplikacji systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
>   
>  Narzędzia wiersza polecenia narzędzi profilowania znajdują się w podkatalogu narzędzia \Team Tools\Performance [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] katalogu instalacyjnego. Na komputerach 64-bitowym zarówno w przypadku 64-bitowych, jak i 32-bitowe wersje narzędzia są dostępne. Za pomocą narzędzi wiersza polecenia profilera, możesz dodać ścieżkę narzędzia do zmiennej środowiskowej PATH w oknie wiersza polecenia lub dodać go do samo polecenie. Aby uzyskać więcej informacji, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
>   
>  Dodawanie danych o interakcji między warstwy do uruchomienia profilowania wymaga określonych procedur przy użyciu wiersza polecenia narzędzia profilowania. Zobacz [zbierania danych o interakcji między warstwy](../profiling/adding-tier-interaction-data-from-the-command-line.md).  
  
 Aby zbierać dane dotyczące wydajności z usługi .NET Framework, należy użyć [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) narzędzia, aby zainicjować zmienne środowiskowe odpowiednie. Następnie należy ponownie uruchomić komputer, który obsługuje usługę i skonfigurować komputera w celu profilowania. Następnie możesz dołączanie profilera do procesu usługi. Gdy profiler jest dołączony do usługi, można wstrzymywać i wznawiać zbierania danych.  
  
 Aby zakończyć sesję profilowania, profilera musi być odłączony od usługi i profilera muszą zostać jawnie wyłączone. W większości przypadków zaleca się czyszczenie profilowania zmienne środowiskowe z końcem sesji.  
  
## <a name="attaching-the-profiler"></a>Dołączanie profilera  
  
#### <a name="to-attach-the-profiler-to-a-net-framework-service"></a>Aby dołączanie profilera do usługi .NET Framework  
  
1.  Zainstaluj usługę.  
  
2.  Otwórz okno wiersza polecenia.  
  
3.  Inicjowanie profilowania zmiennych środowiskowych. Wpisz:  
  
     **VSPerfClrEnv /globalsampleon** [**/samplelineoff**]  
  
    -   **/globalsampleon** umożliwia próbkowania.  
  
    -   **/samplelineoff** wyłącza przypisania zebranych danych do wierszy kodu określonego źródła. W przypadku wybrania tej opcji, danych jest przypisane tylko do funkcji.  
  
4.  Uruchom ponownie komputer.  
  
5.  Otwórz okno wiersza polecenia.  
  
6.  Uruchom profilera. Wpisz:  
  
     **VSPerfCmd**[/start](../profiling/start.md) **: Przykładowe**[/output](../profiling/output.md) **:** `OutputFile` [`Options`]  
  
    -   **/Start:sample** opcji inicjowania profilera.  
  
    -   **/Output:** `OutputFile` jest wymagany w przypadku opcji **/start**. `OutputFile`Określa nazwę i lokalizację profilowania pliku danych (Vsp).  
  
     Można użyć dowolnego z następujących opcji z **/start:sample** opcji.  
  
    > [!NOTE]
    >  **User** i **/crosssession** opcje są zwykle wymagane dla usług.  
  
    |Opcja|Opis|  
    |------------|-----------------|  
    |[/ User](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName`|Określa nazwę domeny i nazwę konta, który jest właścicielem PROFILOWANEGO procesu. Ta opcja jest wymagana tylko wtedy, gdy proces jest uruchomiony jako użytkownik innego niż zalogowanego użytkownika. Właściciel procesu znajduje się w kolumnie Nazwa użytkownika na karcie Procesy Menedżera zadań systemu Windows.|  
    |[/ crosssession](../profiling/crosssession.md)|Włącza profilowanie procesów w innych sesji. Ta opcja jest wymagana, jeśli usługa jest uruchomiona w innej sesji. Identyfikator sesji jest wymieniony w kolumnie Identyfikator sesji, na karcie Procesy Menedżera zadań systemu Windows. **/CS** może być określony jako skrót **/crosssession**.|  
    |[/wincounter](../profiling/wincounter.md) **:**`WinCounterPath`|Określa licznik wydajności systemu Windows, które będą zbierane podczas profilowania.|  
    |[/automark](../profiling/automark.md) **:**`Interval`|Za pomocą **/wincounter** tylko. Określa liczbę milisekund między zdarzeniami kolekcji liczników wydajności systemu Windows. Domyślna to 500 ms.|  
    |[/Events](../profiling/events-vsperfcmd.md) **:**`Config`|Określa zdarzenia funkcji Śledzenie zdarzeń systemu Windows (), które mają być zbierane podczas profilowania. Zdarzenia ETW są gromadzone w pliku oddzielne (ETL).|  
  
7.  W razie potrzeby uruchom usługę.  
  
8.  Dołączanie profilera do usługi. Wpisz:  
  
     **VSPerfCmd**[/ dołączyć](../profiling/attach.md) **:** {`PID`&#124;`ProcName`} [`Sample Event`] [[/targetclr](../profiling/targetclr.md)**:**`Version`]    
  
    -   Określ identyfikator procesu (`PID`) lub nazwa procesu (Nazwa_procedury) usługi. Można wyświetlić nazwy wszystkich uruchomionych procesów i identyfikatorów procesów w Menedżerze zadań systemu Windows.  
  
     Domyślnie wydajności, dane są pobierane co zegara procesora nie zostało zatrzymane 10 000 000 cykle. Jest to około 100 próbek w procesor 1GH na sekundę. Można określić jedną z następujących opcji, aby zmienić interwał cyklu zegara lub określić zdarzenia różnych próbkowania.  
  
    |Zdarzenie próbkowania|Opis|  
    |------------------|-----------------|  
    |[/ Timer](../profiling/timer.md) **:**`Interval`|Zmiany liczby cykli zegara nie zostało zatrzymane, określony przez interwał próbkowania `Interval`.|  
    |[PF](../profiling/pf.md)[**:**`Interval`]|Zmiany zdarzenie próbkowania błędów strony. Jeśli `Interval` jest określony, ustawia liczbę błędów stron między próbkami. Domyślna to 10.|  
    |[sys](../profiling/sys-vsperfcmd.md)[`:``Interval`]|Zdarzenie próbkowania wywołań systemowych zmiany z procesu jądra systemu operacyjnego (syscalls). Jeśli `Interval` jest określony, ustawia liczbę wywołań między próbkami. Domyślna to 10.|  
    |[/ licznika](../profiling/counter.md) **:**`Config`|Zmiany zdarzenie próbkowania i interwał licznika wydajności procesora i interwał określony we `Config`.|  
  
    -   **targetclr:** `Version` Określa wersję środowisko uruchomieniowe języka wspólnego (CLR) do profilu po załadowaniu więcej niż jedną wersję środowiska uruchomieniowego w aplikacji. Opcjonalny.  
  
## <a name="controlling-data-collection"></a>Kontrolowanie zbierania danych  
 Gdy usługa jest uruchomiona, można użyć **VSPerfCmd.exe** opcji, aby uruchomić i zatrzymać przy zapisywaniu danych w pliku danych profilera. Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonania programu, takie jak uruchamianie lub zamykanie aplikacji.  
  
#### <a name="to-start-and-stop-data-collection"></a>Aby uruchomić i zatrzymać zbieranie danych  
  
-   Następujące pary **VSPerfCmd** opcje uruchamiania i zatrzymywania zbierania danych. Określ opcję każdego w osobnym wierszu polecenia. Włączenie funkcji zbierania danych można włączać i wyłączać wiele razy.  
  
    |Opcja|Opis|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Uruchamia (**/globalon**) lub zatrzymania (**/globaloff**) zbierania danych dla wszystkich procesów.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|Uruchamia (**/processon**) lub zatrzymania (**/processoff**) zbierania danych przez proces określony przez identyfikator procesu (`PID`).|  
    |**/ dołączyć:**{`PID`&#124;`ProcName`} [/ detach](../profiling/detach.md)[: {`PID`&#124;`ProcName`}]|**/ dołączyć** rozpoczyna zbieranie danych przez proces określony przez identyfikator procesu lub nazwy procesu. **/ detach** zatrzymuje zbieranie danych dla określonego procesu lub dla wszystkich procesów, jeśli nie określono określonego procesu.|  
  
## <a name="ending-the-profiling-session"></a>Kończenie sesji profilowania  
 Aby zakończyć sesję profilowania, profilera musi być odłączony od wszystkich procesów PROFILOWANEGO i profilera muszą zostać jawnie wyłączone. Można odłączyć z aplikacji profilowany przy użyciu metody pobierania próbek przez zamknięcie aplikacji lub poprzez wywołanie **VSPerfCmd / detach** opcji. Następnie wywołaj **VSPerfCmd/shutdown** opcję, aby wyłączyć profilera i zamknij plik danych profilowania.  
  
 **VSPerfClrEnv /globaloff** polecenie usuwa profilowania zmiennych środowiskowych, ale konfiguracja systemu nie zostanie zresetowana do ponownego uruchomienia komputera.  
  
#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania  
  
1.  Wykonaj jedną z następujących czynności, aby odłączyć profilera z aplikacji docelowej:  
  
    -   Zatrzymaj usługę.  
  
         —lub—  
  
    -   Typ **VSPerfCmd / detach**  
  
2.  Zamknij profilera. Wpisz:  
  
     **VSPerfCmd/shutdown**  
  
3.  (Opcjonalnie) Wyczyść profilowania zmiennych środowiskowych. Wpisz:  
  
     **VSPerfClrEnv /globaloff**  
  
4.  Uruchom ponownie komputer.  
  
## <a name="see-also"></a>Zobacz też  
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)   
 [Widok danych metody próbkowania](../profiling/profiler-sampling-method-data-views.md)