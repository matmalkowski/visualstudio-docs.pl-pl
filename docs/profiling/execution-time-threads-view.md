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
ms.openlocfilehash: 1b06532771aaa432deccb8040c7dd7e5962dd15f
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2018
ms.locfileid: "34764433"
---
# <a name="execution-time-threads-view"></a>Czas wykonywania (Widok wątków)
Te segmenty w oś czasu widoku wątków reprezentują czas wykonania, gdy wątek jest aktywnie podczas pracy nad rdzenia logicznego w systemie.  
  
 Za pomocą zdarzeń przełącznika kontekst jądra zostaną wykryte zmiany w stan wątku. Zdarzenia śledzenia dla systemu Windows (ETW) przechwytuje stosy próbki co milisekund. W bardzo krótkim zielonym segmencie prawdopodobnie nie jest próbki. W związku z tym niektóre segmentów wykonania na krótki może zawierać żadnego stosu wywołań.  
  
 Po kliknięciu segmentu wykonania Concurrency Visualizer przedstawia przykładowy stos najbliżej miejsca po kliknięciu. Wyświetlana jest lokalizacja tego stosu próbki czarna strzałka lub karetkę powyżej osi czasu, a Przykładowy stos pojawia się na **bieżącego** kartę.  
  
 Aby wyświetlić profil próbkowania tradycyjnych dla wszystkich segmentów wykonania w bieżącym widoku, kliknij przycisk **wykonywania** w profil widocznej osi czasu.  
  
## <a name="see-also"></a>Zobacz także  
 [Raport profilu wykonania](../profiling/execution-profile-report.md)   
 [Widok wątków](../profiling/threads-view-parallel-performance.md)