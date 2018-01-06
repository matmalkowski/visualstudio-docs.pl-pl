---
title: Profilowanie wiersza polecenia aplikacji sieci Web programu ASP.NET | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- profiling ASP.NET applications
- profling tools,ASP.NET applications
ms.assetid: 897c00d5-5767-433b-a960-4a29c6023ede
caps.latest.revision: "21"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: aspnet
ms.openlocfilehash: 9c96d83a278f7a82c56a58e4db7ec96cbe426bea
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="command-line-profiling-of-aspnet-web-applications"></a>Profilowanie wiersza polecenia aplikacji sieci Web ASP.NET
W tej sekcji opisano procedury i opcje do zbierania danych wydajności dla [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci Web przy użyciu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzi profilowania z wiersza polecenia.  
  
> [!NOTE]
>  Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagane znaczących zmian w sposobie profilera Visual Studio zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows wymagają również nowe techniki kolekcji. Zobacz [narzędzi wydajności w przypadku aplikacji systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="common-tasks"></a>Typowe zadania  
  
|Zadanie|Zawartość pokrewna|  
|----------|---------------------|  
|**Zbieraj ASP.NET podstawowe dane profilowania łatwo:** użyj **VSPerfASPNETCmd** narzędzia do zbierania próbek, Instrumentacja, pamięci platformy .NET, rywalizacji lub warstwy danych o interakcji między bez wymagania dotyczące konfiguracji i Ponowne uruchomienie usług Internet Information Services (IIS), które są wymagane przez **VSPerfCmd**. **VSPerfASPNETCmd** nie pozwala na gromadzenie dodatkowych danych, oraz kontrolowanie zbierania danych. **Uwaga:****VSPerfASPNETCmd** jest zalecane narzędzie należy używać Autonomiczny profiler do profilu z usługi witryny sieci Web ASP.NET.|-   [Szybkie profilowanie za pomocą VSPerfASPNETCmd witryny sieci Web](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)|  
|**Zbieranie statystyk aplikacji:** zbieranie statystyk wydajności przy użyciu metody pobierania próbek. Próbkowanie danych jest przydatne do analizowania problemów użycia procesora CPU i opis właściwości ogólnej wydajności aplikacji.|-   [Zbieranie statystyk aplikacji za pomocą próbkowania](../profiling/collecting-application-statistics-for-aspnet-web-applications-using-the-profiler-sampling-method-from-the-command-line.md)|  
|**Zbieranie szczegółowych danych o chronometrażu:** zbierać informacje o chronometrażu przy użyciu metody instrumentacji. Dane Instrumentacji jest przydatne do analizowania problemów we/wy i szczegółowa analiza scenariusze aplikacji.|-   [Zbieranie szczegółowych danych o chronometrażu przy użyciu Instrumentacji](../profiling/collecting-detailed-timing-data-for-an-aspnet-web-application-using-the-profiler-instrumentation-method-from-the-command-line.md)|  
|**Zbieranie danych pamięci .NET:** Użyj próbkowania i instrumentacji do zbierania danych alokacji pamięci .NET, który pokazuje rozmiaru i liczby przydzielonych obiektów. Może również zbierać danych o okresie istnienia obiektu wyświetlający rozmiaru i liczby obiektów, które odzyskane w każdej generacji kolekcji pamięci.|-   [Zbieranie danych pamięci](../profiling/collecting-memory-data-from-an-aspnet-web-application-by-using-the-profiler-command-line.md)|  
|**Zbieranie danych współbieżności:** zbieranie danych kontencji zasobów przy użyciu metody współbieżności. **Uwaga:** zbieranie danych o aktywności i wizualizacji wątku nie jest obsługiwana dla aplikacji sieci Web.|-   [Zbieranie danych współbieżności](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
|**Dodawanie danych o interakcji między warstwy:** można dodać dane wydajności dotyczące synchroniczne [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] który wywołuje [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci Web wysyła do firmy Microsoft [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] bazy danych.|-   [Zbieranie danych o interakcji między warstwy](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
  
## <a name="related-tasks"></a>Tematy pokrewne  
  
|Zadanie|Zawartość pokrewna|  
|----------|---------------------|  
|**Profil aplikacji autonomicznej (klient)**|-   [Profilowanie aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)|  
|**Usługi profilowania**|-   [Usługi profilowania](../profiling/command-line-profiling-of-services.md)|