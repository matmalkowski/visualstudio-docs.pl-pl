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
ms.openlocfilehash: 011de9ce3e4e1445354f907dcf56a0f4ecbef6bc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="stepping-in-break-mode"></a>Wykonywanie krok po kroku, w trybie przerwania
Poniżej opisano proces, który występuje, gdy debuger jest w trybie przerwania i musi wykonywać krokowo kodu:  
  
## <a name="stepping-process"></a>Wykonywanie krok po kroku procesu  
  
1.  Wywołanie [IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md) z [STEPKIND](../../extensibility/debugger/reference/stepkind.md) i [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) argumentów, aby wykonać krok.  
  
2.  Po zakończeniu tego kroku wysyłania [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) jako zdarzeniem zatrzymującym.  
  
## <a name="see-also"></a>Zobacz też  
 [Wywoływanie zdarzeń debugera](../../extensibility/debugger/calling-debugger-events.md)