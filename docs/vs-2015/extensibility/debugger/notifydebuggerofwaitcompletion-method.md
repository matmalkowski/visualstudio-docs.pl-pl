---
title: Metoda NotifyDebuggerOfWaitCompletion | Dokumentacja firmy Microsoft
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
- NotifyDebuggerOfWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: 841c5908-4f3f-400b-a7b0-96a95f362817
caps.latest.revision: 6
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4429b89be624960b787b51c3fa085f43e412889e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42678906"
---
# <a name="notifydebuggerofwaitcompletion-method"></a>NotifyDebuggerOfWaitCompletion, metoda
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [metoda NotifyDebuggerOfWaitCompletion](https://docs.microsoft.com/visualstudio/extensibility/debugger/notifydebuggerofwaitcompletion-method).  
  
Metoda symbolu zastępczego używany jako obiekt docelowy punkt przerwania przez debuger. Ta metoda nie może być śródwierszowa lub zoptymalizowane.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Zestaw:** mscorlib (w mscorlib.dll)  
  
## <a name="syntax"></a>Składnia  
  
```vb  
private void NotifyDebuggerOfWaitCompletion()  
```  
  
## <a name="remarks"></a>Uwagi  
 Wszystkie operacje łączenia z zadaniem powinna wywołać tę metodę, jeśli ustawiono bit powiadomienia ich debugera.  
  
## <a name="requirements"></a>Wymagania  
  
## <a name="see-also"></a>Zobacz też  
 [Task — klasa](../../extensibility/debugger/task-class-internal-members.md)

