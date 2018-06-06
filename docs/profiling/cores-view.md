---
title: Rdzenie widok | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.cores
helpviewer_keywords:
- Concurrency Visualizer, Cores View
ms.assetid: e47af672-9785-4899-bd45-4d9dda3c396f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: beec52fe827162720c7c5040f91655d7db02c7e7
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34750220"
---
# <a name="cores-view"></a>Widok rdzeni
**Widok rdzeni** zawiera odwzorowania wykonywanie wątków rdzeni procesora logicznego (wybierz **Analizuj**>**Concurrency Visualizer** można uruchomić CONCURRENCY visualizer). Jeśli pisania aplikacji serwera, ten widok może pomóc zoptymalizować wydajność pamięci podręcznej za pomocą wątku koligacji lub wątku puli zarządzania. On też pomóc Ci Przejrzyj przypadki, w którym użycia koligacji wątku może mieć pogorszyła problem migracji różnych rdzeniach. Widok rdzeni ma dwie części, wykresu i legenda.  
  
 Wykres przedstawia rdzeni logicznych na osi y i godziny na osi x. Każdy wątek na wykresie jest unikatowy kolorów, dzięki czemu można śledzić jego ruchu na rdzeni w czasie. Wątki na tym wykresie można filtrować, wybierając w obszarze legendy.  
  
 Obszar legendy ma wpis dla każdego koloru na wykresie. Każdy wpis zawiera kolor wątku i nazwy, liczby przełączeń kontekstu różnych rdzeniach całkowitej liczby przełączeń kontekstu i procent przełączeń kontekstu przecinających rdzenie. Legenda jest sortowana według liczby przełączeń kontekstu różnych rdzeniach, w kolejności malejącej. Wyświetlane są tylko wątki wykonanych w czasie wyświetlane.  Lista jest aktualizowana, jeśli powiększanie i przesuwanie.  
  
## <a name="see-also"></a>Zobacz także  
 [CONCURRENCY Visualizer](../profiling/concurrency-visualizer.md)   
 [Widok wykorzystania](../profiling/utilization-view.md)   
 [Widok wątków](../profiling/threads-view-parallel-performance.md)