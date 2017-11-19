---
title: Pusty Segment osi czasu | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.cv.threads.timeline.empty
helpviewer_keywords: Concurrency Visualizer, empty timeline segment
ms.assetid: f37b301f-3edc-4e56-8084-feec2dc5a9b1
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b8cc25d03d4565f33ff42267ea0af1c7c31cbfd8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="empty-timeline-segment"></a>Pusty segment osi czasu
W Concurrency Visualizer powód sekcji osi czasu jest pusty (ma białe tło) zależy od rodzaju kanału.  
  
-   Dla kanału wątku procesora CPU oznacza to, że wątek nie istnieje w tej części osi czasu. Jeśli interesuje Cię wątek, można znaleźć sekcji wykonywane za pomocą formantu powiększenia lub przewijanie w poziomie.  
  
-   Kanał We/Wy oznacza to, nie dostępu do dysku wystąpił w danym momencie w imieniu procesu docelowego.  
  
-   Dla kanału DirectX oznacza to, że nie działanie procesora GPU została wykonana w imieniu procesu docelowego podczas tej części osi czasu.  
  
-   Dla kanału znacznika oznacza to, że nie wygenerowano żadnych znaczników.  
  
## <a name="see-also"></a>Zobacz też  
 [Widok wątków](../profiling/threads-view-parallel-performance.md)   
 [Formant powiększania (Widok wątków)](../profiling/zoom-control-threads-view.md)