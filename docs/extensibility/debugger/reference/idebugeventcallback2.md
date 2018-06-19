---
title: IDebugEventCallback2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEventCallback2
helpviewer_keywords:
- IDebugEventCallback2
ms.assetid: 2c935ee0-2e22-4be0-a852-73736f33c8c9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 68d29d928f310cb045ed712a151f9275446465a4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31116207"
---
# <a name="idebugeventcallback2"></a>IDebugEventCallback2
Ten interfejs jest używany przez aparat debugowania (DE) do wysyłania zdarzeń debugowania do menedżera sesji debugowania (SDM).  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugEventCallback2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] implementuje ten interfejs do odbierania zdarzeń z aparatu debugowania.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Aparat debugowania zazwyczaj otrzymuje ten interfejs, gdy wywołuje SDM [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md), lub [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md). Aparat debugowania wysyła zdarzenia do SDM wywołując [zdarzeń](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 W poniższej tabeli przedstawiono metody `IDebugEventCallback2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Zdarzenia](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)|Wysyła powiadomienia o debugowaniu zdarzenia SDM.|  
  
## <a name="remarks"></a>Uwagi  
 Mimo że [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) i [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) określić ich wejściem `IDebugEventCallback2` interfejsu, nie jest to i wskaźnika interfejsu będzie zawsze równa wartości null. Zamiast tego należy użyć aparat debugowania `IDebugEventCallback2` otrzymanych w wywołaniu interfejsu [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md), lub [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).  
  
 Jeśli pakiet implementuje [IDebugEventCallback](../../../extensibility/debugger/reference/idebugeventcallback2.md) w kodzie zarządzanym, zdecydowanie zaleca się który <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> można wywołać dla różnych interfejsów, które są przekazywane do [zdarzeń](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy Core](../../../extensibility/debugger/reference/core-interfaces.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [Dołącz](../../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)