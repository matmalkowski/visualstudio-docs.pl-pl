---
title: Pole TASK_STATE_WAITING_ON_CHILDREN | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: TASK_STATE_WAITING_ON_CHILDREN field, Task class [.NET Framework debug engines]
ms.assetid: 6f26b098-84ad-4f6e-ba27-6136581ba630
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e4ac804160bcbdebfd951c4b281def7eb25265b2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="taskstatewaitingonchildren-field"></a>Pole TASK_STATE_WAITING_ON_CHILDREN
Zadanie zakończono wykonywanie swojego delegata i niejawnie oczekuje na ukończenie zadań podrzędnych dołączone.  
  
 **Namespace:**<xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Zestaw:** mscorlib (w bibliotece mscorlib.dll)  
  
 Ponieważ nie można uzyskać dostępu do tego wewnętrznego elementu członkowskiego z programu .NET Framework, następującej składni podano języka wspólnego pośredniego (CIL).  
  
## <a name="syntax"></a>Składnia  
  
```  
.field static assembly literal int32 TASK_STATE_WAITING_ON_CHILDREN = int32(0x01000000)  
```  
  
## <a name="remarks"></a>Uwagi  
 Jeśli [m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) pole zawiera wartość ta <xref:System.Threading.Tasks.Task.Status%2A> zwraca właściwość <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>.  
  
## <a name="see-also"></a>Zobacz też  
 [Task — klasa](../../extensibility/debugger/task-class-internal-members.md)