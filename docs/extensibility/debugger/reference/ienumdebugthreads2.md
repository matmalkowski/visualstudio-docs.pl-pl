---
title: IEnumDebugThreads2 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugThreads2
helpviewer_keywords:
- IEnumDebugThreads2
ms.assetid: 1854f078-3b49-42c2-b65b-33e3b506fd63
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3405a8ab52591e79f5a865016b68c69c61e6cf8b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31125469"
---
# <a name="ienumdebugthreads2"></a>IEnumDebugThreads2
Ta interfac wylicza wątki uruchomione w bieżącej sesji debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
IEnumDebugThreads2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Aparat debugowania (DE) implementuje ten interfejs reprezentujący listę wątków w programie.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Wywołanie [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md) uzyskać ten interfejs reprezentujący listę wszystkie wątki we wszystkich programach uruchomionych w procesie. Wywołanie [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) uzyskać ten interfejs reprezentujący listę wątki uruchomione w programie.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 W poniższej tabeli przedstawiono metody `IEnumDebugThreads2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Next](../../../extensibility/debugger/reference/ienumdebugthreads2-next.md)|Pobiera określoną liczbę wątków w kolejności wyliczenia.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugthreads2-skip.md)|Pomija określoną liczbę wątków w kolejności wyliczenia.|  
|[Resetowanie](../../../extensibility/debugger/reference/ienumdebugthreads2-reset.md)|Resetuje sekwencję wyliczenia na początku.|  
|[klonowania](../../../extensibility/debugger/reference/ienumdebugthreads2-clone.md)|Tworzy moduł wyliczający, który zawiera takim samym stanie wyliczenie jako bieżący.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugthreads2-getcount.md)|Pobiera liczbę wątków w moduł wyliczający.|  
  
## <a name="remarks"></a>Uwagi  
 Visual Studio zwykle uzyskuje aktualizacji w tym interfejsie **wątków** okna również, aby otrzymać pierwszym wątkiem listy, aby można było wywołać [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md), [Kontynuuj](../../../extensibility/debugger/reference/idebugprocess3-continue.md), i [Krok](../../../extensibility/debugger/reference/idebugprocess3-step.md).  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy Core](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)   
 [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)   
 [Krok](../../../extensibility/debugger/reference/idebugprocess3-step.md)   
 [Kontynuuj](../../../extensibility/debugger/reference/idebugprocess3-continue.md)   
 [Wykonanie](../../../extensibility/debugger/reference/idebugprocess3-execute.md)