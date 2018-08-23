---
title: Metoda GetScheduledTasksForDebugger | Dokumentacja firmy Microsoft
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
- GetScheduledTasksForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 7c9b4cde-6e4a-4cef-929f-7d02b1da5762
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bf2649dbb3e2a4b5cd614f078c461217044ee08b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42682161"
---
# <a name="getscheduledtasksfordebugger-method"></a>GetScheduledTasksForDebugger, metoda
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [metoda GetScheduledTasksForDebugger](https://docs.microsoft.com/visualstudio/extensibility/debugger/getscheduledtasksfordebugger-method).  
  
Pobiera tablicę wszystkich zaplanowanych zadań.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Zestaw:** mscorlib (w mscorlib.dll)  
  
 Ponieważ nie można uzyskać dostępu do tego elementu wewnętrznego z programu .NET Framework, następującej składni znajduje się w typowych Intermediate Language (CIL).  
  
## <a name="syntax"></a>Składnia  
  
```  
.method assembly hidebysig instance class System.Threading.Tasks.Task[] GetScheduledTasksForDebugger() cil managed  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Tablica wszystkich zaplanowanych zadań. Każde zadanie podrzędne jest wykonywanie lub zakończenia.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda nie jest bezpieczny dla wątków i nie powinny być używane równocześnie z innymi wystąpieniami <xref:System.Threading.Tasks.TaskScheduler> powinna być wywoływana z debugera tylko wtedy, gdy jest debugera wstrzymał inne wątki.  
  
## <a name="see-also"></a>Zobacz też  
 [TaskScheduler, klasa](../../extensibility/debugger/taskscheduler-class-internal-members.md)

