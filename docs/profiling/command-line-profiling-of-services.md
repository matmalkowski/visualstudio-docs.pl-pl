---
title: Profilowanie wiersza polecenia usług | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling toos,services
- profiling services
ms.assetid: f0d62318-b0e8-49c6-9a30-9f7a6adef2f6
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 35493114b9dcc0d71248f7edf046c835e04ae374
ms.sourcegitcommit: 37144589d9f850ff81ec7bfb884429989925a43d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2018
ms.locfileid: "34335791"
---
# <a name="command-line-profiling-of-services"></a>Profilowanie wiersza polecenia usług
W tej sekcji opisano procedury i opcji zbierania danych wydajności dla usług systemu Windows przy użyciu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzi profilowania z wiersza polecenia.  
  
> [!NOTE]
>  Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagane znaczących zmian w sposobie profilera Visual Studio zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows wymagają również nowe techniki kolekcji. Zobacz [narzędzi wydajności w przypadku aplikacji systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="common-tasks"></a>Wspólne zadania

  
|Zadanie|Zawartość pokrewna|  
|----------|---------------------|  
|**Zbieranie statystyk aplikacji:** zbieranie statystyk wydajności przy użyciu metody pobierania próbek. Próbkowanie danych jest przydatne do analizowania problemy dotyczące użycia procesora CPU i opis właściwości ogólnej wydajności aplikacji.|-   [Zbieranie statystyk aplikacji za pomocą próbkowania](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)|  
|**Zbieranie szczegółowych danych o chronometrażu:** zbierać informacje o chronometrażu przy użyciu metody instrumentacji. Dane Instrumentacji jest przydatne do analizowania problemów we/wy i szczegółowa analiza scenariusze aplikacji.|-   [Zbieranie szczegółowych danych o chronometrażu przy użyciu Instrumentacji](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md)|  
|**Zbieranie danych pamięci .NET:** Użyj próbkowania i instrumentacji do zbierania danych alokacji pamięci .NET, który pokazuje rozmiaru i liczby przydzielonych obiektów. Może również zbierać danych o okresie istnienia obiektu wyświetlający rozmiaru i liczby obiektów, które odzyskane w każdej generacji kolekcji pamięci.|-   [Zbieranie danych pamięci .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|  
|**Zbieranie danych współbieżności:** umożliwia zbieranie danych kontencji zasobów i danych działanie wątku, który przedstawia wykorzystanie procesora CPU można, rywalizacji wątku, migracji wątku, opóźnienia synchronizacji, obszarów nakładających się we/wy i inne metoda współbieżności zdarzenia systemu.|-   [Zbieranie danych współbieżności](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|  
|**Dodawanie danych o interakcji między warstwy:** możesz dodać dane wydajności dotyczące ADO.NET synchroniczne wywołania usługi do programu Microsoft [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] bazy danych.|-   [Zbieranie danych o interakcji między warstwy](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
  
## <a name="related-tasks"></a>Zadania powiązane  
  
|Zadanie|Zawartość pokrewna|  
|----------|---------------------|  
|**Profil aplikacji autonomicznej (klient)**|-   [Profil aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)|  
|**Profil aplikacji ASP.NET**|-   [Aplikacje sieci web ASP.NET profilu](../profiling/command-line-profiling-of-aspnet-web-applications.md)|