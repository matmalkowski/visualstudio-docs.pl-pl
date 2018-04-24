---
title: Czas synchronizacji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.synchronization
helpviewer_keywords:
- Concurrency Visualizer, Synchronization Time
ms.assetid: affa04cc-8bba-4848-9301-b19846d3c2cb
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4b968ead26d632c70f0b1adc8864600769629a90
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="synchronization-time"></a>Czas synchronizacji
Te segmenty na osi czasu są skojarzone z blokuje razy, które są sklasyfikowane jako synchronizacji. Gdy wątek jest oznaczona jako zablokowane na synchronizacji, jest domniemane jedną z tych czynności:  
  
-   Wykonanie wątku może spowodowały wywołania synchronizacji wątku dobrze znanego interfejsu API takich jak `EnterCriticalSection()` lub `WaitForSingleObject()`.  
  
-   Algorytm dopasowania interfejsu API nie może być całkowicie kompleksowe i w związku z tym niektórych interfejsów API, które mogą zostać zamapowane do innych kategorii może również zostać wyświetlony jako synchronizacji, ponieważ ramka w wywołaniu stosu ostatecznie osiągnięty podstawowej jądra blokuje pierwotnych, która została mapowany do tej kategorii.  
  
 Aby zrozumieć podstawową przyczyną zdarzenie blokowania wątku, sprawdzić blokowania stosy wywołań i profilu, raportów.  
  
## <a name="see-also"></a>Zobacz też  
 [Widok wątków](../profiling/threads-view-parallel-performance.md)