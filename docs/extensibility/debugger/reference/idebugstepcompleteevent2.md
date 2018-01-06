---
title: IDebugStepCompleteEvent2 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugStepCompleteEvent2
helpviewer_keywords: IDebugStepCompleteEvent2 interface
ms.assetid: eba2b76e-f90d-486b-ae5c-c47f1b8ba2e5
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: d9b077f4bcfd0f4344c29659791accee36da60c5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugstepcompleteevent2"></a>IDebugStepCompleteEvent2
Ten interfejs jest wysyłane przez aparat debugowania (DE) z menedżerem sesji debugowania (SDM) po zakończeniu debugowanego programu Wkrocz do, Przekrocz nad lub krok zewnętrzne kodu źródłowego lub instrukcji lub instrukcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugStepCompleteEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Niemcy implementuje ten interfejs do zgłaszania zakończenia operacji kroku. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfejs musi zostać wdrożone na tym samym obiekcie danego interfejsu. Używa SDM [QueryInterface](/cpp/atl/queryinterface) dostępu `IDebugEvent2` interfejsu.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Niemcy tworzy i wysyła ten obiekt zdarzenia zgłoszenia ukończeniu operacji kroku. Zdarzenia są wysyłane przy użyciu [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) funkcja wywołania zwrotnego, która jest dostarczana przez SDM, gdy jest on dołączony do debugowanego programu.  
  
## <a name="remarks"></a>Uwagi  
 Po wykonaniu tego kroku debugowanego programu jest wstrzymana raz i IDE aktualizuje jego systemu windows.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy Core](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)