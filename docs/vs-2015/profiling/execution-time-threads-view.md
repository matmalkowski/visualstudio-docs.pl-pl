---
title: Czas wykonywania (Widok wątków) | Dokumentacja firmy Microsoft
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
- vs.cv.threads.timeline.execution
helpviewer_keywords:
- Concurrency Visualizer, Execution Time (Threads View)
ms.assetid: 80c100f8-2502-4613-bfef-4f4f2e09cc8d
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b25048fdeeea6e1c5724ecc313993cbf74b617be
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42691531"
---
# <a name="execution-time-threads-view"></a>Czas wykonywania (Widok wątków)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [czas wykonywania (Widok wątków)](https://docs.microsoft.com/visualstudio/profiling/execution-time-threads-view).  
  
Te segmenty na osi czasu w widoku wątków reprezentują czas wykonywania, gdy wątek aktywnie wykonywania zadania na rdzeń logiczny w systemie.  
  
 Zmiany w stan wątku są wykrywane przez przekazywanie zdarzeń jądra kontekstu przełącznika. Śledzenie zdarzeń dla Windows (ETW) przechwytuje stosów próbka co milisekund. W bardzo krótkim zielonym segmencie możliwe jest nie pobraniu próbki. Dlatego niektóre segmentów wykonania na krótki mogą być wyświetlane żaden stos wywołań.  
  
 Po kliknięciu segmentu wykonania, Wizualizator współbieżności przedstawia przykładowy stos najbliższą lokalizację kliknięcie. Lokalizacja tego stosu próbki jest wyświetlany za pomocą czarne strzałki lub daszek powyżej osi czasu i Przykładowy stos jest wyświetlana na **bieżącego** kartę.  
  
 Aby wyświetlić profil próbkowania tradycyjny dla wszystkich segmentów wykonania w bieżącym widoku, kliknij **wykonywania** w profil widocznej osi czasu.  
  
## <a name="see-also"></a>Zobacz też  
 [Raport profilu wykonania](../profiling/execution-profile-report.md)   
 [Widok wątków](../profiling/threads-view-parallel-performance.md)



