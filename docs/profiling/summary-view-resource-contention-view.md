---
title: Widok podsumowania — widok Kontencji zasobów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Summary view
ms.assetid: 6da57b83-7b42-4d7c-9aea-8e0a830faf6b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ed1db5bd560c32cdb40ddc728b3ede63c70dbc88
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="summary-view---resource-contention-view"></a>Widok podsumowania — widok Kontencji zasobów
Widok podsumowania przedstawia informacje o zdarzeniach w aplikacji, w którym wątku lub procesu zostało zawieszone, podczas gdy oczekiwano dostęp do zasobu.  
  
 Aby uzyskać więcej informacji, łącznie z opisem łącza powiadomień i listy raport, zobacz [widoku podsumowania](../profiling/summary-view.md).  
  
## <a name="timeline-graph"></a>Oś czasu wykresu  
 Oś czasu wykresu w widoku podsumowania pokazuje liczbę zdarzenia rywalizacji PROFILOWANEGO aplikacji wraz z upływem czasu, który wystąpił profilowania. Oś czasu wykresu umożliwia filtrowanie widoku w wybranym okresie. Aby uzyskać więcej informacji, zobacz [porady: Filtr widoków raportu z podsumowania osi czasu](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).  
  
## <a name="most-contended-resources"></a>Większość utrzymywał zasobów  
 **Najwięcej zasobów utrzymywał** zawiera listę zasobów w aplikacji, który spowodował najbardziej zdarzenia rywalizacji. Kliknięcie nazwy zasobu, aby wyświetlić rywalizacji. Widok Kontencji zawiera szczegółowe osi czasu z kontencji zasobów przez wątek.  
  
 **Najwięcej zasobów utrzymywał** obejmuje następujące dane dla każdego zasobu.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Nazwa**|Nazwa zasobu.|  
|**% Rywalizacji**|Procent wszystkich zdarzenia rywalizacji danych profilowania, które zostały rywalizacji za pośrednictwem tego zasobu.|  
  
## <a name="most-contended-thread"></a>Najbardziej utrzymywał wątku  
 **Większość wątków utrzymywał** wymieniono wątków w aplikacji, która ma największy numer zdarzenia rywalizacji. Kliknięcie Nazwa wątku, aby wyświetlić rywalizacji zapewnia szczegółowe osi czasu z kontencji zasobów przez wątek.  
  
 **Większość wątków utrzymywał** obejmuje następujące dane dla każdego wątku.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**ID**|Identyfikator wątku.|  
|**Nazwa**|Nazwa procesu, który jest właścicielem wątku.|  
|**% Rywalizacji**|Procent wszystkich zdarzenia rywalizacji danych profilowania, które zostały rywalizacji za pośrednictwem tego zasobu.|