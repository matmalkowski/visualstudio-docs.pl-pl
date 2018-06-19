---
title: Błędy punktu przerwania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, errors
- debugging [Debugging SDK], breakpoint errors
- errors [Debugging SDK]
ms.assetid: 79221c6b-a924-4c8e-a778-e312e4e0c0c8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3e3c7271cc573388231045143f275d1032bef437
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31099886"
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