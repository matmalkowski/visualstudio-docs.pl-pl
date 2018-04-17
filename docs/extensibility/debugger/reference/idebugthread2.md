---
title: IDebugThread2 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugThread2
helpviewer_keywords:
- IDebugThread2 interface
ms.assetid: 221b4b1b-4a26-466e-bc29-5eff800fab13
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d93744e55a3e516a131e772fd2df09da5ec23168
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="idebugthread2"></a>IDebugThread2
Ten interfejs reprezentuje wątek uruchomiony w programie.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugThread2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Aparat debugowania (DE) implementuje ten interfejs do reprezentowania wykonanie w jednym programie wątku.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Wywołanie [GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md) uzyskać ten interfejs reprezentujący aktywnego wątku.  
  
 Ten interfejs jest również używany podczas tworzenia żądania przerwania (zobacz [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)).  
  
 Ten interfejs jest także zwracany w trakcie rozwiązywania granicę lub błąd punktu przerwania (zobacz [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) i [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)).  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 W poniższej tabeli przedstawiono metody `IDebugThread2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)|Pobiera listę ramek stosu dla tego wątku.|  
|[GetName](../../../extensibility/debugger/reference/idebugthread2-getname.md)|Pobiera nazwę wątku.|  
|[Setthreadname —](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)|Ustawia nazwę wątku.|  
|[GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)|Pobiera program, w którym jest uruchomiony wątek.|  
|[CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)|Określa, czy kontekst stosu danego ramki i kodu można ustawić następnej instrukcji.|  
|[SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)|Ustawia następną instrukcję do danego stosu kontekstu ramki i kod.|  
|[GetThreadId](../../../extensibility/debugger/reference/idebugthread2-getthreadid.md)|Pobiera identyfikator wątku systemu.|  
|[Wstrzymaj](../../../extensibility/debugger/reference/idebugthread2-suspend.md)|Wstrzymuje wątku.|  
|[Wznów](../../../extensibility/debugger/reference/idebugthread2-resume.md)|Wznawia wątku.|  
|[GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)|Pobiera właściwości, które opisują wątku.|  
|[GetLogicalThread](../../../extensibility/debugger/reference/idebugthread2-getlogicalthread.md)|Pobiera logicznego wątku skojarzone z tym wątku fizycznym.|  
  
## <a name="remarks"></a>Uwagi  
 Ponieważ pojedynczego wątku fizycznym można uruchomić w wielu programach więcej niż jeden `IDebugThread2` z więcej niż jeden program może reprezentować tego samego wątku fizycznym.  
  
 Gdy punkt przerwania lub wyjątek występuje, zdarzenia są wysyłane przez wywołanie metody [zdarzeń](../../../extensibility/debugger/reference/idebugeventcallback2-event.md). Jeden z argumentów dla tej metody jest `IDebugThread2` interfejs reprezentujący bieżącego wątku. [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) służy do uzyskiwania [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) interfejs dla bieżącej ramki stosu.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy Core](../../../extensibility/debugger/reference/core-interfaces.md)   
 [Zdarzenia](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)   
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)