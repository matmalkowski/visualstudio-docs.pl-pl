---
title: IDebugPropertyCreateEvent2 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPropertyCreateEvent2
helpviewer_keywords: IDebugPropertyCreateEvent2 interface
ms.assetid: 33b3082b-a42e-488a-a1e4-dadf506f922c
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 0557fd39d21415dfddb1a571c4f9e6ee69badf10
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugpropertycreateevent2"></a>IDebugPropertyCreateEvent2
Ten interfejs jest wysyłane przez aparat debugowania (DE) z menedżerem sesji debugowania (SDM) tworzy właściwość, która jest skojarzona z określonego dokumentu.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugPropertyCreateEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Niemcy implementuje ten interfejs zgłosić, że właściwość została utworzona. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfejs musi zostać wdrożone na tym samym obiekcie danego interfejsu. Używa SDM [QueryInterface](/cpp/atl/queryinterface) dostępu `IDebugEvent2` interfejsu. Ten interfejs jest wdrażany, jeśli DE utworzył właściwość skojarzony ze skryptem, który został załadowany lub utworzone i tego skryptu musi występować w IDE.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Niemcy tworzy i wysyła ten obiekt zdarzenia do raportu, który został utworzony właściwości. Zdarzenia są wysyłane przy użyciu [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) funkcja wywołania zwrotnego, która jest dostarczana przez SDM, gdy jest on dołączony do debugowanego programu.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 W poniższej tabeli przedstawiono metody `IDebugPropertyCreateEvent2` interfejsu.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md)|Pobiera nową właściwość.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli właściwość ma określony dokument lub skrypt skojarzony z nim, DE wysłać tego zdarzenia do SDM aby można było zaktualizować **dokumentów skryptu** okna o nazwie dokumentu. Wywoła SDM [GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md) z argumentem `guidDocument` można pobrać `VARIANT` zawierający [IUnknown](/cpp/atl/iunknown) wskaźnika. Wywoła SDM [QueryInterface](/cpp/atl/queryinterface) na wskaźnik do pobrania [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) interfejs, który jest używany do zaktualizowania **dokumentów skryptu** okna.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy Core](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)