---
title: IDebugBoundBreakpoint2 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugBoundBreakpoint2
helpviewer_keywords:
- IDebugBoundBreakpoint2 interface
ms.assetid: df33c52e-ded2-48a0-951d-1f36c8fc922e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a37f637e77c342b3af977884241d0e922ac6aaa6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="idebugboundbreakpoint2"></a>IDebugBoundBreakpoint2
Ten interfejs stanowi punkt przerwania, który jest powiązany z lokalizacji kodu.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugBoundBreakpoint2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Aparat debugowania (DE) implementuje ten interfejs w ramach wsparcia dla punktów przerwania.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Wywołanie [powiązać](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) tworzy tego interfejsu. Wywołuje się [GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md) i [dalej](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md) można również uzyskać tego interfejsu.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 W poniższej tabeli przedstawiono metody `IDebugBoundBreakpoint2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|Pobiera oczekującym punktem przerwania, w którym utworzono określonego powiązania punktu przerwania.|  
|[GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|Pobiera stan tego powiązania punktu przerwania.|  
|[GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)|Pobiera bieżący liczba trafień dla tego powiązania punktu przerwania.|  
|[GetBreakpointResolution](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|Pobiera rozpoznawania punkt przerwania, opisujący ten punkt przerwania.|  
|[Włącz](../../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|Włącza lub wyłącza punktu przerwania.|  
|[SetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-sethitcount.md)|Ustawia liczba trafień dla tego powiązania punktu przerwania.|  
|[SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)|Ustawia lub zmienia warunek skojarzony z tym powiązania punktu przerwania.|  
|[SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md)|Ustawia lub zmiany liczby przebiegu skojarzone z tego powiązania punktu przerwania.|  
|[Usuń](../../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|Usuwa punktu przerwania.|  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md)   
 [Dalej](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)   
 [BIND](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)