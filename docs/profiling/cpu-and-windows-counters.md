---
title: Procesor CPU i liczniki systemu Windows | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.performance.property.counters
helpviewer_keywords:
- Windows counters in Profiling Tools
- CPU counters in Profiling Tools
ms.assetid: d2c45c6a-f975-45ab-b8a5-4768ddd518fb
caps.latest.revision: "28"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 62889012c5640fb0f29eadb6f70e678f941ff286
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/11/2017
---
# <a name="cpu-and-windows-counters"></a>CPU i liczniki systemu Windows
Profilera Visual Studio umożliwia zbieranie danych wydajności, który został wygenerowany przez jednostkę procesora (liczniki CPU) i dane wydajności, który został wygenerowany przez system operacyjny (liczniki systemu Windows).  
  
 **Wymagania**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
> [!NOTE]
>  Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagane znaczących zmian w sposobie profilera Visual Studio zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows wymagają również nowe techniki kolekcji. Zobacz [narzędzi wydajności w przypadku aplikacji systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="windows-counters"></a>Liczniki systemu Windows  
 Liczniki systemu Windows są częścią infrastruktury diagnostycznych systemu Windows, który zawiera informacje o wydajności systemu operacyjnego lub aplikacji, usługi lub sterownika. Liczniki systemu Windows zależą od konfiguracji bieżącego komputera i mogą nie być dostępne na innych komputerach. Liczniki wydajności systemu Windows są zbierane w profilowania pliki danych profilowania znaków, które mogą być następnie używane do filtrowania widoków i raportów.  
  
## <a name="cpu-counters"></a>Liczniki CPU  
 Liczniki CPU są funkcją procesora komputera, którym przechowywane liczba zdarzeń związanych ze sprzętem.  Podczas zbierania danych licznika Procesora przy użyciu metoda profilowania instrumentacji, dane są dołączane do danych w modułach i funkcje. Można zebrać wiele liczników CPU przy użyciu metody instrumentacji. Korzystając z metody pobierania próbek, możesz wybrać jeden licznik do użycia jako zdarzenie do próbkowania.  
  
 Liczniki wydajności są specyficzne dla procesora CPU. Różne modele i wersje procesora CPU mogą mieć znacząco różnych ustawień konfiguracji umożliwiające tego samego licznika wydajności. [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]Zdarzenia przenośne profilera oddziel typowe liczniki wydajności z określonych procesorów i umożliwiają zbieranie lub przykładowe zdarzenia dotyczące ogólnego wydajności.  
  
 Jeśli chcesz liczba konkretnego zdarzenia, gdy używasz profilera, na przykład Chybienia pamięci podręcznej L2, można utworzyć sesję wydajności wokół tego nadawcy zdarzeń. Można to zrobić na dowolnym Procesorze z pamięci podręcznej L2. Sesja wydajności mogą zostać przeniesione bez żadnych modyfikacji od platformy.  
  
 Profilera Visual Studio w dalszym ciągu obsługuje określonego zdarzenia dla określonej platformy. Na przykład Deweloper na platformie Pentium 4 chcieć liczba zdarzeń, które są specyficzne dla architektury NetBurst. To zdarzenie nie jest przenośny, ale pozostanie dostępna do projektanta dla sesji wydajności zależnych na danej platformie.  
  
## <a name="portable-and-platform-events"></a>Przenośny i zdarzenia platformy  
 Przenośne zdarzenia są grupy liczniki CPU, które nie są specyficzne dla określonego procesora. Wszystkie liczniki CPU są nazywane zdarzenia platformy i może nie być obsługiwany na różnych platformach.  
  
 Liczniki dla zdarzenia zarówno przenośny i platforma są definiowane w. Pliki XML, w którym znajdują się określone wartości, które są powiązane z liczników. Istnieją różne procesory, wiele plików, ponieważ dane dotyczące firmy Intel i procesory AMD, na przykład są różne. [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)] Profilera używa tych informacji do prezentowania odpowiednich liczników, zarówno przenośne, jak i platformy, dla użytkownika do pomiaru wydajności.  
  
### <a name="portable-events"></a>Przenośne zdarzenia  
 Przenośne zdarzenia zawierają następujące zdarzenia:  
  
 **Zdarzenia ogólne**  
  
|Nazwa zdarzenia|Opis zdarzenia|  
|----------------|-----------------------|  
|Wycofane instrukcje|Wskazuje liczbę instrukcji, które wykonane do czasu ukończenia zdarzenia.|  
|Cykle nie jest zatrzymany|Wskazuje tylko te cykle, w których procesor nie został on zatrzymany, na przykład oczekiwania na We/Wy.|  
  
 **Zdarzenia frontonu**  
  
|Nazwa zdarzenia|Opis zdarzenia|  
|----------------|-----------------------|  
|Chybienia ITLB|Określa liczbę wyszukiwań tłumaczenia instrukcji wygląd Zarezerwuj buforu, które spowodowały nie trafienia.|  
  
 **Zdarzenia gałęzi**  
  
