---
title: Obliczanie wyrażenia (Visual Studio debugowanie zestawu SDK) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5044ced5-c18c-4534-b0bf-cc3e50cd57ac
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 022a0ee21b7a58fdd69249b240490fc3c1df8361
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31109808"
---
# <a name="expression-evaluation-visual-studio-debugging-sdk"></a>Szacowanie wyrażeń (debugowanie zestawu SDK programu Visual Studio)
W trybie przerwania musi być może korzystać z prostych wyrażeń zawierających wiele zmiennych programu IDE. Aby to zrobić, aparat debugowania (DE) musi być mogła przeanalizować i ocenić wyrażenie, które jest wprowadzany do jednego z okien IDE.  
  
 Wyrażenia są tworzone przy użyciu [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) — metoda i są reprezentowane przez powstałe w ten sposób [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interfejsu.  
  
 **IDebugExpression2** interfejs jest implementowany przez Niemcy i wywołania jego **EvalAsync** metodę, aby zwrócić [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interfejs do środowiska IDE, aby wyświetlić wyniki oceny wyrażenia w IDE. [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) zwraca struktury, którego można umieścić wartości wyrażenia w okno czujki lub w oknie zmienne lokalne.  
  
 Wywołuje debugowania pakietu lub sesji debugowania Menedżera (SDM) [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) lub [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) uzyskanie [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interfejs, który reprezentuje wynik oceny. `IDebugProperty2` zawiera metody, które zwracają nazwę, typ i wartość wyrażenia. Te informacje są wyświetlane w różnych oknach debugera.  
  
## <a name="using-expression-evaluation"></a>Za pomocą wyrażenia  
 Aby użyć wyrażenia, musisz zaimplementować [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) — metoda i wszystkie metody [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interfejsu, jak pokazano w poniższej tabeli.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Oblicza wyrażenie asynchronicznie.|  
|[Przerwania](../../extensibility/debugger/reference/idebugexpression2-abort.md)|Kończy się asynchronicznego wyrażenia.|  
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Oblicza wyrażenie synchronicznie.|  
  
 Ocena synchroniczne i asynchroniczne wymagają wykonania [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) metody. Obliczanie wyrażenia asynchroniczne wymaga wykonania [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrola wykonywania i ocena stanu](../../extensibility/debugger/execution-control-and-state-evaluation.md)