---
title: Kontrola wykonywania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 97071846-007e-450f-95a6-f072d0f5e61e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c9fc47a0b73d07e4b24ef55c736ad80197f282cb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="control-of-execution"></a>Kontrola wykonywania
Aparat debugowania (DE) zwykle wysyła jedną z następujących zdarzeń jako ostatnie zdarzenie uruchomienia:  
  
-   Zdarzenie punktu wejścia, jeśli dołączanie do nowo uruchomionego programu  
  
-   Obciążenia zakończonego zdarzenia, jeśli dołączenie do programu, który jest już uruchomione  
  
 Zdarzenia te są zatrzymywanie zdarzeń, co oznacza, że DE czeka na odpowiedź od użytkownika za pomocą środowiska IDE. Aby uzyskać więcej informacji, zobacz [tryby operacyjne](../../extensibility/debugger/operational-modes.md).  
  
## <a name="stopping-event"></a>Zatrzymywanie zdarzeń  
 Gdy zdarzeniem zatrzymującym jest wysyłana do sesji debugowania:  
  
1.  Program i wątku, który zawiera bieżący wskaźnik instrukcji można uzyskać interfejsu zdarzenia.  
  
2.  IDE określa bieżącego pliku kodu źródłowego i pozycji, które wyświetla podświetlane w edytorze.  
  
3.  Sesja debugowania zazwyczaj odpowiada na to pierwsze zdarzenie zatrzymywania wywołując programu **Kontynuuj** metody.  
  
4.  Następnie program będzie uruchamiany aż do napotkania warunek zatrzymania, aktywując punkt przerwania, w których przypadku DE wysyła zdarzenia punktu przerwania sesji debugowania. Zdarzenie punkt przerwania jest zdarzeniem zatrzymującym i DE ponownie czeka na odpowiedź użytkownika.  
  
5.  Jeśli użytkownik wybiera Wkrocz ponad lub funkcji, IDE monituje sesji debugowania do wywołania programu `Step` metody przekazanie jej przez jednostki kroku (instrukcji, instrukcji lub wiersza) i rodzaj krok — oznacza to, czy Wkrocz powyżej , lub z funkcji. Po zakończeniu tego kroku DE wysyła zdarzenie ukończenia kroku do sesji debugowania, który jest zdarzeniem zatrzymującym.  
  
     —lub—  
  
     Jeśli użytkownik wybiera kontynuuje wykonywanie z bieżącego wskaźnika instrukcji, IDE monituje o sesji debugowania do wywołania programu **Execute** metody. Program wznawia wykonywanie, aż do napotkania dalej warunku zatrzymania.  
  
     —lub—  
  
     Jeśli Ignoruj zdarzeniem zatrzymującym określonej sesji debugowania, sesja debugowania wywołuje program **Kontynuuj** metody. Jeśli program został wykonywanie krok po kroku do, za pośrednictwem lub poza funkcją gdy wystąpił warunek zatrzymania, która kontynuuje kroku.  
  
 Programowo, DE napotka warunek zatrzymania, wysyła takich zdarzeń zatrzymywania jako [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) lub [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) do menedżera sesji debugowania (SDM) za pomocą klasy [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) interfejsu. Przekazuje DE [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) i [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) interfejsów, które reprezentują program i wątku zawierające bieżący wskaźnik instrukcji. Wywołania SDM [IDebugThread2::EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) ramki stosu górnej i wywołania [IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) można pobrać kontekstu dokumentu skojarzone z bieżącej instrukcji wskaźnik. Tego kontekstu dokumentu jest zwykle źródła numer nazwy, wierszy i kolumn o pliku kodu. IDE wykorzystuje te, aby wyróżnić kod źródłowy, który zawiera bieżący wskaźnik instrukcji.  
  
 SDM zazwyczaj odpowiada to pierwsze zdarzenie zatrzymywania, wywołując [IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md). Program będzie uruchamiany następnie aż do napotkania warunek zatrzymania, aktywując punkt przerwania, w którego przypadku DE wysyła [interfejsu IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) do SDM. Zdarzenie punkt przerwania jest zdarzeniem zatrzymującym i DE ponownie czeka na odpowiedź użytkownika.  
  
 Jeśli użytkownik wybiera Wkrocz ponad lub funkcji, IDE monituje SDM wywołać [IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md), przekazanie jej [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) (instrukcji, instrukcji lub wiersza) i [ STEPKIND](../../extensibility/debugger/reference/stepkind.md), oznacza to, czy krok do, za pośrednictwem lub z funkcji. Po zakończeniu tego kroku wysyła DE [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) interfejsu SDM, który jest zdarzeniem zatrzymującym.  
  
 Jeśli użytkownik wybiera kontynuuje wykonywanie z bieżącego wskaźnika instrukcji, IDE zapyta SDM wywołać [IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md). Program wznawia wykonywanie, aż do napotkania dalej warunku zatrzymania.  
  
 Jeśli pakiet debugowania jest zignorowanie zdarzeniem zatrzymującym określonego, pakiet debugowania wywołuje SDM, która wywołuje [IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md). Jeśli program został wykonywanie krok po kroku do, za pośrednictwem lub poza funkcją gdy wystąpił warunek zatrzymania, która kontynuuje kroku. Oznacza to, że program przechowuje stan wykonywania krokowego, dzięki czemu potrafi kontynuować.  
  
 Wywołania SDM powoduje `Step`, **Execute**, i **Kontynuuj** są asynchroniczne, co oznacza, że model SDM oczekuje szybko powrót z wywołania. Jeśli DE wysyła SDM zdarzeniem zatrzymującym w tym samym wątku, przed `Step`, **Execute**, lub **Kontynuuj** zwraca SDM zawiesza się.  
  
## <a name="see-also"></a>Zobacz też  
 [Zadania debugowania](../../extensibility/debugger/debugging-tasks.md)