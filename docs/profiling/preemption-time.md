---
title: "Czas wywłaszczania | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.cv.threads.timeline.preemption
helpviewer_keywords: Concurrency Visualizer, Preemption Time
ms.assetid: 6b78f91e-a006-440c-83fb-e7368040951d
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 447229fd3eeb0ded2b8d6ec56716c4ec95c36661
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="preemption-time"></a>Czas wywłaszczania
Te segmenty na osi czasu są skojarzone z blokowaniem czas, który jest skategoryzowany jako wywłaszczanie. Ta kategoria oznacza, że wątek przełączono się z powodu jednego z następujących powodów:  
  
-   Planista zastępuje go przy użyciu wyższy priorytet wątku.  
  
-   Ważność quantum wykonanie wątku i inne wątki były gotowe do wykonania.  
  
 W tym czasie wątek został zablokowany przez Przyczyna oczekiwania jądra, który Concurrency Visualizer jest liczy się jako wywłaszczanie. Wywłaszczanie segmentów Uruchom, gdy wątek spoczywa poza rdzenia logicznego, a zakończy się wątek wznawia wykonywanie.  
  
 Etykietka narzędzia dla segmentu preempted Wyświetla nazwę proces lub wątek, który spowodował wywłaszczanie. Jednak to oznacza, że proces lub wątek, który przejął faktycznie uruchomione przez cały okres preempted.  
  
## <a name="see-also"></a>Zobacz też  
 [Widok wątków](../profiling/threads-view-parallel-performance.md)