---
title: "Działanie procesora GPU (ten proces) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.cv.threads.timeline.gpuexecution
- vs.cv.threads.timeline.gpuactivity
ms.assetid: 0956edbf-9bcd-4afe-9287-fda628648ca0
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 255a1ff62d4f9c444169e1330dcd11eb8e1030ed
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="gpu-activity-this-process"></a>Aktywności procesora GPU (ten proces)
**Aktywności procesora GPU (ten proces)** segmentów w widoku wątków w Concurrency Visualizer reprezentują razy podczas przetwarzania żądania w imieniu bieżącego procesu procesora GPU. Te żądania są wysyłane do procesora GPU jako pamięci (DMA) dostępu do pakietów. Długość segmentu reprezentuje czas procesora GPU zostało przetwarzania pakietów DMA imieniu bieżącego procesu.  
  
 Po wybraniu segmentu działanie procesora GPU, raportu na **bieżącego** karta zawiera informacje o pakiecie DMA, która została przetworzona. Informacje te obejmują ilość czasu oczekiwania pakietów w kolejce sprzętu, powiązanej z aparatu programu DirectX, proces, który przesłał pakiet i czas wymagany do przetwarzania pakietu. Procesu niż bieżący proces może fizycznie przesłany pakiet DMA do procesora GPU. Narzędzia Concurrency Visualizer może wykryć przesyłanej innego procesu roboczego do procesora GPU w imieniu bieżącego procesu.