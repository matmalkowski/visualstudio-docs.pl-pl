---
title: -O Time (Widok wątków) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.io
helpviewer_keywords:
- Concurrency Visualizer, I/O time (Threads View)
ms.assetid: 0c4ec14d-d8dd-49c1-999c-dcbf4e8e1dc8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 070e47d42b5d00058480cf5c4f94437855bfd80b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="io-time-threads-view"></a>I/O Time (Widok wątków)
Te segmenty na osi czasu są skojarzone z blokowaniem razy, które są podzielone na We/Wy. Oznacza to, że wątek oczekuje na zakończenie operacji We/Wy. Wątek może został zablokowany w interfejsie API, lub poczekaj I O powiązanych z/jądra, który Concurrency Visualizer jest liczy się jako operacji We/Wy. Interfejsy API, takich jak `CreateFile()`, `ReadFile()`, i `WSARecv()` należą do tej grupy.  
  
## <a name="see-also"></a>Zobacz też  
 [Widok wątków](../profiling/threads-view-parallel-performance.md)