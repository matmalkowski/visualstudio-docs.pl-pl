---
title: Ewaluator wyrażeń | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expressions [Debugging SDK]
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: f9381b2f-99aa-426c-aea0-d9c15f3c859b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f27ef612fffa380bcec3bd252fb4a4601bf07e8e
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2018
ms.locfileid: "39231623"
---
# <a name="expression-evaluator"></a>Ewaluator wyrażeń
Ewaluatory wyrażeń (EE) Sprawdź składnię języka do analizy i Szacowanie zmiennych i wyrażeń w czasie wykonywania, umożliwiając im wyświetlanie przez użytkownika, gdy IDE jest w trybie przerwania.  
  
## <a name="use-expression-evaluators"></a>Użyj ewaluatory wyrażeń  
 Wyrażenia są tworzone przy użyciu [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) metody w następujący sposób:  
  
1.  Aparat debugowania (DE) implementuje [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfejsu.  
  
2.  Pobiera pakiet debugowania `IDebugExpressionContext2` obiektu z [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) interfejsu, a następnie wywołania `IDebugStackFrame2::ParseText` metody je, aby uzyskać [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) obiektu.  
  
3.  Wywołania pakietu debugowania [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) metody lub [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) metodę, aby uzyskać wartość wyrażenia. `IDebugExpression2::EvaluateAsync` jest wywoływana z polecenia/bezpośrednim. Innych składników interfejsu użytkownika Wywołaj `IDebugExpression2::EvaluateSync`.  
  
4.  Wynikiem obliczenia wyrażenia jest [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) obiekt, który zawiera nazwę, typ i wartość wyniku obliczenia wyrażenia.  
  
 Podczas obliczania wyrażenia EE wymaga informacji z składnika dostawcy symboli. Dostawca symboli dostarcza informacji symbolicznych, używany do identyfikowania i zrozumienia przeanalizowany wyrażenia.  
  
 Po ukończeniu oceny wyrażenia asynchroniczne Zdarzenie asynchroniczne wysyłany przez DE za pośrednictwem Menedżer debugowania sesji (SDM) do powiadamiania IDE zakończeniu oceny wyrażenia. I wynik obliczenia jest zwracany z wywołania `IDebugExpression2::EvaluateSync` metody.  
  
## <a name="implementation-notes"></a>Uwagi o implementacji  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Silniki debugowania chcą skontaktować się z Ewaluator wyrażeń przy użyciu interfejsów środowiska uruchomieniowego języka wspólnego (CLR). W wyniku ewaluatora wyrażeń działające z [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] silniki debugowania musi obsługiwać środowiska CLR (pełna lista wszystkich CLR profilowanie interfejsów znajduje się w debugref.doc, który jest częścią programu [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)]).  
  
## <a name="see-also"></a>Zobacz także  
 [Składniki debugera](../../extensibility/debugger/debugger-components.md)