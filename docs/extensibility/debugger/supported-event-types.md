---
title: "Obsługiwane typy zdarzeń | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], supported events
ms.assetid: a3c0386d-551e-4734-9a0c-368d1c2e6671
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: d161b078e4001ea7f02311bbcefe4c7f1eb6b7b5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="supported-event-types"></a>Typy obsługiwane zdarzeń
Obecnie debugowania programu Visual Studio obsługuje następujące typy zdarzeń:  
  
-   Zdarzenia asynchroniczne  
  
     Powiadamia menedżera debugowania sesji (SDM) i IDE, który zmienia stan debugowanej aplikacji. Te zdarzenia są przetwarzane w wolnym SDM i IDE. Brak odpowiedzi są wysyłane do aparatu debugowania (DE), po przetworzeniu zdarzenia. [IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md) i [IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md) interfejsy są przykładem zdarzenia asynchroniczne.  
  
-   Zdarzenia synchroniczne  
  
     Powiadom SDM i IDE, który zmienia stan debugowanej aplikacji. Jedyną różnicą między te zdarzenia i asynchroniczne jest, że odpowiedzi są przesyłane za pomocą klasy [ContinueFromSynchronousEvent](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md) metody.  
  
     Wysyłanie zdarzeń synchroniczne jest przydatne w przypadku sieci DE, aby kontynuować przetwarzanie po IDE odbiera i przetwarza zdarzenia.  
  
-   Synchroniczne zatrzymywanie zdarzenia lub zatrzymywanie zdarzenia  
  
     Powiadom SDM i IDE debugowanej aplikacji została zatrzymana, wykonywanie kodu. Podczas wysyłania zdarzeń zatrzymywania metodą [zdarzeń](../../extensibility/debugger/reference/idebugeventcallback2-event.md), [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) parametr jest wymagany. Trwa zatrzymywanie zdarzenia są nadal przez wywołanie do jednej z następujących metod:  
  
    -   [Wykonanie](../../extensibility/debugger/reference/idebugprogram2-execute.md)  
  
    -   [Krok](../../extensibility/debugger/reference/idebugprogram2-step.md)  
  
    -   [Kontynuuj](../../extensibility/debugger/reference/idebugprogram2-continue.md)  
  
     Interfejsy [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) i [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) podano przykłady zatrzymywania zdarzeń.  
  
    > [!NOTE]
    >  Zdarzenia asynchroniczne zatrzymywania nie są obsługiwane. Jest błąd, aby wysyłać Zdarzenie asynchroniczne zatrzymywania.  
  
## <a name="discussion"></a>Omówienie  
 Rzeczywista implementacja zdarzeń zależy od projektu z DE. Typ każdego zdarzenia wysyłane jest określany przez jego atrybuty, które są ustawiane podczas projektowania DE. Na przykład może wysłać jeden DE [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) jako zdarzenie asynchroniczne, podczas gdy inny może wysłać zdarzenie zatrzymania.  
  
 W poniższej tabeli określono, które program i wątku parametry są wymagane dla których zdarzenia, a także typy zdarzeń. Wszystkie zdarzenia może być synchroniczne. Żadne zdarzenie musi być synchroniczne.  
  
> [!NOTE]
>  [IDebugEngine2](../../extensibility/debugger/reference/idebugengine2.md) interfejsu jest wymagany dla wszystkich zdarzeń.  
  
|Zdarzenie|IDebugProgram2|IDebugThread2|Zatrzymywanie zdarzenia|  
|-----------|--------------------|-------------------|---------------------|  
|[IDebugActivateDocumentEvent2](../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|Dozwolone, ale nie jest wymagane|Dozwolone, ale nie jest wymagane|Nie|  
|[IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md)|Wymagane|Wymagane|Tak|  
|[IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|Dozwolone, ale nie jest wymagane|Dozwolone, ale nie jest wymagane|Nie|  
|[IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|Dozwolone, ale nie jest wymagane|Dozwolone, ale nie jest wymagane|Nie|  
|[IDebugBreakpointUnboundEvent2](../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|Dozwolone, ale nie jest wymagane|Dozwolone, ale nie jest wymagane|Nie|  
|[IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)|Wymagane|Wymagane|Tak|  
|[IDebugCanStopEvent2](../../extensibility/debugger/reference/idebugcanstopevent2.md)|Wymagane|Wymagane|Nie|  
|[IDebugDocumentTextEvents2](../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|Niedozwolone|Niedozwolone|Nie|  
|[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)|Niedozwolone|Niedozwolone|Nie|  
|[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)|Wymagane|Wymagane|Tak|  
|[IDebugErrorEvent2](../../extensibility/debugger/reference/idebugerrorevent2.md)|Dozwolone, ale nie jest wymagane|Dozwolone, ale nie jest wymagane|Może być|  
|[IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)|Wymagane|Wymagane|Tak|  
|[IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|Dozwolone, ale nie jest wymagane|Dozwolone, ale nie jest wymagane|Może być|  
|[IDebugInterceptExceptionCompleteEvent2](../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|Wymagane|Wymagane|Tak|  
|[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|Wymagane|Wymagane|Tak|  
|[IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md)|Dozwolone, ale nie jest wymagane|Dozwolone, ale nie jest wymagane|Może być|  
|[IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|Wymagane|Dozwolone, ale nie jest wymagane|Nie|  
|[IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md)|Dozwolone, ale nie jest wymagane|Dozwolone, ale nie jest wymagane|Nie|  
|[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|Wymagane|Dozwolone, ale nie jest wymagane|Nie|  
|[IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|Wymagane|Dozwolone, ale nie jest wymagane|Nie|  
|[IDebugPropertyCreateEvent2](../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|Wymagane|Dozwolone, ale nie jest wymagane|Nie|  
|[IDebugPropertyDestroyEvent2](../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|Wymagane|Dozwolone, ale nie jest wymagane|Nie|  
|[IDebugReturnValueEvent2](../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|Dozwolone, ale nie jest wymagane|Dozwolone, ale nie jest wymagane|Nie|  
|IDebugStopCompleteEvent2|Wymagane|Wymagane|Tak|  
|[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|Wymagane|Wymagane|Tak|  
|[IDebugSymbolSearchEvent2](../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|Dozwolone, ale nie jest wymagane|Dozwolone, ale nie jest wymagane|Nie|  
|[IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|Wymagane|Wymagane|Nie|  
|[IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|Wymagane|Wymagane|Nie|  
|[IDebugThreadNameChangedEvent2](../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|Dozwolone, ale nie jest wymagane|Dozwolone, ale nie jest wymagane|Nie|  
  
## <a name="see-also"></a>Zobacz też  
 [Wysyłanie zdarzeń](../../extensibility/debugger/sending-events.md)