---
title: Wykres wykorzystania CPU | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.cpu.graph
helpviewer_keywords:
- CPU Utilization GraphConcurrency Visualizer, CPU Utilization Graph
ms.assetid: 5332fd38-622d-47a3-874f-8c2fd7a30f95
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 22bbe4e49eeb05b17ae7140ec4900895bce9874e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="cpu-utilization-graph"></a>Wykres wykorzystania CPU
Wykres wykorzystania CPU pokazuje poziom użycia w aplikacji w czasie. Osi x reprezentuje czas trwania śledzenia, a oś y — liczba rdzeni logicznych w systemie. Wykres nie pokazuje, które określonym rdzeniu jest aktywny w danym momencie. Na przykład jeśli każdy dwa rdzenie są uruchamiane o pojemności 50 procent w określonym czasie, ten widok przedstawia jednego rdzenia logicznego jej użycia.  
  
## <a name="cpu-utilization-graph-colors"></a>Kolory Wykres wykorzystania CPU  
  
-   Zielony oznacza użycie przez rdzenie logiczne w systemie przez bieżącego procesu.  
  
-   Szary światła wskazuje wykorzystania rdzeni logicznych przez inne procesy w systemie. Wysoki procent światła szarości na wykresie Procesora wskazuje, że system obciążonego przez inne procesy, i proces może być opóźnieniem przez nich. Aby zmniejszyć zużycie rdzeni logicznych przez inne procesy, należy zmniejszyć liczbę ich działa w systemie.  
  
-   Ciemny zwykle wskazuje użycia rdzeni logicznych przez proces systemowy. Nie można bezpośrednio kontrolować to, ale warto wiedzieć, kiedy jest wykonywana, ponieważ może wpłynąć na dostępność rdzeni logicznych procesu.  
  
-   Białe wskazuje dostępność nieużywane rdzenie logiczne w systemie. Rdzenie te są dostępne dla procesu, jeśli można znaleźć więcej możliwości równoległości.  
  
## <a name="see-also"></a>Zobacz też  
 [Widok wykorzystania](../profiling/utilization-view.md)   
 [Średnie wykorzystanie procesora CPU](../profiling/average-cpu-utilization.md)