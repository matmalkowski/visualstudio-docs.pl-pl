---
title: Czas przetwarzania interfejsu użytkownika | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.uiprocessing
helpviewer_keywords:
- Concurrency Visualizer, UI Processing Time
ms.assetid: 0ddb05a3-8c6b-448b-8488-2751c1e5abcc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b1d1e587fa7e089ee3c137ffa836a99d31dd62f8
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="ui-processing-time"></a>Czas przetwarzania interfejsu użytkownika
Te segmenty na osi czasu są skojarzone z blokowaniem razy, które są sklasyfikowane jako przetwarzania interfejsu użytkownika. Oznacza to, że wątek przekazywania komunikatów systemu Windows lub wykonywania innych zadań interfejsu użytkownika. W tym czasie wątek został zablokowany w interfejsie API, który Concurrency Visualizer jest liczy się jako przetwarzania interfejsu użytkownika. Interfejsy API, takich jak `GetMessage()` i `MsgWaitForMultipleObjects()` należą do tej grupy.  
  
 Jeśli zostanie ustalone, nie predefiniowanych blokowania interfejsu API, przejrzyj stosy wywołań i raportów profilu, aby ustalić podstawowe przyczyny opóźnienia.  
  
 Kategoria przetwarzania interfejsu użytkownika jest istotne dla zrozumienia czas odpowiedzi aplikacji z graficznym interfejsem użytkownika i jest pożądane w aplikacjach, które są zależne od czasu odpowiedzi interfejsu użytkownika. Na przykład jeśli wątek interfejsu użytkownika w aplikacji osiągnięcie 100% czasu potrzebnego na przetwarzania interfejsu użytkownika, jest prawdopodobnie bardzo elastyczny. Jednak jeśli wiele czasu w innych kategoriach korzystało z wątku interfejsu użytkownika, wyszukaj główne przyczyny i należy rozważyć opcje redukcji kategorie bez interfejsu użytkownika dla tego wątku.  
  
## <a name="see-also"></a>Zobacz też  
 [Widok wątków](../profiling/threads-view-parallel-performance.md)