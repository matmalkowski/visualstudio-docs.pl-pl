---
title: IDebugEventCallback2::Event | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEventCallback2::Event
helpviewer_keywords: IDebugEventCallback2::Event
ms.assetid: e5a3345b-d460-4e40-8f5b-3111c56a2ed9
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8c1a69c3ce3a8b59c1cea7b9282d0169c3637729
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idebugeventcallback2event"></a>IDebugEventCallback2::Event
Wysyła powiadomienia o zdarzeniach debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Event(   
   IDebugEngine2*  pEngine,  
   IDebugProcess2* pProcess,  
   IDebugProgram2* pProgram,  
   IDebugThread2*  pThread,  
   IDebugEvent2*   pEvent,  
   REFIID          riidEvent,  
   DWORD           dwAttrib  
);  
```  
  
```csharp  
int Event(   
   IDebugEngine2  pEngine,  
   IDebugProcess2 pProcess,  
   IDebugProgram2 pProgram,  
   IDebugThread2  pThread,  
   IDebugEvent2   pEvent,  
   ref Guid       riidEvent,  
   uint           dwAttrib  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pEngine`  
 [in] [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) obiekt, który reprezentuje aparat debugowania (DE), który wysyła tego zdarzenia. Niemcy jest wymagany do wypełniania tego parametru.  
  
 `pProcess`  
 [in] [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) obiekt, który reprezentuje proces, w którym występuje zdarzenie. Ten parametr jest wypełniane przez menedżera sesji debugowania (SDM). Niemcy zawsze przekazuje wartość null dla tego parametru.  
  
 `pProgram`  
 [in] [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) obiekt, który reprezentuje program, w którym to zdarzenie występuje. W przypadku większości zdarzeń ten parametr nie jest wartością null.  
  
 `pThread`  
 [in] [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) obiekt, który reprezentuje wątku, w którym to zdarzenie występuje. Zatrzymywanie zdarzeń, aby uzyskać ten parametr nie może być wartość null, ramka stosu jest otrzymane w wyniku tego parametru.  
  
 `pEvent`  
 [in] [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) obiekt, który reprezentuje zdarzenia debugowania.  
  
 `riidEvent`  
 [in] Identyfikator GUID, który identyfikuje interfejsu zdarzenia, które można uzyskać z `pEvent` parametru.  
  
 `dwAttrib`  
 [in] Kombinacja flag z [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md) wyliczenia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Podczas wywoływania tej metody `dwAttrib` parametru musi być zgodna wartość zwracana z [GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md) przekazano Metoda wywołana dla obiekt zdarzenia `pEvent` parametru.  
  
 Wszystkie zdarzenia debugowania są publikowane asynchronicznie, niezależnie od tego samego zdarzenia jest asynchroniczne lub nie. Gdy URZ wywołuje tę metodę, zwracana wartość nie wskazuje, czy zdarzenie zostało przetworzone, tylko, czy odebrano zdarzenie. W rzeczywistości w większości przypadków zdarzenia nie został przetworzony po powrocie z tej metody.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)