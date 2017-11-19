---
title: IEEVisualizerService | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEEVisualizerService
helpviewer_keywords: IEEVisualizerService interface
ms.assetid: 3bdb124b-c582-47ba-b465-13c6a1cdb702
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 404dcdd61955a1d3ac37fc2206d1b0fdf79684f6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ieevisualizerservice"></a>IEEVisualizerService
> [!IMPORTANT]
>  W programie Visual Studio 2015 ten sposób wdrażania ewaluatorów wyrażeń jest przestarzały. Aby uzyskać informacje dotyczące wdrożenia ewaluatorów wyrażeń CLR, zobacz [Ewaluatorów wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane próbki ewaluatora wyrażenia](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Ten interfejs implementuje klucza metod, zapewniających funkcje do [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) i [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) interfejsów.  
  
## <a name="syntax"></a>Składnia  
  
```  
IEEVisualizerService : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Visual Studio implementuje ten interfejs umożliwia ewaluatora wyrażeń (EE) do obsługi wizualizatorach typu.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Wywołania EE [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md) uzyskać ten interfejs w ramach wsparcia dla wizualizatorach typu.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)|Pobiera liczbę niestandardowych przeglądarki, o których wie, ta usługa.|  
|[GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)|Pobiera listę przeglądarek niestandardowych.|  
|[GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)|Zwraca obiekt serwera proxy dla właściwości.|  
|[GetValueDisplayStringCount](../../../extensibility/debugger/reference/ieevisualizerservice-getvaluedisplaystringcount.md)|Pobiera liczbę ciągi wartości dla określonej właściwości lub pola.|  
  
## <a name="remarks"></a>Uwagi  
 Używa IDE [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) interfejs do ustalenia, czy są wszystkie niestandardowe przeglądarki lub wpisz wizualizatorów dla właściwości. Tworząc usługę wizualizatora (z [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)), EE można podać funkcja `IDebugProperty3` i [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) (który obsługuje wyświetlanie i zmiana wartość właściwości) interfejsy i tym samym wspierania wizualizatorach typu.  
  
 Jeśli EE ma niestandardowy podglądy tego samego implementuje, dołączyć EE `CLSID`s te niestandardowe przeglądarki na końcu listy zwróconych przez [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md). Dzięki temu EE do obsługi własnych niestandardowych przeglądarek i wizualizatorach typu. Po prostu upewnij się, że [GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) odzwierciedla dodanie wszelkie niestandardowe przeglądarki.  
  
 Zobacz [Podgląd niestandardowe i typ wizualizatora](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) omówienie różnicy między wizualizatorów i przeglądarki.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy Obliczanie wyrażenia](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)   
 [Typ wizualizatora i podglądu niestandardowego](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)