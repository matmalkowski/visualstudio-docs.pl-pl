---
title: IDebugBreakpointBoundEvent2 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugBreakpointBoundEvent2
helpviewer_keywords:
- IDebugBreakpointBoundEvent2
ms.assetid: 24ba362e-5be1-481a-b071-e1ebd3cae6e8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 24b965e38a6cf154543a5754870828dde3410a2f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31103230"
---
# <a name="idebugbreakpointboundevent2"></a>IDebugBreakpointBoundEvent2
Ten interfejs informuje menedżera debugowania sesji (SDM) czy oczekującym punktem przerwania pomyślnie powiązano z załadować program.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugBreakpointBoundEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Niemcy implementuje ten interfejs w ramach wsparcia dla punktów przerwania. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfejs musi zostać wdrożone na tym samym obiekcie danego interfejsu (używa SDM [QueryInterface](/cpp/atl/queryinterface) dostępu `IDebugEvent2` interfejs).  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Niemcy tworzy i wysyła ten obiekt zdarzeń, gdy oczekującym punktem przerwania pomyślnie jest powiązana z debugowany program. Zdarzenia są wysyłane przy użyciu [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) dostarczonych przez SDM, gdy jest on dołączony do debugowanego programu funkcja wywołania zwrotnego.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 W poniższej tabeli przedstawiono metody `IDebugBreakpointBoundEvent2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)|Pobiera oczekującym punktem przerwania, jest powiązane.|  
|[EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)|Tworzy moduł wyliczający punktów przerwania, które były powiązane tego zdarzenia.|  
  
## <a name="remarks"></a>Uwagi  
 Zawsze, gdy punkt przerwania jest powiązany, zdarzenia są wysyłane do SDM. Jeśli nie można powiązać punktu przerwania, [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) wysłane, a w przeciwnym razie `IDebugBreakpointBoundEvent2` są wysyłane.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)