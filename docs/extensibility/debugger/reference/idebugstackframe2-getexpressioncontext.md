---
title: IDebugStackFrame2::GetExpressionContext | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugStackFrame2::GetExpressionContext
helpviewer_keywords:
- IDebugStackFrame2::GetExpressionContext
ms.assetid: a2604e6a-502d-473b-868f-b11ac64c7a35
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 23aa07fee47645f50ed0e6d08efa9833d2487259
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="idebugstackframe2getexpressioncontext"></a>IDebugStackFrame2::GetExpressionContext
Pobiera kontekst oceny wyrażenia w kontekście bieżącego wątku lub ramki stosu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetExpressionContext (   
   IDebugExpressionContext2** ppExprCxt  
);  
```  
  
```csharp  
int GetExpressionContext (   
   out IDebugExpressionContext2 ppExprCxt  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppExprCxt`  
 [out] Zwraca [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) obiekt, który reprezentuje kontekst dla wyrażenia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ogólnie rzecz biorąc kontekst oceny wyrażenia można traktować jako zakres do wykonywania wyrażenia. Wywołanie [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) metodę, aby przeanalizować wyrażenia, a następnie wywołać powstałe w ten sposób [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) lub [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) metod można oszacować wyrażenia przeanalizowany.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)   
 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)