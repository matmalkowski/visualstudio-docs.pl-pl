---
title: Zmiana wartości zmiennej lokalnej | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, changing values programmatically
ms.assetid: 8407d3df-d38a-4328-82d1-98084bef43ec
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 422d1702f319db6da21892bcaa1bd50adad7909d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="changing-the-value-of-a-local"></a>Zmiana wartości zmiennej lokalnej
> [!IMPORTANT]
>  W programie Visual Studio 2015 ten sposób wdrażania ewaluatorów wyrażeń jest przestarzały. Aby uzyskać informacje dotyczące wdrożenia ewaluatorów wyrażeń CLR, zobacz [Ewaluatorów wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane próbki ewaluatora wyrażenia](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Gdy jest wpisana nową wartość w polu wartość **zmiennych lokalnych** okna, pakiet debugowania przekazuje ciąg, jak została wpisana do ewaluatora wyrażenia (EE). EE daje w wyniku tego ciągu, który może zawierać prosty wartość lub wyrażenie i przechowuje wartość wynikową w lokalnej skojarzone.  
  
 Ten temat zawiera omówienie procesu zmiany wartości elementu lokalnego:  
  
1.  Gdy użytkownik wprowadzi nową wartość, Visual Studio wymaga [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) na [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) obiekt skojarzony z lokalnym.  
  
2.  `IDebugProperty2::SetValueAsString` wykonuje następujące zadania:  
  
    1.  Oblicza ciąg w celu utworzenia wartości.  
  
    2.  Wiąże skojarzony [IDebugField](../../extensibility/debugger/reference/idebugfield.md) obiektu uzyskanie [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) obiektu.  
  
    3.  Konwertuje wartość na serię bajtów.  
  
    4.  Wywołania [SetValue](../../extensibility/debugger/reference/idebugobject-setvalue.md) aby umieścić wartości bajtów do pamięci, aby program debugowany mogą uzyskiwać do nich dostęp.  
  
3.  Odświeża programu Visual Studio **zmiennych lokalnych** wyświetlić (zobacz [wyświetlanie zmiennych lokalnych](../../extensibility/debugger/displaying-locals.md) szczegółowe informacje).  
  
 Ta procedura umożliwia również zmienić wartość zmiennej w **czujki** okno, ale jest `IDebugProperty2` obiektu skojarzone z wartością używaną zamiast lokalnej `IDebugProperty2` obiekt skojarzony z lokalnym samego siebie.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Przykład implementacji zmieniania wartości](../../extensibility/debugger/sample-implementation-of-changing-values.md)  
 Używa próbki MyCEE do kroków procesu zmiany wartości.  
  
## <a name="see-also"></a>Zobacz też  
 [Zapisywanie Ewaluator wyrażeń CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Wyświetlanie zmiennych lokalnych](../../extensibility/debugger/displaying-locals.md)