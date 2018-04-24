---
title: Czas uśpienia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.sleep
helpviewer_keywords:
- Concurrency Visualizer, Sleep Time
ms.assetid: 3ddb96f9-9bda-4a68-ad4d-ef488a0a68dc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0b9a3894097c553d8505fd61f15fbdec8c188e79
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="sleep-time"></a>Czas uśpienia
Te segmenty na osi czasu są skojarzone z blokowaniem czas, który jest skategoryzowany jako uśpienia. Kategoria uśpienia oznacza to, że wątek dobrowolnie udzielił się jego rdzenia logicznego jest bezczynne. W tym czasie wątek został zablokowany w interfejsie API, który Concurrency Visualizer jest liczy się jako uśpienia. Interfejsy API, takich jak `Sleep()` i `SwitchToThread()` należą do tej grupy.  
  
## <a name="see-also"></a>Zobacz też  
 [Widok wątków](../profiling/threads-view-parallel-performance.md)