---
title: Czas wywłaszczania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.preemption
helpviewer_keywords:
- Concurrency Visualizer, Preemption Time
ms.assetid: 6b78f91e-a006-440c-83fb-e7368040951d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7ac7152ec663a0a7b7bbbeee5c30a38885623cb9
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2018
ms.locfileid: "35254762"
---
# <a name="preemption-time"></a>Czas wywłaszczania
Te segmenty na osi czasu są skojarzone z blokowaniem czas, który jest skategoryzowany jako poboru. Ta kategoria oznacza, że wątek przełączono się z powodu jednego z następujących powodów:  
  
-   Planista zastępuje go przy użyciu wyższy priorytet wątku.  
  
-   Ważność quantum wykonanie wątku i inne wątki były gotowe do wykonania.  
  
 W tym czasie wątek został zablokowany przez Przyczyna oczekiwania jądra, który Concurrency Visualizer jest liczy się jako poboru. Segmenty poboru Uruchom, gdy wątek spoczywa poza rdzenia logicznego, a zakończy się wątek wznawia wykonywanie.  
  
 Etykietka narzędzia dla segmentu opóźnieniem Wyświetla nazwę proces lub wątek, który spowodował poboru. Jednak to oznacza, że proces lub wątek, który przejął faktycznie uruchomione przez cały okres preempted.  
  
## <a name="see-also"></a>Zobacz także  
 [Widok wątków](../profiling/threads-view-parallel-performance.md)