---
title: Korzystanie z metod profilowania do zbierania danych wydajności z wiersza polecenia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
ms.assetid: 5613fafc-f298-4e7a-9a2d-a853b61cdf9c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 056b65361576c1578b4985dc202863d77464652e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="using-profiling-methods-to-collect-performance-data-from-the-command-line"></a>Korzystanie z metod profilowania do zbierania danych o wydajności z wiersza polecenia
Wybór [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] opcje i narzędzi wiersza polecenia narzędzi profilowania jest zależna od czynników, takich jak typ aplikacji czy możesz się profilowania, metodę profilowania, która ma być używany, oraz określa, czy aplikacja docelowa jest zapisywane w macierzystym lub [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]kodu.  
  
 W tym temacie organizuje wiersza polecenia procedurach tematów w zależności od wybranej metody profilowania.  
  
## <a name="in-this-topic"></a>W tym temacie:  
 [Zbieranie statystyk wydajności za pomocą metody pobierania próbek](#BKMK_Using_the_sampling_method_to_collect_performance_statistics)  
  
 [Do zbierania danych o chronometrażu przy użyciu metody Instrumentacji](#BKMK_Using_the_instrumentation_method_to_collect_detailed_timing_data)  
  
 [Gromadzenie danych okres istnienia alokacji i obiektu pamięci za pomocą metod pamięci .NET](#BKMK_Using__NET_memory_methods_to_collect_memory_allocation_and_object_lifetime_data)  
  
 [Zbieranie danych działania rywalizacji i wątku zasobów za pomocą metody współbieżności](#BKMK_Using_the_concurrency_method_to_collect_resource_contention_and_thread_activity_data)  
  
 [Dodawanie danych o interakcji między warstwy do uruchomienia profilowania](#BKMK_Adding_tier_interaction_data_to_a_profiling_run)  
  
##  <a name="BKMK_Using_the_sampling_method_to_collect_performance_statistics"></a> Zbieranie statystyk wydajności za pomocą metody pobierania próbek  
 Metody próbkowania w narzędziach profilowania zbiera dane dotyczące wydajności w określonych odstępach czasu w przebiegu profilowania. Próbkowanie danych zapewniają wgląd w informacje powiązane z Procesora problemy z wydajnością i może być dobry sposób, aby rozpocząć eksplorowanie wydajność aplikacji.  
  
 Profiler i aplikacji w tym samym czasie można uruchomić lub może dołączanie profilera do uruchomionego wystąpienia aplikacji.  
  
|Zadanie|Typ aplikacji docelowej|  
|----------|-----------------------------|  
|**Uruchom aplikację**|-   [Aplikacje autonomiczne](../profiling/how-to-launch-a-stand-alone-application-with-the-profiler-and-collect-application-statistics-by-using-the-command-line.md)|  
|**Dołączanie do uruchomionego procesu**|-   [Aplikacji autonomicznej .NET framework](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-and-collect-application-statistics-by-using-the-command-line.md)<br />-   [Natywnych aplikacji autonomicznych](../profiling/how-to-attach-the-profiler-to-a-native-stand-alone-application-and-collect-application-statistics-by-using-the-command-line.md)<br />-   [Aplikacje sieci Web ASP.NET](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [Usług .NET](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [Usługi macierzyste](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line.md)|  
  
##  <a name="BKMK_Using_the_instrumentation_method_to_collect_detailed_timing_data"></a> Do zbierania danych o chronometrażu przy użyciu metody Instrumentacji  
 Metody Instrumentacji w narzędziach profilowania gromadzi dane wydajności z kopie plików binarnych aplikacji zawierające sond oprogramowania do informacji o wydajności rekordów. Na początku i na końcu każdej funkcji instrumentowanych i w każdym wywołaniu innych funkcji z Instrumentacją funkcji zbierane są dane z Instrumentacji. Metoda Instrumentacji jest przydatna do wykrywania problemów z wydajnością z problemami dotyczącymi operacji We/Wy, takich jak użycie dysku.  
  
 Utwórz instrumentowanego pliku binarnego z [VInstr.exe](../profiling/vsinstr.md) narzędzia. Po inicjowania profilera automatycznie zebraniu danych z instrumentowanych danych binarnych po uruchomieniu aplikacji docelowej.  
  
 **Typ aplikacji docelowej**  
  
-   [Składniki autonomicznej .NET framework](../profiling/how-to-instrument-a-stand-alone-dotnet-framework-component-and-collect-timing-data-with-the-profiler-from-the-command-line.md)  
  
-   [Natywny autonomicznej składników](../profiling/how-to-instrument-a-native-stand-alone-component-and-collect-timing-data-with-the-profiler-from-the-command-line.md)  
  
-   [Aplikacje sieci Web ASP.NET statycznie skompilowanej](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line.md)  
  
-   [Aplikacje sieci Web ASP.NET dynamicznie skompilowanej](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler.md)  
  
-   [Usług .NET](../profiling/how-to-instrument-a-dotnet-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)  
  
-   [Usługi macierzyste](../profiling/how-to-instrument-a-native-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)  
  
##  <a name="BKMK_Using__NET_memory_methods_to_collect_memory_allocation_and_object_lifetime_data"></a> Gromadzenie danych okres istnienia alokacji i obiektu pamięci za pomocą metod pamięci .NET  
 Metoda pamięci .NET narzędzi profilowania umożliwia zbieranie [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] danych alokacji pamięci oraz informacje o okresie istnienia obiektów w [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
 Można uruchomić aplikacji docelowej za pomocą profilera; Możesz dołączyć profilera uruchomione wystąpienie aplikacji; można również utworzyć instrumentowanej wersji aplikacji do zbierania informacji chronometrażu razem z [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] danych pamięci.  
  
|Zadanie|Typ aplikacji docelowej|  
|----------|-----------------------------|  
|**Uruchom aplikację**|-   [Aplikacji autonomicznej .NET Framework](../profiling/how-to-launch-a-stand-alone-dotnet-framework-application-with-the-profiler-to-collect-memory-data-by-using-the-command-line.md)|  
|**Dołączanie do uruchomionego procesu**|-   [Aplikacji autonomicznej .NET framework](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-to-collect-memory-data-by-using-the-command-line.md)<br />-   [Aplikacje sieci Web ASP.NET](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)<br />-   [Usług .NET](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-memory-data-by-using-the-command-line.md)|  
|**Moduły dokumentu**|-   [Składniki autonomicznej .NET framework](../profiling/how-to-instrument-a-stand-alone-dotnet-framework-component-and-collect-memory-data-with-the-profiler-by-using-the-command-line.md)<br />-   [Aplikacje sieci Web ASP.NET statycznie skompilowanej](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)<br />-   [Aplikacje sieci Web ASP.NET dynamicznie skompilowanej](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data.md)<br />-   [Usług .NET](../profiling/how-to-instrument-a-dotnet-framework-service-and-collect-memory-data-by-using-the-profiler-command-line.md)|  
  
##  <a name="BKMK_Using_the_concurrency_method_to_collect_resource_contention_and_thread_activity_data"></a> Zbieranie danych działania rywalizacji i wątku zasobów za pomocą metody współbieżności  
 Metoda współbieżności narzędziach profilowania umożliwia zbieranie danych działanie wątku i procesu i rywalizacji z aplikacji wielowątkowych.  
  
 Aplikację można uruchomić za pomocą profilera, lub można dołączanie profilera do uruchomionego wystąpienia aplikacji.  
  
|Zadanie|Typ aplikacji docelowej|  
|----------|-----------------------------|  
|**Uruchom aplikację**|-   [Aplikacji autonomicznej .NET Framework](../profiling/how-to-launch-a-stand-alone-dotnet-framework-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Autonomicznej aplikacji natywnej](../profiling/how-to-launch-a-stand-alone-native-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**Dołączanie do uruchomionego procesu**|-   [Aplikacji autonomicznej .NET framework](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Autonomicznej aplikacji natywnej](../profiling/how-to-attach-the-profiler-to-a-native-stand-alone-application-and-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Aplikacja sieci Web ASP.NET](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Usługa .NET](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Usługi natywnej](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|  
  
##  <a name="BKMK_Adding_tier_interaction_data_to_a_profiling_run"></a> Dodawanie danych o interakcji między warstwy do uruchomienia profilowania  
 Dodawanie danych o interakcji między warstwy do uruchomienia profilowania wymaga określonych procedur przy użyciu wiersza polecenia narzędzia profilowania. Zobacz [zbierania danych o interakcji między warstwy](../profiling/adding-tier-interaction-data-from-the-command-line.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Profilowanie aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)