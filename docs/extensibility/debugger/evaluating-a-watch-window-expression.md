---
title: "Obliczenie wyrażenia okna czujki | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Watch window expressions
- Watch window, expressions
- expression evaluation, Watch window expressions
ms.assetid: b07e72c7-60d3-4b30-8e3f-6db83454c348
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 03a74bf73f457009a6f17f8e7bdda8e4e7b9e35f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="evaluating-a-watch-window-expression"></a>Obliczenie wyrażenia okno czujki
> [!IMPORTANT]
>  W programie Visual Studio 2015 ten sposób wdrażania ewaluatorów wyrażeń jest przestarzały. Aby uzyskać informacje dotyczące wdrożenia ewaluatorów wyrażeń CLR, zobacz [Ewaluatorów wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane próbki ewaluatora wyrażenia](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Podczas wykonywania jest wstrzymana, Visual Studio wymaga aparat debugowania (DE), aby określić bieżącą wartość każde wyrażenie na liście czujki. Niemcy ocenia każdy wyrażenie, używając ewaluatora wyrażeń (EE) i Visual Studio wyświetla jego wartość w **czujki** okna.  
  
 Poniżej przedstawiono omówienie sposobu szacowania wyrażenia czujki listy:  
  
1.  Visual Studio wymaga DE [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) można pobrać z kontekstu wyrażenia, który może służyć do oceny wyrażenia.  
  
2.  Dla każdego wyrażenia na liście wymaga programu Visual Studio [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) Aby przekonwertować wyrażenia przeanalizowany tekst wyrażenia.  
  
3.  `IDebugExpressionContext2::ParseText`wywołania [przeanalizować](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) do wykonują rzeczywistą pracę z analizy tekstu i produktu [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) obiektu.  
  
4.  `IDebugExpressionContext2::ParseText`Tworzy [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) obiekt i naraża `IDebugParsedExpression` obiektu do niego. Mam`DebugExpression2` obiekt jest następnie zwracany do programu Visual Studio.  
  
5.  Visual Studio wywołania [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) można oszacować wyrażenia przeanalizowany.  
  
6.  `IDebugExpression2::EvaluateSync`przekazuje wywołanie [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) rzeczywiste oceny i utworzyć [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) obiekt, który jest zwracany do programu Visual Studio.  
  
7.  Visual Studio wywołania [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) można uzyskać wartość wyrażenia, który następnie jest wyświetlany na liście.  
  
## <a name="parse-then-evaluate"></a>Analizy, a następnie ocenić  
 Ponieważ podczas analizowania złożone wyrażenie może trwać dłużej niż oceny, proces obliczenia wyrażenia został podzielony na dwa kroki: 1) przeanalizować wyrażenia i 2) oszacować wyrażenia przeanalizowany. W ten sposób obliczania może wystąpić wiele razy, ale wyrażenie musi być analizowana tylko raz. Pośredni przeanalizowany wyrażenie jest zwracana z EE w [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) obiekt, który z kolei jest hermetyzowany i zwrócony z DE jako [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) obiektu. `IDebugExpression` Obiektu różni się wszystkie oceny `IDebugParsedExpression` obiektu.  
  
> [!NOTE]
>  Nie jest niezbędna dla EE odpowiadać ten dwuetapowy proces, mimo że program Visual Studio zakłada EE można przeanalizować i oceny w tym samym kroku podczas [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) nosi nazwę (jest to przykład MyCEE działania, na przykład). Język utworzenia złożonych wyrażeń, można oddzielić krok analizy z kroku oceny. Umożliwia to zwiększenie wydajności w debugerze programu Visual Studio, gdy wiele Obejrzyj wyrażenia są pokazywane.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Przykładowe zastosowanie Szacowanie wyrażeń](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md)  
 Używa próbki MyCEE do kroków procesu Obliczanie wyrażenia.  
  
 [Obliczenie wyrażenia czujki](../../extensibility/debugger/evaluating-a-watch-expression.md)  
 W tym artykule wyjaśniono, co się dzieje po analizy wyrażenia powiodło się.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Kontekst oceny](../../extensibility/debugger/evaluation-context.md)  
 Zawiera argumenty, które są przekazywane, gdy aparat debugowania (DE) wywołuje ewaluatora wyrażenia (EE).  
  
## <a name="see-also"></a>Zobacz też  
 [Zapisywanie Ewaluator wyrażeń CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)