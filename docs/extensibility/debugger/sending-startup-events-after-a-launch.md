---
title: Wysyłanie zdarzeń do uruchomienia po Launch | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], startup events
ms.assetid: 306ea0b4-6d9e-4871-8d8d-a4032d422940
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d6ffd1a47f4d1d82feecb35110151a8b32d7d245
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="sending-startup-events-after-a-launch"></a>Wysyłanie zdarzeń do uruchomienia po Launch
Gdy aparat debugowania (DE) jest dołączony do programu, szereg zdarzenia uruchamiania wysyłane z powrotem do sesji debugowania.  
  
 Następujące zdarzenia uruchamiania wysyłane z powrotem do sesji debugowania:  
  
-   Aparat tworzenia zdarzenia.  
  
-   Zdarzenie tworzenia programu.  
  
-   Wątek, tworzenie i zdarzeń ładowania modułu.  
  
-   Zdarzenie complete obciążenia, wysyłane, jeśli kod jest załadowany i gotowa do uruchomienia, ale przed wykonaniem żadnego kodu  
  
    > [!NOTE]
    >  Gdy to zdarzenie jest kontynuowane, zmienne globalne są inicjowane i uruchamianie procedury uruchamiania.  
  
-   Możliwe innych wątków, tworzenie i zdarzeń ładowania modułu.  
  
-   Zdarzenie punktu wejścia, która sygnalizuje, że program została osiągnięta jego główny punkt wejścia, takich jak **Main** lub `WinMain`. To zdarzenie nie są zwykle wysyłane Jeśli DE dołącza do programu, który jest już uruchomiony.  
  
 Programowo, DE najpierw wysyła Menedżera debugowania sesji (SDM) [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) interfejsu reprezentuje aparatu tworzenia zdarzeń, a następnie [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) , która reprezentuje zdarzenie tworzenia programu.  
  
 To jest zazwyczaj następuje co najmniej jeden [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) zdarzenia Tworzenie wątków i [IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md) zdarzeń ładowania modułu.  
  
 Jeśli kod jest załadowany i gotowa do uruchomienia, ale przed wykonaniem dowolny kod DE wysyła SDM [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) zdarzenie ukończenia ładowania. Na koniec, jeśli program nie jest już uruchomiony, wysyła DE [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) zdarzenie punktu wejścia, sygnalizowania, że program osiągnął swoją główny punkt wejścia i jest gotowy do debugowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrola wykonywania](../../extensibility/debugger/control-of-execution.md)   
 [Zadania debugowania](../../extensibility/debugger/debugging-tasks.md)