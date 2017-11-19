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
ms.openlocfilehash: 960ea3a50a5c937b93b81c56e3b775d3fde49bd8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="gpu-activity-paging"></a>Aktywność GPU (Stronicowanie)
**Aktywność GPU (stronicowanie)** segmentów na karcie wątków reprezentują razy podczas przetwarzania żądania stronicowania procesora GPU.  Długość segmentu reprezentuje czas przetwarzania pakiet stronicowania pamięci bezpośrednio dostępu (DMA) czy procesora GPU. Zazwyczaj stronicowania pakiety są skojarzone z transferu pamięci między procesora CPU i procesora GPU.  
  
 Po wybraniu segment stronicowania GPU raportu na **bieżącego** karta zawiera informacje o pakiecie DMA, która została przetworzona. Dotyczy to czas, który go oczekiwano kolejki sprzętu, która jest skojarzona z aparatu programu DirectX, proces, który przesłał pakiet DMA i czasu, która jest wymagana do przetwarzania pakietu.  
  
## <a name="see-also"></a>Zobacz też  
 [Widok wykorzystania](../profiling/utilization-view.md)