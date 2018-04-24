---
title: Widok podsumowania - dane Instrumentacji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Summary view
ms.assetid: 0a3b3a1f-e22b-4ac8-b46e-71694e9b2cf1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0a62c7dc2d8f0e0e80b3cfd8ba74b968ebd2e116
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="summary-view---instrumentation-data"></a>Widok podsumowania - dane Instrumentacji
Widok podsumowania Wyświetla informacje o wydajności najdroższych funkcje w przebiegu profilowania. Aby uzyskać więcej informacji, łącznie z opisem łącza powiadomień i listy raport, zobacz [widoku podsumowania](../profiling/summary-view.md).  
  
## <a name="timeline-graph"></a>Oś czasu wykresu  
 Oś czasu wykresu w widoku Podsumowanie zawiera użycie procesora (CPU) przez aplikację PROFILOWANEGO wraz z upływem czasu, który wystąpił profilowania. Oś czasu wykresu umożliwia filtrowanie widoku w wybranym okresie. Aby uzyskać więcej informacji, zobacz [porady: Filtr widoków raportu z podsumowania osi czasu](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).  
  
## <a name="hot-path"></a>Aktywnej ścieżki  
 **Aktywnej ścieżki** jest wyświetlana ścieżka wykonywania zużytej najwięcej czasu. Możesz kliknąć funkcji, aby wyświetlić widok szczegółów funkcji dla funkcji. Wyświetlanie innych widoków dla funkcji prawym przyciskiem myszy funkcji, a następnie kliknij przycisk Widok z listy.  
  
 **Aktywnej ścieżki** obejmuje następujące dane dla każdej funkcji:  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Nazwa**|Nazwa funkcji.|  
|**% Całkowity czas, który upłynął**|Procent czasu wszystkich funkcji poświęcony na wykonywanie kodu w jego treści funkcji i funkcji, które mu danych profilowania.|  
|**% Wyłącznego czas, który upłynął**|Procent wszystkich czasu w danych profilowania, że funkcja poświęcony na wykonywanie kodu w jego treści funkcji. Czas spędzony w funkcje, które funkcja wywoływana nie jest włączony.|  
  
## <a name="functions-with-most-individual-work"></a>Funkcje z największą ilością indywidualnej pracy  
 Lista funkcji, które używane większość czasu wykonywania kodu w treści funkcji, a nie w funkcje, które mu.  
  
 **Funkcje z najbardziej indywidualnej pracy** obejmuje następujące dane dla każdej funkcji:  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Nazwa**|Nazwa funkcji.|  
|**% Własny czas**|Procent wszystkich czasu w danych profilowania, że funkcja poświęcony na wykonywanie kodu w jego treści funkcji. Czas spędzony w funkcje, które funkcja wywoływana nie jest włączony.|  
  
## <a name="see-also"></a>Zobacz też  
 [Widok podsumowania](../profiling/summary-view-sampling-data.md)   
 [Widok podsumowania](../profiling/summary-view-dotnet-memory-data.md)