|Nazwa zdarzenia|Opis zdarzenia|  
|----------------|-----------------------|  
|Wycofane gałęzi|Wskazuje liczbę instrukcje gałęzi wykonane do czasu ukończenia zdarzenia.|  
|Źle przewidywane gałęzi|Wskazuje źle przewidywane gałęzie, które występuje, ponieważ procesor przewidzieć niepoprawną ścieżkę. Źle przewidywane gałęzie wpłynąć na wydajność, ponieważ procesor Odrzuć wszystkie pracy i uruchom ponownie na poprawną ścieżkę.|  
  
 **Zdarzenia pamięci:**  
  
|Nazwa zdarzenia|Opis zdarzenia|  
|----------------|-----------------------|  
|L2 Chybienia odczytu pamięci podręcznej|Wskazuje, że liczba drugiego poziomu pamięci podręcznej odczytu Chybienia.|  
|L2 Odwołania odczytu pamięci podręcznej|Wskazuje, że liczba drugiego poziomu pamięci podręcznej odczytu odwołania. Chybienia ładowania obejmuje, a odczytu Chybienia własność (RFO) i trafień.|  
  
## <a name="viewing-available-counters"></a>Przeglądanie dostępnych liczników  
 Można wyświetlić listę dostępnych liczniki CPU w środowisku IDE programu Visual Studio na, w oknie wiersza polecenia.  
  
### <a name="visual-studio-ui"></a>Visual Studio interfejsu użytkownika  
 Aby wyświetlić listę dostępnych liczników na komputerze w środowisku IDE programu Visual Studio, musi mieć sesję wydajności programu profilującego Otwórz w Eksploratorze wydajności.  
  
##### <a name="to-view-a-list-of-a-list-of-all-cpu-counters-that-are-supported-on-the-current-platform"></a>Aby wyświetlić listę listę wszystkie liczniki CPU, które są obsługiwane na bieżącej platformie  
  
1.  W Eksploratorze wydajności, kliknij prawym przyciskiem myszy sesję wydajności, a następnie kliknij przycisk **właściwości**.  
  
2.  Wykonaj jedną z następujących czynności:  
  
    -   Kliknij przycisk **próbkowania**, a następnie wybierz **licznika wydajności** z **próbki** listy zdarzeń. Liczniki CPU są wymienione w **dostępnych liczników wydajności**.  
  
         **Uwaga** kliknij **anulować** aby powrócić do poprzedniej konfiguracji próbkowania.  
  
     —lub—  
  
    -   Wybierz **liczniki CPU**, a następnie wybierz **zbieranie liczniki CPU**. Liczniki CPU są wymienione w **dostępne liczniki**.  
  
         **Uwaga** kliknij **anulować** aby powrócić do poprzedniej konfiguracji licznika w kolekcji.  
  
##### <a name="to-view-a-list-of-a-list-of-window-counters-that-are-supported-on-the-current-platform"></a>Aby wyświetlić listę listę liczników okna, które są obsługiwane na bieżącej platformie  
  
1.  W Eksploratorze wydajności, kliknij prawym przyciskiem myszy sesję wydajności, a następnie kliknij przycisk **właściwości**.  
  
2.  Kliknij przycisk **liczników systemu Windows**.  
  
3.  Wybierz **zbierania liczników systemu Windows**.  
  
4.  Z **kategorii licznika** listy, wybierz grupę licznika. Licznik systemu Windows dla grupy jest wyświetlana w polu listy.  
  
     **Uwaga:** kliknij **anulować** aby powrócić do poprzedniej konfiguracji licznika w kolekcji.  
  
### <a name="command-line"></a>Wiersz polecenia  
 Przy użyciu [VSPerfCmd](../profiling/vsperfcmd.md) narzędzia wiersza polecenia, można wyświetlić listę liczniki CPU, które są dostępne na komputerze z poziomu wiersza polecenia.  
  
##### <a name="to-list-of-cpu-counters-that-are-supported-on-the-current-platform"></a>Do listy Liczniki CPU, które są obsługiwane na bieżącej platformie  
  
1.  Otwórz okno wiersza polecenia.  
  
2.  Typ  
  
     **\<Katalogu narzędzi wydajności programu Visual Studio > \VSPerfCmd /querycounters**  
  
     gdzie  **\<katalogu narzędzi wydajności programu Visual Studio >** zazwyczaj jest to ścieżka do katalogu narzędzi wydajności instalację programu Visual Studio  
  
     C:\Program Files\Microsoft Visual Studio 10.0\Team narzędzia Tools  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie](../profiling/overviews-performance-tools.md)   
 [Porady: Wybieranie zdarzeń pobierania próbek](../profiling/how-to-choose-sampling-events.md)   
 [Porady: zbieranie danych licznika Procesora](../profiling/how-to-collect-cpu-counter-data.md)   
 [Porady: zbieranie danych liczników systemu Windows](../profiling/how-to-collect-windows-counter-data.md)