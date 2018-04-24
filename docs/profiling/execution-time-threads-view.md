---
title: Czas wykonywania (Widok wątków) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.execution
helpviewer_keywords:
- Concurrency Visualizer, Execution Time (Threads View)
ms.assetid: 80c100f8-2502-4613-bfef-4f4f2e09cc8d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bce4b4e5c0d4a9d4f66fade6b01044ac149968a0
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="execution-time-threads-view"></a>Czas wykonywania (Widok wątków)
Te segmenty w oś czasu widoku wątków reprezentują czas wykonania, gdy wątek jest aktywnie podczas pracy nad rdzenia logicznego w systemie.  
  
 Za pomocą zdarzeń przełącznika kontekst jądra zostaną wykryte zmiany w stan wątku. Zdarzenia śledzenia dla systemu Windows (ETW) przechwytuje stosy próbki co milisekund. W bardzo krótkim zielonym segmencie prawdopodobnie nie jest próbki. W związku z tym niektóre segmentów wykonania na krótki może zawierać żadnego stosu wywołań.  
  
 Po kliknięciu segmentu wykonania Concurrency Visualizer przedstawia przykładowy stos najbliżej miejsca po kliknięciu. Wyświetlana jest lokalizacja tego stosu próbki czarna strzałka lub karetkę powyżej osi czasu, a Przykładowy stos pojawia się na **bieżącego** kartę.  
  
 Aby wyświetlić profil próbkowania tradycyjnych dla wszystkich segmentów wykonania w bieżącym widoku, kliknij przycisk **wykonywania** w profil widocznej osi czasu.  
  
## <a name="see-also"></a>Zobacz też  
 [Raport profilu wykonania](../profiling/execution-profile-report.md)   
 [Widok wątków](../profiling/threads-view-parallel-performance.md)