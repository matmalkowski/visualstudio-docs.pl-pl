---
title: "Widok podsumowania - dane pamięci platformy .NET | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Summary view
ms.assetid: 0cb317c3-0ae6-4531-aaa8-447576eec037
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 968d46c4fe771229647282c719815982d81bf416
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="summary-view---net-memory-data"></a>Widok podsumowania - dane pamięci .NET
Widok podsumowania Wyświetla informacje o funkcji .NET i typy, które przydzielone najwięcej pamięci i typy, które zostały utworzone na większości czas przebiegu profilowania. Aby uzyskać więcej informacji, łącznie z opisem łącza powiadomień i listy raport, zobacz [widoku podsumowania](../profiling/summary-view.md).  
  
## <a name="timeline-graph"></a>Oś czasu wykresu  
 Oś czasu wykresu w widoku Podsumowanie zawiera użycie procesora (CPU) przez aplikację PROFILOWANEGO wraz z upływem czasu, który wystąpił profilowania. Oś czasu wykresu umożliwia filtrowanie widoku w wybranym okresie. Aby uzyskać więcej informacji, zobacz [porady: Filtr widoków raportu z podsumowania osi czasu](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).  
  
## <a name="functions-allocating-most-memory"></a>Funkcje przydzielające najwięcej pamięci  
 Zawiera listę funkcji, które przydzielone największą liczbę bajtów pamięci w przebiegu profilowania.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Nazwa**|Nazwa funkcji.|  
|**% Bajtów**|Procent wszystkich przydzielonych bajtów w przebiegu profilowania przydzielone przez tej funkcji lub funkcji podrzędnej, która została wywołana przez tę funkcję.|  
  
## <a name="types-with-most-memory-allocated"></a>Typy z największą ilością przydzielonej pamięci  
 Wyświetla listę typów, dla których największą liczbę bajtów pamięci przydzielone w przebiegu profilowania.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Nazwa**|Nazwa typu.|  
|**% Bajtów**|Procent wszystkich przydzielonych bajtów w przebiegu profilowania, które zostały przyznane dla tego typu.|  
  
## <a name="types-with-most-instances"></a>Typy z największą liczbą wystąpień  
 Wyświetla listę typów, które zostały utworzone najbardziej razy podczas przebiegu profilowania. Gdyby  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Nazwa**|Nazwa typu.|  
|**% Wystąpień**|Wartość procentowa łączna liczba obiektów of.NET utworzonych w przebiegu, który profilowania były wystąpień tego typu.|  
  
## <a name="see-also"></a>Zobacz też  
 [Widok podsumowania](../profiling/summary-view-sampling-data.md)   
 [Widok podsumowania](../profiling/summary-view-instrumentation-data.md)