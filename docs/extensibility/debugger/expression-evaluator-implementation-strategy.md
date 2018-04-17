---
title: Strategii wdrażania ewaluatora wyrażeń | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, implementation strategy
- debug engines, implementation strategies
ms.assetid: 1bccaeb3-8109-4128-ae79-16fd8fbbaaa2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e67b2496c2e30428cd4cc830526e53cf0cc61fdd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="expression-evaluator-implementation-strategy"></a>Strategii wdrażania ewaluatora wyrażenia
> [!IMPORTANT]
>  W programie Visual Studio 2015 ten sposób wdrażania ewaluatorów wyrażeń jest przestarzały. Aby uzyskać informacje dotyczące wdrożenia ewaluatorów wyrażeń CLR, zobacz [Ewaluatorów wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane próbki ewaluatora wyrażenia](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Jednym z podejść do szybkiego tworzenia ewaluatora wyrażeń (EE) jest najpierw zaimplementowanie minimalna kod niezbędne do wyświetlania zmiennych lokalnych w **zmiennych lokalnych** okna. Warto należy pamiętać, że każdy wiersz w **zmiennych lokalnych** okno wyświetla nazwę, typ i wartość zmiennej lokalnej, a wszystkie trzy są reprezentowane przez [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) obiektu. Nazwa, typ i wartość zmiennej lokalnej można uzyskać od `IDebugProperty2` obiektu przez wywołanie jego [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) metody. Aby uzyskać więcej informacji o wyświetlaniu zmiennych lokalnych w **zmiennych lokalnych** okna, zobacz [wyświetlanie zmiennych lokalnych](../../extensibility/debugger/displaying-locals.md).  
  
## <a name="discussion"></a>Omówienie  
 Sekwencja wdrażanych rozpoczyna się od wykonania [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md). [Przeanalizować](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) i [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) metody muszą być wdrożone w celu wyświetlenia zmiennych lokalnych. Wywoływanie `IDebugExpressionEvaluator::GetMethodProperty` zwraca `IDebugProperty2` obiekt, który reprezentuje metodę: czyli [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) obiektu. Metody siebie nie są wyświetlane w **zmiennych lokalnych** okna.  
  
 [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) metody, które powinny być implementowane dalej. Aparat debugowania (DE) wywołuje tę metodę, aby uzyskać listę zmiennych lokalnych i argumenty przez przekazanie `IDebugProperty2::EnumChildren` `guidFilter` argument `guidFilterLocalsPlusArgs`. `IDebugProperty2::EnumChildren` wywołania [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) i [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md), połączenie wyników w pojedyncze wyliczenie. Zobacz [wyświetlanie zmiennych lokalnych](../../extensibility/debugger/displaying-locals.md) więcej szczegółów.  
  
## <a name="see-also"></a>Zobacz też  
 [Implementowanie ewaluatora wyrażeń](../../extensibility/debugger/implementing-an-expression-evaluator.md)   
 [Wyświetlanie zmiennych lokalnych](../../extensibility/debugger/displaying-locals.md)