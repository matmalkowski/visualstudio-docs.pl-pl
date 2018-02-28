---
title: m_stateObject pola | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- m_stateObject field, Task class [.NET Framework debug engines]
ms.assetid: 68c54b22-3e1c-4031-b9c7-b972c519d8a0
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 9638be7b2f3f3a6c235a4768cdb493fea701a4dd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="mstateobject-field"></a>m_stateObject pola
Obiekt, który reprezentuje dane, które będzie używane przez akcję.  
  
 **Namespace:**<xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Zestaw:** mscorlib (w bibliotece mscorlib.dll)  
  
 Ponieważ nie można uzyskać dostępu do tego wewnętrznego elementu członkowskiego z programu .NET Framework, następującej składni podano języka wspólnego pośredniego (CIL).  
  
## <a name="syntax"></a>Składnia  
  
```  
.field assembly object m_stateObject  
```  
  
## <a name="remarks"></a>Uwagi  
 Jest to `state` parametru w <xref:System.Threading.Tasks.Task.%23ctor%2A> konstruktora. Istnieje również pole zapasowe dla <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=fullName> właściwości.  
  
## <a name="see-also"></a>Zobacz też  
 [Task — klasa](../../extensibility/debugger/task-class-internal-members.md)