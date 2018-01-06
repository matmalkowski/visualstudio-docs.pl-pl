---
title: "Aktywność GPU (stronicowanie) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.cv.threads.timeline.gpuactivity
- vs.cv.threads.timeline.gpupaging
ms.assetid: 95284ac5-3492-4f7b-a79f-7d2840a07679
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 01c61fb193ebc29c6eb76615e339327e71c24002
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="gpu-activity-paging"></a>Aktywność GPU (Stronicowanie)
**Aktywność GPU (stronicowanie)** segmentów na karcie wątków reprezentują razy podczas przetwarzania żądania stronicowania procesora GPU.  Długość segmentu reprezentuje czas przetwarzania pakiet stronicowania pamięci bezpośrednio dostępu (DMA) czy procesora GPU. Zazwyczaj stronicowania pakiety są skojarzone z transferu pamięci między procesora CPU i procesora GPU.  
  
 Po wybraniu segment stronicowania GPU raportu na **bieżącego** karta zawiera informacje o pakiecie DMA, która została przetworzona. Dotyczy to czas, który go oczekiwano kolejki sprzętu, która jest skojarzona z aparatu programu DirectX, proces, który przesłał pakiet DMA i czasu, która jest wymagana do przetwarzania pakietu.  
  
## <a name="see-also"></a>Zobacz też  
 [Widok wykorzystania](../profiling/utilization-view.md)