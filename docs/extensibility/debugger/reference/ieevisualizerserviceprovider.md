---
title: IEEVisualizerServiceProvider | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEEVisualizerServiceProvider
helpviewer_keywords: IEEVisualizerServiceProvider interface
ms.assetid: 859d1a51-1c65-4c8b-ae74-3b74b181ebcd
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4bd55bb42f902bcda7cdef1ea28a8d1c39d96f26
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ieevisualizerserviceprovider"></a>IEEVisualizerServiceProvider
> [!IMPORTANT]
>  W programie Visual Studio 2015 ten sposób wdrażania ewaluatorów wyrażeń jest przestarzały. Aby uzyskać informacje dotyczące wdrożenia ewaluatorów wyrażeń CLR, zobacz [Ewaluatorów wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane próbki ewaluatora wyrażenia](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Ten interfejs umożliwia dostęp do metody, której można utworzyć usługę wizualizatora, który jest używany do obsługi zadań wizualizatora typu dla IDE.  
  
## <a name="syntax"></a>Składnia  
  
```  
IEEVisualizerServiceProvider : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Visual Studio implementuje ten interfejs do utworzenia obiektu usługi wizualizatora, który z kolei jest używany do dostarczania identyfikatorów klas (`CLSID`s) o wizualizatorach typu do środowiska IDE programu Visual Studio.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Wywołuje ewaluatora wyrażenia (EE) [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md) uzyskanie tego interfejsu.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)|Tworzy usługę wizualizatora|  
  
## <a name="remarks"></a>Uwagi  
 `IEEVisualizerServiceProvider` Interfejsu są uzyskiwane podczas stosowania [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). Usługę wizualizatora, która tworzy ten interfejs jest używany do dostarczania funkcje [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) interfejsu, który EE jest odpowiedzialny za wdrażanie. EE jest również odpowiedzialne za wdrożenie [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) interfejs, umożliwiający wizualizatorach typu wyświetlić i zmodyfikować wartości właściwości.  
  
 Zobacz [Visualizing i wyświetlanie danych](../../../extensibility/debugger/visualizing-and-viewing-data.md) szczegółowe informacje dotyczące sposobu interakcji tych interfejsów.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy Obliczanie wyrażenia](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)   
 [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [Wizualizacja i wyświetlanie danych](../../../extensibility/debugger/visualizing-and-viewing-data.md)