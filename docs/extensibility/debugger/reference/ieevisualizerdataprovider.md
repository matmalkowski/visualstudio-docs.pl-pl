---
title: IEEVisualizerDataProvider | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEEVisualizerDataProvider
helpviewer_keywords:
- IEEVisualizerDataProvider interface
ms.assetid: 5fdfe6e3-b94e-4edb-acc5-41d8773d8ca5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8e37561957d592ecd9ae855f2816c860f84e7b20
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="ieevisualizerdataprovider"></a>IEEVisualizerDataProvider
> [!IMPORTANT]
>  W programie Visual Studio 2015 ten sposób wdrażania ewaluatorów wyrażeń jest przestarzały. Aby uzyskać informacje dotyczące wdrożenia ewaluatorów wyrażeń CLR, zobacz [Ewaluatorów wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane próbki ewaluatora wyrażenia](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Ten interfejs umożliwia zmienić wartości obiektu za pomocą typu wizualizatora.  
  
## <a name="syntax"></a>Składnia  
  
```  
IEEVisualizerDataProvider : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Ewaluator wyrażeń implementuje ten interfejs obsługuje modyfikowanie danych w obiekcie właściwości za pośrednictwem wizualizatora typu.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Ten interfejs jest używany do tworzenia [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) obiektu poprzez wywołanie [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md). Zobacz [Visualizing i wyświetlanie danych](../../../extensibility/debugger/visualizing-and-viewing-data.md) więcej szczegółów.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CanSetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-cansetobjectforvisualizer.md)|Określa, czy można zaktualizować obiektu (i następnie jego wartość) reprezentujących tego wizualizatora.|  
|[GetNewObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getnewobjectforvisualizer.md)|Wymusza ponowną ocenę obiektu dla tego wizualizatora.|  
|[GetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getobjectforvisualizer.md)|Pobiera istniejący obiekt dla tego wizualizatora (nie oceny odbywa się).|  
|[SetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-setobjectforvisualizer.md)|Aktualizuje obiekt dla tego wizualizatora, zmieniając wartość, która przedstawia wizualizatora.|  
  
## <a name="remarks"></a>Uwagi  
 Usługę wizualizatora (reprezentowany przez [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) interfejsu i zwrócony przez [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)) przechowuje odwołanie do implementacji obiektu `IEEVisualizerDataProvider` — interfejs . W związku z tym `IEEVisualizerDataProvider` interfejsu nie powinny być implementowane w tym obiekcie, który implementuje [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) Jeśli ten obiekt przechowuje odwołanie do `IEEVisualizerService` obiektu: wyniki odwołanie cykliczne i Zakleszczenie występuje, gdy obiekty zostaną zniszczone. Zalecanym podejściem jest zaimplementowanie `IEEVisualizerDataProvider` na oddzielny obiekt, do którego `IDebugProperty2` obiekt delegatów bez wywoływania elementu `IUnknown::AddRef` na nim.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy Obliczanie wyrażenia](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)   
 [Wizualizacja i wyświetlanie danych](../../../extensibility/debugger/visualizing-and-viewing-data.md)