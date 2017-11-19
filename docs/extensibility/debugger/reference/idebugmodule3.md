---
title: IDebugModule3 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugModule3
helpviewer_keywords: IDebugModule3 interface
ms.assetid: 44f8e96e-9c59-4ffc-9a08-9c908a0e4de7
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 95e1c9056b12f1c624a52ee0cf4cbfc8c3272904
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idebugmodule3"></a>IDebugModule3
Ten interfejs reprezentuje moduł, który obsługuje alternatywne lokalizacje symboli i JustMyCode stanów.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugModule3 : IDebugModule2  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Aparat debugowania (DE) implementuje ten interfejs do obsługi alternatywne lokalizacje symboli i do pracy z JustMyCode stanów (zobacz [programu Visual Studio Debugger słownik](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md) dla definicji "JustMyCode").  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Wywołanie [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md) zwraca tego interfejsu. Wysyła DE [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) interfejsu menedżerowi sesji debugowania (SDM) przy użyciu [zdarzeń](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) metody. Ponadto wywołanie [QueryInterface](/cpp/atl/queryinterface) na [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) interfejsu zwraca tego interfejsu.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 Oprócz metod na [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) interfejsu, tego interfejsu implementuje następujących metod:  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)|Zwraca listę ścieżki wyszukiwane symbole i wyniki wyszukiwania poszczególnych ścieżek.|  
|[LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)|Ładuje i inicjuje symboli dla bieżącego modułu.|  
|[IsUserCode](../../../extensibility/debugger/reference/idebugmodule3-isusercode.md)|Zwraca flagę określenie, czy moduł reprezentuje kod użytkownika.|  
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugmodule3-setjustmycodestate.md)|Określa, czy moduł należy traktować jako kod użytkownika lub nie.|  
  
## <a name="remarks"></a>Uwagi  
 Program Visual Studio jest typowej tego interfejsu.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy Core](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)   
 [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)