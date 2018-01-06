---
title: IDebugBinder | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugBinder
helpviewer_keywords: IDebugBinder interface
ms.assetid: d1f31e5b-c6e2-4e02-8959-b3e86041b29c
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f3377ade8cc4301e1d8a5be19c5d828755934ce9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugbinder"></a>IDebugBinder
> [!IMPORTANT]
>  W programie Visual Studio 2015 ten sposób wdrażania ewaluatorów wyrażeń jest przestarzały. Aby uzyskać informacje dotyczące wdrożenia ewaluatorów wyrażeń CLR, zobacz [Ewaluatorów wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane próbki ewaluatora wyrażenia](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Ten interfejs wiąże pole symbolu, zwykle zwrócony przez dostawcę symbolu, w kontekście pamięci lub obiekt zawierający bieżącą wartość symbolu.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugBinder : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Ten interfejs obsługuje Szacowanie wyrażeń i musi być implementowana przez aparat debugowania (DE).  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Ten interfejs jest używany w procesie oceny wyrażenia i zazwyczaj jest używane do implementacji [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) i [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md).  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 W poniższej tabeli przedstawiono metody `IDebugBinder`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[BIND](../../../extensibility/debugger/reference/idebugbinder-bind.md)|Pobiera kontekst pamięci lub obiekt zawierający bieżącą wartość symbolu.|  
|[ResolveRuntimeType](../../../extensibility/debugger/reference/idebugbinder-resolveruntimetype.md)|Określa typ obiektu środowiska wykonawczego.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugbinder-getmemorycontext.md)|Konwertuje adres pamięci lub lokalizacji obiektu do kontekstu pamięci.|  
|[GetFunctionObject](../../../extensibility/debugger/reference/idebugbinder-getfunctionobject.md)|Pobiera [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) obiekt używany do tworzenia parametrów funkcji.|  
|[ResolveDynamicType](../../../extensibility/debugger/reference/idebugbinder-resolvedynamictype.md)|Pobiera dokładnego typu zmienną.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs zwraca obiekty, które są używane przez ewaluatora wyrażenia w drzewach analizy. Ewaluator wyrażeń analizuje wyrażenie przy użyciu dostawcy symbol do przekonwertowania symbole w wyrażeniu do wystąpień [IDebugField](../../../extensibility/debugger/reference/idebugfield.md), opisywać każdego symbolu pod względem typu i lokalizacji w kodzie źródłowym. [Powiązać](../../../extensibility/debugger/reference/idebugbinder-bind.md) metoda konwertuje `IDebugField` obiekty do [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) typ obiektów, które nawiązania połączenia lub powiązać symbol na rzeczywistą wartość w pamięci. Te `IDebugObject` obiekty są następnie przechowywane w drzewie analizy w nowszej wersji ewaluacyjnej.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy Obliczanie wyrażenia](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)