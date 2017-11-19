---
title: "Porady: dołączanie profilera do aplikacji autonomicznej .NET Framework do zbierania danych pamięci przy użyciu wiersza polecenia | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a869fa4-3c98-4e08-b5d9-f43523059f0e
caps.latest.revision: "33"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ca6318b5280e2098858bdcf523a3131cf68b7c84
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-attach-the-profiler-to-a-net-framework-stand-alone-application-to-collect-memory-data-by-using-the-command-line"></a>Porady: dołączanie profilera do aplikacji autonomicznej .NET Framework w celu zbierania danych pamięci przy użyciu wiersza polecenia
W tym temacie opisano sposób użycia [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)] narzędzia wiersza polecenia narzędzi profilowania dołączanie profilera do uruchomionej aplikacji autonomicznej (klient) .NET Framework i zbieranie danych pamięci.  
  
> [!NOTE]
>  Narzędzia wiersza polecenia narzędzi profilowania znajdują się w podkatalogu narzędzia \Team Tools\Performance [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] katalogu instalacyjnego. Na komputerach 64-bitowych zarówno 64-bitowe i 32-bitowe wersje narzędzia są dostępne. Za pomocą narzędzi wiersza polecenia profilera, możesz dodać ścieżkę narzędzia do zmiennej środowiskowej PATH w oknie wiersza polecenia lub dodać go do samo polecenie. Aby uzyskać więcej informacji, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Aby dołączyć do aplikacji .NET Framework i zbieranie pamięci danych, należy użyć [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) narzędzia, aby zainicjować zmienne środowiskowe odpowiednie przed uruchomieniem aplikacji docelowej. Gdy profiler jest dołączony do aplikacji, można użyć **VSPerfCmd.exe** narzędzie w celu wstrzymania i wznowienia zbierania danych.  
  
 Aby zakończyć sesję profilowania, profilera musi być odłączony od wszystkich procesów PROFILOWANEGO i profilera muszą zostać jawnie wyłączone. W większości przypadków zaleca się czyszczenie profilowania zmienne środowiskowe z końcem sesji.  
  
## <a name="attaching-the-profiler"></a>Dołączanie profilera  
  
#### <a name="to-attach-the-profiler-to-a-running-net-framework-application"></a>Aby dołączanie profilera do uruchomionej aplikacji .NET Framework  
  
1.  Otwórz okno wiersza polecenia.  
  
