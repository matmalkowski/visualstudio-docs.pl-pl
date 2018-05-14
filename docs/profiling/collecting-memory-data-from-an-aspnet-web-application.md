---
title: Zbieranie danych pamięci z aplikacji sieci Web ASP.NET przy użyciu wiersza polecenia profilera | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- .NET memory profiling method
- profiling tools,.NET memory method
ms.assetid: 57acf2b0-327a-4c0e-8078-ac2f6d99457d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 161f96c38a12de1f29a0f4ebd5d3779f31cf8f23
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/11/2018
---
# <a name="collecting-memory-data-from-an-aspnet-web-application-by-using-the-profiler-command-line"></a>Zbieranie danych pamięci z aplikacji sieci Web ASP.NET przy użyciu wiersza polecenia profilera
W tej sekcji opisano procedury i opcji zbierania danych pamięci alokacji i obiekt okres istnienia dla aplikacji sieci Web ASP.NET przy użyciu **VSPerfCmd** narzędzia wiersza polecenia.  
  
> [!NOTE]
>  **VSPerfCmd** narzędzie zapewnia pełny dostęp do narzędzi profilowania funkcjonalność, co obejmuje wstrzymywanie i wznawianie profilowania i zbierania dodatkowych danych z procesora i liczników wydajności systemu Windows. Można również użyć **VSPerfASPNETCmd** narzędzia wiersza polecenia, gdy nie ma potrzeby tę funkcję. W porównaniu z [VSPerfCmd](../profiling/vsperfcmd.md) narzędzia wiersza polecenia, zmienne środowiskowe, nie trzeba ustawić i ponowne uruchomienie komputera nie jest wymagane. Aby uzyskać więcej informacji, zobacz [szybkie profilowanie witryny sieci Web za pomocą VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).  
  
## <a name="common-tasks"></a>Typowe zadania  
  
|Zadanie|Zawartość pokrewna|  
|----------|---------------------|  
|**Dołączanie profilera do uruchomionej aplikacji ASP.NET**|-   [Porady: dołączanie profilera do aplikacji sieci Web ASP.NET w celu zbierania danych pamięci](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)|  
|**Instrument statycznie skompilowane pliki binarne**|-   [Porady: Instrumentacja statycznie skompilowanej ASP.NET aplikacji i zbieranie danych pamięci](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)|  
|**Instrument dynamicznie skompilowanych plików binarnych**|-   [Porady: Instrumentacja dynamicznie skompilowanej ASP.NET aplikacji i zbieranie danych pamięci](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data.md)|  
  
## <a name="related-tasks"></a>Tematy pokrewne  
  
### <a name="profiling-aspnet-web-applications"></a>Profilowanie aplikacji sieci Web ASP.NET  
  
|Zadanie|Zawartość pokrewna|  
|----------|---------------------|  
|**Profil przy użyciu metody pobierania próbek**|-   [Zbieranie statystyk aplikacji za pomocą próbkowania](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md)|  
|**Profil przy użyciu metody Instrumentacji**|-   [Zbieranie szczegółowych danych o chronometrażu przy użyciu Instrumentacji](../profiling/collecting-detailed-timing-data-aspnet-profiler-instrumentation-method.md)|  
|**Profil działania rywalizacji i wątku zasobów**|-   [Zbieranie danych współbieżności](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|  
  
### <a name="profiling-net-framework-memory-data"></a>Profilowanie danych pamięci .NET Framework  
  
|Zadanie|Zawartość pokrewna|  
|----------|---------------------|  
|**Profil aplikacji autonomicznej (klient)**|-   [Zbieranie danych pamięci .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md)|  
|**Usługi profilowania**|-   [Zbieranie danych pamięci .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|  
  
### <a name="analyzing-net-memory-data-views-and-reports"></a>Analizowanie danych pamięci .NET widoków i raportów  
 [Widoki danych pamięci .NET](../profiling/dotnet-memory-data-views.md)  
  
## <a name="reference"></a>Tematy pomocy  
 [Wiersza polecenia narzędzi profilowania](../profiling/command-line-profiling-tools-reference.md)