---
title: Szacowanie wyrażeń (zestaw SDK debugowania programu Visual Studio) | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 52c897e40b825f85e07b4b4f14796655618280a8
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2018
ms.locfileid: "39230737"
---
# <a name="expression-evaluation-visual-studio-debugging-sdk"></a>Obliczanie wyrażenia (Visual Studio debugowanie zestawu SDK)
W trybie break IDE musi zwrócić proste wyrażenia wielu zmiennych program. Aby wykonać ocenę, aparat debugowania (DE) należy przeanalizować i ocenić wyrażenie, które jest wprowadzany do jednego z okien środowiska IDE. 
  
 Wyrażenia są tworzone za pomocą [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) metody i reprezentowany przez wartość wynikowa [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interfejsu.  
  
 **IDebugExpression2** interfejs jest implementowany przez DE i wywołuje jego **EvalAsync** metodę, aby zwrócić [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interfejsu środowiska IDE, aby wyświetlić wyniki oceny wyrażenia w środowisku IDE. [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) zwraca strukturę, która jest używana do umieszczenia wartości wyrażenia w **Obejrzyj** okna lub **lokalne** okna.  
  
 Debugowanie pakietu lub sesja debugowania manager (SDM) wywołuje [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) lub [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) można pobrać [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interfejs, który reprezentuje wynik oceny. `IDebugProperty2` zawiera metody, które zwracają nazwa, typ i wartość wyrażenia. Te informacje są wyświetlane w różnych oknach debugera.  
  
## <a name="using-expression-evaluation"></a>Za pomocą oceny wyrażenia  
 Aby użyć obliczenia wyrażenia, należy zaimplementować [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) metody i wszystkie metody [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interfejsu, jak pokazano w poniższej tabeli.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Oblicza wyrażenie asynchronicznie.|  
|[Przerwij](../../extensibility/debugger/reference/idebugexpression2-abort.md)|Kończy się obliczenia wyrażenia asynchroniczne.|  
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Oblicza wyrażenie synchronicznie.|  
  
 Ocena synchroniczne i asynchroniczne wymagać zaimplementowania [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) metody. Obliczanie wyrażenia asynchroniczne wymaga implementacji [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Wykonanie kontroli i stan oceny](../../extensibility/debugger/execution-control-and-state-evaluation.md)