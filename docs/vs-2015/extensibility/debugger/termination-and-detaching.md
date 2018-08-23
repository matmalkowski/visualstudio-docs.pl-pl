---
title: Kończenie i odłączanie | Dokumentacja firmy Microsoft
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
- programs, termination events
- debug engines, detaching from programs
ms.assetid: 268c1e51-6363-45d1-964c-1ab99bdfa4f9
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7742ec8ef896006bc00bcbdfcf4961c15acdf746
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42678536"
---
# <a name="termination-and-detaching"></a>Kończenie i odłączanie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [zakończenia i Detaching](https://docs.microsoft.com/visualstudio/extensibility/debugger/termination-and-detaching).  
  
Poniżej opisano normalne zakończenie.  
  
## <a name="discussion"></a>Dyskusja  
 Po [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) lub [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) interfejsu będzie nadal występować, jeśli nie ma żadnych punktów przerwania, wyjątki, błędy czasu wykonywania ani pętli nieskończonej w aplikacji przeznaczonej do debugowania, do ukończenia uruchomią się debugowanego programu. Jest to normalne zakończenie.  
  
 Konieczne jest wysłanie [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) do zaimplementowania normalne zakończenie. Wymaga to wykonania [IDebugProgramDestroyEvent2::GetExitCode](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md) metody.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie niestandardowego aparatu debugowania](../../extensibility/debugger/creating-a-custom-debug-engine.md)

