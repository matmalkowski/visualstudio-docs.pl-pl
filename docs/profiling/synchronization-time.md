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
ms.openlocfilehash: f3236530c1a7b92fd1cba1bdd61e3e1c0973b58c
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "35676385"
---
# <a name="synchronization-time"></a>Czas synchronizacji
Te segmenty na osi czasu są skojarzone z zablokowania prób są klasyfikowane jako synchronizacji. Gdy wątek jest oznaczony jako zablokowane na synchronizacji, jeden z nich jest implikowane:  
  
-   Wykonywanie wątku może spowodować utworzenie wywołanie synchronizacji wątków dobrze znanych interfejsów API takich jak `EnterCriticalSection()` lub `WaitForSingleObject()`.  
  
-   Algorytm dopasowania interfejsu API nie może być całkowicie kompleksowe i w związku z tym niektóre interfejsy API, który mógłby być mapowany na innych kategoriach może również wystąpić, ponieważ synchronizacji, ponieważ ramki w wywołaniu stosu po pewnym czasie osiągnięto bazowego jądra blokuje pierwotnych, która została mapowany do tej kategorii.  
  
 Aby zrozumieć przyczyny wydarzeniu blokowania wątku, należy dokładnie bada blokowania stosy wywołań i profilu, raportów.  
  
## <a name="see-also"></a>Zobacz także  
 [Widok wątków](../profiling/threads-view-parallel-performance.md)