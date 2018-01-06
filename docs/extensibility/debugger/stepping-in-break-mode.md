---
title: Wykonywanie krok po kroku, w trybie przerwania | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- break mode, stepping
- stepping, in break mode
- debugging [Debugging SDK], stepping in break mode
ms.assetid: b08dc8ee-6c63-4462-a097-6f525cfbb35a
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: bb56cef2f60b0268528ea75e4fe2b991a7472192
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="stepping-in-break-mode"></a>Wykonywanie krok po kroku, w trybie przerwania
Poniżej opisano proces, który występuje, gdy debuger jest w trybie przerwania i musi wykonywać krokowo kodu:  
  
## <a name="stepping-process"></a>Wykonywanie krok po kroku procesu  
  
1.  Wywołanie [IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md) z [STEPKIND](../../extensibility/debugger/reference/stepkind.md) i [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) argumentów, aby wykonać krok.  
  
2.  Po zakończeniu tego kroku wysyłania [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) jako zdarzeniem zatrzymującym.  
  
## <a name="see-also"></a>Zobacz też  
 [Wywoływanie zdarzeń debugera](../../extensibility/debugger/calling-debugger-events.md)