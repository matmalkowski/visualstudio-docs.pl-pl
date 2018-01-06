---
title: "Błędy punktu przerwania | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- breakpoints, errors
- debugging [Debugging SDK], breakpoint errors
- errors [Debugging SDK]
ms.assetid: 79221c6b-a924-4c8e-a778-e312e4e0c0c8
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 9cd9347290199ce695f7b2f42733ad8e5d108ac0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="breakpoint-errors"></a>Błędy punktu przerwania
Poniżej opisano proces, gdy punkt przerwania próbuje powiązać kodu, ale nie powiedzie się:  
  
## <a name="troubleshooting-a-breakpoint-error"></a>Rozwiązywanie problemów z błędem punktu przerwania  
  
1.  Aparat debugowania (DE) wysyła [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) do menedżera sesji debugowania (SDM).  
  
2.  Wywołania SDM [IDebugBreakpointErrorEvent2::GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) (IDebugErrorBreakpoint2 ** `ppErrorBP`) można pobrać błąd punktu przerwania.  
  
3.  Wywołania SDM [IDebugErrorBreakpoint2::GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md) uzyskać oczekującym punktem przerwania, z którego pochodzi błąd punktu przerwania.  
  
4.  Wywołania SDM [IDebugErrorBreakpoint2::GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) uzyskać przyczyny, dlaczego nie można powiązać punktu przerwania błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [Wywoływanie zdarzeń debugera](../../extensibility/debugger/calling-debugger-events.md)