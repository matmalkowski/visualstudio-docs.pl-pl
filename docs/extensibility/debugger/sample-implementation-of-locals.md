---
title: "Przykładowe implementacji zmienne lokalne | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], local variables
- expression evaluation, local variables
ms.assetid: 66a2e00a-f558-4e87-96b8-5ecf5509e04c
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 3e8157d6ecede516ca1dcb2900cf081c11a2b790
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="sample-implementation-of-locals"></a>Przykładowe zastosowanie zmiennych lokalnych
> [!IMPORTANT]
>  W programie Visual Studio 2015 ten sposób wdrażania ewaluatorów wyrażeń jest przestarzały. Aby uzyskać informacje dotyczące wdrożenia ewaluatorów wyrażeń CLR, zobacz [Ewaluatorów wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane próbki ewaluatora wyrażenia](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Poniżej przedstawiono omówienie sposobu uzyskiwania zmiennych lokalnych metody Visual Studio z ewaluatora wyrażenia (EE):  
  
1.  Visual Studio wymaga aparatu debugowania (DE) [GetDebugProperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) uzyskanie [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) obiekt, który reprezentuje wszystkie właściwości ramki stosu, w tym oknie zmienne lokalne.  
  
2.  `IDebugStackFrame2::GetDebugProperty`wywołania [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) można uzyskać obiektu, który opisuje metodę, w którym wystąpił punktu przerwania. Niemcy dostarcza dostawcy symbolu ([IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)), adres ([IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)) i integratora ([IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)).  
  
3.  `IDebugExpressionEvaluator::GetMethodProperty`wywołania [GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md) z podane `IDebugAddress` obiekt, aby pobrać [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) reprezentujący metodę zawierających określony adres.  
  
4.  `IDebugContainerField` Interfejs zostanie zapytany o [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) interfejsu. Jest to interfejs, który zapewnia dostęp do zmiennych lokalnych metody.  
  
5.  `IDebugExpressionEvaluator::GetMethodProperty`tworzy wystąpienie klasy (o nazwie `CFieldProperty` w próbce), który zawiera `IDebugProperty2` interfejs do reprezentowania metody zmiennych lokalnych. `IDebugMethodField` Obiekt znajduje się w tym `CFieldProperty` obiekt wraz z `IDebugSymbolProvider`, `IDebugAddress` i `IDebugBinder` obiektów.  
  
6.  Gdy `CFieldProperty` obiekt został zainicjowany, [GetInfo](../../extensibility/debugger/reference/idebugfield-getinfo.md) jest wywoływana w `IDebugMethodField` obiekt, aby uzyskać [FIELD_INFO](../../extensibility/debugger/reference/field-info.md) strukturę, która zawiera wszystkie zawiera informacje dotyczące tej metody .  
  
7.  `IDebugExpressionEvaluator::GetMethodProperty`Zwraca `CFieldProperty` obiekt jako `IDebugProperty2` obiektu.  
  
8.  Visual Studio wywołania [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) w zwróconym `IDebugProperty2` obiektu z filtrem `guidFilterLocalsPlusArgs`. To polecenie zwróci [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) obiekt zawierający metody zmiennych lokalnych. To wyliczenie jest wypełniane wywołań [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) i [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md).  
  
9. Visual Studio wywołania [dalej](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md) uzyskanie [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) struktury dla każdego lokalnych. Ta struktura zawiera wskaźnik do `IDebugProperty2` interfejsu na komputerze lokalnym.  
  
10. Visual Studio wywołania [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) dla każdego lokalnych można uzyskać nazwę, wartość oraz typu lokalnego. Są to informacje wyświetlane w **zmiennych lokalnych** okna.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Implementowanie metody GetMethodProperty](../../extensibility/debugger/implementing-getmethodproperty.md)  
 W tym artykule opisano implementacja [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md).  
  
 [Wyliczanie zmiennych lokalnych](../../extensibility/debugger/enumerating-locals.md)  
 W tym artykule opisano, jak aparat debugowania (DE) umożliwia wywołanie wyliczyć zmienne lokalne lub argumentów.  
  
 [Pobieranie właściwości lokalnych](../../extensibility/debugger/getting-local-properties.md)  
 W tym artykule opisano, jak DE nawiązuje połączenie uzyskać nazwę, typ i wartość jednego lub więcej zmiennych lokalnych.  
  
 [Pobieranie wartości lokalnych](../../extensibility/debugger/getting-local-values.md)  
 W tym artykule omówiono uzyskiwania wartości lokalnej, która wymaga usługi określonego przez kontekst oceny obiektu wiążącego.  
  
 [Ocenianie zmiennych lokalnych](../../extensibility/debugger/evaluating-locals.md)  
 W tym artykule wyjaśniono, jak są analizowane zmiennych lokalnych.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Kontekst oceny](../../extensibility/debugger/evaluation-context.md)  
 Zawiera argumenty, które są przekazywane, gdy DE wywołuje ewaluatora wyrażenia (EE).  
  
 [Przykładowe MyCEE](http://msdn.microsoft.com/en-us/624a018b-9179-402f-9d48-3aec87b48f4f)  
 Pokazuje, co implementacji podejście do tworzenia ewaluatora wyrażeń języka MyC.  
  
## <a name="see-also"></a>Zobacz też  
 [Wyświetlanie zmiennych lokalnych](../../extensibility/debugger/displaying-locals.md)