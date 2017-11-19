---
title: "Tworzenie Basic profilowania raportów z poziomu wiersza polecenia | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6d73e21e-c04e-48ea-91cc-e517a5f2cd3f
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 111227b41b3fe48af963f93f07cdee5e5511661f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="creating-basic-profiling-reports-from-the-command-line"></a>Tworzenie podstawowych raportów dotyczących profilowania z wiersza polecenia
W tym temacie opisano podstawowe polecenia VSPerfReport generujących raporty wartości oddzielanych przecinkami (.csv) z pliku Vsp lub vsps pliku danych profilowania. Opis wszystkich opcji raportów, zobacz [VSPerfReport](../profiling/vsperfreport.md).  
  
## <a name="report-commands"></a>Polecenia raportu  
 Użyj jednej z poniższych poleceń, aby utworzyć raport dla określonego pliku danych profilowania.  
  
 **VSPerfReport** `VSPFile` **/Summary:All**  
 Generuje raporty wszystkie dostępne dla pliku Vsp lub vsps.  
  
 **VSPerfReport** `VSPFile` **/Summary:**`ReportType`[,`ReportType`...]  
 Generuje typu określonego raportu.  
  
 **VSPerfReport** `VSPFile`   **/calltrace**  
 Generuje raport zawierający listę każdego zdarzenia zbierania danych. Dotyczy to tylko instrumentacji.  
  
## <a name="summary-report-type-parameters"></a>Raport z podsumowaniem parametry typu  
 W poniższej tabeli opisano raportów, które są generowane przez opcję typu określonego raportu. Kolumny raportu są zależne od metodę profilowania, którego użyto do zbierania danych.  
  
|Parametr podsumowania|Opis raportu|Dokumentacja raportów|  
|-----------------------|------------------------|----------------------|  
|**CallerCallee**|Reprezentuje relacji nadrzędny/podrzędny między funkcji.|-   [Dane z próbkowania](../profiling/caller-callee-view-sampling-data.md)<br />-   [Dane z Instrumentacji](../profiling/caller-callee-view-instrumentation-data.md)<br />-   [Dane z próbkowania pamięci .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)<br />-   [Dane z Instrumentacji pamięci .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)<br />-   [Dane kontencji](../profiling/caller-callee-view-contention-data.md)|  
|**Funkcja**|Wyświetla dane profilowania według funkcji.|-   [Dane z próbkowania](../profiling/functions-view-sampling-data.md)<br />-   [Dane z Instrumentacji](../profiling/functions-view-instrumentation-data.md)<br />-   [Dane z próbkowania pamięci .NET](../profiling/functions-view-dotnet-memory-sampling-data.md)<br />-   [Dane z Instrumentacji pamięci .NET](../profiling/functions-view-dotnet-memory-instrumentation-data.md)<br />-   [Dane kontencji](../profiling/functions-view-contention-data.md)|  
|**Widokach drzewa wywołań**|Reprezentuje ścieżek wykonywania i danych profilowania funkcji w przebiegu profilowania.|-   [Dane z Instrumentacji](../profiling/call-tree-view-instrumentation-data.md)<br />-   [Dane z próbkowania](../profiling/call-tree-view-sampling-data.md)<br />-   [Dane z próbkowania pamięci .NET](../profiling/call-tree-view-dotnet-memory-sampling-data.md)<br />-   [Dane z Instrumentacji pamięci .NET](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)<br />-   [Dane kontencji](../profiling/call-tree-view-contention-data.md)|  
|**Licznik**|Wyświetla profilowania znaków i wartości licznika wydajności systemu Windows, które zostały zebrane podczas przebiegu profilowania.|-   [Widok znaczników](../profiling/marks-view.md)|  
|**IP**|Wyświetla dane profilowania według instrukcji.|-   [Dane z próbkowania](../profiling/instruction-pointers-ips-view-sampling-data.md)<br />-   [Dane z próbkowania pamięci .NET](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)<br />-   [Dane kontencji](../profiling/instruction-pointers-ips-view-contention-data.md)|  
|**Życia**|Wyświetla listę okres istnienia przydzielonych obiektów.|-   [Widok okresu istnienia obiektu](../profiling/object-lifetime-view.md)|  
|**Wiersz**|Wyświetla dane profilowania według wiersza kodu źródłowego.|-   [Dane z próbkowania](../profiling/lines-view-sampling-data.md)<br />-   [Dane z próbkowania pamięci .NET](../profiling/lines-view-dotnet-memory-sampling-data.md)<br />-   [Dane kontencji](../profiling/lines-view-contention-data.md)|  
|**Nagłówek**|Profilowanie informacje nagłówka pliku danych.|Specyficzne dla pliku.|  
|**Znak**|Profilowanie znaczniki zebranych podczas przebiegu profilowania.|-   [Widok znaczników](../profiling/marks-view.md)|  
|**Moduł**|Wyświetla dane dla modułów profilowania.|-   [Dane z próbkowania](../profiling/modules-view-sampling-data.md)<br />-   [Dane z Instrumentacji](../profiling/modules-view-instrumentation-data.md)<br />-   [Dane z próbkowania pamięci .NET](../profiling/modules-view-dotnet-memory-sampling-data.md)<br />-   [Dane z Instrumentacji pamięci .NET](../profiling/modules-view-dotnet-memory-instrumentation-data.md)<br />-   [Dane kontencji](../profiling/modules-view-contention-data.md)|  
|**Proces**|Wyświetla dane dla procesów profilowania.|-   [Widok procesu](../profiling/process-view.md)<br />-   [Dane kontencji](../profiling/process-view-contention-data.md)|  
|**Wątek**|Wyświetla dane dla wątków profilowania.|-   [Widok procesu](../profiling/process-view.md)|  
|**Typ**|Wyświetla listę alokacji dane profilowania według typu.|-   [Widok alokacji](../profiling/dotnet-memory-allocations-view.md)|  
|**Rywalizacji**|Kontencji zasobów.|-   [Kontencji zasobów](../profiling/resource-contentions-view-contention-data.md)|  
|**RuleWarnings**|Wyświetla listę reguł problemy z wydajnością.|-Listy CheckId, opis i lokalizacji kodu źródłowego wydania reguły.|  
|**ETW**|Wyświetla zdarzenia funkcji Śledzenie zdarzeń systemu Windows () zebranych podczas przebiegu profilowania.|-   [Raportu ETW](../profiling/event-tracing-for-windows-etw-report.md)|