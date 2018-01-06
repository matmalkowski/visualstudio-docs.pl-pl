---
title: IDebugThread2 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugThread2
helpviewer_keywords: IDebugThread2 interface
ms.assetid: 221b4b1b-4a26-466e-bc29-5eff800fab13
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: dca773ca63e2ab6bbc852648d2dea92b0b9813d4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy Core](../../../extensibility/debugger/reference/core-interfaces.md)   
 [Zdarzenia](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)   
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)