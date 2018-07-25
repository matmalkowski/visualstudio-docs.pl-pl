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
ms.openlocfilehash: 648d48f34681865a34654ed9f82bd790d77b2395
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2018
ms.locfileid: "39231167"
---
# <a name="getscheduledtasksfordebugger-method"></a>GetScheduledTasksForDebugger, metoda
Pobiera tablicę wszystkich zaplanowanych zadań.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Zestaw:** mscorlib (w *mscorlib.dll*)  
  
 Ponieważ nie można uzyskać dostępu do tego elementu wewnętrznego z programu .NET Framework, następującej składni znajduje się w typowych Intermediate Language (CIL).  
  
## <a name="syntax"></a>Składnia  
  
```csharp  
.method assembly hidebysig instance class System.Threading.Tasks.Task[] GetScheduledTasksForDebugger() cil managed  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Tablica wszystkich zaplanowanych zadań. Każde zadanie podrzędne jest wykonywanie lub zakończenia.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda nie jest bezpieczny dla wątków i nie należy jej używać równocześnie z innymi wystąpieniami <xref:System.Threading.Tasks.TaskScheduler>. Tę metodę można wywołać z debugera, tylko wtedy, gdy jest debugera wstrzymał inne wątki.  
  
## <a name="see-also"></a>Zobacz także  
 [TaskScheduler, klasa](../../extensibility/debugger/taskscheduler-class-internal-members.md)