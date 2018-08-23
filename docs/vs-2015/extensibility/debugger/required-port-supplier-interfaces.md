---
title: Wymagane interfejsy dostawcy portów | Dokumentacja firmy Microsoft
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
- port suppliers, required interfaces
- debugging [Debugging SDK], port suppliers
ms.assetid: 0c2cdd40-9f6f-425e-b305-858f7734161e
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 960cd5668fe49ba50e79f036848948ec8e0bbfc2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42680540"
---
# <a name="required-port-supplier-interfaces"></a>Wymagane interfejsy dostawcy portów
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [wymagane interfejsy dostawcy portów](https://docs.microsoft.com/visualstudio/extensibility/debugger/required-port-supplier-interfaces).  
  
Dostawcy portu musi implementować [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) interfejsu.[ IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)  
  
 Ponieważ dostawcy portu dostarcza, portów, musi on również implementować ich. W związku z tym musi on implementować następujących interfejsów:  
  
-   [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)  
  
     W tym artykule opisano port i można wyliczyć wszystkie procesy uruchomione na tym porcie.  
  
-   [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md)  
  
     Umożliwia uruchomienie i zakończenie procesów na porcie.  
  
-   [IDebugPortNotify2](../../extensibility/debugger/reference/idebugportnotify2.md)  
  
     Udostępnia mechanizm dla programów uruchomionych w kontekście tego portu do powiadamiania o program węzła tworzenia i niszczenia. Aby uzyskać więcej informacji, zobacz [węzły programu](../../extensibility/debugger/program-nodes.md).  
  
-   `IConnectionPointContainer`  
  
     Zapewnia punkt połączenia dla [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md).  
  
## <a name="port-supplier-operation"></a>Obsługa dostawcy portu  
 [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md) ujścia odbiera powiadomienia, gdy proces i programy są tworzone i niszczone na porcie. Port jest wymagany do wysłania [IDebugProcessCreateEvent2](../../extensibility/debugger/reference/idebugprocesscreateevent2.md) po utworzeniu procesu i [IDebugProcessDestroyEvent2](../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) kiedy niszczony jest procesem na porcie. Port jest również wymagany do wysłania [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) po utworzeniu programu i [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) gdy program zostanie zniszczony w proces uruchomiony na porcie.  
  
 Port zwykle wysyła program tworzą i niszczą zdarzenia w odpowiedzi na [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) i [RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) metod, odpowiednio.  
  
 Port można uruchomić, a następnie zakończyć procesy fizyczne i logiczne programów, dlatego te interfejsy musi też być implementowany przez aparat debugowania:  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Implementowanie dostawcy portu](../../extensibility/debugger/implementing-a-port-supplier.md)

