---
title: "Wymagany Port dostawcy interfejsów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- port suppliers, required interfaces
- debugging [Debugging SDK], port suppliers
ms.assetid: 0c2cdd40-9f6f-425e-b305-858f7734161e
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: ab243886341d720045fc2d1fbd7a813b7d81c9e5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="required-port-supplier-interfaces"></a>Wymagany Port dostawcy interfejsów
Port dostawca musi implementować [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) interfejsu.[ IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)  
  
 Ponieważ dostawca portu udostępnia porty, musi on również implementować ich. W związku z tym musi on implementować następujące interfejsy:  
  
-   [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)  
  
     Zawiera opis portu i można wyliczyć wszystkich procesów działających na porcie.  
  
-   [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md)  
  
     Umożliwia uruchamianie i kończenie procesów na porcie.  
  
-   [IDebugPortNotify2](../../extensibility/debugger/reference/idebugportnotify2.md)  
  
     Udostępnia mechanizm programom działającym w kontekście tego portu do powiadamiania o program węzła tworzenie i likwidacja. Aby uzyskać więcej informacji, zobacz [węzłów programu](../../extensibility/debugger/program-nodes.md).  
  
-   `IConnectionPointContainer`  
  
     Udostępnia punkt połączenia dla [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md).  
  
## <a name="port-supplier-operation"></a>Obsługa dostawcy portu  
 [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md) zbiornika odbiera powiadomienia, gdy proces i programy są tworzone i niszczone na porcie. Port jest wymagany do wysłania [IDebugProcessCreateEvent2](../../extensibility/debugger/reference/idebugprocesscreateevent2.md) utworzenia procesu i [IDebugProcessDestroyEvent2](../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) podczas procesu zostanie zniszczony na porcie. Port jest również wymagany do wysłania [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) po utworzeniu programu i [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) gdy program zostanie zniszczony w procesu uruchomionego na porcie.  
  
 Port zazwyczaj program wysyła tworzone i zniszcz zdarzenia w odpowiedzi na [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) i [RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) metod, odpowiednio.  
  
 Port można uruchomić i przerwanie zarówno procesy fizyczne i logiczne programy, dlatego te interfejsy również musi być implementowana przez aparat debugowania:  
  
-   [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)  
  
     W tym artykule opisano proces fizycznej. Co najmniej musi być implementowana następujących metod:  
  
    -   [EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)  
  
    -   [GetName](../../extensibility/debugger/reference/idebugprocess2-getname.md)  
  
    -   [GetServer](../../extensibility/debugger/reference/idebugprocess2-getserver.md)  
  
    -   [GetPhysicalProcessId](../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)  
  
    -   [GetProcessId](../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)  
  
    -   [GetAttachedSessionName](../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)  
  
-   [IDebugProcessEx2](../../extensibility/debugger/reference/idebugprocessex2.md)  
  
     Umożliwia SDM do dołączania i odłączania się z procesem.  
  
-   [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)  
  
     Zawiera opis programu logiczne. Co najmniej musi być implementowana następujących metod:  
  
    -   [GetName](../../extensibility/debugger/reference/idebugprogram2-getname.md)  
  
    -   [GetProcess](../../extensibility/debugger/reference/idebugprogram2-getprocess.md)  
  
    -   [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)  
  
-   [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)  
  
     Umożliwia SDM można dołączyć do tego programu.  
  
## <a name="see-also"></a>Zobacz też  
 [Implementowanie dostawcy portu](../../extensibility/debugger/implementing-a-port-supplier.md)