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
ms.openlocfilehash: 1e1a91de0d2a0f4f4e114ccfc77c6a3ce97084d1
ms.sourcegitcommit: 36835f1b3ec004829d6aedf01938494465587436
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2018
ms.locfileid: "39203384"
---
# <a name="display-locals"></a>Wyświetlanie zmiennych lokalnych
> [!IMPORTANT]
>  W programie Visual Studio 2015 ten sposób implementowania ewaluatory wyrażeń jest przestarzały. Uzyskać informacji o implementowaniu ewaluatory wyrażeń CLR, zobacz [ewaluatory wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [przykładowe ewaluatora wyrażeń zarządzane](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Wykonanie zawsze odbywa się w kontekście metody, nazywana również metodą zawierającą lub bieżącej metody. Podczas wykonywania jest wstrzymana, Visual Studio wywołuje aparat debugowania (DE), aby uzyskać listę zmiennych lokalnych i argumenty, nazywane zmienne lokalne, metody. Visual Studio wyświetla te zmienne lokalne i ich wartości w **lokalne** okna.  
  
 Aby wyświetlić elementy lokalne, wywołuje DE [metody GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) metoda należąca do EE i nadaje jej kontekst oceny, który jest, dostawca symboli (SP), bieżący adres wykonywania i obiekt integratora. Aby uzyskać więcej informacji, zobacz [kontekst oceny](../../extensibility/debugger/evaluation-context.md). Jeśli wywołanie zakończy się powodzeniem, `IDebugExpressionEvaluator::GetMethodProperty` metoda zwraca [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) obiektu, który reprezentuje metodę, która zawiera bieżący adres wykonywania.  
  
 Wywołania DE [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) można pobrać [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) obiektu, który jest filtrowana, aby zwrócić tylko elementy lokalne i wyliczenia w celu wygenerowania listy [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md)struktury. Każda struktura zawiera nazwę, typ i wartość zmiennej lokalnej. Typ i wartość są przechowywane jako odpowiednią do wyświetlania sformatowanych ciągów. Nazwa, typ i wartość są zwykle wyświetlane razem w jednym wierszu **lokalne** okna.  
  
> [!NOTE]
>  **QuickWatch** i **Obejrzyj** również wyświetlania zmiennych o tym samym formacie nazwy, wartości i typ systemu windows. Jednak te wartości są uzyskiwane przez wywołanie metody [getpropertyinfo —](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) zamiast `IDebugProperty2::EnumChildren`.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Przykłady implementacji zmiennych lokalnych](../../extensibility/debugger/sample-implementation-of-locals.md)  
 Używa przykładów, aby przejść przez proces implementowania zmiennych lokalnych.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Kontekst oceny](../../extensibility/debugger/evaluation-context.md)  
 W tym artykule wyjaśniono, że gdy aparat debugowania (DE) wywołuje Ewaluator wyrażeń (EE), przekazuje on trzy argumenty.  
  
## <a name="see-also"></a>Zobacz także  
 [Pisanie ewaluatora wyrażeń środowiska CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)