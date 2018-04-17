---
title: IDebugExceptionEvent2 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugExceptionEvent2
helpviewer_keywords:
- IDebugExceptionEvent2 interface
ms.assetid: 53d32e59-a84b-4710-833e-c5ab08100516
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3f2cb866c12cacc2c0fcc81c3021e7cc5af448d3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="idebugexceptionevent2"></a>IDebugExceptionEvent2
Aparat debugowania (DE) wysyła ten interfejs do menedżera sesji debugowania (SDM) podczas wyjątek w aktualnie wykonywanego programu.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugExceptionEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Niemcy implementuje ten interfejs do raportu wystąpił wyjątek w programie debugowany. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfejs musi zostać wdrożone na tym samym obiekcie danego interfejsu. Używa SDM [QueryInterface](/cpp/atl/queryinterface) dostępu `IDebugEvent2` interfejsu.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Niemcy tworzy i wysyła ten obiekt zdarzeń, aby zgłosić wyjątek. Zdarzenia są wysyłane przy użyciu [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) funkcja wywołania zwrotnego, która jest dostarczana przez SDM, gdy on dołączony do debugowanego programu.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 W poniższej tabeli przedstawiono metody `IDebugExceptionEvent2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)|Pobiera szczegółowe informacje o wyjątku, która wywołała zdarzenie.|  
|[GetExceptionDescription](../../../extensibility/debugger/reference/idebugexceptionevent2-getexceptiondescription.md)|Pobiera opis czytelny dla człowieka zgłoszony wyjątek, która wywołała zdarzenie.|  
|[CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)|Określa, czy aparat debugowania (DE) obsługuje opcja przekazywania ten wyjątek do debugowanego po wznowieniu pracy wykonywania programu.|  
|[PassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md)|Określa, czy wyjątek powinny być przekazywane do programu debugowany po wznowieniu pracy wykonywania, czy wyjątek powinien zostać odrzucone.|  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="remarks"></a>Uwagi  
 Przed wysłaniem zdarzenia, DE sprawdza, czy to zdarzenie wyjątku wyznaczony wyjątek szansy pierwszej lub drugiej szansy przez poprzednie wywołanie [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md). Jeśli zostanie wyznaczona jako wyjątkach pierwszej szansy `IDebugExceptionEvent2` SDM jest wysyłane zdarzenie. Jeśli nie, DE daje aplikacji możliwość obsługi wyjątku. Jeśli podano bez obsługi wyjątków i jeśli wyjątek został wyznaczony jako wyjątek drugiej szansy `IDebugExceptionEvent2` SDM jest wysyłane zdarzenie. W przeciwnym razie DE wznawia wykonywanie programu i systemu operacyjnego lub środowisko uruchomieniowe obsługuje wyjątek.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy Core](../../../extensibility/debugger/reference/core-interfaces.md)   
 [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)