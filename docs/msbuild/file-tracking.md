---
title: Śledzenie plików | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- msbuild, file tracking
ms.assetid: e6c66ac0-3464-451f-9192-3b98dca21b4a
author: Mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 827d8e13249ec3c7a9effc909a881bf434e356b1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="file-tracking"></a>Śledzenie plików
Plik śledzenia rejestruje wywołań do systemu plików dla procesu i jego procesy podrzędne. Programy kontroli przez wywołanie funkcji wymienionych poniżej, kiedy należy włączyć rejestrowanie i wyłączyć i określ plik dziennika, który będzie używany.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [EndTrackingContext](../msbuild/endtrackingcontext.md)  
 Zatrzymaj śledzenie bieżącego kontekstu.  
  
 [ResumeTracking](../msbuild/resumetracking.md)  
 Resume śledzenia po wywołaniu [SuspendTracking](../msbuild/suspendtracking.md).  
  
 [SetThreadCount](../msbuild/setthreadcount.md)  
 Ustaw liczbę wątków używanych podczas śledzenia.  
  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)  
 Rozpocznij nowy kontekst śledzenia.  
  
 [StartTrackingContextWithRoot](../msbuild/starttrackingcontextwithroot.md)  
 Rozpocznij nowy kontekst śledzenia z określonego katalogu głównego.  
  
 [StopTrackingAndCleanup](../msbuild/stoptrackingandcleanup.md)  
 Końcowy śledzenia i wersji zasoby używane.  
  
 [SuspendTracking](../msbuild/suspendtracking.md)  
 Tymczasowo wstrzymać śledzenia.  
  
 [WriteAllTLogs](../msbuild/writealltlogs.md)  
 Zapisać wszystkie konteksty można znaleźć w dziennikach śledzenia.  
  
 [WriteContextTLogs](../msbuild/writecontexttlogs.md)  
 Zapisać dziennik śledzenia dla bieżącego kontekstu.