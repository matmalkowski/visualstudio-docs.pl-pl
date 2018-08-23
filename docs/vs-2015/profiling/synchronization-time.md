---
title: Czas synchronizacji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.cv.threads.timeline.synchronization
helpviewer_keywords:
- Concurrency Visualizer, Synchronization Time
ms.assetid: affa04cc-8bba-4848-9301-b19846d3c2cb
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2b1ca6b7a0d6e7f7c3be41bb091674a3526edf53
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42685996"
---
# <a name="synchronization-time"></a>Czas synchronizacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [czas synchronizacji](https://docs.microsoft.com/visualstudio/profiling/synchronization-time).  
  
Te segmenty na osi czasu są skojarzone z zablokowania prób są klasyfikowane jako synchronizacji. Gdy wątek jest oznaczony jako zablokowane na synchronizacji, jeden z nich jest implikowane:  
  
-   Wykonywanie wątku może spowodować utworzenie wywołanie synchronizacji wątków dobrze znanych interfejsów API takich jak `EnterCriticalSection()` lub `WaitForSingleObject()`.  
  
-   Algorytm dopasowania interfejsu API nie może być całkowicie kompleksowe i w związku z tym niektóre interfejsy API, który mógłby być mapowany na innych kategoriach może również wystąpić, ponieważ synchronizacji, ponieważ ramki w wywołaniu stosu po pewnym czasie osiągnięto bazowego jądra blokuje pierwotnych, która została mapowany do tej kategorii.  
  
 Aby zrozumieć przyczyny wydarzeniu blokowania wątku, należy dokładnie bada blokowania stosy wywołań i profilu, raportów.  
  
## <a name="see-also"></a>Zobacz też  
 [Widok wątków](../profiling/threads-view-parallel-performance.md)



