---
title: Metoda SetNotificationForWaitCompletion | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SetNotificationForWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: da149c9a-20f4-4543-a29e-429c8c1d2e19
caps.latest.revision: "5"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 385ae98e90d8f3a466c0983405c367347bb8ca10
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="setnotificationforwaitcompletion-method"></a>SetNotificationForWaitCompletion — metoda
Ustawia lub czyści stanu TASK_STATE_WAIT_COMPLETION_NOTIFICATION.  
  
 **Namespace:**<xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Zestaw:** mscorlib (w bibliotece mscorlib.dll)  
  
## <a name="syntax"></a>Składnia  
  
```vb  
internal void SetNotificationForWaitCompletion(bool enabled)  
```  
  
#### <a name="parameters"></a>Parametry  
 `enabled`  
  
 `true`Aby ustawić bit; `false` do nie ustawiono bitu.  
  
## <a name="exceptions"></a>Wyjątki  
  
## <a name="remarks"></a>Uwagi  
 Debuger ustawia tego bit ułatwiające krok poza treści metody asynchronicznej. Jeśli `enabled` jest `true`, ta metoda musi zostać wywołana tylko dla zadania, które nie zostało jeszcze zakończone. Jeśli `enabled` jest `false`, ta metoda może być wywołana dla zadania ukończone. W obu przypadkach można stosować tylko dla zadania zapowiadanego.  
  
## <a name="requirements"></a>Wymagania  
  
## <a name="see-also"></a>Zobacz też  
 [Task — klasa](../../extensibility/debugger/task-class-internal-members.md)