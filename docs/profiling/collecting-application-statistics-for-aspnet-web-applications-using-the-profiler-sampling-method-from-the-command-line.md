---
title: Zbieranie statystyk dla platformy ASP.NET sieci web apps | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, sampling method
- sampling profling method
ms.assetid: f8383ab1-eb49-4d3f-8608-d8b4d51a81be
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: ea70f8f665196aff94c04796204881a0e16b261c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="collect-statistics-for-aspnet-web-apps"></a>Zbieranie statystyk aplikacji sieci web ASP.NET

W tej sekcji opisano procedury i zbieranie statystyk wydajności dla aplikacji sieci Web ASP.NET przy użyciu opcji **VSPerfASPNETCmd** i **VSPerfCmd** narzędzia wiersza polecenia i Metoda profilowania próbkowania.  
  
> [!NOTE]
>  Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagane znaczących zmian w sposobie profilera Visual Studio zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows wymagają również nowe techniki kolekcji. Zobacz [narzędzi wydajności w przypadku aplikacji systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
> [!NOTE]
>  Mimo że **VSPerfCmd** narzędzie zapewnia pełny dostęp do narzędzi profilowania funkcjonalność, co obejmuje wstrzymywanie i wznawianie profilowania, i zbieranie dodatkowych danych z procesora i liczników wydajności systemu Windows, należy używać **VSPerfASPNETCmd** narzędzia wiersza polecenia, gdy nie ma potrzeby tę funkcję. **VSPerfASPNETCmd** narzędzia wiersza polecenia jest to preferowana metoda gdy jesteś profilowanie witryny sieci Web ASP.NET przy użyciu autonomiczny profilera. W porównaniu z [VSPerfCmd](../profiling/vsperfcmd.md) narzędzia wiersza polecenia, zmienne środowiskowe, nie trzeba ustawić i ponowne uruchomienie komputera nie jest wymagane. Aby uzyskać więcej informacji, zobacz [szybkie profilowanie witryny sieci Web za pomocą VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).  
  
## <a name="common-tasks"></a>Typowe zadania  
  
|Zadanie|Zawartość pokrewna|  
|----------|---------------------|  
|**Dołączanie profilera do aplikacji ASP.NET**|-   [Porady: dołączanie profilera do aplikacji sieci Web ASP.NET w celu zbierania statystyk aplikacji](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line.md)|  
  
## <a name="related-tasks"></a>Tematy pokrewne  
  
### <a name="profiling-aspnet-web-applications"></a>Profilowanie aplikacji sieci Web ASP.NET  
  
|Zadanie|Zawartość pokrewna|  
|----------|---------------------|  
|**Profil przy użyciu metody Instrumentacji**|-   [Zbieranie szczegółowych danych o chronometrażu przy użyciu Instrumentacji](../profiling/collecting-detailed-timing-data-for-an-aspnet-web-application-using-the-profiler-instrumentation-method.md)|  
|**Profil pamięci alokacji i odzyskiwanie pamięci**|-   [Zbieranie danych pamięci](../profiling/collecting-memory-data-from-an-aspnet-web-application-by-using-the-profiler-command-line.md)|  
|**Profil działania rywalizacji i wątku zasobów**|-   [Zbieranie danych współbieżności](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
  
### <a name="sampling-method"></a>Metoda pobierania próbek  
  
|Zadanie|Zawartość pokrewna|  
|----------|---------------------|  
|**Profil aplikacji autonomicznej (klient)**|-   [Zbieranie statystyk aplikacji za pomocą próbkowania](../profiling/collecting-application-statistics-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|-   **Usługi profilowania**|-   [Zbieranie statystyk aplikacji za pomocą próbkowania](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)|  
  
### <a name="analyzing-sampling-data-views-and-reports"></a>Analizowanie danych próbkowania widoków i raportów  
 [Widok danych metody próbkowania](../profiling/profiler-sampling-method-data-views.md)