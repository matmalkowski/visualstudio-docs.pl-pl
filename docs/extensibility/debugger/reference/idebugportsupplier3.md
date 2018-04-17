---
title: IDebugPortSupplier3 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPortSupplier3
helpviewer_keywords:
- IDebugPortSupplier3 interface
ms.assetid: e458cd02-2370-4435-8953-17d7a60ce152
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d5a35e212c98d6e62b667c4305d8ae4874feb3aa
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="idebugportsupplier3"></a>IDebugPortSupplier3
Ten interfejs umożliwia obiekt wywołujący określić, czy dostawca portu można zachować portów (zapisując je na dysku) między wywołań debugera, a następnie Pobierz listę tych portów konserwowane.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugPortSupplier3 : IDebugPortSupplier2  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Dostawcy niestandardowego numeru portu implementuje ten interfejs obsługuje przechowywanie lub portu informacje są zapisywane na dysku. Ten interfejs musi zostać wdrożone na tym samym obiekcie jako [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) interfejsu.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Wywołanie [QueryInterface](/cpp/atl/queryinterface) na `IDebugPortSupplier2` interfejs do uzyskania tego interfejsu.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 Oprócz dziedziczone z metody [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) interfejsu, ten interfejs obsługuje następujące:  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CanPersistPorts](../../../extensibility/debugger/reference/idebugportsupplier3-canpersistports.md)|Zwraca, czy dostawca portu można utrwalić portów (zapisując je na dysku) między wywołań debugera.|  
|[EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)|Zwraca obiekt, który może służyć do wyliczenia przez wszystkie porty, które były zapisywane na dysku przez dostawcę tego portu.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli dostawca portu portów między wywołań może się powtarzać, powinien implementować ten interfejs. Porty powinny być ładowane, gdy port dostawcy jest wystąpienie zostało utworzone i zapisywane na dysku, jeśli dostawca portu zostanie zniszczony.  
  
 Aparat debugowania zazwyczaj nie wchodzi w interakcję z dostawcą portu, a nie odniesie bez użycia dla tego interfejsu.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy Core](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)