---
title: IDebugPortRequest2 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPortRequest2
helpviewer_keywords:
- IDebugPortRequest2 interface
ms.assetid: 556e610d-7c4b-44a8-965a-76a9d02b601a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f5af5ef2f4371350529d1e5fa60fb5ad1539aa87
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="idebugportrequest2"></a>IDebugPortRequest2
Ten interfejs opisuje portu. Ten opis jest służy do dodawania portu dostawcy portu.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugPortRequest2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Visual Studio zwykle implementuje ten interfejs w trakcie pobierania port debugowania od dostawcy portu.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Ten interfejs jest przekazywany do [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) utworzyć portu debugowania. Wywołanie [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md) zwraca ten interfejs reprezentujący żądanie użyty do utworzenia portu w pierwszej kolejności.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 W poniższej tabeli przedstawiono metody `IDebugPortRequest2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetPortName](../../../extensibility/debugger/reference/idebugportrequest2-getportname.md)|Pobiera nazwę portu do utworzenia.|  
  
## <a name="remarks"></a>Uwagi  
 Aparat debugowania zazwyczaj nie wchodzi w interakcję z dostawcą portu, a nie odniesie bez użycia dla tego interfejsu.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy Core](../../../extensibility/debugger/reference/core-interfaces.md)   
 [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)   
 [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)