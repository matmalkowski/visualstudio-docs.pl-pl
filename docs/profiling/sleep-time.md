---
title: "Czas uśpienia | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.cv.threads.timeline.sleep
helpviewer_keywords: Concurrency Visualizer, Sleep Time
ms.assetid: 3ddb96f9-9bda-4a68-ad4d-ef488a0a68dc
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 4385fd42c14d13e83f85683ef33a613fd6f78765
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="sleep-time"></a>Czas uśpienia
Te segmenty na osi czasu są skojarzone z blokowaniem czas, który jest skategoryzowany jako uśpienia. Kategoria uśpienia oznacza to, że wątek dobrowolnie udzielił się jego rdzenia logicznego jest bezczynne. W tym czasie wątek został zablokowany w interfejsie API, który Concurrency Visualizer jest liczy się jako uśpienia. Interfejsy API, takich jak `Sleep()` i `SwitchToThread()` należą do tej grupy.  
  
## <a name="see-also"></a>Zobacz też  
 [Widok wątków](../profiling/threads-view-parallel-performance.md)