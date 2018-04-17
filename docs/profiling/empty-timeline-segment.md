---
title: Pusty Segment osi czasu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.empty
helpviewer_keywords:
- Concurrency Visualizer, empty timeline segment
ms.assetid: f37b301f-3edc-4e56-8084-feec2dc5a9b1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 122eb98fcac3bd03d3a4043399cb31041bab52f5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="empty-timeline-segment"></a>Pusty segment osi czasu
W Concurrency Visualizer powód sekcji osi czasu jest pusty (ma białe tło) zależy od rodzaju kanału.  
  
-   Dla kanału wątku procesora CPU oznacza to, że wątek nie istnieje w tej części osi czasu. Jeśli interesuje Cię wątek, można znaleźć sekcji wykonywane za pomocą formantu powiększenia lub przewijanie w poziomie.  
  
-   Kanał We/Wy oznacza to, nie dostępu do dysku wystąpił w danym momencie w imieniu procesu docelowego.  
  
-   Dla kanału DirectX oznacza to, że nie działanie procesora GPU została wykonana w imieniu procesu docelowego podczas tej części osi czasu.  
  
-   Dla kanału znacznika oznacza to, że nie wygenerowano żadnych znaczników.  
  
## <a name="see-also"></a>Zobacz też  
 [Widok wątków](../profiling/threads-view-parallel-performance.md)   
 [Ustawianie powiększenia (Widok wątków)](../profiling/zoom-control-threads-view.md)