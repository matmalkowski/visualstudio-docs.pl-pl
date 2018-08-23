---
title: Przejście do trybu Break | Dokumentacja firmy Microsoft
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
- break mode
- debugging [Debugging SDK], entering break mode
ms.assetid: e9a8a241-cd21-4d4e-999a-283554c288b1
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 25adcc12e6d474899165c1a486fd550f34dd99a4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42678518"
---
# <a name="entering-break-mode"></a>Włączanie trybu przerwania
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [wprowadzania trybu przerwania](https://docs.microsoft.com/visualstudio/extensibility/debugger/entering-break-mode).  
  
Poniżej opisano proces, który występuje w przypadku napotkania punktu przerwania po przechodzenie krok po kroku do funkcji, uruchamianie aż do wiersza kodu źródłowego, który ma kursor w nim lub uruchamianie aż do punktu przerwania.  
  
## <a name="break-mode-process"></a>Proces trybu przerwania  
  
1.  Aparat debugowania (DE) wysyła [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md), [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md), lub dowolne inne zdarzenie zatrzymywania, aby spowodować, że środowisko IDE, aby przejść do trybu przerwania.  
  
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

