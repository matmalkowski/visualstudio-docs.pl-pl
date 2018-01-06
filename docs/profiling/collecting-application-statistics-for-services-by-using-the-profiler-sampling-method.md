---
title: "Zbieranie statystyk aplikacji dla usług przy użyciu metody próbkowania profilera | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 07840ab2-3a92-4744-ac87-48b19e0ceecd
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 96c4bb5a9ea5b7ff85f115048fc057191884a016
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="collecting-application-statistics-for-services-by-using-the-profiler-sampling-method"></a>Zbieranie statystyk aplikacji dla usług przy użyciu metody próbkowania profilera
W tej sekcji opisano procedury i opcje dla zbieranie statystyk wydajności dla usług systemu Windows przy użyciu metody próbkowania w wierszu polecenia.  
  
> [!NOTE]
>  Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagane znaczących zmian w sposobie profilera Visual Studio zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows wymagają również nowe techniki kolekcji. Zobacz [narzędzi wydajności w przypadku aplikacji systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="common-tasks"></a>Typowe zadania  
  
|Zadanie|Zawartość pokrewna|  
|----------|---------------------|  
|**Dołączanie profilera do usługi .NET**|-   [Porady: dołączanie profilera do usługi .NET w celu zbierania statystyk aplikacji](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-application-statistics-by-using-the-command-line.md)|  
|**Dodawanie danych o interakcji między warstwy**|-   [Zbieranie danych o interakcji między warstwy](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
|**Dołączanie profilera do usługi C/C++**|-   [Porady: dołączanie profilera do usługi natywnej i zbieranie statystyk aplikacji](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line.md)|  
  
## <a name="related-tasks"></a>Tematy pokrewne  
  
### <a name="profiling-windows-services"></a>Profilowanie usług systemu Windows  
  
|Zadanie|Zawartość pokrewna|  
|----------|---------------------|  
|**Profil przy użyciu metody Instrumentacji**|-   [Zbieranie szczegółowych danych o chronometrażu przy użyciu Instrumentacji](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method-from-the-profiler-command-line.md)|  
|**Profil pamięci .NET alokacji i odzyskiwanie pamięci**|-   [Zbieranie danych pamięci .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|  
|**Profil działania rywalizacji i wątku zasobów**|-   [Zbieranie danych współbieżności](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|  
  
### <a name="profiling-by-using-the-sampling-method"></a>Profilowanie przy użyciu metody pobierania próbek  
  
|Zadanie|Zawartość pokrewna|  
|----------|---------------------|  
|**Profil aplikacji autonomicznej (klient)**|-   [Zbieranie statystyk aplikacji za pomocą próbkowania](../profiling/collecting-application-statistics-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Profil aplikacji sieci Web ASP.NET**|-   [Zbieranie statystyk aplikacji za pomocą próbkowania](../profiling/collecting-application-statistics-for-aspnet-web-applications-using-the-profiler-sampling-method-from-the-command-line.md)|  
  
### <a name="analyzing-sampling-data-views-and-reports"></a>Analizowanie danych próbkowania widoków i raportów  
 [Widok danych metody próbkowania](../profiling/profiler-sampling-method-data-views.md)