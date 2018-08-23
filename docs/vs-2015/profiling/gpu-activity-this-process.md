---
title: Aktywność procesora GPU (ten proces) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.cv.threads.timeline.gpuexecution
- vs.cv.threads.timeline.gpuactivity
ms.assetid: 0956edbf-9bcd-4afe-9287-fda628648ca0
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dc7741e46d9b7ae3bf7e53e6a07f5601e7dbbd83
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42684160"
---
# <a name="gpu-activity-this-process"></a>Aktywności procesora GPU (ten proces)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [aktywności procesora GPU (ten proces)](https://docs.microsoft.com/visualstudio/profiling/gpu-activity-this-process).  
  
**Aktywności procesora GPU (ten proces)** segmenty w widoku wątków w Wizualizatorze współbieżności reprezentują razy podczas przetwarzania żądania w imieniu bieżącego procesu procesora GPU. Te żądania są wysyłane do procesora GPU jako pakiety dostępu (DMA) pamięci. Długość segmentu reprezentuje czas procesora GPU zostało przetwarzania pakietu DMA imieniu bieżącego procesu.  
  
 Po wybraniu segmentu działanie procesora GPU, raport na **bieżącego** karta zawiera informacje o pakiecie DMA, która została przetworzona. Informacje te obejmują czas, który pakiet jest oczekiwany w kolejce sprzętowej, skojarzony z aparatu programu DirectX, proces, który przesłał pakiet i czas wymagany do przetwarzania pakietów. Procesu niż bieżący proces może fizycznie przesłany pakiet DMA do procesora GPU. Narzędzie Concurrency Visualizer można wykrywać przesyłanej przez inny proces roboczy do procesora GPU w imieniu bieżący proces.



