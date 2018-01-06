---
title: "Wskazówki: Profilowanie wiersza polecenia przy użyciu Instrumentacji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- profiling tools, walkthroughs
- performance tools, walkthroughs
- performance tools, command-line tools
ms.assetid: 1c6f1586-3d6a-431f-bedf-c54088e280ba
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 29a68dc22a348c787d192bebecea91caed7aa0cc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-command-line-profiling-using-instrumentation"></a>Wskazówki: Profilowanie wiersza polecenia przy użyciu metody instrumentacji
W tym przewodniku zaprezentowano profilowania [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] autonomiczną aplikację w celu zbierania chronometrażu i wywołań liczba dane za pomocą metody Instrumentacji w narzędziach profilowania. W tym przewodniku będzie wykonywać następujące zadania:  
  
-   Użyj [VSInstr](../profiling/vsinstr.md) narzędzia wiersza polecenia, aby wygenerować instrumentowanych danych binarnych.  
  
-   Użyj [VSPerfCLREnv](../profiling/vsperfclrenv.md) narzędzia, aby ustawić zmienne środowiskowe do zbierania danych profilowania platformy .NET.  
  
-   Użyj [VSPerfCmd](../profiling/vsperfcmd.md) narzędzia do zbierania danych profilowania.  
  
-   Użyj [VSPerfReport](../profiling/vsperfreport.md) narzędzie do generowania raportów na podstawie pliku danych profilowania.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
  
-   [!INCLUDE[vsprvsts](../code-quality/includes/vsprvsts_md.md)]  
  
-   Opis pośredniego języka C#  
  
-   Pośredniego opis pracy z narzędzi wiersza polecenia  
  
-   Kopię [PeopleTrax — przykład](../profiling/peopletrax-sample-profiling-tools.md)  
  
-   Aby pracować z informacjami pochodzącymi profilowania, jest najlepszym rozwiązaniem jest dostępne informacje dotyczące symboli debugowania. Aby uzyskać więcej informacji, zobacz [porady: odwołanie do systemu Windows — informacje o symbolach](../profiling/how-to-reference-windows-symbol-information.md).  
  
## <a name="command-line-profiling-using-the-instrumentation-method"></a>Polecenie wiersza profilowania przy użyciu metody Instrumentacji  
 Instrumentacja to metoda profilowania za pomocą którego specjalnie wbudowanych wersje plików binarnych PROFILOWANEGO zawierają funkcje sondowania, zbierające informacje chronometrażu na wejście i wyjście do funkcji w module Instrumentacją. Ponieważ ta metoda profilowania jest bardziej inwazyjne niż próbkowanie, wiąże większej liczbie czynności. Instrumentowanych danych binarnych jest większy niż debugowania lub wersji plików binarnych i nie są przeznaczone do wdrożenia.  
  
> [!NOTE]
>  Nie wysyłaj instrumentowanych danych binarnych dla klientów. Instrumentowane pliki binarne może zawierać kilka ryzyka. Pliki binarne obejmują informacje, które ułatwia aplikacji do odtwarzania, a także zagrożenia bezpieczeństwa.  
  
#### <a name="to-profile-the-peopletrax-application-by-using-the-instrumentation-method"></a>Do profilu aplikacji PeopleTrax przy użyciu metody Instrumentacji  
  
1.  Zainstaluj PeopleTrax przykładowej aplikacji i wersji kompilacji.  
  
2.  Otwórz okno wiersza polecenia i Dodaj **narzędziach profilowania** do lokalnej zmiennej środowiskowej ścieżki katalogu.  
  
3.  Zmień katalog roboczy na katalog zawierający pliki binarne PeopleTrax.  
  
4.  Utwórz katalog zawierający plik na podstawie raportów. Wpisz następujące polecenie:  
  
    ```  
    md Reports  
    ```  
  
5.  Za pomocą narzędzia wiersza polecenia VSInstr Instrumentacja plików binarnych w aplikacji. Wpisz następujące polecenia w osobnych wierszach polecenia:  
  
    ```  
    VSInstr PeopleTrax.exe  
    VSInstr PeopleTrax.exe  
    VSInstr People.dll  
    VSInstr Person.dll  
    VSInstr Operation.dll  
    ```  
  
     **Uwaga** domyślnie VSInstr zapisuje nieinstrumentowanego kopii zapasowej oryginalnego pliku. Rozszerzenie nazwy pliku kopii zapasowej. orig. Na przykład z oryginalną wersją "MyApp.exe" będzie można zapisać jako "MyApp.exe.orig."  
  
6.  Wpisz następujące polecenie, aby ustawić zmienne środowiskowe odpowiednie:  
  
    ```  
    VsPerfCLREnv /traceon  
    ```  
  
7.  Aby uruchomić profilera, wpisz następujące polecenie:  
  
    ```  
    VsPerfCmd /start:trace /output:Reports\Report.vsp  
    ```  
  
8.  Po uruchomieniu profilera w trybie śledzenia, należy uruchomić instrumentowanej wersji PeopleTrax.exe proces zbierania danych.  
  
     **PeopleTrax** zostanie wyświetlone okno aplikacji.  
  
9. Kliknij przycisk **uzyskać osób**.  
  
     Siatki danych PeopleTrax wypełnia danych.  
  
10. Kliknij przycisk **eksportować dane**.  
  
     Notatnik uruchamia i wyświetla nowy plik, który zawiera listę użytkowników z **PeopleTrax** aplikacji.  
  
11. Zamknij Notatnik, a następnie Zamknij **PeopleTrax** aplikacji.  
  
12. Zamknij profilera. Wpisz następujące polecenie:  
  
    ```  
    VSPerfCmd /shutdown  
    ```  
  
13. Wpisz następujące polecenie, aby zresetować zmiennych środowiskowych:  
  
    ```  
    VSPerfCLREnv /off  
    ```  
  
14. Użyj VSPerfReport — narzędzie do generowania lub plików raportów wartości oddzielanych przecinkami (CSV). Wpisz:  
  
    ```  
    VSPerfReport Reports\Report.vsp /output:Reports /summary:all  
    ```  
  
     Można analizować wygenerowanych raportów w programie arkusza kalkulacyjnego, albo użyć [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE w celu analizowania danych profilowania w pliku Report.vsp. Aby uzyskać więcej informacji, zobacz [analizowanie danych narzędzi wydajności](../profiling/analyzing-performance-tools-data.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Sesja wydajności — omówienie](../profiling/performance-session-overview.md)   
 [Profilowanie z wiersza polecenia](../profiling/using-the-profiling-tools-from-the-command-line.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Opis pobierania wartości danych](../profiling/understanding-sampling-data-values.md)   
 [Widoki raportu wydajności](../profiling/performance-report-views.md)