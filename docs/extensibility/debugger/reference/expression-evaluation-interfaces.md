---
title: Interfejsy oceny wyrażenia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, interfaces
ms.assetid: 2d259f60-2cd7-460e-b02d-24a8fb202850
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: be9582f965fe1d8a00c97548dbc5f458ae4e1198
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31107403"
---
# <a name="expression-evaluation-interfaces"></a>Interfejsy Obliczanie wyrażenia
> [!IMPORTANT]
>  W programie Visual Studio 2015 ten sposób wdrażania ewaluatorów wyrażeń jest przestarzały. Aby uzyskać informacje dotyczące wdrożenia ewaluatorów wyrażeń CLR, zobacz [Ewaluatorów wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane próbki ewaluatora wyrażenia](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Poniżej przedstawiono interfejsy oceny wyrażenia [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] debugowanie zestawu SDK.  
  
## <a name="discussion"></a>Omówienie  
 Te interfejsy są używane do analizowania wyrażenia w stosie wywołań w trybie przerwania. Są one wykonywane tylko w przypadku typowych oceniających wyrażenia czasu wykonywania języka (EE).  
  
 Każdy interfejs w tabeli przedstawiono składnik, który można wdrożyć z poniższej listy:  
  
-   Debugowanie aparat (DE)  
  
-   Ewaluator wyrażeń (EE)  
  
-   Visual Studio (VS)  
  
|Interface|Implementowany przez|Opis|  
|---------------|--------------------|-----------------|  
|[IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)|EE|Reprezentuje alias liczbowa zmiennej.|  
|[IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)|EE|Reprezentuje alias liczbowa zmiennej i umożliwia ewaluatora wyrażeń (EE) można uzyskać w domenie aplikacji alias.|  
|[IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)|EE|Reprezentuje obiekt array.|  
|[IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)|EE|Reprezentuje obiekt tablicy zarządzanej i umożliwia ewaluatora wyrażeń (EE), aby określić indeks podstawowej (dolną granicę) dla tablicy.|  
|[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)|DE|Reprezentuje integrator, że wiązania debugowania symboli do rzeczywistego adresów w pamięci.|  
|[IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)|DE|Taki sam jak [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) interfejsu ale zapewnia dostęp do typów, aliasy i wizualizatory niestandardowe.|  
|[IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)|EE|Reprezentuje ewaluatora wyrażenia.|  
|[IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)|EE|Reprezentuje rozbudowaną wersją ewaluatora wyrażeń (EE).|  
|[IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md)|EE|Reprezentuje ewaluatora wyrażeń (EE) z drzewo rozszerzone analizatora.|  
|[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)|EE|Reprezentuje funkcję.|  
|[IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)|EE|Reprezentuje funkcję i zwiększa [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) interfejsu.|  
|[IDebugIDECallback](../../../extensibility/debugger/reference/idebugidecallback.md)|DE|Umożliwia ewaluatora wyrażeń (EE) wyświetlić komunikat w oknie danych wyjściowych debugera.|  
|[IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)|EE|Reprezentuje obiekt kodu zarządzanego.|  
|[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)|EE|Podstawowy interfejs, który reprezentuje dowolny symbol powiązany adres pamięci.|  
|[IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)|EE|Taki sam jak [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interfejsu ale zapewnia dostęp do dodatkowych informacji.|  
|[IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)|EE|Reprezentuje wyrażenie przeanalizowany gotowy do obliczenia.|  
|[IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)|EE|Reprezentuje wskaźnik.|  
|[IDebugPointerObject3](../../../extensibility/debugger/reference/idebugpointerobject3.md)|EE|Reprezentuje wskaźnik myszy w drzewie analizy i rozszerza **IDebugPointerObject** interfejsu.|  
|[IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)|EE|Pozwala, aby zmodyfikować wartości typu za pomocą typu wizualizatora.|  
|[IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)|VS|Zapewnia dostęp do niestandardowych przeglądarki i wizualizatorach typu.|  
|[IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)|VS|Zapewnia możliwość tworzenia [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) obiektu.|  
|[IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)|EE|Reprezentuje kolekcję [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) obiektów.|  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja interfejsu API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)   
 [Zapisywanie Ewaluator wyrażeń CLR](../../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Wizualizator typów i przeglądarka niestandardowa](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)