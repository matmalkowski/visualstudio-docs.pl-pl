---
title: Tworzenie Basic profilowania raportów z poziomu wiersza polecenia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 6d73e21e-c04e-48ea-91cc-e517a5f2cd3f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d6b076023f725ac037ae5863bc8955e6952285ac
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2018
ms.locfileid: "34764910"
---
# <a name="create-basic-profiling-reports-from-the-command-line"></a>Tworzenie podstawowych raportów dotyczących profilowania z wiersza polecenia
W tym artykule opisano podstawowe polecenia VSPerfReport, które generują plik wartości rozdzielanych przecinkami (. *CSV*) raporty z. *vsp* lub. *vsps* pliku danych profilowania. Opis wszystkich opcji raportów, zobacz [VSPerfReport](../profiling/vsperfreport.md).  
  
## <a name="report-commands"></a>Polecenia raportu  
 Użyj jednej z poniższych poleceń, aby utworzyć raport dla określonego pliku danych profilowania.  
  
 **VSPerfReport** `VSPFile` **/Summary:All**  
 Generuje dostępne dla wszystkich raportów. *vsp* lub. *vsps* pliku.  
  
 **VSPerfReport** `VSPFile` **/Summary:**`ReportType`[,`ReportType`...]  
 Generuje typu określonego raportu.  
  
 **VSPerfReport** `VSPFile`   **/calltrace**  
 Generuje raport zawierający listę każdego zdarzenia zbierania danych. Dotyczy to tylko instrumentacji.  
  
## <a name="summary-report-type-parameters"></a>Raport z podsumowaniem parametry typu  
 W poniższej tabeli opisano raportów, które są generowane przez opcję typu określonego raportu. Kolumny raportu są zależne od metodę profilowania, którego użyto do zbierania danych.  
  
|Parametr podsumowania|Opis raportu|Dokumentacja raportów|  
|-----------------------|------------------------|----------------------|  
|**CallerCallee**|Reprezentuje relacji nadrzędny/podrzędny między funkcji.|-   [Dane z próbkowania](../profiling/caller-callee-view-sampling-data.md)<br />-   [Dane z Instrumentacji](../profiling/caller-callee-view-instrumentation-data.md)<br />-   [Dane z próbkowania pamięci .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)<br />-   [Dane z Instrumentacji pamięci .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)<br />-   [Dane kontencji](../profiling/caller-callee-view-contention-data.md)|  
|**Function**|Wyświetla dane profilowania według funkcji.|-   [Dane z próbkowania](../profiling/functions-view-sampling-data.md)<br />-   [Dane z Instrumentacji](../profiling/functions-view-instrumentation-data.md)<br />-   [Dane z próbkowania pamięci .NET](../profiling/functions-view-dotnet-memory-sampling-data.md)<br />-   [Dane z Instrumentacji pamięci .NET](../profiling/functions-view-dotnet-memory-instrumentation-data.md)<br />-   [Dane kontencji](../profiling/functions-view-contention-data.md)|  
|**Widokach drzewa wywołań**|Reprezentuje ścieżek wykonywania i danych profilowania funkcji w przebiegu profilowania.|-   [Dane z Instrumentacji](../profiling/call-tree-view-instrumentation-data.md)<br />-   [Dane z próbkowania](../profiling/call-tree-view-sampling-data.md)<br />-   [Dane z próbkowania pamięci .NET](../profiling/call-tree-view-dotnet-memory-sampling-data.md)<br />-   [Dane z Instrumentacji pamięci .NET](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)<br />-   [Dane kontencji](../profiling/call-tree-view-contention-data.md)|  
|**Counter**|Wyświetla profilowania znaków i wartości licznika wydajności systemu Windows, które zostały zebrane podczas przebiegu profilowania.|-   [Widok znaczników](../profiling/marks-view.md)|  
|**IP**|Wyświetla dane profilowania według instrukcji.|-   [Dane z próbkowania](../profiling/instruction-pointers-ips-view-sampling-data.md)<br />-   [Dane z próbkowania pamięci .NET](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)<br />-   [Dane kontencji](../profiling/instruction-pointers-ips-view-contention-data.md)|  
|**Życia**|Wyświetla listę okres istnienia przydzielonych obiektów.|-   [Widok okresu istnienia obiektu](../profiling/object-lifetime-view.md)|  
|**wiersz**|Wyświetla dane profilowania według wiersza kodu źródłowego.|-   [Dane z próbkowania](../profiling/lines-view-sampling-data.md)<br />-   [Dane z próbkowania pamięci .NET](../profiling/lines-view-dotnet-memory-sampling-data.md)<br />-   [Dane kontencji](../profiling/lines-view-contention-data.md)|  
|**Nagłówek**|Profilowanie informacje nagłówka pliku danych.|Specyficzne dla pliku.|  
|**Mark**|Profilowanie znaczniki zebranych podczas przebiegu profilowania.|-   [Widok znaczników](../profiling/marks-view.md)|  
|**Module**|Wyświetla dane dla modułów profilowania.|-   [Dane z próbkowania](../profiling/modules-view-sampling-data.md)<br />-   [Dane z Instrumentacji](../profiling/modules-view-instrumentation-data.md)<br />-   [Dane z próbkowania pamięci .NET](../profiling/modules-view-dotnet-memory-sampling-data.md)<br />-   [Dane z Instrumentacji pamięci .NET](../profiling/modules-view-dotnet-memory-instrumentation-data.md)<br />-   [Dane kontencji](../profiling/modules-view-contention-data.md)|  
|**Proces**|Wyświetla dane dla procesów profilowania.|-   [Widok procesu](../profiling/process-view.md)<br />-   [Dane kontencji](../profiling/process-view-contention-data.md)|  
|**Wątek**|Wyświetla dane dla wątków profilowania.|-   [Widok procesu](../profiling/process-view.md)|  
|**Typ**|Wyświetla listę alokacji dane profilowania według typu.|-   [Widok alokacji](../profiling/dotnet-memory-allocations-view.md)|  
|**Rywalizacji**|Kontencji zasobów.|-   [Kontencji zasobów](../profiling/resource-contentions-view-contention-data.md)|  
|**RuleWarnings**|Wyświetla listę reguł problemy z wydajnością.|-Listy CheckId, opis i lokalizacji kodu źródłowego wydania reguły.|  
|**ETW**|Wyświetla zdarzenia funkcji Śledzenie zdarzeń systemu Windows () zebranych podczas przebiegu profilowania.|-   [Raportu ETW](../profiling/event-tracing-for-windows-etw-report.md)|