---
title: Wysyłanie zdarzeń uruchamiania po uruchomieniu | Dokumentacja firmy Microsoft
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
- debugging [Debugging SDK], startup events
ms.assetid: 306ea0b4-6d9e-4871-8d8d-a4032d422940
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 21b98fccac32b50e6aec643a7b69832e65d53dd8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42685273"
---
# <a name="sending-startup-events-after-a-launch"></a>Wysyłanie zdarzeń uruchamiania po uruchomieniu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [wysyłania uruchamiania zdarzenia po Uruchom](https://docs.microsoft.com/visualstudio/extensibility/debugger/sending-startup-events-after-a-launch).  
  
Gdy aparat debugowania (Niemcy) jest dołączony do programu, wysyła szereg zdarzeń uruchamiania powrót do sesji debugowania.  
  
 Zdarzenia uruchamiania wysyłanych z powrotem do sesji debugowania są następujące:  
  
-   Zdarzenie tworzenia aparatu.  
  
-   Zdarzenie tworzenia programu.  
  
-   Wątek, tworzenia i zdarzeń ładowania modułu.  
  
-   Ładowanie ukończone zdarzenie wysyłane, gdy kod jest załadowany i gotowa do uruchomienia, ale przed wykonaniem jakiegokolwiek kodu  
  
    > [!NOTE]
    >  Gdy to zdarzenie jest kontynuowany, zmienne globalne są inicjowane i uruchamianie procedury uruchamiania.  
  
-   Możliwe innych wątków, tworzenia i zdarzeń ładowania modułu.  
  
-   Zdarzenie punktu wejścia sygnalizuje, że program został osiągnięty jego główny punkt wejścia, takich jak **Main** lub `WinMain`. To zdarzenie nie są zwykle wysyłane, jeśli DE dołącza do programu, który jest już uruchomiony.  
  
 Programowo, DE najpierw wysyła Menedżer debugowania sesji (SDM) [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) interfejs, który przedstawia zdarzenie tworzenia aparatu, a następnie [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) , która reprezentuje zdarzenie tworzenia programu.  
  
 To jest zwykle następuje co najmniej jeden [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) wątek zdarzenia tworzenia i [IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md) zdarzeń ładowania modułu.  
  
 Gdy kod jest załadowany i gotowa do uruchomienia, ale przed wykonaniem jakiegokolwiek kodu DE wysyła SDM [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) zdarzenie ukończenia obciążenia. Na koniec, jeśli program nie jest już uruchomiona, wysyła DE [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) zdarzenie punktu wejścia, sygnalizowania, że program osiągnęła jego główny punkt wejścia i jest gotowy do debugowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrola wykonywania](../../extensibility/debugger/control-of-execution.md)   
 [Zadania debugowania](../../extensibility/debugger/debugging-tasks.md)

