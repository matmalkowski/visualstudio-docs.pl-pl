---
title: Aktywność GPU (stronicowanie) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.gpuactivity
- vs.cv.threads.timeline.gpupaging
ms.assetid: 95284ac5-3492-4f7b-a79f-7d2840a07679
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2b8b682c47844a9bc88afdce4a532b1188746a85
ms.sourcegitcommit: 269b55b413d2c82e6aa56c6ab8e53da7926fb2e8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2018
ms.locfileid: "35238036"
---
# <a name="gpu-activity-paging"></a>Aktywność GPU (Stronicowanie)
**Aktywność GPU (stronicowanie)** segmenty na **wątków** karcie reprezentują razy podczas przetwarzania żądania stronicowania procesora GPU.  Długość segmentu reprezentuje czas przetwarzania pakiet stronicowania pamięci bezpośrednio dostępu (DMA) czy procesora GPU. Zazwyczaj stronicowania pakiety są skojarzone z transferu pamięci między procesora CPU i procesora GPU.  
  
 Po wybraniu segment stronicowania GPU raportu na **bieżącego** karta zawiera informacje o pakiecie DMA, która została przetworzona. Dotyczy to czas, który go oczekiwano kolejki sprzętu, która jest skojarzona z aparatu programu DirectX, proces, który przesłał pakiet DMA i czasu, która jest wymagana do przetwarzania pakietu.  
  
## <a name="see-also"></a>Zobacz także  
 [Widok wykorzystania](../profiling/utilization-view.md)