---
title: Metoda GetScheduledTasksForDebugger | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- GetScheduledTasksForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 7c9b4cde-6e4a-4cef-929f-7d02b1da5762
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 20cde88083acd38df780468927faec5fbd142b67
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31100315"
---
# <a name="getscheduledtasksfordebugger-method"></a>GetScheduledTasksForDebugger — metoda
Pobiera tablicę wszystkich zaplanowanych zadań.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
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