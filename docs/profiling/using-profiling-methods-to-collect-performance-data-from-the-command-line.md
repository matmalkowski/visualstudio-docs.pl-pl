---
title: Korzystanie z metod profilowania do zbierania danych wydajności z wiersza polecenia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 5613fafc-f298-4e7a-9a2d-a853b61cdf9c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 141341c09d9028e90900a29c702667304cfea7f7
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34477713"
---
# <a name="use-profiling-methods-to-collect-performance-data-from-the-command-line"></a>Korzystanie z metod profilowania do zbierania danych o wydajności z wiersza polecenia
Wybór [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] opcje i narzędzi wiersza polecenia narzędzi profilowania jest zależna od czynników, takich jak typ aplikacji czy możesz się profilowania, metodę profilowania, która ma być używany, oraz określa, czy aplikacja docelowa jest zapisywane w macierzystym lub [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]kodu.  
  
 W tym temacie organizuje wiersza polecenia procedurach tematów w zależności od wybranej metody profilowania.  
  
## <a name="use-the-sampling-method-to-collect-performance-statistics"></a>Zbieranie statystyk wydajności przy użyciu metody pobierania próbek  
 Metody próbkowania w narzędziach profilowania zbiera dane dotyczące wydajności w określonych odstępach czasu w przebiegu profilowania. Próbkowanie danych zapewniają wgląd w informacje powiązane z Procesora problemy z wydajnością i może być dobry sposób, aby rozpocząć eksplorowanie wydajność aplikacji.  
  
 Profiler i aplikacji w tym samym czasie można uruchomić lub może dołączanie profilera do uruchomionego wystąpienia aplikacji.  
  
