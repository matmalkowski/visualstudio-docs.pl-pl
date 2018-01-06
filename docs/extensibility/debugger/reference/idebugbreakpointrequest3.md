---
title: IDebugBreakpointRequest3 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugBreakpointRequest3
helpviewer_keywords: IDebugBreakpointRequest3
ms.assetid: 8a042beb-b319-48e3-b3c8-9c8336ab371b
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: acccf830983239f81ba5c896c848ec13007c5d6f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugbreakpointrequest3"></a>IDebugBreakpointRequest3
Ten interfejs reprezentuje informacje niezbędne do tworzenia i powiązać dowolnego typu punktu przerwania. To rozszerzenie [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugBreakpointRequest3 : IDebugBreakpointRequest2  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Menedżer debugowania sesji (SDM) zwykle implementuje ten interfejs.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Aparat debugowania (DE) uzyskuje dostęp do tego interfejsu, wywołując [QueryInterface](/cpp/atl/queryinterface) otrzymanych w wywołaniu interfejsu IDebugBreakpointRequest2 [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md).  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 Oprócz dziedziczone z metody [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md), `IDebugBreakpointRequest3` interfejsu udostępnia następujące metody.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)|Pobiera informacje o żądanie przerwania, opisujący to żądanie przerwania.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs jest używany do znajdują się dodatkowe informacje do DE za pośrednictwem [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) struktury. Dodatkowe informacje zawiera identyfikator dostawcy DE (w formie identyfikatora GUID), nazwę śledzenia i nazwy ograniczenia punktu przerwania.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)