---
title: IDebugEvent2 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEvent2
helpviewer_keywords: IDebugEvent2 interface
ms.assetid: de3d714d-96fb-4e12-b66b-a75391472153
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c1ddf80bca13c390c2d889674120b168cb79e89e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idebugevent2"></a>IDebugEvent2
Ten interfejs jest używany do komunikacji zarówno informacje o debugowaniu krytyczne, takie jak zatrzymywanie w punkcie przerwania i niekrytyczne informacje, takie jak wiadomości debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Aparat debugowania (DE) i portu niestandardowego dostawcy implementuje ten interfejs dla tego samego obiektu, jak wszystkie inne interfejsy zdarzeń.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Przy użyciu interfejsu argument identyfikator (IID) do [zdarzeń](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) lub [zdarzeń](../../../extensibility/debugger/reference/idebugportevents2-event.md), Menedżer debugowania sesji (SDM) wywołuje [QueryInterface](/cpp/atl/queryinterface) na `IDebugEvent2` interfejs do uzyskania Interfejs odpowiednie zdarzenie.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 W poniższej tabeli przedstawiono metody `IDebugEvent2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Operacja GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md)|Pobiera atrybuty dla tego zdarzenia debugowania.|  
  
## <a name="remarks"></a>Uwagi  
 Interfejsy bardziej konkretnego zdarzenia, takie jak [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md), pochodzi z interfejsu IDebugEvent2, ale zamiast tego są zaimplementowane jako osobny interfejs dla tego samego obiektu jako `IDebugEvent2`.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy Core](../../../extensibility/debugger/reference/core-interfaces.md)   
 [Zdarzenia](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [Zdarzenia](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)