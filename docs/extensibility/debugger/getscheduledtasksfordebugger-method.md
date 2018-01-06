---
title: Metoda GetScheduledTasksForDebugger | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: GetScheduledTasksForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 7c9b4cde-6e4a-4cef-929f-7d02b1da5762
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 1c27bd57684fc0a4de0bf56bcc8db9a5561f7d1f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="getscheduledtasksfordebugger-method"></a>GetScheduledTasksForDebugger — metoda
Pobiera tablicę wszystkich zaplanowanych zadań.  
  
 **Namespace:**<xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Zestaw:** mscorlib (w bibliotece mscorlib.dll)  
  
 Ponieważ nie można uzyskać dostępu do tego wewnętrznego elementu członkowskiego z programu .NET Framework, następującej składni podano języka wspólnego pośredniego (CIL).  
  
## <a name="syntax"></a>Składnia  
  
```  
.method assembly hidebysig instance class System.Threading.Tasks.Task[] GetScheduledTasksForDebugger() cil managed  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Tablica wszystkich zaplanowanych zadań. Każde zadanie jest wykonywane lub Zakończono wykonywanie.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda nie jest bezpieczne dla wątków i nie powinny być używane równocześnie z innymi wystąpieniami <xref:System.Threading.Tasks.TaskScheduler> go powinna być wywoływana z debugera tylko wtedy, gdy debuger wstrzymał inne wątki.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md)