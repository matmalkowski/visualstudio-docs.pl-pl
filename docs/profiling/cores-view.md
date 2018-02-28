---
title: Rdzenie widok | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performance.view.cores
helpviewer_keywords:
- Concurrency Visualizer, Cores View
ms.assetid: e47af672-9785-4899-bd45-4d9dda3c396f
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 1867f2b0ba84590068b1ae54b0a7aa1d48475247
ms.sourcegitcommit: 342e5ec5cec4d07864d65379c2add5cec247f3d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2018
---
# <a name="cores-view"></a>Widok rdzeni
**Widok rdzeni** zawiera odwzorowania wykonywanie wątków rdzeni procesora logicznego (wybierz **Analizuj** > **Concurrency Visualizer** można uruchomić CONCURRENCY visualizer). Jeśli pisania aplikacji serwera, ten widok może pomóc zoptymalizować wydajność pamięci podręcznej za pomocą wątku koligacji lub wątku puli zarządzania. On też pomóc Ci Przejrzyj przypadki, w którym użycia koligacji wątku może mieć pogorszyła problem migracji różnych rdzeniach. Widok rdzeni ma dwie części, wykresu i legenda.  
  
 Wykres przedstawia rdzeni logicznych na osi y i godziny na osi x. Każdy wątek na wykresie jest unikatowy kolorów, dzięki czemu można śledzić jego ruchu na rdzeni w czasie. Wątki na tym wykresie można filtrować, wybierając w obszarze legendy.  
  
 Obszar legendy ma wpis dla każdego koloru na wykresie. Każdy wpis zawiera kolor wątku i nazwy, liczby przełączeń kontekstu różnych rdzeniach całkowitej liczby przełączeń kontekstu i procent przełączeń kontekstu przecinających rdzenie. Legenda jest sortowana według liczby przełączeń kontekstu różnych rdzeniach, w kolejności malejącej. Wyświetlane są tylko wątki wykonanych w czasie wyświetlane.  Lista jest aktualizowana, jeśli powiększanie i przesuwanie.  
  
## <a name="see-also"></a>Zobacz też  
 [CONCURRENCY Visualizer](../profiling/concurrency-visualizer.md)   
 [Widok wykorzystania](../profiling/utilization-view.md)   
 [Widok wątków](../profiling/threads-view-parallel-performance.md)