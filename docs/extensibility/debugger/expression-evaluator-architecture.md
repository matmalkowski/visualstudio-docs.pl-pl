---
title: "Architektura ewaluatora wyrażeń | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- architecture, expression evaluators
- expression evaluators, architecture
- debugging [Debugging SDK], expression evaluators
ms.assetid: aad7c4c6-1dc1-4d32-b975-f1fdf76bdeda
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6805b97da8e8f742b1b6c0bb3298e9324bb1f72e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="expression-evaluator-architecture"></a>Architektura ewaluatora wyrażenia
> [!IMPORTANT]
>  W programie Visual Studio 2015 ten sposób wdrażania ewaluatorów wyrażeń jest przestarzały. Aby uzyskać informacje dotyczące wdrożenia ewaluatorów wyrażeń CLR, zobacz [Ewaluatorów wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane próbki ewaluatora wyrażenia](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Integrowanie właściwy język pakiet debugowania programu Visual Studio oznacza implementacji interfejsów ewaluatora (EE) wymagane wyrażenie i wywoływania dostawcy symbol środowiska wykonawczego języka wspólnego (SP) i interfejsów integratora. Obiekt SP i integratora, wraz z bieżącego adresu wykonywania są kontekst, w jakiej są oceniane wyrażenia. Informacje te interfejsy tworzenia i wykorzystywania reprezentuje kluczowych pojęć związanych z architekturą EE.  
  
## <a name="overview"></a>Omówienie  
  
### <a name="parsing-the-expression"></a>Podczas analizowania wyrażenia  
 Podczas debugowania programu wyrażenia są oceniane pod kątem kilka przyczyn, ale zawsze gdy debugowanego programu został zatrzymany w punkcie przerwania (punkt przerwania wprowadzane przez użytkownika lub jedną spowodowane przez wyjątek). Jest w tej chwili, gdy program Visual Studio uzyskuje ramka stosu reprezentowany przez [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) interfejsu z aparatu debugowania (DE). Wywołuje program Visual Studio [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) uzyskanie [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfejsu. Ten interfejs reprezentuje kontekst, w którym można oszacować wyrażenia; [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) jest punkt wejścia do procesu oceny. Do tego punktu wszystkich interfejsów implementowanych przez Niemcy.  
  
 Gdy `IDebugExpressionContext2::ParseText` jest nazywane, DE tworzy EE językowej pliku źródłowego, w którym wystąpił punkt przerwania (DE również tworzy SH w tym momencie). EE jest reprezentowana przez [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md) interfejsu. Następnie wywołuje DE [przeanalizować](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) można przekonwertować wyrażenia (w postaci tekstu) do przeanalizowanej wyrażenia, gotowe do oceny. To wyrażenie przeanalizowany jest reprezentowana przez [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) interfejsu. Należy pamiętać, że wyrażenie jest zwykle przeanalizować i nie są oceniane w tym momencie.  
  
 Niemcy tworzy obiekt, który implementuje [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interfejsu naraża `IDebugParsedExpression` obiekt do `IDebugExpression2` obiektu i zwraca `IDebugExpression2` obiekt z `IDebugExpressionContext2::ParseText`.  
  
### <a name="evaluating-the-expression"></a>Obliczenie wyrażenia  
 Wywołuje program Visual Studio, albo [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) lub [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) można oszacować wyrażenia przeanalizowany. Obie te metody wywołania [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) (`IDebugExpression2::EvaluateSync` wywołuje metodę natychmiast, podczas gdy `IDebugExpression2::EvaluateAsync` wywołuje metodę za pośrednictwem wątku w tle) można oszacować wyrażenia przeanalizowany i zwracać [ IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interfejs, który reprezentuje wartości i typ wyrażenia przeanalizowany. `IDebugParsedExpression::EvaluateSync`używa podanej SH, adres i integratora można przekonwertować wyrażenia przeanalizowane na wartość rzeczywistą reprezentowany przez `IDebugProperty2` interfejsu.  
  
### <a name="for-example"></a>Na przykład  
 Po trafieniu w uruchomiony program użytkownik wybierze opcję Wyświetl zmienną w **QuickWatch** okno dialogowe. To okno dialogowe zawiera nazwę zmiennej, jego wartość i jego typu. Użytkownik może zmienić zwykle wartość.  
  
 Gdy **QuickWatch** okno dialogowe jest wyświetlane, nazwa zmiennej badane są wysyłane jako tekst, który ma [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md). To polecenie zwróci [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) obiekt reprezentujący przeanalizowany wyrażenie w tym przypadku, zmienna. [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) następnie jest wywoływana w celu utworzenia `IDebugProperty2` obiekt, który reprezentuje wartość zmiennej i typ, a także jej nazwę. Jest to wyświetlane informacje.  
  
 Jeśli użytkownik zmieni wartość zmiennej [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) jest wywoływana przy użyciu nowej wartości, która zmienia wartość zmiennej w pamięci, będą używane po wznowieniu pracy program uruchomiony.  
  
 Zobacz [wyświetlanie zmiennych lokalnych](../../extensibility/debugger/displaying-locals.md) więcej szczegółów na ten proces wyświetlanie wartości zmiennych. Zobacz [zmiana wartości zmiennej lokalnej](../../extensibility/debugger/changing-the-value-of-a-local.md) więcej szczegółów, w jaki sposób zostanie zmieniona wartość zmiennej.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Kontekst oceny](../../extensibility/debugger/evaluation-context.md)  
 Zawiera argumenty, które są przekazywane, gdy DE wywołuje EE.  
  
 [Wyrażenie klucza ewaluatora interfejsów](../../extensibility/debugger/key-expression-evaluator-interfaces.md)  
 Opisuje kluczowe interfejsy potrzebne podczas zapisywania EE oraz kontekst oceny.  
  
## <a name="see-also"></a>Zobacz też  
 [Zapisywanie Ewaluator wyrażeń CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Wyświetlanie zmiennych lokalnych](../../extensibility/debugger/displaying-locals.md)   
 [Zmiana wartości zmiennej lokalnej](../../extensibility/debugger/changing-the-value-of-a-local.md)