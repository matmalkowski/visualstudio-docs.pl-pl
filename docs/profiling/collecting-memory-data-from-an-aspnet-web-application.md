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
ms.openlocfilehash: 64dd2704891594b5d23eb4a536ee3ddf2ce9be98
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="collect-memory-data-from-an-aspnet-web-application-by-using-the-profiler-command-line"></a>Zbieranie danych pamięci z aplikacji sieci web ASP.NET przy użyciu wiersza polecenia profilera
W tej sekcji opisano procedury i opcji zbierania danych pamięci alokacji i obiekt okres istnienia dla aplikacji sieci Web ASP.NET przy użyciu **VSPerfCmd** narzędzia wiersza polecenia.  
  
> [!NOTE]
>  **VSPerfCmd** narzędzie zapewnia pełny dostęp do narzędzi profilowania funkcjonalność, co obejmuje wstrzymywanie i wznawianie profilowania i zbierania dodatkowych danych z procesora i liczników wydajności systemu Windows. Można również użyć **VSPerfASPNETCmd** narzędzia wiersza polecenia, gdy nie ma potrzeby tę funkcję. W porównaniu z [VSPerfCmd](../profiling/vsperfcmd.md) narzędzia wiersza polecenia, zmienne środowiskowe, nie trzeba ustawić i ponowne uruchomienie komputera nie jest wymagane. Aby uzyskać więcej informacji, zobacz [profilowania szybkie witryny sieci web za pomocą VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).  
  
## <a name="common-tasks"></a>Wspólne zadania
  
|Zadanie|Zawartość pokrewna|  
|----------|---------------------|  
|**Dołączanie profilera do uruchomionej aplikacji ASP.NET**|-   [Porady: dołączanie profilera do aplikacji sieci web ASP.NET w celu zbierania danych pamięci](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)|  
|**Instrument statycznie skompilowane pliki binarne**|-   [Porady: Instrumentacja statycznie skompilowanej aplikacji ASP.NET i zbieranie danych pamięci](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)|  
|**Instrument dynamicznie skompilowanych plików binarnych**|-   [Porady: Instrumentacja dynamicznie skompilowanej aplikacji ASP.NET i zbieranie danych pamięci](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data.md)|  
  
## <a name="related-tasks"></a>Zadania powiązane
  
### <a name="profile-aspnet-web-applications"></a>Aplikacje sieci web ASP.NET profilu  
  
|Zadanie|Zawartość pokrewna|  
|----------|---------------------|  
|**Profil przy użyciu metody pobierania próbek**|-   [Zbieranie statystyk aplikacji za pomocą próbkowania](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md)|  
|**Profil przy użyciu metody Instrumentacji**|-   [Zbieranie szczegółowych danych o chronometrażu przy użyciu Instrumentacji](../profiling/collecting-detailed-timing-data-aspnet-profiler-instrumentation-method.md)|  
|**Profil działania rywalizacji i wątku zasobów**|-   [Zbieranie danych współbieżności](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|  
  
### <a name="profile-net-framework-memory-data"></a>Profil danych pamięci .NET Framework  
  
|Zadanie|Zawartość pokrewna|  
|----------|---------------------|  
|**Profil aplikacji autonomicznej (klient)**|-   [Zbieranie danych pamięci .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md)|  
|**Usługi profilowania**|-   [Zbieranie danych pamięci .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|  
  
### <a name="analyze-net-memory-data-views-and-reports"></a>Analizowanie widoki danych pamięci .NET i raportów  
 [Widoki danych pamięci .NET](../profiling/dotnet-memory-data-views.md)  
  
## <a name="reference"></a>Tematy pomocy  
 [Narzędzia profilowania wiersza polecenia — dokumentacja](../profiling/command-line-profiling-tools-reference.md)