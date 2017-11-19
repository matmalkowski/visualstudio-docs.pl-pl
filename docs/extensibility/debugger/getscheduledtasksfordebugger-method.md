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
ms.openlocfilehash: 0f3099cdbcc8c49c7b6cb5064efad240ea32dea4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
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