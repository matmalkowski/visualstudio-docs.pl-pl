---
title: Zbieranie danych współbieżności dla usługi przy użyciu wiersza polecenia profilera | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 275aacba-b2af-4d34-8931-ee30d777a256
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6fb73d202251df71a165c586d02d345329b97342
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34267368"
---
# <a name="collect-concurrency-data-for-a-service-by-using-the-profiler-command-line"></a>Zbieranie danych współbieżności dla usługi przy użyciu wiersza polecenia profilera
Metoda współbieżności [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędziach profilowania umożliwia zbieranie danych działanie wątku, który pokazuje wykorzystania Procesora należy, rywalizacji wątku, wątek migracji, opóźnienia synchronizacji, obszarów nakładających się we/wy i inne i danych kontencji zasobów zdarzenia systemu.  
  
> [!NOTE]
>  Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagane znaczących zmian w sposobie profilera Visual Studio zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows wymagają również nowe techniki kolekcji. Zobacz [narzędzi wydajności w przypadku aplikacji systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="common-tasks"></a>Wspólne zadania  
  
|Zadanie|Zawartość pokrewna|  
|----------|---------------------|  
|**Dołącz do uruchomionej usługi .NET**|-   [Porady: dołączanie profilera do usługi .NET i zbieranie danych współbieżności](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**Dodawanie danych o interakcji między warstwy**|-   [Zbieranie danych o interakcji między warstwy](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
|**Dołącz do uruchomionej usługi C/C++**|-   [Porady: dołączanie profilera do usługi natywnej i zbieranie danych współbieżności](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|  
  
## <a name="related-tasks"></a>Zadania powiązane  
  
### <a name="profile-windows-services"></a>Profil usługi systemu Windows  
  
|Zadanie|Zawartość pokrewna|  
|----------|---------------------|  
|**Profil przy użyciu metody pobierania próbek**|-   [Zbieranie statystyk aplikacji za pomocą próbkowania](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)|  
|**Profil przy użyciu metody Instrumentacji**|-   [Zbieranie szczegółowych danych o chronometrażu przy użyciu Instrumentacji](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md)|  
|**Profile.NET pamięci alokacji i odzyskiwanie pamięci**|-   [Zbieranie danych pamięci .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|  
  
### <a name="profile-concurrency-data"></a>Profil współbieżność danych  
  
|Zadanie|Zawartość pokrewna|  
|----------|---------------------|  
|**Profil aplikacji autonomicznych**|-   [Zbieranie danych współbieżności](../profiling/collecting-concurrency-data-for-stand-alone-applications.md)|  
|**Profil aplikacji sieci Web ASP.NET**|-   [Zbieranie danych współbieżności](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|  
  
### <a name="analyze-concurrency-data-views-and-reports"></a>Analizowanie współbieżności widoków danych i raportów  
 [Widok danych kontencji zasobów](../profiling/resource-contention-data-views.md)  
  
 [Concurrency Visualizer](../profiling/concurrency-visualizer.md)  
  
## <a name="reference"></a>Tematy pomocy  
 [Narzędzia profilowania wiersza polecenia — dokumentacja](../profiling/command-line-profiling-tools-reference.md)