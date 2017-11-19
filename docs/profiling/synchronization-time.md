---
title: Czas synchronizacji | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.cv.threads.timeline.synchronization
helpviewer_keywords: Concurrency Visualizer, Synchronization Time
ms.assetid: affa04cc-8bba-4848-9301-b19846d3c2cb
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c6f792e58a2c98219d15e889846921f537d74140
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="synchronization-time"></a>Czas synchronizacji
Te segmenty na osi czasu są skojarzone z blokuje razy, które są sklasyfikowane jako synchronizacji. Gdy wątek jest oznaczona jako zablokowane na synchronizacji, jest domniemane jedną z tych czynności:  
  
-   Wykonanie wątku może spowodowały wywołania synchronizacji wątku dobrze znanego interfejsu API takich jak `EnterCriticalSection()` lub `WaitForSingleObject()`.  
  
-   Algorytm dopasowania interfejsu API nie może być całkowicie kompleksowe i w związku z tym niektórych interfejsów API, które mogą zostać zamapowane do innych kategorii może również zostać wyświetlony jako synchronizacji, ponieważ ramka w wywołaniu stosu ostatecznie osiągnięty podstawowej jądra blokuje pierwotnych, która została mapowany do tej kategorii.  
  
 Aby zrozumieć podstawową przyczyną zdarzenie blokowania wątku, sprawdzić blokowania stosy wywołań i profilu, raportów.  
  
## <a name="see-also"></a>Zobacz też  
 [Widok wątków](../profiling/threads-view-parallel-performance.md)