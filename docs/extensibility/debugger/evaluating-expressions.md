---
title: Ocenianie wyrażeń | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: bfd6248b06b69fa89d1888467a70718cf98b2a9a
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2018
ms.locfileid: "39232471"
---
# <a name="evaluate-expressions"></a>Ocena wyrażenia
Wyrażenia są tworzone na podstawie ciągi przekazywane z **Autos**, **Obejrzyj**, **QuickWatch**, lub **bezpośrednie** systemu windows. Gdy wyrażenie jest obliczane, generuje drukowalnych ciąg, który zawiera nazwę i typ zmiennej lub argumentu i jego wartość. Ten ciąg jest wyświetlany w odpowiednie okno środowiska IDE.  
  
## <a name="implementation"></a>Implementacja  
 Wyrażenia są obliczane po zatrzymaniu w punkcie przerwania programu. Wyrażenia jest reprezentowany przez [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interfejs, który reprezentuje przeanalizowany wyrażenie, które jest gotowy do powiązania i oceniania w ramach oceny wyrażenia danego kontekstu. Ramka stosu Określa kontekst oceny wyrażeń dostarczający aparat debugowania (DE) przez zaimplementowanie [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfejsu.  
  
 Podany ciąg użytkownika i [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfejsu, aparat debugowania (DE) można uzyskać [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interfejsu, przekazując ciąg użytkownika [ IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) metody. Interfejs IDebugExpression2, która jest zwracana zawiera wyrażenie przeanalizowany gotowy do oceny.  
  
 Za pomocą `IDebugExpression2` interfejsu, DE można uzyskać wartość wyrażenia przez Obliczanie wyrażenia synchroniczna lub asynchroniczna, za pomocą [IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) lub [IDebugExpression2:: EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md). Tę wartość, wraz z nazwą i typ zmiennej lub argumentu, są wysyłane do IDE do wyświetlenia. Wartość, nazwę i typ są reprezentowane przez [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interfejsu.  
  
 Do włączenia oceny wyrażenia, musi implementować DE [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) i [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfejsów. Ocena synchroniczne i asynchroniczne, wymagają wprowadzenia [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) metody.  
  
## <a name="see-also"></a>Zobacz także  
 [Ramki stosu](../../extensibility/debugger/stack-frames.md)   
 [Kontekst oceny wyrażeń](../../extensibility/debugger/expression-evaluation-context.md)   
 [Debugowanie zadań](../../extensibility/debugger/debugging-tasks.md)