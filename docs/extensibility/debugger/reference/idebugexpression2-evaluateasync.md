---
title: IDebugExpression2::EvaluateAsync | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugExpression2::EvaluateAsync
helpviewer_keywords:
- IDebugExpression2::EvaluateAsync
ms.assetid: 848fe6cb-0759-42f2-890b-d2b551c527d6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 13364d94f33eca33bf71b7077c19b9da54298ed7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31122486"
---
# <a name="idebugexpression2evaluateasync"></a>IDebugExpression2::EvaluateAsync
Ta metoda oblicza wyrażenie asynchronicznie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EvaluateAsync (   
   EVALFLAGS             dwFlags,  
   IDebugEventCallback2* pExprCallback  
);  
```  
  
```csharp  
int EvaluateAsync(  
   enum_EVALFLAGS       dwFlags,   
   IDebugEventCallback2 pExprCallback  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwFlags`  
 [in] Kombinacja flag z [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) wyliczenie przez Obliczanie wyrażenia.  
  
 `pExprCallback`  
 [in] Ten parametr jest zawsze wartość null.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu. Kod błędu typowe jest:  
  
|Błąd|Opis|  
|-----------|-----------------|  
|E_EVALUATE_BUSY_WITH_EVALUATION|Obecnie trwa Obliczanie wyrażenia innego, a jednocześnie wyrażenia nie jest obsługiwana.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda powinna zwrócić natychmiast po jego uruchomieniu Obliczanie wyrażenia. Gdy wyrażenie jest obliczane pomyślnie, [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) muszą zostać przesłane do [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) zdarzenia wywołania zwrotnego, ponieważ dostarczane za pośrednictwem [Dołącz ](../../../extensibility/debugger/reference/idebugprogram2-attach.md) lub [dołączyć](../../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób zaimplementować tę metodę dla prostego `CExpression` obiekt, który implementuje [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) interfejsu.  
  
```cpp  
HRESULT CExpression::EvaluateAsync(EVALFLAGS dwFlags,  
                                   IDebugEventCallback2* pExprCallback)  
{  
    // Set the aborted state to FALSE  
    // in case the user tries to redo the evaluation after aborting.  
    m_bAborted = FALSE;  
    // Post the WM_EVAL_EXPR message in the message queue of the current thread.  
    // This starts the expression evaluation on a background thread.  
    PostThreadMessage(GetCurrentThreadId(), WM_EVAL_EXPR, 0, (LPARAM) this);  
    return S_OK;  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)   
 [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)   
 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)