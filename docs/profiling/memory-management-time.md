---
title: Czas zarządzania pamięcią | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.paging
helpviewer_keywords:
- Concurrency Visualizer, Paging Time
ms.assetid: 67af3509-3a7d-435d-bc37-5262448da915
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0284d312a4157c41f93fec17d601406c669a83c1
ms.sourcegitcommit: 269b55b413d2c82e6aa56c6ab8e53da7926fb2e8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2018
ms.locfileid: "35238254"
---
# <a name="memory-management-time"></a>Czas zarządzania pamięcią
Te segmenty na osi czasu są skojarzone z blokuje razy, które są sklasyfikowane jako zarządzania pamięcią. W tym scenariuszu oznacza, że wątek jest zablokowany przez zdarzenie, który jest skojarzony z operacji zarządzania pamięcią, takich jak stronicowania. W tym czasie wątek został zablokowany w stanie interfejsu API lub jądra Concurrency Visualizer jest liczy się jako zarządzania pamięcią. Obejmują one zdarzenia, takie jak alokacji pamięci i stronicowania.  
  
 Sprawdź, czy stosy wywołań skojarzone i profilu, raportów i Poznaj lepiej podstawowe przyczyny bloków, które są sklasyfikowane jako zarządzania pamięcią.  
  
## <a name="see-also"></a>Zobacz także  
 [Widok wątków](../profiling/threads-view-parallel-performance.md)