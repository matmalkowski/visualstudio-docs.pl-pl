---
title: Implementowanie Wizualizatorach typu i niestandardowych podglądy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: abef18c0-8272-4451-b82a-b4624edaba7d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c56d093c2e6380b29c8c9a788ea34d148fbe64b4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31105356"
---
# <a name="implementing-type-visualizers-and-custom-viewers"></a>Implementowanie Wizualizatorach typu i niestandardowych przeglądarki
> [!IMPORTANT]
>  W programie Visual Studio 2015 ten sposób wdrażania ewaluatorów wyrażeń jest przestarzały. Aby uzyskać informacje dotyczące wdrożenia ewaluatorów wyrażeń CLR, zobacz [Ewaluatorów wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane próbki ewaluatora wyrażenia](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Wizualizatorach typu i niestandardowych podglądy zezwolić użytkownikowi na wyświetlanie danych określonego typu w sposób bardziej zrozumiałą proste zrzutu szesnastkową liczby. Ewaluatora wyrażeń (EE) można skojarzyć niestandardowe przeglądarki z określonych typów danych lub zmienne. Te niestandardowe podglądy są implementowane przez EE. EE może również obsługiwać wizualizatorach typu zewnętrznego, które mogą pochodzić z innego dostawcy innych firm lub nawet użytkownika końcowego.  
  
## <a name="discussion"></a>Omówienie  
  
### <a name="type-visualizers"></a>Wizualizatorach typu  
 Visual Studio zapyta, aby uzyskać listę wizualizatorach typu i niestandardowych przeglądarki dla każdego obiektu do wyświetlenia w oknie czujki. Ewaluator wyrażeń (EE) udostępnia listę dla każdego typu, dla których chce obsługuje wizualizatorach typu i niestandardowych przeglądarki. Wywołuje się [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) i [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) start cały proces uzyskiwania dostępu do wizualizatorach typu i niestandardowych przeglądarki (zobacz [Visualizing i wyświetlanie danych](../../extensibility/debugger/visualizing-and-viewing-data.md)szczegółowe informacje na temat sekwencja wywoływania).  
  
### <a name="custom-viewers"></a>Niestandardowe przeglądarki  
 Niestandardowe przeglądarki są implementowane w EE dla określonego typu danych i są reprezentowane przez [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) interfejsu. Podglądu niestandardowego nie jest tak elastyczne, jak typ wizualizatora, ponieważ jest dostępny tylko wtedy, gdy jest wykonywany EE, implementujący tego konkretnego podglądu niestandardowego. Implementowanie podglądu niestandardowego jest łatwiejsze niż w przypadku implementowania obsługę wizualizatorach typu. Jednak obsługa wizualizatorach typu zapewnia maksymalną elastyczność dla użytkownika końcowego do wizualizacji danych własnego. W pozostałej części tej dyskusji dotyczy tylko typu wizualizatorów.  
  
## <a name="interfaces"></a>Interfejsy  
 EE implementuje następujące interfejsy do obsługi wizualizatorach typu, jest używane przez program Visual Studio:  
  
-   [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)  
  
-   [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md)  
  
-   [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md)  
  
-   [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md)  
  
-   [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md)  
  
-   [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
 EE wykorzystuje następujące interfejsy do obsługi wizualizatorach typu:  
  
-   [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)  
  
-   [IEEVisualizerServiceProvider](../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)  
  
-   [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Zapisywanie Ewaluator wyrażeń CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Wizualizacja i wyświetlanie danych](../../extensibility/debugger/visualizing-and-viewing-data.md)   
 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)