---
title: IDebugExpression2::Abort | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugExpression2::Abort
helpviewer_keywords: IDebugExpression2::Abort
ms.assetid: 4fcb712e-1bdb-4b75-a440-35cc79ee147e
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f927971b18bfc9a7956ff5cf0cfcbc6bd09e1dda
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idebugexpression2abort"></a>IDebugExpression2::Abort
Ta metoda umożliwia anulowanie asynchronicznego wyrażenia uruchomienia przez wywołanie do [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) metody.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Abort(  
   void  
);  
```  
  
```csharp  
int Abort();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Podczas obliczania wyrażenia asynchroniczne zostało anulowane, nie wysyłane [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) zdarzenia do zdarzenia wywołanie zwrotne przekazane do [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md) lub [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) metody.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)   
 [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)