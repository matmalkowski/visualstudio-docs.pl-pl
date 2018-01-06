---
title: Rdzenie widok | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.performance.view.cores
helpviewer_keywords: Concurrency Visualizer, Cores View
ms.assetid: e47af672-9785-4899-bd45-4d9dda3c396f
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 6a2ce5cc9d80e7b96318d0e1fcf8aead09652b41
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="cores-view"></a>Widok rdzeni
Widok rdzeni zawiera odwzorowania wykonywanie wątków rdzeni procesora logicznego. Jeśli pisania aplikacji serwera, ten widok może pomóc zoptymalizować wydajność pamięci podręcznej za pomocą wątku koligacji lub wątku puli zarządzania. On też pomóc Ci Przejrzyj przypadki, w którym użycia koligacji wątku może mieć pogorszyła problem migracji różnych rdzeniach. Widok rdzeni ma dwie części, wykresu i legenda.  
  
 Wykres przedstawia rdzeni logicznych na osi y i godziny na osi x. Każdy wątek na wykresie jest unikatowy kolorów, dzięki czemu można śledzić jego ruchu na rdzeni w czasie. Wątki na tym wykresie można filtrować, wybierając w obszarze legendy.  
  
 Obszar legendy ma wpis dla każdego koloru na wykresie. Każdy wpis zawiera kolor wątku i nazwy, liczby przełączeń kontekstu różnych rdzeniach całkowitej liczby przełączeń kontekstu i procent przełączeń kontekstu przecinających rdzenie. Legenda jest sortowana według liczby przełączeń kontekstu różnych rdzeniach, w kolejności malejącej. Wyświetlane są tylko wątki wykonanych w czasie wyświetlane.  Lista jest aktualizowana, jeśli powiększanie i przesuwanie.  
  
## <a name="see-also"></a>Zobacz też  
 [CONCURRENCY Visualizer](../profiling/concurrency-visualizer.md)   
 [Widok wykorzystania](../profiling/utilization-view.md)   
 [Widok wątków](../profiling/threads-view-parallel-performance.md)