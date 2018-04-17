---
title: Działanie procesora GPU (inne procesy) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
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
ms.openlocfilehash: edbe8a49ed65fbd51a53cf9e197154489d4ca271
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="gpu-activity-other-processes"></a>Aktywność procesora GPU (inne procesy)
**Aktywności procesora GPU (inne procesy)** segmentów w widoku wątków Concurrency Visualizer reprezentują razy podczas przetwarzania żądania w imieniu innych procesów w systemie procesora GPU. Te żądania są wysyłane procesora GPU w pamięci (DMA) dostępu do pakietów.  Długość segmentu reprezentuje czas przetwarzania przez procesor GPU pakiet.  
  
 Po wybraniu tego rodzaju segmentu, raportu na **bieżącego** karta zawiera informacje o pakiecie, który był przetwarzany.  Informacje obejmują ilość czasu oczekiwania pakietów w kolejce sprzętu, powiązanej z aparatu programu DirectX, proces, który przesłał pakiet i czas wymagany do przetwarzania pakietu.