---
title: "Implementowanie ewaluatora wyrażeń | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
ms.assetid: e9ada7be-845e-4baa-bf8f-e4890e7ba490
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b8cb80098edf4f05de550c8b8a22e0ed0649ca26
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="implementing-an-expression-evaluator"></a>Implementowanie ewaluatora wyrażeń
> [!IMPORTANT]
>  W programie Visual Studio 2015 ten sposób wdrażania ewaluatorów wyrażeń jest przestarzały. Aby uzyskać informacje dotyczące wdrożenia ewaluatorów wyrażeń CLR, zobacz [Ewaluatorów wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane próbki ewaluatora wyrażenia](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Obliczenia wyrażenia jest złożona, wzajemna zależność między aparat debugowania (DE), dostawca symbolu (SP), obiektu wiążącego i ewaluatora wyrażenia (EE) sam. Te cztery składniki są połączone za interfejsów implementowanych przez jeden składnik i używane przez inną.  
  
 EE pobiera wyrażenie DE w postaci ciągu analizuje i ocenia go. EE implementuje następujące interfejsy, które są używane przez Niemcy:  
  
-   [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)  
  
-   [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)  
  
 EE wywołuje obiekt integratora dostarczonych przez DE, można uzyskać wartość symboli i obiektów. EE zużywa następujących interfejsów implementowanych przez Niemcy:  
  
-   [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
-   [IDebugArrayObject](../../extensibility/debugger/reference/idebugarrayobject.md)  
  
-   [IDebugFunctionObject](../../extensibility/debugger/reference/idebugfunctionobject.md)  
  
-   [IDebugPointerObject](../../extensibility/debugger/reference/idebugpointerobject.md)  
  
-   [IDebugManagedObject](../../extensibility/debugger/reference/idebugmanagedobject.md)  
  
-   [IEnumDebugObjects](../../extensibility/debugger/reference/ienumdebugobjects.md)  
  
-   [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)  
  
 Implementuje EE [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md). `IDebugProperty2`udostępnia mechanizm opisujące wynik wyrażenia, takie jak zmienna lokalna, typu pierwotnego lub obiekt, do programu Visual Studio, w którym są wyświetlane odpowiednie informacje w **zmiennych lokalnych**,  **Obejrzyj**, lub **Immediate** okna.  
  
 PS otrzymuje EE przez DE gdy sprawdza, czy informacje. PS implementuje interfejsów, które opisują pola, takie jak następujące interfejsy i ich pochodne i adresy:  
  
-   [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)  
  
-   [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)  
  
-   [IDebugField](../../extensibility/debugger/reference/idebugfield.md)  
  
 EE wykorzystuje wszystkie te interfejsy.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Strategii wdrażania ewaluatora wyrażenia](../../extensibility/debugger/expression-evaluator-implementation-strategy.md)  
 Definiuje proces trzech etapów strategii wdrażania expression evaluator (EE).  
  
## <a name="see-also"></a>Zobacz też  
 [Zapisywanie Ewaluator wyrażeń CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)