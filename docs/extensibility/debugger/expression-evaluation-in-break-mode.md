---
title: Szacowanie wyrażeń w trybie przerwania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- break mode, expression evaluation
- debugging [Debugging SDK], expression evaluation
- expression evaluation, break mode
ms.assetid: 34fe5b58-15d5-4387-a266-72120f90a4b6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 66c69d6dc3dbce328e519f6d078e0aa4a5208ca0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31100289"
---
# <a name="expression-evaluation-in-break-mode"></a>Szacowanie wyrażeń w trybie przerwania
Poniżej opisano proces, który występuje, gdy debuger jest w trybie przerwania i musi przeprowadzić Obliczanie wyrażenia.  
  
## <a name="expression-evaluation-process"></a>Proces oceny wyrażenia  
 Poniżej przedstawiono podstawowe etapy obliczenia wyrażenia:  
  
1.  Wywołuje Menedżera debugowania sesji (SDM) [IDebugStackFrame2::GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) można uzyskać interfejsu kontekstu wyrażenia [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md).  
  
2.  Następnie wywołuje SDM [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) z ciągiem do przeanalizowania.  
  
3.  Jeśli ParseText nie może zwracać wartość S_OK, zwracany jest przyczyną tego błędu.  
  
     — w przeciwnym razie wartość-  
  
     Jeśli ParseText zwróci wartość S_OK, SDM może wywoływać albo [IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) lub [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) uzyskać końcowa wartość z wyrażenia przeanalizowany.  
  
    -   W przypadku przy użyciu `IDebugExpression2::EvaluateSync`, interfejsu danego wywołania zwrotnego jest używany do komunikacji ciągły proces oceny. Końcowa wartość jest zwracana w [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interfejsu.  
  
    -   W przypadku przy użyciu `IDebugExpression2::EvaluateAsync`, interfejsu danego wywołania zwrotnego jest używany do komunikacji ciągły proces oceny. Po zakończeniu oceny EvaluateAsync wysyła [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) interfejsu za pomocą wywołania zwrotnego. Z tego interfejsu zdarzenia końcowa wartość można uzyskać z [GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wywoływanie zdarzeń debugera](../../extensibility/debugger/calling-debugger-events.md)