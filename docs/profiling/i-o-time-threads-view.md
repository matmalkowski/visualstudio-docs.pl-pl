---
title: -O Time (Widok wątków) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: 253aa8c3a8ca5161fbb95e18f38f0ff232cd37bc
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/07/2018
ms.locfileid: "34844849"
---
# <a name="io-time-threads-view"></a>I/O time (Widok wątków)
Te segmenty na osi czasu są skojarzone z blokowaniem razy, które są podzielone na We/Wy. Oznacza to, że wątek oczekuje na zakończenie operacji We/Wy. Wątek może został zablokowany w interfejsie API, lub poczekaj I O powiązanych z/jądra, który Concurrency Visualizer jest liczy się jako operacji We/Wy. Interfejsy API, takich jak `CreateFile()`, `ReadFile()`, i `WSARecv()` należą do tej grupy.  
  
## <a name="see-also"></a>Zobacz także  
 [Widok wątków](../profiling/threads-view-parallel-performance.md)