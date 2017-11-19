---
title: "-O Time (Widok wątków) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.cv.threads.timeline.io
helpviewer_keywords: Concurrency Visualizer, I/O time (Threads View)
ms.assetid: 0c4ec14d-d8dd-49c1-999c-dcbf4e8e1dc8
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d53cfcf4daa5e1ac1129230884684692867b121d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="io-time-threads-view"></a>I/O Time (Widok wątków)
Te segmenty na osi czasu są skojarzone z blokowaniem razy, które są podzielone na We/Wy. Oznacza to, że wątek oczekuje na zakończenie operacji We/Wy. Wątek może został zablokowany w interfejsie API, lub poczekaj I O powiązanych z/jądra, który Concurrency Visualizer jest liczy się jako operacji We/Wy. Interfejsy API, takich jak `CreateFile()`, `ReadFile()`, i `WSARecv()` należą do tej grupy.  
  
## <a name="see-also"></a>Zobacz też  
 [Widok wątków](../profiling/threads-view-parallel-performance.md)