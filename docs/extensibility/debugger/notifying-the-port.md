---
title: Port powiadamiania | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: ports, notification
ms.assetid: f9fce48e-7d4e-4627-a0fb-77b75428146a
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 154a5891d9a11dd77c92f3f297a2e905d40f0327
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="notifying-the-port"></a>Port powiadamiania
Po uruchomieniu programu, numer portu musi otrzymać powiadomienie, w następujący sposób:  
  
1.  Port odebrania nowego węzła programu wysyła zdarzenie tworzenia programu do sesji debugowania. Zdarzenie niesie ze sobą interfejs, który reprezentuje program.  
  
2.  Program identyfikatora aparat debugowania (DE), który można dołączyć do wysyła zapytanie do sesji debugowania.  
  
3.  Sesji debugowania sprawdza, czy DE znajduje się na liście dopuszczalnych DEs dla tego programu. Sesja debugowania pobiera tej listy z ustawień programu active rozwiązania, pierwotnie przekazana do niej przez pakiet debugowania.  
  
     Niemcy musi znajdować się na liście dopuszczalna, w przeciwnym razie DE nie zostanie dołączony do programu.  
  
 Programowo, kiedy port otrzymuje najpierw nowy węzeł program, tworzy [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) interfejs do reprezentowania program.  
  
> [!NOTE]
>  To nie należy mylić z `IDebugProgram2` interfejsu później utworzone przez aparat debugowania (DE).  
  
 Port wysyła [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) zdarzeń tworzenia program do menedżera sesji debugowania (SDM) za pomocą COM `IConnectionPoint` interfejsu.  
  
> [!NOTE]
>  To nie należy mylić z `IDebugProgramCreateEvent2` interfejsu, który jest wysyłany później przez Niemcy.  
  
 Wraz z interfejsu zdarzenia za pomocą samej siebie, wysyła port [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md), [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md), i [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) interfejsy, które reprezentują port, przetwarzanie, i Program, odpowiednio. Wywołania SDM [IDebugProgram2::GetEngineInfo](../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md) można uzyskać identyfikatora GUID DE, który można zdebugować program. Identyfikator GUID pierwotnie został uzyskany z [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) interfejsu.  
  
 SDM sprawdza, czy DE jest na liście dopuszczalnych DEs. SDM pobiera tej listy z ustawień programu active rozwiązania, pierwotnie przekazana do niej przez pakiet debugowania. Niemcy musi znajdować się na liście dopuszczalna, w przeciwnym razie nie można dołączyć do programu.  
  
 Po tożsamość DE jest znana, SDM jest gotowy do dołączenie go do programu.  
  
## <a name="see-also"></a>Zobacz też  
 [Uruchamianie programu](../../extensibility/debugger/launching-a-program.md)   
 [Dołączanie po Launch](../../extensibility/debugger/attaching-after-a-launch.md)   
 [Zadania debugowania](../../extensibility/debugger/debugging-tasks.md)