2.  Inicjowanie profilowania zmiennych środowiskowych. Wpisz:  
  
     **VSPerfClrEnv** {**/samplegc** &#124; **/samplegclife**} [**/samplelineoff**]  
  
    -   **/Samplegc** i **/samplegclife** Opcje określ, czy zbieranie danych alokacji pamięci tylko lub zbieranie alokacji pamięci i danych o okresie istnienia obiektu. Opcja jeden i tylko jeden musi być określona.  
  
        |Opcja|Opisy|  
        |------------|------------------|  
        |**/samplegc**|Zbieraj tylko dane alokacji pamięci.|  
        |**/samplegclife**|Zbieranie alokacji pamięci i danych o okresie istnienia obiektu.|  
  
    -   **/Samplelineoff** opcja powoduje wyłączenie zbierania danych numer wiersza kodu źródłowego.  
  
3.  Uruchom profilera. Wpisz:  
  
     **/ OUTPUT /start:sample VSPerfCmd:** `OutputFile` [`Options`]  
  
    -   [/Start](../profiling/start.md)**: Przykładowe** opcji inicjowania profilera.  
  
    -   [/Output](../profiling/output.md)**:** `OutputFile` jest wymagany w przypadku opcji **/start**. `OutputFile`Określa nazwę i lokalizację profilowania pliku danych (Vsp).  
  
     Można użyć dowolnego z następujących opcji z **/start:sample** opcji.  
  
    |Opcja|Opis|  
    |------------|-----------------|  
    |[/ User](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName`|Określa nazwę domeny i nazwę konta, który jest właścicielem PROFILOWANEGO procesu. Ta opcja jest wymagana tylko wtedy, gdy proces jest uruchomiony jako użytkownik innego niż zalogowanego użytkownika. Właściciel procesu znajduje się w kolumnie Nazwa użytkownika na karcie Procesy Menedżera zadań systemu Windows.|  
    |[/ crosssession &#124; /CS](../profiling/crosssession.md)|Włącza profilowanie procesów w innych sesji. Ta opcja jest wymagana, jeśli aplikacja jest uruchomiona w innej sesji. Idenitifer sesji to wymienione w kolumnie Identyfikator sesji, na karcie Procesy Menedżera zadań systemu Windows. **/CS** może być określony jako skrót **/crosssession**.|  
    |[/wincounter](../profiling/wincounter.md) **:**`WinCounterPath`|Określa licznik wydajności systemu Windows, które będą zbierane podczas profilowania.|  
    |[/automark](../profiling/automark.md) **:**`Interval`|Za pomocą **/wincounter** tylko. Określa liczbę milisekund między zdarzeniami kolekcji liczników wydajności systemu Windows. Domyślna to 500 ms.|  
  
4.  W razie potrzeby uruchom aplikacji docelowej w typowy sposób.  
  
5.  Dołączanie profilera do aplikacji docelowej. Wpisz:  
  
     **VSPerfCmd**[/ dołączyć](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [[/targetclr](../profiling/targetclr.md)**:**`Version`]  
  
    -   `PID`Określa identyfikator procesu aplikacji docelowej. `ProcessName`Określa nazwę procesu. Należy pamiętać, że jeśli określisz `ProcessName` i działa wiele procesów, które mają taką samą nazwę, są nieprzewidywalne wyniki. Identyfikatory wszystkich procesów uruchomionych procesów można wyświetlić w Menedżerze zadań systemu Windows.  
  
    -   **/targetclr:** `Version` Określa wersję środowisko uruchomieniowe języka wspólnego (CLR) do profilu po załadowaniu więcej niż jedną wersję środowiska uruchomieniowego w aplikacji. Opcjonalny.  
  
## <a name="controlling-data-collection"></a>Kontrolowanie zbierania danych  
 Po uruchomieniu aplikacji docelowej zbieranie danych można kontrolować przy uruchamianie i zatrzymywanie przy zapisywaniu danych do pliku przy użyciu **VSPerfCmd.exe** opcje. Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonania programu, takie jak uruchamianie lub zamykanie aplikacji.  
  
#### <a name="to-start-and-stop-data-collection"></a>Aby uruchomić i zatrzymać zbieranie danych  
  
-   Następujące pary opcje uruchamiania i zatrzymywania zbierania danych. Określ opcję każdego w osobnym wierszu polecenia. Włączenie funkcji zbierania danych można włączać i wyłączać wiele razy.  
  
    |Opcja|Opis|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Uruchamia (**/globalon**) lub zatrzymania (**/globaloff**) zbierania danych dla wszystkich procesów.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|Uruchamia (**/processon**) lub zatrzymania (**/processoff**) zbierania danych dla procesu, który jest określony przez `PID`.|  
    |[/ dołączyć](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [/ detach](../profiling/detach.md)[**:**{`PID`&#124;`ProcName`}]|**/ dołączyć** rozpoczyna zbieranie danych dla procesu, który jest określony przez `PID` lub nazwa procesu (Nazwa_procedury). **/ detach** zatrzymuje zbieranie danych dla określonego procesu lub dla wszystkich procesów, jeśli nie określono określonego procesu.|  
  
## <a name="ending-the-profiling-session"></a>Kończenie sesji profilowania  
 Aby zakończyć sesję profilowania, profilera musi być odłączony od wszystkich procesów PROFILOWANEGO i profilera muszą zostać jawnie wyłączone. Można odłączyć profilera z aplikacji, która była profilowany przy użyciu metody próbkowania przez zamknięcie aplikacji, przez wywołanie **VSPerfCmd / detach** opcji. Następnie wywołaj **VSPerfCmd/shutdown** opcję, aby wyłączyć profilera i zamknij plik danych profilowania. **VSPerfClrEnv / Wyłącz** polecenie czyści profilowania zmiennych środowiskowych.  
  
#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania  
  
1.  Wykonaj jedną z poniższych czynności, aby odłączyć profilera z aplikacji docelowej:  
  
    -   Typ **VSPerfCmd / detach**  
  
         —lub—  
  
    -   Zamknij aplikacji docelowej.  
  
2.  Zamknij profilera. Wpisz:  
  
     **VSPerfCmd** [ /shutdown  ](../profiling/shutdown.md)  
  
3.  (Opcjonalnie) Wyczyść profilowania zmiennych środowiskowych. Wpisz:  
  
     **VSPerfCmd / Wyłącz**  
  
## <a name="see-also"></a>Zobacz też  
 [Profilowanie aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Widoki danych pamięci .NET](../profiling/dotnet-memory-data-views.md)