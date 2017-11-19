---
title: "Kluczowe interfejsy ewaluatora wyrażeń | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, interfaces
ms.assetid: 1cac9aa3-0867-4e12-a16e-1e90abbc0fb6
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a03d419122f3cb72b3b9573279b41bc0de2636c5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="key-expression-evaluator-interfaces"></a>Wyrażenie klucza ewaluatora interfejsów
> [!IMPORTANT]
>  W programie Visual Studio 2015 ten sposób wdrażania ewaluatorów wyrażeń jest przestarzały. Aby uzyskać informacje dotyczące wdrożenia ewaluatorów wyrażeń CLR, zobacz [Ewaluatorów wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane próbki ewaluatora wyrażenia](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Podczas zapisywania ewaluatora wyrażeń (EE), oraz kontekst oceny, należy zapoznać się z następujących interfejsów.  
  
## <a name="interface-descriptions"></a>Opis interfejsu  
  
-   [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)  
  
     Zawiera tylko jedną metodę [GetAddress](../../extensibility/debugger/reference/idebugaddress-getaddress.md), które pobiera to struktura danych który reprezentuje bieżącego punktu wykonania. Ta struktura danych jest jednym z trzech argumentów, które aparat debugowania (DE) przekazuje do [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) metody można obliczyć wyrażenia. Ten interfejs jest zwykle implementowana przez dostawcę symbolu.  
  
-   [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)  
  
     Ma [powiązać](../../extensibility/debugger/reference/idebugbinder-bind.md) metodę, która pobiera obszar pamięci, która zawiera bieżącą wartość symbolu. Podano zarówno zawierającego metodę reprezentowany przez [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) obiekt i symbol, reprezentowany przez [IDebugField](../../extensibility/debugger/reference/idebugfield.md) obiektu, `IDebugBinder::Bind` zwraca wartość symbolu. `IDebugBinder`Zazwyczaj jest implementowany przez Niemcy.  
  
-   [IDebugField](../../extensibility/debugger/reference/idebugfield.md)  
  
     Reprezentuje prostego typu danych. Dla typów złożonych, takich jak tablice i metody, użyj pochodnej [IDebugArrayField](../../extensibility/debugger/reference/idebugarrayfield.md) i [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) interfejsy odpowiednio. [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) jest inny interfejs pochodny ważne reprezentuje symbole zawierające inne symbole, takie jak metod lub klas. `IDebugField` Interfejsu (i jego pochodne) jest zwykle implementowana przez dostawcę symbolu.  
  
     `IDebugField` Obiekt może być używane, aby znaleźć nazwę i typ symbolu i wraz z [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) obiektów, można użyć w celu znalezienia jej wartość.  
  
-   [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
     Reprezentuje liczbę bitów wartości środowiska wykonawczego symbolu. [Powiąż](../../extensibility/debugger/reference/idebugbinder-bind.md) przyjmuje [IDebugField](../../extensibility/debugger/reference/idebugfield.md) obiektu, który reprezentuje symbol i zwraca [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) obiektu. [GetValue](../../extensibility/debugger/reference/idebugobject-getvalue.md) metoda zwraca wartość symbolu w buforze pamięci. Niemcy zwykle implementuje ten interfejs reprezentujący wartość właściwości w pamięci.  
  
-   [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)  
  
     Ten interfejs reprezentuje sama ewaluatora wyrażenia. Metoda klucza jest [przeanalizować](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md), która zwraca [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) interfejsu.  
  
-   [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)  
  
     Ten interfejs reprezentuje wyrażenie przeanalizowany gotowy do obliczenia. Metoda klucza jest [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) co powoduje zwrócenie jako IDebugProperty2 reprezentujący wartości i typ wyrażenia.  
  
-   [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)  
  
     Ten interfejs reprezentuje wartość i jej typu i jest wynikiem Obliczanie wyrażenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontekst oceny](../../extensibility/debugger/evaluation-context.md)