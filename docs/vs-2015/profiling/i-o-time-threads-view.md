---
title: -O Time (Widok wątków) | Dokumentacja firmy Microsoft
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
- vs.cv.threads.timeline.io
helpviewer_keywords:
- Concurrency Visualizer, I/O time (Threads View)
ms.assetid: 0c4ec14d-d8dd-49c1-999c-dcbf4e8e1dc8
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d25512da43fc32b42c2a1f79e3c8dbe992ea30ce
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42684781"
---
# <a name="io-time-threads-view"></a>I/O Time (Widok wątków)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [I-O Time (Widok wątków)](https://docs.microsoft.com/visualstudio/profiling/i-o-time-threads-view).  
  
Te segmenty na osi czasu są skojarzone z zablokowania prób są podzielone na We/Wy. Oznacza to, że wątek czeka na zakończenie operacji We/Wy. Wątek może został zablokowany w interfejsie API, lub zaczekaj I dotyczących wejścia/wyjścia jądra, który Concurrency Visualizer jest liczy się jako operacji We/Wy. Interfejsy API, takie jak `CreateFile()`, `ReadFile()`, i `WSARecv()` należą do tej grupy.  
  
## <a name="see-also"></a>Zobacz też  
 [Widok wątków](../profiling/threads-view-parallel-performance.md)



