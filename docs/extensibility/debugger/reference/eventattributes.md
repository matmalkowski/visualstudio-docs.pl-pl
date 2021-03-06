---
title: EVENTATTRIBUTES | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- EVENTATTRIBUTES
helpviewer_keywords:
- EVENTATTRIBUTES enumeration
ms.assetid: 04db10f7-df31-4464-98e8-b3777428179e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 87d6a2176dcd3c4cf748549f94d071b181d0d14f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31103932"
---
# <a name="eventattributes"></a>EVENTATTRIBUTES
Określa atrybuty zdarzeń.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
enum enum_EVENTATTRIBUTES {   
   EVENT_ASYNCHRONOUS          = 0x0000,  
   EVENT_SYNCHRONOUS           = 0x0001,  
   EVENT_STOPPING              = 0x0002,  
   EVENT_ASYNC_STOP            = 0x0002,  
   EVENT_SYNC_STOP             = 0x0003,  
   EVENT_IMMEDIATE             = 0x0004,  
   EVENT_EXPRESSION_EVALUATION = 0x0008  
};  
typedef DWORD EVENTATTRIBUTES;  
```  
  
```csharp  
public enum enum_EVENTATTRIBUTES {   
   EVENT_ASYNCHRONOUS          = 0x0000,  
   EVENT_SYNCHRONOUS           = 0x0001,  
   EVENT_STOPPING              = 0x0002,  
   EVENT_ASYNC_STOP            = 0x0002,  
   EVENT_SYNC_STOP             = 0x0003,  
   EVENT_IMMEDIATE             = 0x0004,  
   EVENT_EXPRESSION_EVALUATION = 0x0008  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 EVENT_ASYNCHRONOUS  
 Wskazuje, że zdarzenie jest asynchroniczne i niezbędne jest brak odpowiedzi na zdarzenia.  
  
 EVENT_SYNCHRONOUS  
 Wskazuje, że zdarzenie jest synchroniczne; Odpowiedz za pomocą klasy [ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md).  
  
 EVENT_STOPPING  
 Wskazuje, że jest zdarzeniem zatrzymującym. Musi być połączona z jedną `EVENT_ASYNCHRONOUS` lub `EVENT_SYNCHRONOUS`.  
  
 EVENT_ASYNC_STOP  
 Wskazuje zdarzenie asynchroniczne zatrzymania. Obecnie nie ma żadnego takie zdarzenia. Ta flaga jest tylko symbol zastępczy.  
  
 EVENT_SYNC_STOP  
 Wskazuje zdarzeniem zatrzymującym synchroniczne (kombinację `EVENT_SYNCHRONOUS` i `EVENT_STOPPING`). Ta wartość jest używana przez aparat debugowania (DE) podczas wysyłania zdarzeniem zatrzymującym. Odpowiedź jest wprowadzone za pomocą wywołania [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md), [krok](../../../extensibility/debugger/reference/idebugprogram2-step.md), lub [Kontynuuj](../../../extensibility/debugger/reference/idebugprogram2-continue.md).  
  
 EVENT_IMMEDIATE  
 Wskazuje zdarzenie, które są wysyłane do IDE natychmiast. Ta flaga jest połączone z innymi flagi, takich jak `EVENT_ASYNCHRONOUS`, `EVENT_SYNCHRONOUS`, lub `EVENT_SYNC_STOP` wskazująca typ zdarzenia i fakt, że mechanizm odpowiedzi (jeżeli istniał) jest znany.  
  
 EVENT_EXPRESSION_EVALUATION  
 Zdarzenie jest wynikiem obliczania wyrażenia.  
  
## <a name="remarks"></a>Uwagi  
 Te wartości są przekazywane w `dwAttrib` parametr [zdarzeń](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) metody.  
  
 Te wartości mogą być łączone z bitowego `OR`.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)   
 [Zdarzenia](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)