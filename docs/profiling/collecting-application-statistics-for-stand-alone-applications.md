---
title: Zbieranie statystyk aplikacji dla aplikacji autonomicznych przy użyciu wiersza polecenia profilera | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method
- profilng tools,sampling method
ms.assetid: be2dbdd0-fc88-45f9-a1d5-bcb4f64e17ad
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 69c9fe7ac91b8e4015204ee157f30c65583dc1df
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/11/2018
---
# <a name="collecting-application-statistics-for-stand-alone-applications-by-using-the-profiler-command-line"></a>Zbieranie statystyk aplikacji dla aplikacji autonomicznych przy użyciu wiersza polecenia profilera
W tej sekcji opisano procedury i opcje dla zbieranie statystyk wydajności dla aplikacji (autonomiczny) klienta za pomocą metody pobierania próbek w wierszu polecenia.  
  
> [!NOTE]
>  Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagane znaczących zmian w sposobie profilera Visual Studio zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows wymagają również nowe techniki kolekcji. Zobacz [narzędzi wydajności w przypadku aplikacji systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="common-tasks"></a>Typowe zadania  
  
|Zadanie|Zawartość pokrewna|  
|----------|---------------------|  
|**Uruchom aplikację za pomocą profilowania**|-   [Porady: uruchamianie aplikacji autonomicznej i zbieranie statystyk aplikacji](../profiling/how-to-launch-a-stand-alone-application-with-the-profiler-and-collect-application-statistics-by-using-the-command-line.md)|  
|**Dołączanie profilera do uruchomionej aplikacji .NET Framework**|-   [Porady: dołączanie profilera do aplikacji autonomicznej .NET Framework i zbieranie statystyk aplikacji](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-application-statistics.md)|  
|**Dołączanie profilera do uruchomionej aplikacji C/C++**|-   [Porady: dołączanie profilera do aplikacji natywnej i zbieranie statystyk aplikacji](../profiling/how-to-attach-the-profiler-to-a-native-stand-alone-application-and-collect-application-statistics-by-using-the-command-line.md)|  
|**Dodawanie danych o interakcji między warstwy**|-   [Zbieranie danych o interakcji między warstwy](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
  
## <a name="related-tasks"></a>Tematy pokrewne  
  
### <a name="profiling-stand-alone-applications"></a>Profilowanie aplikacji autonomicznych  
  
|Zadanie|Zawartość pokrewna|  
|----------|---------------------|  
|**Instrumentacja aplikacji**|-   [Zbieranie szczegółowych danych o chronometrażu przy użyciu Instrumentacji](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md)|  
|**Zbieranie danych pamięci .NET alokacji i odzyskiwanie kolekcji**|-   [Zbieranie danych pamięci .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md)|  
|**Zbieranie danych wykonywania rywalizacji i wątku zasobów**|-   [Zbieranie danych współbieżności](../profiling/collecting-concurrency-data-for-stand-alone-applications.md)|  
  
### <a name="profiling-by-using-the-sampling-method"></a>Profilowanie przy użyciu metody pobierania próbek  
  
|Zadanie|Zawartość pokrewna|  
|----------|---------------------|  
|**Profil aplikacji sieci Web ASP.NET**|-   [Zbieranie statystyk aplikacji za pomocą próbkowania](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md)|  
|**Usługi profilowania**|-   [Zbieranie statystyk aplikacji za pomocą próbkowania](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md). Opisuje sposób zbieranie statystyk wydajności z usługi systemu Windows za pomocą metody pobierania próbek.|  
  
### <a name="analyzing-sampling-data-views-and-reports"></a>Analizowanie danych próbkowania widoków i raportów  
 [Widok danych metody próbkowania](../profiling/profiler-sampling-method-data-views.md)