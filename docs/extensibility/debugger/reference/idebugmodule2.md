---
title: IDebugModule2 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugModule2
helpviewer_keywords:
- IDebugModule2 interface
ms.assetid: 24c2a126-f4ab-4891-8509-8ef99b994c08
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ac5c39ed386763689d504eda7a85e6a77fab4db3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31115596"
---
# <a name="idebugmodule2"></a>IDebugModule2
Ten interfejs reprezentuje moduł — to znaczy jednostki pliku wykonywalnego programu — takich jak biblioteki DLL.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugModule2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Aparat debugowania (DE) implementuje ten interfejs do reprezentowania modułu oraz w celu zapewnienia dostępu do informacji na temat tego modułu.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Wywołanie [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md) zwraca tego interfejsu. Wysyła DE [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md) interfejsu menedżerowi sesji debugowania (SDM) przy użyciu [zdarzeń](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) metody.  
  
 Ten interfejs może również być zwracane w [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) struktury (który jest zwracany przez wywołanie do [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)).  
  
 [Następny](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md) zwraca również wartość tego interfejsu ([EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) zwraca [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md) interfejs).  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 W poniższej tabeli przedstawiono metody `IDebugModule2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)|Pobiera [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) opisujący ten moduł.|  
|[ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md)|OBSOLETE. NIE UŻYWAJ. Ponownie ładuje symbole dla tego modułu.|  
  
## <a name="remarks"></a>Uwagi  
 Informacje o module mogą być wyświetlane w **modułów** okno środowiska IDE.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy Core](../../../extensibility/debugger/reference/core-interfaces.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)   
 [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)   
 [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)