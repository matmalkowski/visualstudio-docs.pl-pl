---
title: Metoda GetTaskSchedulersForDebugger | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GetTaskSchedulersForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 58aa236a-5ab8-4695-b303-89dffdbcd946
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: a2c657b7cef89871e17af442e41229c2fda0f4b7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="gettaskschedulersfordebugger-method"></a>GetTaskSchedulersForDebugger — metoda
Pobiera tablicę wszystkich <xref:System.Threading.Tasks.TaskScheduler> obiektów, które są obecnie aktywne.  
  
 **Namespace:**<xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Zestaw:** mscorlib (w bibliotece mscorlib.dll)  
  
 Ponieważ nie można uzyskać dostępu do tego wewnętrznego elementu członkowskiego z programu .NET Framework, następującej składni podano języka wspólnego pośredniego (CIL).  
  
## <a name="syntax"></a>Składnia  
  
```  
.method assembly hidebysig static class System.Threading.Tasks.TaskScheduler[] GetTaskSchedulersForDebugger() cil managed  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Tablica wszystkich <xref:System.Threading.Tasks.TaskScheduler> obiektów, które są aktualnie aktywne w tym <xref:System.AppDomain>.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda nie jest bezpieczne dla wątków i nie powinny być używane równocześnie z innymi wystąpieniami <xref:System.Threading.Tasks.TaskScheduler>. Powinien zostać wywołany z debugera, tylko wtedy, gdy debuger wstrzymał inne wątki.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md)