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
ms.openlocfilehash: ad48cd912bfdc117496bc9f876a1a2174e76dc04
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2018
ms.locfileid: "34477538"
---
# <a name="ui-processing-time"></a>Czas przetwarzania interfejsu użytkownika
Te segmenty na osi czasu są skojarzone z blokowaniem razy, które są sklasyfikowane jako przetwarzania interfejsu użytkownika. Oznacza to, że wątek przekazywania komunikatów systemu Windows lub wykonywania innych zadań interfejsu użytkownika. W tym czasie wątek został zablokowany w interfejsie API, który Concurrency Visualizer jest liczy się jako przetwarzania interfejsu użytkownika. Interfejsy API, takich jak `GetMessage()` i `MsgWaitForMultipleObjects()` należą do tej grupy.  
  
 Jeśli zostanie ustalone, nie predefiniowanych blokowania interfejsu API, przejrzyj stosy wywołań i raportów profilu, aby ustalić podstawowe przyczyny opóźnienia.  
  
 Kategoria przetwarzania interfejsu użytkownika pomaga w zrozumieniu czas odpowiedzi aplikacji z graficznym interfejsem użytkownika i jest pożądane w aplikacjach, które są zależne od czasu odpowiedzi interfejsu użytkownika. Na przykład jeśli wątek interfejsu użytkownika w aplikacji osiągnięcie 100% czasu potrzebnego na przetwarzania interfejsu użytkownika, jest prawdopodobnie reakcji. Jednak jeśli wiele czasu w innych kategoriach korzystało z wątku interfejsu użytkownika, wyszukaj główne przyczyny i należy rozważyć opcje redukcji kategorie bez interfejsu użytkownika dla tego wątku.  
  
## <a name="see-also"></a>Zobacz także  
 [Widok wątków](../profiling/threads-view-parallel-performance.md)