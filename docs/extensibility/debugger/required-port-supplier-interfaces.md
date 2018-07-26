---
title: Wymagane interfejsy dostawcy portów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- port suppliers, required interfaces
- debugging [Debugging SDK], port suppliers
ms.assetid: 0c2cdd40-9f6f-425e-b305-858f7734161e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1c727cb39b480d72a3e0aa2083ca795bb65ac0ff
ms.sourcegitcommit: 71b307ce86c4079cc7ad686d8d5f96a6a123aadd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/25/2018
ms.locfileid: "39252417"
---
# <a name="required-port-supplier-interfaces"></a>Wymagane interfejsy dostawcy portów
Dostawcy portu musi implementować [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) interfejsu.[ IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)  
  
 Dostawcy portu dostarcza, portów i zaimplementowano je. W związku z tym należy uruchomić następujące interfejsy:  
  
-   [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)  
  
     W tym artykule opisano port i wylicza wszystkie procesy uruchomione na tym porcie.  
  
-   [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md)  
  
     Umożliwia uruchomienie i zakończenie procesów na porcie.  
  
-   [IDebugPortNotify2](../../extensibility/debugger/reference/idebugportnotify2.md)  
  
     Udostępnia mechanizm dla programów uruchomionych w kontekście tego portu do powiadamiania o program węzła tworzenia i niszczenia. Aby uzyskać więcej informacji, zobacz [Program węzłów](../../extensibility/debugger/program-nodes.md).  
  
-   `IConnectionPointContainer`  
  
     Zapewnia punkt połączenia dla [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md).  
  
## <a name="port-supplier-operation"></a>Obsługa dostawcy portu  
 [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md) ujścia odbiera powiadomienia, gdy proces i programy są tworzone i niszczone na porcie. Port jest wymagany do wysłania [IDebugProcessCreateEvent2](../../extensibility/debugger/reference/idebugprocesscreateevent2.md) po utworzeniu procesu i [IDebugProcessDestroyEvent2](../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) kiedy niszczony jest procesem na porcie. Port jest również wymagany do wysłania [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) po utworzeniu programu i [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) gdy program zostanie zniszczony w proces uruchomiony na porcie.  
  
 Port zwykle wysyła program tworzą i niszczą zdarzenia w odpowiedzi na [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) i [RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) metod, odpowiednio.  
  
 Ponieważ portu można uruchomić i zakończyć procesy fizyczne i logiczne programy, następujące interfejsy musi też być implementowany przez aparat debugowania:  
  
-   [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)  
  
     W tym artykule opisano proces fizycznego. Co najmniej należy zaimplementować następujące metody:  
  
    -   [EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)  
  
    -   [Getname —](../../extensibility/debugger/reference/idebugprocess2-getname.md)  
  
    -   [GetServer](../../extensibility/debugger/reference/idebugprocess2-getserver.md)  
  
    -   [GetPhysicalProcessId](../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)  
  
    -   [Getprocessid —](../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)  
  
    -   [GetAttachedSessionName](../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)  
  
-   [IDebugProcessEx2](../../extensibility/debugger/reference/idebugprocessex2.md)  
  
     Zapewnia sposób SDM dołączyć i odłączyć się od procesu.  
  
-   [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)  
  
     W tym artykule opisano logicznych program. Co najmniej należy zaimplementować następujące metody:  
  
    -   [Getname —](../../extensibility/debugger/reference/idebugprogram2-getname.md)  
  
    -   [GetProcess](../../extensibility/debugger/reference/idebugprogram2-getprocess.md)  
  
    -   [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)  
  
-   [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)  
  
     Zapewnia sposób SDM dołączyć do tego programu.  
  
## <a name="see-also"></a>Zobacz także  
 [Implementowanie dostawcy portu](../../extensibility/debugger/implementing-a-port-supplier.md)