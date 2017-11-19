---
title: IDebugCoreServer2 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCoreServer2
helpviewer_keywords: IDebugCoreServer2 interface
ms.assetid: 9c47d0a6-9eb1-464e-bd44-fa2b552d4d36
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 42695a58ecab7f898a0ef8561a9bc715909f6c06
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idebugcoreserver2"></a>IDebugCoreServer2
Ten interfejs jest używany do reprezentowania i uzyskiwania informacji z serwera na komputerze w sieci.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugCoreServer2 : IUknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Visual Studio implementuje ten interfejs do reprezentowania serwera. Każde wystąpienie programu Visual Studio tworzy wystąpienie tego interfejsu.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Dostawcy niestandardowego numeru portu odbiera ten interfejs w wywołaniu [zdarzeń](../../../extensibility/debugger/reference/idebugportevents2-event.md).  
  
 Aparat debugowania można uzyskać interfejsu pośrednio poprzez wywołanie [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) (która zwraca [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md), interfejs, który jest pochodną `IDebugCoreServer2`).  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 W poniższej tabeli przedstawiono metody `IDebugCoreServer2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)|Pobiera nazwę i atrybuty maszyny.|  
|[GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md)|Pobiera nazwę maszyny.|  
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)|Pobiera dostawcę portu, która istnieje na maszynie.|  
|[GetPort](../../../extensibility/debugger/reference/idebugcoreserver2-getport.md)|Pobiera port, który już istnieje na komputerze.|  
|[EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)|Tworzy moduł wyliczający dla wszystkich portów na maszynie.|  
|[EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)|Tworzy moduł wyliczający dla wszystkich dostawców port na komputerze.|  
|[GetMachineUtilities_V7](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineutilities-v7.md)|Pobiera narzędzia maszyny dla maszyny.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs jest również używany przez program Visual Studio do przeglądania procesów uruchomionych na komputerach w sieci.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [Zdarzenia](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)   
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)