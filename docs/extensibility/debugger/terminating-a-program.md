---
title: Trwa przerywanie wykonywania programu | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- programs, termination events
- debugging [Debugging SDK], terminating a program
ms.assetid: eedda0a3-5e05-44fe-841d-a2f4866ac72d
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ef92896ebdb847dd16e00911dc49b53d9ceb5877
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="terminating-a-program"></a>Trwa przerywanie wykonywania programu
Poniżej znajduje się opis rozwiązania programu jednego z jednego wątku.  
  
## <a name="termination-process"></a>Zakończenie procesu  
  
1.  Wysyła DE [IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) z prawidłowym [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md).  
  
2.  Wysyła DE [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) z prawidłowym [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md).  
  
 IDE przechodzi do trybu projektowania. Aparat debugowania lub wywołań środowisko wykonawcze [IDebugPortNotify2::RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) usunięcie programu z portu.  
  
## <a name="see-also"></a>Zobacz też  
 [Wywoływanie zdarzeń debugera](../../extensibility/debugger/calling-debugger-events.md)