---
title: "Czas wykonywania (Widok wątków) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.cv.threads.timeline.execution
helpviewer_keywords: Concurrency Visualizer, Execution Time (Threads View)
ms.assetid: 80c100f8-2502-4613-bfef-4f4f2e09cc8d
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 626f6b0eb9d20685c0b8f71f8dea6f4f02e27254
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="execution-time-threads-view"></a>Czas wykonywania (Widok wątków)
Te segmenty w oś czasu widoku wątków reprezentują czas wykonania, gdy wątek jest aktywnie podczas pracy nad rdzenia logicznego w systemie.  
  
 Za pomocą zdarzeń przełącznika kontekst jądra zostaną wykryte zmiany w stan wątku. Zdarzenia śledzenia dla systemu Windows (ETW) przechwytuje stosy próbki co milisekund. W bardzo krótkim zielonym segmencie prawdopodobnie nie jest próbki. W związku z tym niektóre segmentów wykonania na krótki może zawierać żadnego stosu wywołań.  
  
 Po kliknięciu segmentu wykonania Concurrency Visualizer przedstawia przykładowy stos najbliżej miejsca po kliknięciu. Wyświetlana jest lokalizacja tego stosu próbki czarna strzałka lub karetkę powyżej osi czasu, a Przykładowy stos pojawia się na **bieżącego** kartę.  
  
 Aby wyświetlić profil próbkowania tradycyjnych dla wszystkich segmentów wykonania w bieżącym widoku, kliknij przycisk **wykonywania** w profil widocznej osi czasu.  
  
## <a name="see-also"></a>Zobacz też  
 [Raport profilu wykonania](../profiling/execution-profile-report.md)   
 [Widok wątków](../profiling/threads-view-parallel-performance.md)