|Zadanie|Typ aplikacji docelowej|  
|----------|-----------------------------|  
|**Uruchom aplikację**|-   [Aplikacje autonomiczne](../profiling/how-to-launch-a-stand-alone-application-with-the-profiler-and-collect-application-statistics-by-using-the-command-line.md)|  
|**Dołączanie do uruchomionego procesu**|-   [Aplikacji autonomicznej .NET framework](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-application-statistics.md)<br />-   [Natywnych aplikacji autonomicznych](../profiling/how-to-attach-the-profiler-to-a-native-stand-alone-application-and-collect-application-statistics-by-using-the-command-line.md)<br />-   [Aplikacje sieci web ASP.NET](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [Usług .NET](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [Usługi macierzyste](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line.md)|  
  
## <a name="use-the-instrumentation-method-to-collect-detailed-timing-data"></a>Zbieranie szczegółowych danych o chronometrażu przy użyciu metody Instrumentacji  
 Metody Instrumentacji w narzędziach profilowania gromadzi dane wydajności z kopie plików binarnych aplikacji zawierające sond oprogramowania do informacji o wydajności rekordów. Na początku i na końcu każdej funkcji instrumentowanych i w każdym wywołaniu innych funkcji z Instrumentacją funkcji zbierane są dane z Instrumentacji. Metoda Instrumentacji jest przydatna do wykrywania problemów z wydajnością z problemami dotyczącymi operacji We/Wy, takich jak użycie dysku.  
  
 Utwórz instrumentowanego pliku binarnego z [VInstr.exe](../profiling/vsinstr.md) narzędzia. Po inicjowania profilera automatycznie zebraniu danych z instrumentowanych danych binarnych po uruchomieniu aplikacji docelowej.  
  
 **Typ aplikacji docelowej**  
  
-   [Składniki autonomicznej .NET framework](../profiling/how-to-instrument-a-stand-alone-dotnet-framework-component-and-collect-timing-data-with-the-profiler-from-the-command-line.md)  
  
-   [Natywny autonomicznej składników](../profiling/how-to-instrument-a-native-stand-alone-component-and-collect-timing-data-with-the-profiler-from-the-command-line.md)  
  
-   [Statycznie skompilowanej aplikacji sieci web ASP.NET](../profiling/how-to-instrument-statically-compiled-aspnet-and-collect-detailed-timing-data.md)  
  
-   [Dynamicznie skompilowanej aplikacji sieci web ASP.NET](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-app-and-collect-timing-data.md)  
  
-   [Usług .NET](../profiling/how-to-instrument-a-dotnet-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)  
  
-   [Usługi macierzyste](../profiling/how-to-instrument-a-native-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)  
  
## <a name="use-net-memory-methods-to-collect-memory-allocation-and-object-lifetime-data"></a>Umożliwia zbieranie danych pamięci alokacji i obiekt okres istnienia metod pamięci .NET  
 Metoda pamięci .NET narzędzi profilowania umożliwia zbieranie [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] danych alokacji pamięci oraz informacje o okresie istnienia obiektów w [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
 Można uruchomić aplikacji docelowej za pomocą profilera; Możesz dołączyć profilera uruchomione wystąpienie aplikacji; można również utworzyć instrumentowanej wersji aplikacji do zbierania informacji chronometrażu razem z [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] danych pamięci.  
  
|Zadanie|Typ aplikacji docelowej|  
|----------|-----------------------------|  
|**Uruchom aplikację**|-   [Aplikacji autonomicznej .NET Framework](../profiling/how-to-launch-a-stand-alone-dotnet-framework-application-with-the-profiler-to-collect-memory-data-by-using-the-command-line.md)|  
|**Dołączanie do uruchomionego procesu**|-   [Aplikacji autonomicznej .NET framework](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-to-collect-memory-data-by-using-the-command-line.md)<br />-   [Aplikacje sieci web ASP.NET](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)<br />-   [Usług .NET](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-memory-data-by-using-the-command-line.md)|  
|**Moduły dokumentu**|-   [Składniki autonomicznej .NET framework](../profiling/how-to-instrument-a-dotnet-framework-component-and-collect-memory-data.md)<br />-   [Statycznie skompilowanej aplikacji sieci web ASP.NET](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)<br />-   [Dynamicznie skompilowanej aplikacji sieci web ASP.NET](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data.md)<br />-   [Usług .NET](../profiling/how-to-instrument-a-dotnet-framework-service-and-collect-memory-data-by-using-the-profiler-command-line.md)|  
  
## <a name="use-the-concurrency-method-to-collect-resource-contention-and-thread-activity-data"></a>Zbieranie danych działania rywalizacji i wątku zasobów przy użyciu metody współbieżności  
 Metoda współbieżności narzędziach profilowania umożliwia zbieranie danych działanie wątku i procesu i rywalizacji z aplikacji wielowątkowych.  
  
 Aplikację można uruchomić za pomocą profilera, lub można dołączanie profilera do uruchomionego wystąpienia aplikacji.  
  
|Zadanie|Typ aplikacji docelowej|  
|----------|-----------------------------|  
|**Uruchom aplikację**|-   [Aplikacji autonomicznej .NET Framework](../profiling/how-to-launch-a-stand-alone-dotnet-framework-app-to-collect-concurrency-data.md)<br />-   [Autonomicznej aplikacji natywnej](../profiling/how-to-launch-a-stand-alone-native-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**Dołączanie do uruchomionego procesu**|-   [Aplikacji autonomicznej .NET framework](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-concurrency-data.md)<br />-   [Autonomicznej aplikacji natywnej](../profiling/how-to-attach-the-profiler-to-a-native-stand-alone-application-and-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Aplikacja sieci web ASP.NET](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Usługa .NET](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Usługi natywnej](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|  
  
## <a name="add-tier-interaction-data-to-a-profiling-run"></a>Dodawanie danych o interakcji między warstwy do uruchomienia profilowania  
 Dodawanie danych o interakcji między warstwy do uruchomienia profilowania wymaga określonych procedur przy użyciu wiersza polecenia narzędzia profilowania. Zobacz [zbierania danych o interakcji między warstwy](../profiling/adding-tier-interaction-data-from-the-command-line.md)  
  
## <a name="see-also"></a>Zobacz także  
 [Profil aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Aplikacje sieci web ASP.NET profilu](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)