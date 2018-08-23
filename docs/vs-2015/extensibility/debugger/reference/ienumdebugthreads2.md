---
title: IEnumDebugThreads2 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IEnumDebugThreads2
helpviewer_keywords:
- IEnumDebugThreads2
ms.assetid: 1854f078-3b49-42c2-b65b-33e3b506fd63
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 96a86c322ed2fa1ac750171116a0a11c9b2b4d99
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42673386"
---
# <a name="ienumdebugthreads2"></a>IEnumDebugThreads2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [IEnumDebugThreads2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/ienumdebugthreads2).  
  
Ta interfac wylicza wątki uruchomione w bieżącej sesji debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
IEnumDebugThreads2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Aparat debugowania (DE) implementuje ten interfejs reprezentujący listę wątków w programie.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Wywołaj [enumthreads —](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md) uzyskać ten interfejs reprezentujący listę wszystkich wątków we wszystkich programów uruchomionych w ramach procesu. Wywołaj [enumthreads —](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) uzyskać ten interfejs reprezentujący listę wątków uruchomionych w programie.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 W poniższej tabeli przedstawiono metody `IEnumDebugThreads2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Next](../../../extensibility/debugger/reference/ienumdebugthreads2-next.md)|Pobiera określoną liczbę wątków w kolejności wyliczenia.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugthreads2-skip.md)|Pomija określoną liczbę wątków w kolejności wyliczenia.|  
|[Resetuj](../../../extensibility/debugger/reference/ienumdebugthreads2-reset.md)|Resetuje sekwencji wyliczenia na początku.|  
|[Klon](../../../extensibility/debugger/reference/ienumdebugthreads2-clone.md)|Tworzy moduł wyliczający, który zawiera ten sam stan wyliczenia jako bieżący.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugthreads2-getcount.md)|Pobiera liczbę wątków w moduł wyliczający.|  
  
## <a name="remarks"></a>Uwagi  
 Program Visual Studio zwykle uzyskuje tego interfejsu, aby zaktualizować **wątków** okna również, aby otrzymać pierwszym wątkiem listy, aby wywołać [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md), [Kontynuuj](../../../extensibility/debugger/reference/idebugprocess3-continue.md), i [Kroku](../../../extensibility/debugger/reference/idebugprocess3-step.md).  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)   
 [Enumthreads —](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)   
 [Enumthreads —](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)   
 [Krok](../../../extensibility/debugger/reference/idebugprocess3-step.md)   
 [Kontynuuj](../../../extensibility/debugger/reference/idebugprocess3-continue.md)   
 [Wykonywanie](../../../extensibility/debugger/reference/idebugprocess3-execute.md)

