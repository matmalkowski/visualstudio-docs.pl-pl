---
title: "Czas przetwarzania interfejsu użytkownika | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.cv.threads.timeline.uiprocessing
helpviewer_keywords:
- Concurrency Visualizer, UI Processing Time
ms.assetid: 0ddb05a3-8c6b-448b-8488-2751c1e5abcc
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 8171fa96848aa53fb151ed4d4701268308e4ad1c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ui-processing-time"></a>Czas przetwarzania interfejsu użytkownika
Te segmenty na osi czasu są skojarzone z blokowaniem razy, które są sklasyfikowane jako przetwarzania interfejsu użytkownika. Oznacza to, że wątek przekazywania komunikatów systemu Windows lub wykonywania innych zadań interfejsu użytkownika. W tym czasie wątek został zablokowany w interfejsie API, który Concurrency Visualizer jest liczy się jako przetwarzania interfejsu użytkownika. Interfejsy API, takich jak `GetMessage()` i `MsgWaitForMultipleObjects()` należą do tej grupy.  
  
 Jeśli zostanie ustalone, nie predefiniowanych blokowania interfejsu API, przejrzyj stosy wywołań i raportów profilu, aby ustalić podstawowe przyczyny opóźnienia.  
  
 Kategoria przetwarzania interfejsu użytkownika jest istotne dla zrozumienia czas odpowiedzi aplikacji z graficznym interfejsem użytkownika i jest pożądane w aplikacjach, które są zależne od czasu odpowiedzi interfejsu użytkownika. Na przykład jeśli wątek interfejsu użytkownika w aplikacji osiągnięcie 100% czasu potrzebnego na przetwarzania interfejsu użytkownika, jest prawdopodobnie bardzo elastyczny. Jednak jeśli wiele czasu w innych kategoriach korzystało z wątku interfejsu użytkownika, wyszukaj główne przyczyny i należy rozważyć opcje redukcji kategorie bez interfejsu użytkownika dla tego wątku.  
  
## <a name="see-also"></a>Zobacz też  
 [Widok wątków](../profiling/threads-view-parallel-performance.md)