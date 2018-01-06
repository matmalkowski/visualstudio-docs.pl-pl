---
title: Procesy | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], processes
ms.assetid: a6a1efdc-b243-40c8-a778-6f69f6b018be
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e69270c5d90c26cf653ee31b81bcb9f453b814e1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="processes"></a>Procesy
Pod względem architektury debugera **procesu**:  
  
-   To kontener dla zestawu programów. Jest ściśle analogiczne do procesu systemu Windows to kontener dla zestawu wątków.  
  
-   Można zidentyfikować samej nazwy, identyfikatora lub identyfikatora fizycznych.  
  
-   Można wyliczyć wszystkie uruchomione programy (i ich wątki).  
  
-   Można opisać, port, który jest uruchomiony w i maszynę, która go zawiera.  
  
-   Można utworzyć jeden lub więcej programów, przerwanie dowolnego programu, który tworzy lub spowodować, że program zatrzymać.  
  
-   Jest reprezentowana przez [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) interfejsu, która jest tworzona po uruchomieniu procesu. Proces jest uruchamiana przez albo sesji debugowania Menedżera (SDM) lub [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).  
  
 Pakiet debugowania można dołączyć aparat debugowania (DE) do procesu przez wywołanie metody [Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md). Oznacza to, że DE dołącza do wszystkich możliwych programom działającym w proces, który może obsługiwać. Na przykład jeśli środowisko uruchomieniowe języka wspólnego DE dołącza do procesu, dołącza tylko do programów uruchamianych kodu zarządzanego.  
  
## <a name="see-also"></a>Zobacz też  
 [Programy](../../extensibility/debugger/programs.md)   
 [Wątki](../../extensibility/debugger/threads.md)   
 [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)   
 [Debugowanie pakietu](../../extensibility/debugger/debug-package.md)   
 [Aparat debugowania](../../extensibility/debugger/debug-engine.md)   
 [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)   
 [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md)