---
title: Uruchamianie debugera | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], launching the debugger
- debugger [Debugging SDK], launching
ms.assetid: f24da1a1-f923-48b4-989f-18a22b581d1b
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 23fd772b74c4caafbde37541933c38e306f9dc75
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="launching-the-debugger"></a>Uruchamianie debugera
Uruchamianie debugera wymaga wysyłania prawidłowej sekwencji metod i zdarzeń o ich odpowiednich atrybutów.  
  
## <a name="sequences-of-methods-and-events"></a>Sekwencje metod i zdarzeń  
  
1.  Menedżer debugowania sesji (SDM) jest wywoływana przez wybranie **debugowania** menu, a następnie wybierając **Start**. Zobacz [uruchomienia programu](../../extensibility/debugger/launching-a-program.md) Aby uzyskać więcej informacji.  
  
2.  Wywołania SDM [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) metody.  
  
3.  Oparte na modelu procesu (DE) Aparat debugowania, `IDebugProgramNodeAttach2::OnAttach` metoda zwraca jedną z następujących metod, które określa, co dalej.  
  
     Jeśli `S_FALSE` jest zwracany, aparat debugowania (DE) ma zostać załadowany w trakcie maszyny wirtualnej.  
  
     —lub—  
  
     Jeśli `S_OK` jest zwracany, DE ma być załadowany wewnątrzprocesowe SDM. SDM następnie wykonuje następujące zadania:  
  
    1.  Wywołania [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) można pobrać informacji aparat DE.  
  
    2.  Tworzy wspólnie DE.  
  
    3.  Wywołania [dołączyć](../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
4.  Wysyła DE [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) do SDM z `EVENT_SYNC` atrybutu.  
  
5.  Wysyła DE [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) do SDM z `EVENT_SYNC` atrybutu.  
  
6.  Wysyła DE [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) do SDM z `EVENT_SYNC` atrybutu.  
  
7.  Wysyła DE [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) do SDM z `EVENT_SYNC` atrybutu.  
  
8.  Wysyła DE [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) do SDM z `EVENT_SYNC` atrybutu.  
  
## <a name="see-also"></a>Zobacz też  
 [Wywoływanie zdarzeń debugera](../../extensibility/debugger/calling-debugger-events.md)   
 [Uruchamianie programu](../../extensibility/debugger/launching-a-program.md)