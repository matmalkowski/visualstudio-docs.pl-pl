---
title: Działanie procesora GPU (inne procesy) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.gpuother
- vs.cv.threads.timeline.gpuactivity
ms.assetid: 8a68df65-eb63-452f-9285-fb4ffc92f2b2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 586aeb9b2b6d674c14106a911872c967c272f3e6
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
ms.locfileid: "31573079"
---
# <a name="gpu-activity-other-processes"></a>Aktywność procesora GPU (inne procesy)
**Aktywności procesora GPU (inne procesy)** segmentów w widoku wątków Concurrency Visualizer reprezentują razy podczas przetwarzania żądania w imieniu innych procesów w systemie procesora GPU. Te żądania są wysyłane procesora GPU w pamięci (DMA) dostępu do pakietów.  Długość segmentu reprezentuje czas przetwarzania przez procesor GPU pakiet.  
  
 Po wybraniu tego rodzaju segmentu, raportu na **bieżącego** karta zawiera informacje o pakiecie, który był przetwarzany.  Informacje obejmują ilość czasu oczekiwania pakietów w kolejce sprzętu, powiązanej z aparatu programu DirectX, proces, który przesłał pakiet i czas wymagany do przetwarzania pakietu.