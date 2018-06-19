---
title: Metoda SetNotificationForWaitCompletion | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- SetNotificationForWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: da149c9a-20f4-4543-a29e-429c8c1d2e19
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a005ee7d624604dd716042bd839b48b7a367dd48
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31127021"
---
# <a name="setnotificationforwaitcompletion-method"></a>SetNotificationForWaitCompletion — metoda
Ustawia lub czyści stanu TASK_STATE_WAIT_COMPLETION_NOTIFICATION.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Zestaw:** mscorlib (w bibliotece mscorlib.dll)  
  
## <a name="syntax"></a>Składnia  
  
```vb  
internal void SetNotificationForWaitCompletion(bool enabled)  
```  
  
#### <a name="parameters"></a>Parametry  
 `enabled`  
  
 `true` Aby ustawić bit; `false` do nie ustawiono bitu.  
  
## <a name="exceptions"></a>Wyjątki  
  
## <a name="remarks"></a>Uwagi  
 Debuger ustawia tego bit ułatwiające krok poza treści metody asynchronicznej. Jeśli `enabled` jest `true`, ta metoda musi zostać wywołana tylko dla zadania, które nie zostało jeszcze zakończone. Jeśli `enabled` jest `false`, ta metoda może być wywołana dla zadania ukończone. W obu przypadkach można stosować tylko dla zadania zapowiadanego.  
  
## <a name="requirements"></a>Wymagania  
  
## <a name="see-also"></a>Zobacz też  
 [Task — klasa](../../extensibility/debugger/task-class-internal-members.md)