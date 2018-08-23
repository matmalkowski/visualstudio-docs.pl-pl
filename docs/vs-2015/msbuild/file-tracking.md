---
title: Śledzenie plików | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- msbuild, file tracking
ms.assetid: e6c66ac0-3464-451f-9192-3b98dca21b4a
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 40598ba8fbe693d44ee49228a36be75a9e851eea
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42630863"
---
# <a name="file-tracking"></a>Śledzenie plików
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [pliku śledzenia](https://docs.microsoft.com/visualstudio/msbuild/file-tracking).  
  
  
Śledzenie pliku rejestruje wywołania do Windows systemu plików dla procesu i jego procesów podrzędnych. Przez wywołanie funkcji wymienionych poniżej, programy kontrolują kiedy należy włączyć rejestrowanie i wyłączyć i określ plik dziennika do użycia.  
  
## <a name="in-this-section"></a>W tej sekcji  
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



