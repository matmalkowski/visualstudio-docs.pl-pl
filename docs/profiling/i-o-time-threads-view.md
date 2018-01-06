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
ms.workload: multiple
ms.openlocfilehash: abea2c5ed246fe3463205894326a7f9611b56043
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="io-time-threads-view"></a>I/O Time (Widok wątków)
Te segmenty na osi czasu są skojarzone z blokowaniem razy, które są podzielone na We/Wy. Oznacza to, że wątek oczekuje na zakończenie operacji We/Wy. Wątek może został zablokowany w interfejsie API, lub poczekaj I O powiązanych z/jądra, który Concurrency Visualizer jest liczy się jako operacji We/Wy. Interfejsy API, takich jak `CreateFile()`, `ReadFile()`, i `WSARecv()` należą do tej grupy.  
  
## <a name="see-also"></a>Zobacz też  
 [Widok wątków](../profiling/threads-view-parallel-performance.md)