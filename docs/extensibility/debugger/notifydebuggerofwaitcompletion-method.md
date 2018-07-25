---
title: Metoda NotifyDebuggerOfWaitCompletion | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- NotifyDebuggerOfWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: 841c5908-4f3f-400b-a7b0-96a95f362817
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1288034f171c56e78f17d02f39843cf4ff600e5e
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2018
ms.locfileid: "39233103"
---
# <a name="notifydebuggerofwaitcompletion-method"></a>Metoda NotifyDebuggerOfWaitCompletion
Metoda symbolu zastępczego używany jako obiekt docelowy punkt przerwania przez debuger. Ta metoda nie może być śródwierszowa lub zoptymalizowane.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Zestaw:** mscorlib (w *mscorlib.dll*)  
  
## <a name="syntax"></a>Składnia  
  
```vb  
private void NotifyDebuggerOfWaitCompletion()  
```  
  
## <a name="remarks"></a>Uwagi  
 Wszystkie operacje łączenia z zadaniem powinna wywołać tę metodę, jeśli ustawiono bit powiadomienia ich debugera.  
  
## <a name="requirements"></a>Wymagania  
  
## <a name="see-also"></a>Zobacz także  
 [Task — klasa](../../extensibility/debugger/task-class-internal-members.md)