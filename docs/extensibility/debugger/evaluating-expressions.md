---
title: Ocena wyrażeń | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expressions [Debugging SDK], evaluating
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5ccfcc80-dea5-48a1-8bae-6a26f8d3bc56
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 47de275d63f5be1743408aa93c971dcff2959c25
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31102795"
---
# <a name="evaluating-expressions"></a>Obliczenia wyrażenia
Wyrażenia są tworzone na podstawie ciągi przekazywane z automatycznych, Watch, QuickWatch lub bezpośredniego systemu windows. Wyrażenie jest obliczane, generuje drukowalnych ciąg znaków zawierający nazwę i typ zmiennej lub argumentu i jego wartość. Ten ciąg jest wyświetlane w oknie odpowiedniego IDE.  
  
## <a name="implementation"></a>Implementacja  
 Wyrażenia są oceniane po zatrzymaniu programu w punkcie przerwania. Wyrażenia jest reprezentowana przez [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interfejsu, co oznacza wyrażenie przeanalizowane, który jest gotowy do powiązania i oceny w kontekście oceny danego wyrażenia. Ramka stosu Określa kontekst oceny wyrażenia, który dostarcza aparat debugowania (DE) przez zaimplementowanie [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfejsu.  
  
 Podany ciąg użytkownika i [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfejsu, aparat debugowania (DE) można uzyskać [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interfejsu przez przekazanie użytkownika ciąg [ IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) metody. Interfejs IDebugExpression2 zwrócił zawiera wyrażenie przeanalizowany gotowy do oceny.  
  
 Z `IDebugExpression2` interfejsu, DE można uzyskać wartość wyrażenia za pomocą wyrażenia synchroniczna lub asynchroniczna, za pomocą [IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) lub [IDebugExpression2:: EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md). Ta wartość, oraz nazwę i typ zmiennej lub argumentu, są wysyłane do środowiska IDE do wyświetlenia. Wartość, nazwę i typ są reprezentowane przez [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interfejsu.  
  
 Aby umożliwić obliczenie wyrażenia, musi implementować URZ [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) i [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfejsów. Ocena synchroniczne i asynchroniczne wymagają wykonania [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) metody.  
  
## <a name="see-also"></a>Zobacz też  
 [Ramki stosu](../../extensibility/debugger/stack-frames.md)   
 [Kontekst oceny wyrażenia](../../extensibility/debugger/expression-evaluation-context.md)   
 [Zadania debugowania](../../extensibility/debugger/debugging-tasks.md)