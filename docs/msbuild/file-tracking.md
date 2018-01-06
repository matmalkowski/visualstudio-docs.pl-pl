---
title: "Śledzenie plików | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: msbuild, file tracking
ms.assetid: e6c66ac0-3464-451f-9192-3b98dca21b4a
caps.latest.revision: "6"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: ea3972ae1ce268a85a41be47b81f1abb76d7d409
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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