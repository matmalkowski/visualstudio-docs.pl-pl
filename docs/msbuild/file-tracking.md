---
title: Śledzenie plików | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- msbuild, file tracking
ms.assetid: e6c66ac0-3464-451f-9192-3b98dca21b4a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 394b40a304d2aba3b79c5878befe33a8a1aaf8b8
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37945562"
---
# <a name="file-tracking"></a>Śledzenie plików
Śledzenie pliku rejestruje wywołania do Windows systemu plików dla procesu i jego procesów podrzędnych. Przez wywołanie funkcji wymienionych poniżej, programy kontrolują kiedy należy włączyć rejestrowanie i wyłączyć i określ plik dziennika do użycia.  
  
 [EndTrackingContext](../msbuild/endtrackingcontext.md)  
 Zatrzymaj śledzenie bieżącego kontekstu.  
  
 [ResumeTracking](../msbuild/resumetracking.md)  
 Wznów śledzenie po wywołaniu [SuspendTracking](../msbuild/suspendtracking.md).  
  
 [SetThreadCount](../msbuild/setthreadcount.md)  
 Ustaw liczbę wątków używanych na potrzeby śledzenia.  
  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)  
 Rozpocznij nowy kontekst śledzenia.  
  
 [StartTrackingContextWithRoot](../msbuild/starttrackingcontextwithroot.md)  
 Rozpocznij nowy kontekst śledzenia z określonym katalogiem głównym.  
  
 [StopTrackingAndCleanup](../msbuild/stoptrackingandcleanup.md)  
 Zakończenia śledzenia i zwolnienia zasobów używane.  
  
 [SuspendTracking](../msbuild/suspendtracking.md)  
 Czasowo zawieszają śledzenie.  
  
 [WriteAllTLogs](../msbuild/writealltlogs.md)  
 Zapisać dziennik śledzenia dla wszystkich kontekstów.  
  
 [WriteContextTLogs](../msbuild/writecontexttlogs.md)  
 Zapisać dziennik śledzenia dla bieżącego kontekstu.