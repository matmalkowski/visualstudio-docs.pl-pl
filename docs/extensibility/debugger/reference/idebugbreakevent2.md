---
title: IDebugBreakEvent2 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugBreakEvent2
helpviewer_keywords:
- IDebugBreakEvent2 interface
ms.assetid: 57dfdbc2-4e68-4dbf-9579-006cd6fb1c62
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 3b58e0fb18b8f41f16a6cc92e682363ff531d5ec
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugbreakevent2"></a>IDebugBreakEvent2
Ten interfejs informuje menedżera debugowania sesji (SDM) pomyślnym ukończeniu asynchronicznego przerwania.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugBreakEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Niemcy implementuje ten interfejs obsługuje podziały użytkownika w programie. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfejs musi zostać wdrożone na tym samym obiekcie danego interfejsu (używa SDM [QueryInterface](/cpp/atl/queryinterface) dostępu `IDebugEvent2` interfejs).  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Wywołania SDM [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) gdy użytkownik zażądał debugowanego do wstrzymania programu. Gdy program został pomyślnie zostały wstrzymane, DE wysyła `IDebugBreakEvent2` zdarzeń. To zdarzenie jest wysyłany przy użyciu [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) dostarczonych przez SDM, gdy jest on dołączony do debugowanego programu funkcja wywołania zwrotnego.  
  
## <a name="remarks"></a>Uwagi  
 Na przykład użytkownik może wybrać **podziału wszystkich** na **debugowania** menu, aby przerwać poza program, który jest uruchomiony w pętli nieskończonej. SDM informuje program przestanie wywołując [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md). Wysyła DE `IDebugBreakEvent2` po finally zatrzymuje program.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)