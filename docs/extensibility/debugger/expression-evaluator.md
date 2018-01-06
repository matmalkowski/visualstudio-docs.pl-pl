---
title: "Ewaluator wyrażeń | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- expressions [Debugging SDK]
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: f9381b2f-99aa-426c-aea0-d9c15f3c859b
caps.latest.revision: "19"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 55aaa595c49d0c50cff5f874d1b322c3adbb9729
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="expression-evaluator"></a>Ewaluator wyrażeń
Ewaluatory wyrażeń (EE) sprawdź, czy składnia języka aby przeanalizować i ocena wyrażeń i zmienne w czasie wykonywania, dzięki czemu mogą być odczytywane przez użytkownika, gdy IDE jest w trybie przerwania.  
  
## <a name="using-expression-evaluators"></a>Przy użyciu Ewaluatory wyrażeń  
 Wyrażenia są tworzone przy użyciu [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) metody, w następujący sposób:  
  
1.  Aparat debugowania (DE) implementuje [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfejsu.  
  
2.  Pobiera pakiet debugowania `IDebugExpressionContext2` obiekt z [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) interfejs, a następnie wywołania `IDebugStackFrame2::ParseText` metody w celu pobrania [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) obiektu.  
  
3.  Wywołania pakietu debugowania [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) metody lub [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) metodę, aby uzyskać wartość wyrażenia. `IDebugExpression2::EvaluateAsync`jest wywoływana z polecenia/bezpośrednim. Wywołaj wszystkie inne składniki interfejsu użytkownika `IDebugExpression2::EvaluateSync`.  
  
4.  Wynikiem wyrażenia jest [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) obiekt, który zawiera nazwę, typ i wartość wyniku Obliczanie wyrażenia.  
  
 Podczas obliczania wyrażenia EE wymaga informacji ze składnika dostawcy symbolu. Dostawca symbol udostępnia symboliczne informacje używane do identyfikacji i opis przeanalizowany wyrażenia.  
  
 Po zakończeniu asynchronicznego wyrażenia Zdarzenie asynchroniczne jest wysyłane przez DE za pośrednictwem Menedżera sesji debugowania (SDM) do powiadamiania IDE zakończeniu Obliczanie wyrażenia. Po zakończeniu oceny wyrażenia synchroniczne wyniki oceny jest zwracana z wywołania `IDebugExpression2::EvaluateSync` metody.  
  
## <a name="implementation-notes"></a>Uwagi dotyczące implementacji  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Aparatami debugowania oczekiwać Porozmawiaj z ewaluatora wyrażenia, za pomocą interfejsów środowiska uruchomieniowego języka wspólnego (CLR). W związku z tym ewaluatora wyrażeń działające z [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] aparatami debugowania musi obsługiwać środowiska CLR (pełna lista wszystkich debugowanie interfejsy CLR można znaleźć w debugref.doc, który jest częścią programu [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)]).  
  
## <a name="see-also"></a>Zobacz też  
 [Składniki debugera](../../extensibility/debugger/debugger-components.md)