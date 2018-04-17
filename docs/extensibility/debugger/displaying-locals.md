---
title: Wyświetlanie zmiennych lokalnych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, displaying locals
ms.assetid: 62264cec-845b-4233-aed7-0b038fa79250
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 03a3f08498e8b046b02defd32083677b7f39e7e5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="displaying-locals"></a>Wyświetlanie zmiennych lokalnych
> [!IMPORTANT]
>  W programie Visual Studio 2015 ten sposób wdrażania ewaluatorów wyrażeń jest przestarzały. Aby uzyskać informacje dotyczące wdrożenia ewaluatorów wyrażeń CLR, zobacz [Ewaluatorów wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane próbki ewaluatora wyrażenia](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Wykonanie zawsze odbywa się w kontekście metody, nazywany również metody zawierającej lub bieżącej metody. Podczas wykonywania jest wstrzymana, Visual Studio wywołuje aparat debugowania (DE), aby uzyskać listę zmiennych lokalnych i argumentów, nazywane zmiennych lokalnych metody. Visual Studio wyświetla te zmienne lokalne i ich wartości w **zmiennych lokalnych** okna.  
  
 Aby wyświetlić elementy lokalne, wywołuje DE [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) metoda należąca do EE i nadaje mu kontekst oceny, który jest, dostawcę symbolu (SP), bieżący adres wykonywania i obiektu wiążącego. Aby uzyskać więcej informacji, zobacz [kontekst oceny](../../extensibility/debugger/evaluation-context.md). Jeśli wywołanie zakończy się powodzeniem, `IDebugExpressionEvaluator::GetMethodProperty` metoda zwraca [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) obiektu, który reprezentuje metodę, która zawiera bieżący adres wykonywania.  
  
 Wywołania DE [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) uzyskanie [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) obiektu, który jest filtrowana do zwrócenia tylko zmienne lokalne i wyliczane w celu utworzenia listy [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md)struktury. Każda struktura zawiera nazwę, typ i wartość zmiennej lokalnej. Typu i wartości są przechowywane jako ciągi sformatowane odpowiednią do wyświetlania. Nazwa, typ i wartość są zwykle wyświetlane razem w jednym wierszu **zmiennych lokalnych** okna.  
  
> [!NOTE]
>  **QuickWatch** i **czujki** systemu windows również wyświetlane zmienne w tym samym formacie nazwę, wartość i typu. Jednak te wartości są uzyskiwane przez wywołanie metody [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) zamiast `IDebugProperty2::EnumChildren`.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Przykłady implementacji zmiennych lokalnych](../../extensibility/debugger/sample-implementation-of-locals.md)  
 Przykłady nawiązywał kroków procesu wdrażania zmiennych lokalnych.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Kontekst oceny](../../extensibility/debugger/evaluation-context.md)  
 W tym artykule wyjaśniono, że gdy aparat debugowania (DE) wywołuje ewaluatora wyrażenia (EE), przekazanie trzech argumentów.  
  
## <a name="see-also"></a>Zobacz też  
 [Zapisywanie Ewaluator wyrażeń CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)