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
ms.workload: multiple
ms.openlocfilehash: 91fda110b3bf73b59d7c9d7d8ff6f7226f9ec5fa
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="execution-time-threads-view"></a>Czas wykonywania (Widok wątków)
Te segmenty w oś czasu widoku wątków reprezentują czas wykonania, gdy wątek jest aktywnie podczas pracy nad rdzenia logicznego w systemie.  
  
 Za pomocą zdarzeń przełącznika kontekst jądra zostaną wykryte zmiany w stan wątku. Zdarzenia śledzenia dla systemu Windows (ETW) przechwytuje stosy próbki co milisekund. W bardzo krótkim zielonym segmencie prawdopodobnie nie jest próbki. W związku z tym niektóre segmentów wykonania na krótki może zawierać żadnego stosu wywołań.  
  
 Po kliknięciu segmentu wykonania Concurrency Visualizer przedstawia przykładowy stos najbliżej miejsca po kliknięciu. Wyświetlana jest lokalizacja tego stosu próbki czarna strzałka lub karetkę powyżej osi czasu, a Przykładowy stos pojawia się na **bieżącego** kartę.  
  
 Aby wyświetlić profil próbkowania tradycyjnych dla wszystkich segmentów wykonania w bieżącym widoku, kliknij przycisk **wykonywania** w profil widocznej osi czasu.  
  
## <a name="see-also"></a>Zobacz też  
 [Raport profilu wykonania](../profiling/execution-profile-report.md)   
 [Widok wątków](../profiling/threads-view-parallel-performance.md)