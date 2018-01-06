---
title: Profilowanie wiersza polecenia aplikacji autonomicznych | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- profillng tools,stand-alone applications
- profling stand-alone applications
ms.assetid: a47f2bf2-186d-4120-bb79-34e2f3a1ee42
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: dd2b50ae03263cd072143481a91679663f126c53
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="command-line-profiling-of-stand-alone-applications"></a>Profilowanie wiersza polecenia aplikacji autonomicznych
W tej sekcji opisano procedury i opcji zbierania danych wydajności dla aplikacji autonomicznej (klient) przy użyciu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzi profilowania z wiersza polecenia.  
  
## <a name="common-tasks"></a>Typowe zadania  
  
|Zadanie|Zawartość pokrewna|  
|----------|---------------------|  
|**Zbieranie statystyk aplikacji:** zbieranie statystyk wydajności przy użyciu metody pobierania próbek. Próbkowanie danych jest przydatne do analizowania problemy dotyczące użycia procesora CPU i opis właściwości ogólnej wydajności aplikacji.|-   [Zbieranie statystyk aplikacji za pomocą próbkowania](../profiling/collecting-application-statistics-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Zbieranie szczegółowych danych o chronometrażu:** zbierać informacje o chronometrażu przy użyciu metody instrumentacji. Dane Instrumentacji jest przydatne do analizowania problemów we/wy i szczegółowa analiza scenariusze aplikacji.|-   [Zbieranie szczegółowych danych o chronometrażu przy użyciu Instrumentacji](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application-by-using-the-profiler-command-line.md)|  
|**Zbieranie danych pamięci .NET:** Użyj próbkowania i instrumentacji do zbierania danych alokacji pamięci .NET, który pokazuje rozmiaru i liczby przydzielonych obiektów. Może również zbierać danych o okresie istnienia obiektu wyświetlający rozmiaru i liczby obiektów, które odzyskane w każdej generacji kolekcji pamięci.|-   [Zbieranie danych pamięci .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Zbieranie danych współbieżności:** umożliwia zbieranie danych kontencji zasobów i danych działanie wątku, który przedstawia wykorzystanie procesora CPU można, rywalizacji wątku, wątek migracji, opóźnienia synchronizacji, obszarów pokrywającej się z inną operacji We/Wy i inne metoda współbieżności zdarzenia systemu.|-   [Zbieranie danych współbieżności](../profiling/collecting-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Dodawanie danych o interakcji między warstwy:** możesz dodać dane wydajności dotyczące ADO.NET synchroniczne wywołania aplikacji do firmy Microsoft [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] bazy danych. Dodawanie danych o interakcji między warstwy do uruchomienia profilowania wymaga określonych procedur przy użyciu wiersza polecenia narzędzia profilowania.|-   [Zbieranie danych o interakcji między warstwy](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
|**Podczas próby:** użyć procedury krok po kroku do profilowania przykładowej aplikacji klienta przy użyciu metody próbkowania i instrumentacji.|-   [Wskazówki: Profilowanie wiersza polecenia przy użyciu pobierania próbek](../profiling/walkthrough-command-line-profiling-using-sampling.md)<br />-   [Wskazówki: Profilowanie wiersza polecenia przy użyciu Instrumentacji](../profiling/walkthrough-command-line-profiling-using-instrumentation.md)|  
  
## <a name="related-tasks"></a>Tematy pokrewne  
  
|Zadanie|Zawartość pokrewna|  
|----------|---------------------|  
|**Profil aplikacji ASP.NET**|-   [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)|  
|**Usługi profilowania**|-   [Usługi profilowania](../profiling/command-line-profiling-of-services.md)|