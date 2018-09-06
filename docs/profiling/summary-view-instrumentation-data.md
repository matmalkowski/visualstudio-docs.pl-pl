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
ms.openlocfilehash: 606ba5ebe7c485adb33fbcfa6884ad5e625d821e
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "35677057"
---
# <a name="summary-view---instrumentation-data"></a>Widok podsumowania - dane Instrumentacji
Widok podsumowania Wyświetla informacje na temat wydajności najdroższych funkcji w przebiegu profilowania. Aby uzyskać więcej informacji, łącznie z opisem powiadomienie łącza i listy raportów, zobacz [widok podsumowania](../profiling/summary-view.md).  
  
## <a name="timeline-graph"></a>Wykres osi czasu  
 Wykres osi czasu w widoku podsumowania przedstawia użycie procesora (CPU) według profilowanej aplikacji wraz z upływem czasu, który wystąpił profilowania. Wykres osi czasu można użyć do filtrowania widoku, aby w wybranym okresie. Aby uzyskać więcej informacji, zobacz [porady: filtrowanie widoków raportu z podsumowania osi czasu](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).  
  
## <a name="hot-path"></a>Ścieżka aktywna  
 **Ścieżka aktywna** Wyświetla ścieżka wykonania, która używane najwięcej czasu. Możesz kliknąć funkcję, aby wyświetlić widok szczegółów funkcji dla tej funkcji. Aby wyświetlić inne widoki dotyczące funkcji kliknij prawym przyciskiem myszy funkcję, a następnie kliknij widok z listy.  
  
 **Ścieżka aktywna** zawiera następujące dane dotyczące każdej funkcji:  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Nazwa**|Nazwa funkcji.|  
|**% Całkowitego czasu, który upłynął**|Procent cały czas w danych profilowania, która funkcja poświęcony na wykonywanie kodu, w jego treści funkcji i funkcji, które je wywołuje.|  
|**% Wyłącznego czasu, który upłynął**|Procent cały czas w danych profilowania, że funkcja poświęcony na wykonywanie kodu w jego treści funkcji. Czas w funkcje, które wywołały funkcję nie jest włączony.|  
  
## <a name="functions-with-most-individual-work"></a>Funkcje z największą ilością indywidualnej pracy  
 Lista funkcji, które używane większość czasu wykonywania kodu w treści funkcji, a nie w funkcje, które go wywołały.  
  
 **Funkcje z najbardziej samodzielnej pracy** zawiera następujące dane dotyczące każdej funkcji:  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Nazwa**|Nazwa funkcji.|  
|**% Własnego czasu**|Procent cały czas w danych profilowania, że funkcja poświęcony na wykonywanie kodu w jego treści funkcji. Czas w funkcje, które wywołały funkcję nie jest włączony.|  
  
## <a name="see-also"></a>Zobacz także  
 [Widok podsumowania — dane próbkowania](../profiling/summary-view-sampling-data.md)   
 [Widok podsumowania - dane pamięci platformy .NET](../profiling/summary-view-dotnet-memory-data.md)