---
title: Metoda GetTaskSchedulersForDebugger | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: GetTaskSchedulersForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 58aa236a-5ab8-4695-b303-89dffdbcd946
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 474d809f36d21b254dbb8bf302cd21bc83db88a9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
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