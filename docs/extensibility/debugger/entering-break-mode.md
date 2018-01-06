---
title: Trybu przerwania | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- break mode
- debugging [Debugging SDK], entering break mode
ms.assetid: e9a8a241-cd21-4d4e-999a-283554c288b1
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 5774161bdeb33ee954965262532406834a5c5eb1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="entering-break-mode"></a>Wprowadzanie tryb przerwania
Poniżej opisano proces, który występuje po napotkaniu punktu przerwania po Wkraczanie do funkcji, uruchamiania do wiersza kodu źródłowego, który ma kursor w nim lub do punktu przerwania.  
  
## <a name="break-mode-process"></a>Proces tryb przerwania  
  
1.  Aparat debugowania (DE) wysyła [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md), [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md), lub inne zdarzenia zatrzymywania spowodować IDE tryb przerwania.  
  
2.  SDM są pobierane informacje stosu wywołań z wątku, w następujący sposób:  
  
    -   [IDebugThread2::EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)  
  
    -   [IEnumDebugFrameInfo2::GetCount](../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)  
  
    -   [IEnumDebugFrameInfo2::Next](../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)  
  
    -   [IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) można pobrać informacji dotyczących kodu źródłowego  
  
    -   [IDebugDocumentContext2::GetName](../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md) można pobrać nazwy pliku  
  
    -   [IDebugDocumentContext2::GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) można pobrać zakresu instrukcji  
  
    -   [IDebugStackFrame2::GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md) można pobrać informacji o pamięci  
  
## <a name="see-also"></a>Zobacz też  
 [Wywoływanie zdarzeń debugera](../../extensibility/debugger/calling-debugger-events.md)