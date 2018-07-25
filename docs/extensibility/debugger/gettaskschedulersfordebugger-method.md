---
title: Metoda GetTaskSchedulersForDebugger | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- GetTaskSchedulersForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 58aa236a-5ab8-4695-b303-89dffdbcd946
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4dc8e43629eab80dc3164813d0b8d0f380e8f86a
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2018
ms.locfileid: "39231188"
---
# <a name="gettaskschedulersfordebugger-method"></a>GetTaskSchedulersForDebugger, metoda
Pobiera tablicę wszystkich <xref:System.Threading.Tasks.TaskScheduler> obiektów, które są aktualnie aktywne.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Zestaw:** mscorlib (w *mscorlib.dll*)  
  
 Ponieważ nie można uzyskać dostępu do tego elementu wewnętrznego z programu .NET Framework, następującej składni znajduje się w typowych Intermediate Language (CIL).  
  
## <a name="syntax"></a>Składnia  
  
```csharp  
.method assembly hidebysig static class System.Threading.Tasks.TaskScheduler[] GetTaskSchedulersForDebugger() cil managed  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Tablica wszystkich <xref:System.Threading.Tasks.TaskScheduler> obiekty, które są aktualnie aktywne, w tym <xref:System.AppDomain>.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda nie jest bezpieczny dla wątków i nie należy jej używać równocześnie z innymi wystąpieniami <xref:System.Threading.Tasks.TaskScheduler>. Tę metodę można wywołać z debugera, tylko wtedy, gdy jest debugera wstrzymał inne wątki.  
  
## <a name="see-also"></a>Zobacz także  
 [TaskScheduler, klasa](../../extensibility/debugger/taskscheduler-class-internal-members.md)