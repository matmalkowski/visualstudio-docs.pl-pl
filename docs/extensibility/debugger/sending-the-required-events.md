---
title: Wysyłanie zdarzeń wymagane | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], required events
ms.assetid: 08319157-43fb-44a9-9a63-50b919fe1377
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: deeffb814dacc58b1fb3a3f993203139d9b1a081
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31126179"
---
# <a name="sending-the-required-events"></a>Wysyłanie zdarzeń wymagane
Ta procedura służy do wysyłania zdarzeń wymagane.  
  
## <a name="process-for-sending-required-events"></a>Proces do wysyłania zdarzeń wymagane  
 Następujące zdarzenia są wymagane w tej kolejności, gdy tworzenie debugowania aparat (DE) i dołączenie go do programu:  
  
1.  Wyślij [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) zdarzeń obiektu do sesji debugowania Menedżera (SDM) podczas inicjowania DE do debugowania jednego lub wielu programów w procesie.  
  
2.  Gdy program do debugowania jest dołączony do, Wyślij [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) obiekt zdarzenia do SDM. To zdarzenie może być zdarzeniem zatrzymującym, w zależności od projektu aparatu.  
  
3.  Jeśli program jest dołączony do po uruchomieniu procesu, Wyślij [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) obiekt zdarzenia do SDM powiadomiono IDE nowego wątku. To zdarzenie może być zdarzeniem zatrzymującym, w zależności od projektu aparatu.  
  
4.  Wyślij [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) obiekt zdarzenia do SDM, gdy jest debugowany program Zakończono ładowania lub po wykonaniu dołączenie do programu. To zdarzenie musi być zdarzeniem zatrzymującym.  
  
5.  Jeśli aplikacja do debugowania jest uruchamiana, Wyślij [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) obiekt zdarzenia do SDM przy pierwszej instrukcji kodu w czasie wykonywania architektury ma zostać wykonana. To zdarzenie jest zawsze zdarzeniem zatrzymującym. Przy przechodzeniu do sesji debugowania, IDE zatrzymuje się na to zdarzenie.  
  
> [!NOTE]
>  Wiele języków Użyj globalnego inicjatory lub zewnętrznych, wstępnie skompilowanych funkcji (Biblioteka CRT lub elementem _Main) na początku ich kodu. Jeśli język programu debugowania zawiera jedną z następujących typów elementów przed punkt wejścia początkowej, uruchamiać ten kod i jest wysyłane zdarzenie punkt wejścia gdy użytkownika punkt wejścia, takich jak **głównego** lub `WinMain`, zostanie osiągnięty.  
  
## <a name="see-also"></a>Zobacz też  
 [Włączanie debugowania programu](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)