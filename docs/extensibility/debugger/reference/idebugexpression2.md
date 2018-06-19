---
title: IDebugExpression2 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugExpression2
helpviewer_keywords:
- IDebugExpression2 interface
ms.assetid: f5e4b124-1e30-47c8-a511-80084a02dba5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8cd5dcce6f81e8f61f13cc09dffb460449b0deae
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31114641"
---
# <a name="idebugexpression2"></a>IDebugExpression2
Ten interfejs reprezentuje gotowym przeanalizowany wyrażenia powiązania i oceny.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugExpression2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Aparat debugowania (DE) implementuje ten interfejs do reprezentowania gotowy do obliczenia wyrażenia przeanalizowany.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Wywołanie [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) zwraca tego interfejsu. [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) zwraca [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfejsu. Te interfejsy są dostępne tylko wtedy, gdy debugowany program został wstrzymany i ramka stosu jest dostępny.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 W poniższej tabeli przedstawiono metody `IDebugExpression2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Asynchronicznie obliczane wyrażenie.|  
|[Przerwania](../../../extensibility/debugger/reference/idebugexpression2-abort.md)|Kończy się asynchronicznego wyrażenia.|  
|[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Oblicza wyrażenie synchronicznie.|  
  
## <a name="remarks"></a>Uwagi  
 Gdy program został zatrzymany, Menedżer debugowania sesji (SDM) uzyskuje ramki stosu z DE wywołaniem [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md). Następnie wywołuje SDM [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) uzyskanie [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfejsu. Następuje wywołanie [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) utworzyć `IDebugExpression2` interfejsu reprezentuje wyrażenie przeanalizowany gotowy do obliczenia.  
  
 Wywołuje SDM, albo [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) lub [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) faktycznie oszacować wyrażenia i zwraca wartości.  
  
 W celu wykonania `IDebugExpressionContext2::ParseText`, DE używa modelu COM `CoCreateInstance` funkcja wystąpienia ewaluatora wyrażeń w celu uzyskania [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md) interfejsu (Zobacz przykład w `IDebugExpressionEvaluator` interfejs). Następnie wywołuje DE [przeanalizować](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) uzyskanie [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) interfejsu. Ten interfejs jest używany do implementacji `IDebugExpression2::EvaluateSync` i `IDebugExpression2::EvaluateAsync` Aby wykonać obliczenie.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy Core](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)