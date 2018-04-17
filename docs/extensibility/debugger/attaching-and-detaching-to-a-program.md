---
title: Dołączanie i odłączanie programu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
- debug engines, detaching from programs
ms.assetid: 79dcbb9b-c7f8-40fc-8a00-f37fe1934f51
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ca1eab8c6b5e1edc2354ea5f2dfd8922bb7cae16
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="attaching-and-detaching-to-a-program"></a>Dołączanie i odłączanie do programu
Dołączanie debugera wymaga wysyłania prawidłowej sekwencji metod i zdarzeń z odpowiednich atrybutów.  
  
## <a name="sequence-of-methods-and-events"></a>Sekwencja metod i zdarzeń  
  
1.  Wywołuje Menedżera debugowania sesji (SDM) [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) metody.  
  
     Oparte na modelu procesu (DE) Aparat debugowania, `IDebugProgramNodeAttach2::OnAttach` metoda zwraca jedną z następujących metod, które określa, co dalej.  
  
     Jeśli `S_FALSE` jest zwracany, aparat debugowania został pomyślnie dołączony do programu. W przeciwnym razie [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) metoda jest wywoływana w celu ukończenia procesu dołączania.  
  
     Jeśli `S_OK` jest zwracany, DE ma być załadowany w tym samym procesie jako SDM. SDM wykonuje następujące zadania:  
  
    1.  Wywołania [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) można pobrać informacji aparat DE.  
  
    2.  Tworzy wspólnie DE.  
  
    3.  Wywołania [dołączyć](../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
2.  Wysyła DE [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) do SDM z `EVENT_SYNC` atrybutu.  
  
3.  Wysyła DE [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) do SDM z `EVENT_SYNC` atrybutu.  
  
4.  Wysyła DE [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) do SDM z `EVENT_SYNC_STOP` atrybutu.  
  
 Odłączanie od programu jest proste, dwuetapowy proces:  
  
1.  Wywołania SDM [Detach](../../extensibility/debugger/reference/idebugprogram2-detach.md).  
  
2.  Wysyła DE [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wywoływanie zdarzeń debugera](../../extensibility/debugger/calling-debugger-events.md)