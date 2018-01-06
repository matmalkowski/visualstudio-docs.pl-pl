---
title: IDebugModule2 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugModule2
helpviewer_keywords: IDebugModule2 interface
ms.assetid: 24c2a126-f4ab-4891-8509-8ef99b994c08
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 4ffa4044e6490f8de8228541787b7bf8ab80285a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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
|[ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md)|PRZESTARZAŁE. NIE UŻYWAJ. Ponownie ładuje symbole dla tego modułu.|  
  
## <a name="remarks"></a>Uwagi  
 Informacje o module mogą być wyświetlane w **modułów** okno środowiska IDE.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy Core](../../../extensibility/debugger/reference/core-interfaces.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)   
 [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)   
 [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)