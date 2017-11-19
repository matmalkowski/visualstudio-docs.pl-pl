---
title: "Działanie procesora GPU (inne procesy) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.cv.threads.timeline.gpuother
- vs.cv.threads.timeline.gpuactivity
ms.assetid: 8a68df65-eb63-452f-9285-fb4ffc92f2b2
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3b32ee2967ccc4a7cf1f02935a58cfff5c9e8a33
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="gpu-activity-other-processes"></a>Aktywność procesora GPU (inne procesy)
**Aktywności procesora GPU (inne procesy)** segmentów w widoku wątków Concurrency Visualizer reprezentują razy podczas przetwarzania żądania w imieniu innych procesów w systemie procesora GPU. Te żądania są wysyłane procesora GPU w pamięci (DMA) dostępu do pakietów.  Długość segmentu reprezentuje czas przetwarzania przez procesor GPU pakiet.  
  
 Po wybraniu tego rodzaju segmentu, raportu na **bieżącego** karta zawiera informacje o pakiecie, który był przetwarzany.  Informacje obejmują ilość czasu oczekiwania pakietów w kolejce sprzętu, powiązanej z aparatu programu DirectX, proces, który przesłał pakiet i czas wymagany do przetwarzania pakietu.