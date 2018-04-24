---
title: Zbieranie szczegółowych danych o chronometrażu dla aplikacji sieci Web ASP.NET przy użyciu metody Instrumentacji profilera z wiersza polecenia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools,instrumentation method
- instrumentation profiling method
ms.assetid: 29f2fc55-aaf7-4e18-a672-8815455fba73
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 3665046320b644ebd9689e14c18cc68b79c95347
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="collecting-detailed-timing-data-for-an-aspnet-web-application-using-the-profiler-instrumentation-method-from-the-command-line"></a>Zbieranie szczegółowych danych o chronometrażu dla aplikacji sieciowej ASP.NET przy użyciu Metody instrumentacji profilera z wiersza polecenia
W tej sekcji opisano procedury i opcji zbierania wydajności szczegółowe dane dla [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci Web przy użyciu **VSPerfCmd** narzędzia wiersza polecenia i metody instrumentacji.  
  
> [!NOTE]
>  **VSPerfCmd** narzędzie zapewnia pełny dostęp do narzędzi profilowania funkcjonalność, co obejmuje wstrzymywanie i wznawianie profilowania i zbierania dodatkowych danych z procesora i liczników wydajności systemu Windows. Można również użyć **VSPerfASPNETCmd** narzędzia wiersza polecenia, gdy nie ma potrzeby tę funkcję. W porównaniu z [VSPerfCmd](../profiling/vsperfcmd.md) narzędzie wiersza polecenia, zmienne środowiskowe, nie muszą być ustawione i ponowne uruchomienie komputera nie jest wymagane. Aby uzyskać więcej informacji, zobacz [szybkie profilowanie witryny sieci Web za pomocą VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).  
  
## <a name="common-tasks"></a>Typowe zadania  
  
|Zadanie|Zawartość pokrewna|  
|----------|---------------------|  
|**Profil statycznie skompilowane pliki binarne**|-   [Porady: Instrumentacja statycznie skompilowanej ASP.NET aplikacji i zbieranie szczegółowych danych o chronometrażu](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line.md)|  
|**Profilowania dynamicznie skompilowanych plików binarnych**|-   [Porady: Instrumentacja dynamicznie skompilowanej ASP.NET aplikacji i zbieranie szczegółowych danych o chronometrażu](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler.md)|  
  
## <a name="related-tasks"></a>Tematy pokrewne  
  
### <a name="profiling-aspnet-web-applications"></a>Profilowanie aplikacji sieci Web ASP.NET  
  
|Zadanie|Zawartość pokrewna|  
|----------|---------------------|  
|**Profil przy użyciu metody pobierania próbek**|-   [Zbieranie statystyk aplikacji za pomocą próbkowania](../profiling/collecting-application-statistics-for-aspnet-web-applications-using-the-profiler-sampling-method-from-the-command-line.md)|  
|**Profil pamięci alokacji i odzyskiwanie pamięci**|-   [Zbieranie danych pamięci](../profiling/collecting-memory-data-from-an-aspnet-web-application-by-using-the-profiler-command-line.md)|  
|**Profil działania rywalizacji i wątku zasobów**|-   [Zbieranie danych współbieżności](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
  
### <a name="profiling-by-using-the-instrumentation-method"></a>Profilowanie przy użyciu metody Instrumentacji  
  
|Zadanie|Zawartość pokrewna|  
|----------|---------------------|  
|**Profil aplikacji autonomicznej (klient)**|-   [Zbieranie szczegółowych danych o chronometrażu przy użyciu Instrumentacji](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application-by-using-the-profiler-command-line.md)|  
|**Usługi profilowania**|-   [Zbieranie szczegółowych danych o chronometrażu przy użyciu Instrumentacji](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method-from-the-profiler-command-line.md)|  
  
### <a name="analyzing-instrumentation-data-views-and-reports"></a>Analizowanie danych Instrumentacji widoków i raportów  
 [Widoki danych metody instrumentacji](../profiling/instrumentation-method-data-views.md)