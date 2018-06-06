---
title: Pusty Segment osi czasu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: ad8d87c0574ac2c7671012fff6a81a568d6bff5f
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2018
ms.locfileid: "34764533"
---
# <a name="empty-timeline-segment"></a>Pusty segment osi czasu
W Concurrency Visualizer powód sekcji osi czasu jest pusty (ma białe tło) zależy od rodzaju kanału.  
  
-   Dla kanału wątku procesora CPU oznacza to, że wątek nie istnieje w tej części osi czasu. Jeśli interesuje Cię wątek, można znaleźć sekcji wykonywane za pomocą formantu powiększenia lub przewijanie w poziomie.  
  
-   Kanał We/Wy oznacza to, nie dostępu do dysku wystąpił w danym momencie w imieniu procesu docelowego.  
  
-   Dla kanału DirectX oznacza to, że nie działanie procesora GPU została wykonana w imieniu procesu docelowego podczas tej części osi czasu.  
  
-   Dla kanału znacznika oznacza to, że nie wygenerowano żadnych znaczników.  
  
## <a name="see-also"></a>Zobacz także  
 [Widok wątków](../profiling/threads-view-parallel-performance.md)   
 [Formant powiększania (Widok wątków)](../profiling/zoom-control-threads-view.md)