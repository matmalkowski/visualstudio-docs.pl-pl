---
title: IDebugPendingBreakpoint2 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPendingBreakpoint2
helpviewer_keywords:
- IDebugPendingBreakpoint2 interface
ms.assetid: d416b095-917e-475e-b796-ec0a03ffb8da
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3e5e84180747a3e6a3b9e5a34e7694f4cd07867c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="idebugpendingbreakpoint2"></a>IDebugPendingBreakpoint2
Ten interfejs stanowi punkt przerwania, który jest gotowy do powiązania do lokalizacji kodu.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugPendingBreakpoint2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Aparat debugowania (DE) implementuje ten interfejs w ramach wsparcia dla punktów przerwania.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Wywołanie [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) tworzy oczekującym punktem przerwania z [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) interfejsu. Wywołanie [powiązać](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) tworzy `IDebugBreakpoint2` interfejs, który reprezentuje powiązania punktu przerwania w programie.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 W poniższej tabeli przedstawiono metody `IDebugPendingBreakpoint2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Określa, czy ten oczekujący punkt przerwania można powiązać z lokalizacji kodu.|  
|[BIND](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Co najmniej jedna lokalizacja kodu wiąże ten oczekujący punkt przerwania.|  
|[GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|Pobiera stan oczekującego punktu przerwania.|  
|[GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Pobiera żądanie przerwania, który został użyty do utworzenia ten oczekujący punkt przerwania.|  
|[Wirtualizacji](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)|Przełącza stan zwirtualizowanych tego oczekujących punktu przerwania.|  
|[Włącz](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Włącza/wyłącza włączony stan to oczekujących punktu przerwania.|  
|[SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)|Ustawia lub zmienia stan skojarzonego z tą oczekującą punktu przerwania.|  
|[SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)|Ustawia lub zmienia liczba przebiegu skojarzonego z tą oczekującą punktu przerwania.|  
|[EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Wylicza wszystkie punkty przerwania powiązany z tym oczekującym punktem przerwania.|  
|[EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|Wylicza wszystkie punkty przerwania błędów, które powstały w wyniku tego oczekującym punktem przerwania.|  
|[Usuń](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|Usuwa ten oczekujący punkt przerwania i powiązany z niego wszystkie punkty przerwania.|  
  
## <a name="remarks"></a>Uwagi  
 `IDebugPendingBreakpoint2` można traktować jako dostawca wszystkich informacji niezbędnych do powiązania punktu przerwania do kodu, który można zastosować do jednego lub wielu programów.  
  
 Oczekującym punktem przerwania potencjalnie można utworzyć więcej niż jednego powiązania punktu przerwania. Na przykład punkt przerwania w szablonie stylu C++ może utworzyć powiązania punktu przerwania dla każdego unikatowego wystąpienia szablonu.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)   
 [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)   
 [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)   
 [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)