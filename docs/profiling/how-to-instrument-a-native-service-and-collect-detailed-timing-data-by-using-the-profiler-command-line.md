---
title: "Porady: Instrumentacja natywnych usługi i zbieranie szczegółowych danych o chronometrażu przy użyciu wiersza polecenia profilera | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dfe58b39-63f8-4a87-ab3a-2b5b14faa8d0
caps.latest.revision: "22"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5219a55c009b313ef3b0059efc588213729ff43e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-instrument-a-native-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line"></a>Porady: instrumentowanie usługi natywnej i zbieranie szczegółowych danych o chronometrażu przy użyciu wiersza polecenia profilera
W tym temacie opisano sposób użycia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzia wiersza polecenia narzędzi profilowania do Instrumentacja natywnego (C/C++) usługi i zbieranie szczegółowych danych o chronometrażu.  
  
> [!NOTE]
>  Jeśli usługi nie można uruchomić ponownie po uruchomieniu komputera nie może profilować usługi przy użyciu metody instrumentacji, takie usługi, która uruchomić tylko wtedy, gdy system operacyjny był uruchamiany.  
>   
>  Narzędzia wiersza polecenia narzędzi profilowania znajdują się w podkatalogu narzędzia \Team Tools\Performance [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] katalogu instalacyjnego. Na komputerach 64-bitowym zarówno w przypadku 64-bitowych, jak i 32-bitowe wersje narzędzia są dostępne. Za pomocą narzędzi wiersza polecenia profilera, możesz dodać ścieżkę narzędzia do zmiennej środowiskowej PATH w oknie wiersza polecenia lub dodać go do samo polecenie. Aby uzyskać więcej informacji, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Zbieranie szczegółowych danych o chronometrażu z macierzystego usługi przy użyciu metody instrumentacji, użyj [VSInstr.exe](../profiling/vsinstr.md) narzędzie do generowania instrumentowanej wersji składnika. Można następnie zamienić nieinstrumentowanego wersję usługi instrumentowaną wersję, upewniając się, że usługa jest skonfigurowana do uruchamiania ręcznego. Następnie należy uruchomić profilera.  
  
 Gdy usługa jest uruchomiona, dane chronometrażu są zbierane automatycznie w pliku danych. Można wstrzymywać i wznawiać zbierania danych podczas sesji profilowania.  
  
 Aby zakończyć sesję profilowania, możesz wyłączyć usługę, a następnie jawnie Wyłącz profilera.  
  
## <a name="starting-the-application-with-the-profiler"></a>Uruchamianie aplikacji przy użyciu profilera  
  
#### <a name="to-start-profiling-a-native-service"></a>Do uruchomienia profilowania usługi natywnej  
  
1.  Otwórz okno wiersza polecenia.  
  
2.  Użyj **VSInstr** narzędzie do generowania instrumentowaną wersję pliku binarnego usługi.  
  
3.  Zastąp instrumentowanej wersji oryginalnego pliku binarnego. W Menedżerze sterowania usługi systemu Windows upewnij się, że usługa uruchamiana ma ustawiony ręczny.  
  
