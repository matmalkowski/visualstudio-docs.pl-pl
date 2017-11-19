---
title: "Kończenie działania i odłączanie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- programs, termination events
- debug engines, detaching from programs
ms.assetid: 268c1e51-6363-45d1-964c-1ab99bdfa4f9
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9efd8e7bdaf9f75f3c3d81f7738d6bfb078cfcb2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="termination-and-detaching"></a>Kończenie działania i odłączanie
Poniżej opisano normalne zakończenia.  
  
## <a name="discussion"></a>Omówienie  
 Po [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) lub [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) interfejsu będzie nadal występować, jeśli nie ma żadnych punktów przerwania, wyjątki, błędy środowiska wykonawczego ani w aplikacji można debugować nieskończone pętle program debugowany zostanie uruchomiony do zakończenia. Jest to normalne zakończenia.  
  
 Konieczne jest wysłanie [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) do zaimplementowania normalne zakończenia. Wymaga to wykonania [IDebugProgramDestroyEvent2::GetExitCode](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md) metody.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie aparat debugowania niestandardowych](../../extensibility/debugger/creating-a-custom-debug-engine.md)