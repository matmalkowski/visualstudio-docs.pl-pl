---
title: IDebugProgram3 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugProgram3 interface
ms.assetid: 4301ba23-c00c-4ce5-8b1e-3f27da312034
caps.latest.revision: "5"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2da4dcb4911488bd82c358efc3b8075f1941af6f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprogram3"></a>IDebugProgram3
Ten interfejs reprezentuje program, który działa w procesie i rozszerza [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md) przez podanie informacji o wątku.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugProgram3 : IDebugProgram3  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Aparat debugowania (DE) i dostawcy niestandardowego numeru portu należy zaimplementować ten interfejs do reprezentowania program w procesie. Menedżer debugowania sesji (SDM) również implementuje ten interfejs, aby zapewnić informacje [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md).  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) zdarzeń zwraca ten interfejs dla nowy program. Ten interfejs jest również używany jako parametr dla wielu metod w wielu interfejsach.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 W poniższej tabeli przedstawiono metody `IDebugProgram3`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[ExecuteOnThread](../../../extensibility/debugger/reference/idebugprogram3-executeonthread.md)|Wykonuje program. Wątek jest zwracana do przekazywania informacji debugera w wątku, który użytkownik jest wyświetlana podczas wykonywania.|  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="remarks"></a>Uwagi  
 Program jest kontenerem wątku uruchomiony w ramach określonej architektury środowiska wykonawczego podczas procesu składa się z jednego lub wielu programów.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy Core](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)   
 [Dalej](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)   
 [Zdarzenia](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [Dołącz](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)   
 [Zdarzenia](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)