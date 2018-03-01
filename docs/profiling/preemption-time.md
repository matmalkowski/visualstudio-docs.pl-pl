---
title: "Czas wywłaszczania | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.cv.threads.timeline.preemption
helpviewer_keywords:
- Concurrency Visualizer, Preemption Time
ms.assetid: 6b78f91e-a006-440c-83fb-e7368040951d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 0ee0f1be5d687c145bc2c8af448b30ec364df2f7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="preemption-time"></a>Czas wywłaszczania
Te segmenty na osi czasu są skojarzone z blokowaniem czas, który jest skategoryzowany jako wywłaszczanie. Ta kategoria oznacza, że wątek przełączono się z powodu jednego z następujących powodów:  
  
-   Planista zastępuje go przy użyciu wyższy priorytet wątku.  
  
-   Ważność quantum wykonanie wątku i inne wątki były gotowe do wykonania.  
  
 W tym czasie wątek został zablokowany przez Przyczyna oczekiwania jądra, który Concurrency Visualizer jest liczy się jako wywłaszczanie. Wywłaszczanie segmentów Uruchom, gdy wątek spoczywa poza rdzenia logicznego, a zakończy się wątek wznawia wykonywanie.  
  
 Etykietka narzędzia dla segmentu preempted Wyświetla nazwę proces lub wątek, który spowodował wywłaszczanie. Jednak to oznacza, że proces lub wątek, który przejął faktycznie uruchomione przez cały okres preempted.  
  
## <a name="see-also"></a>Zobacz też  
 [Widok wątków](../profiling/threads-view-parallel-performance.md)