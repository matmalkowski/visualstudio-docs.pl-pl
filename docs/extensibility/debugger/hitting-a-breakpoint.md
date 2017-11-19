---
title: "Aktywując punkt przerwania | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], hitting breakpoints
- breakpoints, hitting
ms.assetid: a77816e3-b15b-46a0-90cd-be7242e4d6c9
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 73cdce5415dd50059dcd443f67424203430aba87
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="hitting-a-breakpoint"></a>Aktywując punkt przerwania
Poniżej opisano proces, gdy aparat debugowania (DE) trafienia punktu przerwania podczas uruchamiania lub wykonywanie krok po kroku:  
  
## <a name="troubleshooting-a-hit-breakpoint"></a>Rozwiązywanie problemów z trafień punktu przerwania  
  
1.  Wysyła DE [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) interfejsu jako **EVENT_SYNC_STOP**.  
  
2.  Wywołuje Menedżera debugowania sesji (SDM) [IDebugBreakpointEvent2:::EnumBreakpoints](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) do pobrania, który został trafiony punkt przerwania.  
  
## <a name="see-also"></a>Zobacz też  
 [Wywoływanie zdarzeń debugera](../../extensibility/debugger/calling-debugger-events.md)