4.  Uruchom profilera. Wpisz:  
  
     **VSPerfCmd** [/start](../profiling/start.md) **: śledzenia**[/output](../profiling/output.md) **:** `OutputFile` [`Options`]    
  
    -   **/Start:trace** opcji inicjowania profilera.  
  
    -   **/Output:** `OutputFile` jest wymagany w przypadku opcji **/start**. `OutputFile`Określa nazwę i lokalizację profilowania pliku danych (Vsp).  
  
     Można użyć dowolnego z następujących opcji z **/start:trace** opcji.  
  
    > [!NOTE]
    >  **User** i **/crosssession** opcje są zwykle wymagane dla aplikacji ASP.NET.  
  
    |Opcja|Opis|  
    |------------|-----------------|  
    |[/ User](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName`|Określa nazwę domeny i użytkownika konta, który jest właścicielem proces roboczy programu ASP.NET. Ta opcja jest wymagana, jeśli proces jest uruchomiony jako użytkownik innego niż zalogowanego użytkownika. Właściciel procesu znajduje się w kolumnie Nazwa użytkownika na karcie Procesy Menedżera zadań systemu Windows.|  
    |[/ crosssession](../profiling/crosssession.md)|Włącza profilowanie procesów w innych sesji logowania. Ta opcja jest wymagana, jeśli aplikacja ASP.NET działa w innej sesji. Identyfikator sesji jest wymieniony w kolumnie Identyfikator sesji, na karcie Procesy Menedżera zadań systemu Windows. **/CS** może być określony jako skrót **/crosssession**.|  
    |[/waitstart](../profiling/waitstart.md)[**:**`Interval`]|Określa liczbę sekund oczekiwania profilera zainicjować przed zwraca błąd. Jeśli `Interval` nie zostanie określony, profilera oczekiwania przez czas nieokreślony. Domyślnie **/start** natychmiast kończy pracę.|  
    |[/globaloff](../profiling/globalon-and-globaloff.md)|Do uruchomienia profilera ze zbierania danych wstrzymana, Dodaj **/globaloff** opcji w celu **/start** wiersza polecenia. Użyj **/globalon** wznowienie profilowania.|  
    |[/ licznika](../profiling/counter.md) **:**`Config`|Zbiera informacje o wydajności procesora licznika określony w konfiguracji. Informacje o liczniku jest dodawany do danych zbieranych na każdym zdarzeniu profilowania.|  
    |[/wincounter](../profiling/wincounter.md) **:**`WinCounterPath`|Określa licznik wydajności systemu Windows, które będą zbierane podczas profilowania.|  
    |[/automark](../profiling/automark.md) **:**`Interval`|Za pomocą **/wincounter** tylko. Określa liczbę milisekund między zdarzeniami kolekcji liczników wydajności systemu Windows. Domyślna to 500 ms.|  
    |[/Events](../profiling/events-vsperfcmd.md) **:**`Config`|Określa zdarzenia funkcji Śledzenie zdarzeń systemu Windows (), które mają być zbierane podczas profilowania. Zdarzenia ETW są gromadzone w pliku oddzielne (ETL).|  
  
5.  Uruchom usługę z Menedżera kontroli usług.  
  
## <a name="controlling-data-collection"></a>Kontrolowanie zbierania danych  
 Gdy usługa jest uruchomiona, można użyć **VSPerfCmd.exe** opcji, aby uruchomić i zatrzymać przy zapisywaniu danych w pliku danych profilera. Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonania programu, takie jak uruchamianie lub zamykanie usługi.  
  
#### <a name="to-start-and-stop-data-collection"></a>Aby uruchomić i zatrzymać zbieranie danych  
  
-   Następujące pary **VSPerfCmd** opcje uruchamiania i zatrzymywania zbierania danych. Określ opcję każdego w osobnym wierszu polecenia. Włączenie funkcji zbierania danych można włączać i wyłączać wiele razy.  
  
    |Opcja|Opis|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Uruchamia (**/globalon**) lub zatrzymania (**/globaloff**) zbierania danych dla wszystkich procesów.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|Uruchamia (**/processon**) lub zatrzymania (**/processoff**) zbierania danych przez proces określony przez identyfikator procesu (`PID`).|  
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:**`TID`|Uruchamia (**/threadon**) lub zatrzymania (**/threadoff**) zbierania danych dla wątku określony przez identyfikator wątku (`TID`).|  
  
## <a name="ending-the-profiling-session"></a>Kończenie sesji profilowania  
 Aby zakończyć sesję profilowania, Zatrzymaj usługę działa instrumentowanych składnik, a następnie wywołać **VSPerfCmd**[/shutdown](../profiling/shutdown.md) opcję, aby wyłączyć profilera i zamknij plik danych profilowania.  
  
#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania  
  
1.  Zatrzymaj usługę z Menedżera kontroli usług.  
  
2.  Zamknij profilera. Wpisz:  
  
     **VSPerfCmd/shutdown**  
  
3.  Zastąp oryginalny instrumentowanych modułu. Jeśli to konieczne, należy ponownie skonfigurować typ uruchomienia usługi.  
  
## <a name="see-also"></a>Zobacz też  
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)   
 [Widok danych metody Instrumentacji](../profiling/instrumentation-method-data-views.md)