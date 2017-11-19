---
title: IEnumDebugThreads2 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugThreads2
helpviewer_keywords: IEnumDebugThreads2
ms.assetid: 1854f078-3b49-42c2-b65b-33e3b506fd63
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ca4fedeb7e52fff627a8fab9e100c0a99792f1c6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
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
|[Dalej](../../../extensibility/debugger/reference/ienumdebugthreads2-next.md)|Pobiera określoną liczbę wątków w kolejności wyliczenia.|  
|[Pomiń](../../../extensibility/debugger/reference/ienumdebugthreads2-skip.md)|Pomija określoną liczbę wątków w kolejności wyliczenia.|  
|[Resetowanie](../../../extensibility/debugger/reference/ienumdebugthreads2-reset.md)|Resetuje sekwencję wyliczenia na początku.|  
|[Klonowania](../../../extensibility/debugger/reference/ienumdebugthreads2-clone.md)|Tworzy moduł wyliczający, który zawiera takim samym stanie wyliczenie jako bieżący.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugthreads2-getcount.md)|Pobiera liczbę wątków w moduł wyliczający.|  
  
## <a name="remarks"></a>Uwagi  
 Visual Studio zwykle uzyskuje aktualizacji w tym interfejsie **wątków** okna również, aby otrzymać pierwszym wątkiem listy, aby można było wywołać [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md), [Kontynuuj](../../../extensibility/debugger/reference/idebugprocess3-continue.md), i [Krok](../../../extensibility/debugger/reference/idebugprocess3-step.md).  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy Core](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)   
 [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)   
 [Krok](../../../extensibility/debugger/reference/idebugprocess3-step.md)   
 [Kontynuuj](../../../extensibility/debugger/reference/idebugprocess3-continue.md)   
 [Wykonanie](../../../extensibility/debugger/reference/idebugprocess3-execute.md)