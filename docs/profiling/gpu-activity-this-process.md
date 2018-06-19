---
title: Działanie procesora GPU (ten proces) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.gpuexecution
- vs.cv.threads.timeline.gpuactivity
ms.assetid: 0956edbf-9bcd-4afe-9287-fda628648ca0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d7fe5512cf131dfede701fb47df2ef956c01437d
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
ms.locfileid: "31570388"
---
# <a name="gpu-activity-this-process"></a>Aktywności procesora GPU (ten proces)
**Aktywności procesora GPU (ten proces)** segmentów w widoku wątków w Concurrency Visualizer reprezentują razy podczas przetwarzania żądania w imieniu bieżącego procesu procesora GPU. Te żądania są wysyłane do procesora GPU jako pamięci (DMA) dostępu do pakietów. Długość segmentu reprezentuje czas procesora GPU zostało przetwarzania pakietów DMA imieniu bieżącego procesu.  
  
 Po wybraniu segmentu działanie procesora GPU, raportu na **bieżącego** karta zawiera informacje o pakiecie DMA, która została przetworzona. Informacje te obejmują ilość czasu oczekiwania pakietów w kolejce sprzętu, powiązanej z aparatu programu DirectX, proces, który przesłał pakiet i czas wymagany do przetwarzania pakietu. Procesu niż bieżący proces może fizycznie przesłany pakiet DMA do procesora GPU. Narzędzia Concurrency Visualizer może wykryć przesyłanej innego procesu roboczego do procesora GPU w imieniu bieżącego procesu.