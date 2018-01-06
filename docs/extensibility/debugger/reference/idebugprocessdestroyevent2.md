---
title: IDebugProcessDestroyEvent2 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProcessDestroyEvent2
helpviewer_keywords: IDebugProcessDestroyEvent2
ms.assetid: 1b8e0528-95bc-48fa-9653-2cea66c8dc3a
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 91eb4e9f749111e96bec2e527432b1f1851cd24c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprocessdestroyevent2"></a>IDebugProcessDestroyEvent2
Ten interfejs jest wysyłany, gdy proces zostanie zakończony, zamyka nietypowo lub jest odłączona od.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugProcessDestroyEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Aparat debugowania (DE) lub dostawcy niestandardowego numeru portu należy zaimplementować ten interfejs, aby zgłosić, że proces został zakończony. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfejs musi zostać wdrożone na tym samym obiekcie danego interfejsu. Używa SDM [QueryInterface](/cpp/atl/queryinterface) dostępu `IDebugEvent2` interfejsu.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Niemcy lub dostawcę, port niestandardowy, tworzy i wysyła ten obiekt zdarzeń do raportowania przerwanie procesu. Niemcy wysyła tego zdarzenia przy użyciu [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) funkcja wywołania zwrotnego, która jest dostarczana przez SDM, gdy jest on dołączony do debugowanego programu. Dostawcy niestandardowego numeru portu wysyła za pomocą tego zdarzenia [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) interfejsu.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy Core](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)