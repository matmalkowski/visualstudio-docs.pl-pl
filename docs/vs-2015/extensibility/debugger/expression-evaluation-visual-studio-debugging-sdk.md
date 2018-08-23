---
title: Szacowanie wyrażeń (zestaw SDK debugowania programu Visual Studio) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5044ced5-c18c-4534-b0bf-cc3e50cd57ac
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bd5fb9ac88b2535c897978cdd63f9cf0716d53a1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42684909"
---
# <a name="expression-evaluation-visual-studio-debugging-sdk"></a>Obliczanie wyrażeń (zestaw SDK debugowania w programie Visual Studio)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [Obliczanie wyrażenia (Visual Studio debugowanie zestawu SDK)](https://docs.microsoft.com/visualstudio/extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk).  
  
W trybie break IDE musi umożliwiać można obliczyć wartości wyrażenia proste wielu zmiennych programu. Aby to osiągnąć, aparat debugowania (DE) musi umożliwiać do analizy i ocenić wyrażenie, które jest wprowadzany do jednego z okien środowiska IDE.  
  
 Wyrażenia są tworzone przy użyciu [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) metody i są reprezentowane przez wynikowy [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interfejsu.  
  
 **IDebugExpression2** interfejs jest implementowany przez DE i wywołuje jego **EvalAsync** metodę, aby zwrócić [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interfejsu środowiska IDE, aby wyświetlić wyniki oceny wyrażenia w środowisku IDE. [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) zwraca strukturę, który może służyć do umieszczenia wartości wyrażenia w oknie czujki lub okno zmiennych lokalnych.  
  
 Debugowanie pakietu lub sesja debugowania manager (SDM) wywołuje [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) lub [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) można pobrać [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interfejs, który reprezentuje wynik oceny. `IDebugProperty2` zawiera metody, które zwracają nazwa, typ i wartość wyrażenia. Te informacje są wyświetlane w różnych oknach debugera.  
  
## <a name="using-expression-evaluation"></a>Za pomocą oceny wyrażenia  
 Aby użyć obliczenia wyrażenia, należy zaimplementować [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) metody i wszystkie metody [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interfejsu, jak pokazano w poniższej tabeli.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Oblicza wyrażenie asynchronicznie.|  
|[Przerwij](../../extensibility/debugger/reference/idebugexpression2-abort.md)|Kończy się obliczenia wyrażenia asynchroniczne.|  
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Oblicza wyrażenie synchronicznie.|  
  
 Ocena synchroniczne i asynchroniczne, wymagają wprowadzenia [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) metody. Obliczanie wyrażenia asynchroniczne wymaga implementacji [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrola wykonywania i ocena stanu](../../extensibility/debugger/execution-control-and-state-evaluation.md)

