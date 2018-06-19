---
title: Wizualizacja i wyświetlanie danych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], viewing data
- debugging [Debugging SDK], visualizing data
ms.assetid: 699dd0f5-7569-40b3-ade6-d0fe53e832bc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ebaa07c8fe70e1842334b0bf7c28eb7491fd9c44
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31132485"
---
# <a name="visualizing-and-viewing-data"></a>Wizualizacja i wyświetlanie danych
Wpisz wizualizatorów i niestandardowych podglądy wyświetlania danych w sposób zapewniający szybkie zrozumiały dla dewelopera. Ewaluator wyrażeń (EE) można obsługuje typ innych firm wizualizatorów a także podać własne niestandardowe przeglądarki.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Określa, ile wizualizatorach typu i podglądy niestandardowe są skojarzone z obiektu typu przez wywołanie metody [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) metody. Jeśli istnieje co najmniej jeden typ wizualizatora lub podglądu niestandardowego dostępne, Visual Studio wymaga [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) metodę, aby pobrać listę tych wizualizatorów i przeglądarki (w rzeczywistości listę `CLSID`s, który implementuje wizualizatory i przeglądarki) i wyświetla je użytkownikowi.  
  
## <a name="supporting-type-visualizers"></a>Obsługa Wizualizatorach typu  
 Istnieje wiele interfejsów, które EE musi implementować do obsługi wizualizatorach typu. Te interfejsy mogą być podzielone na dwie kategorie: te, które wizualizatorach typu i tych, które uzyskują dostęp do danych właściwości.  
  
### <a name="listing-type-visualizers"></a>Wizualizatorach typu Lista  
 EE obsługuje wyświetlanie wizualizatorach typu jego wykonywania `IDebugProperty3::GetCustomViewerCount` i `IDebugProperty3::GetCustomViewerList`. Te metody przekazywania wywołań do odpowiednich metod [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) i [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md).  
  
 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) są uzyskiwane przez wywołanie metody [CreateVisualizerService](../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md). Ta metoda wymaga [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md) interfejsu, które są uzyskiwane z [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) interfejsu przekazany do [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). `IEEVisualizerServiceProvider::CreateVisualizerService` wymaga również [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) i [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) interfejsów, które zostały przekazane do `IDebugParsedExpression::EvaluateSync`. Interfejs końcowe wymagane do utworzenia `IEEVisualizerService` interfejs jest [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md) interfejs, który implementuje EE. Ten interfejs umożliwia zmiany wprowadzane do właściwości wizualizowanego. Wszystkie właściwości dane są umieszczane w [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) interfejs, który również jest implementowana przez EE.  
  
### <a name="accessing-property-data"></a>Uzyskiwanie dostępu do danych właściwości  
 Uzyskiwanie dostępu do właściwości danych odbywa się za pośrednictwem [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md) interfejsu. Aby uzyskać ten interfejs, wymaga programu Visual Studio [QueryInterface](/cpp/atl/queryinterface) właściwości obiektu można pobrać [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md) interfejsu (wdrożone na tym samym obiekcie, który implementuje [ IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) interface), a następnie wywołuje [GetPropertyProxy](../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) metodę, aby uzyskać `IPropertyProxyEESide` interfejsu.  
  
 Wszystkie dane przekazywane do i z `IPropertyProxyEESide` interfejsu jest hermetyzowany w [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md) interfejsu. Ten interfejs reprezentuje tablicę bajtów i jest implementowany przez EE i Visual Studio. Gdy właściwość data ma zostać zmieniony, program Visual Studio tworzy `IEEDataStorage` nowe dane i wywołania obiektu [CreateReplacementObject](../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) z tego obiektu danych, aby można było uzyskać nową `IEEDataStorage` obiekt, który z kolei jest przekazany do [InPlaceUpdateObject](../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md) , aby zaktualizować dane właściwości. `IPropertyProxyEESide::CreateReplacementObject` Umożliwia EE można utworzyć wystąpienia własnej klasy, która implementuje `IEEDataStorage` interfejsu.  
  
## <a name="supporting-custom-viewers"></a>Obsługa niestandardowych przeglądarki  
 Flaga `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` jest ustawiany w `dwAttrib` pole [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) struktury (zwrócony przez wywołanie do [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)) wskazująca, że obiekt ma podglądu niestandardowego skojarzone z nim. Gdy ta flaga jest ustawiona, Visual Studio uzyskuje [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) interfejsu z [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interfejs, za pomocą [QueryInterface](/cpp/atl/queryinterface).  
  
 Jeśli użytkownik wybierze podglądu niestandardowego, Visual Studio tworzy podglądu niestandardowego korzystanie z przeglądarki `CLSID` dostarczonych przez `IDebugProperty3::GetCustomViewerList` metody. Wywołuje program Visual Studio [się pozycje DisplayValue](../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) wyświetlać wartość dla użytkownika.  
  
 Zwykle `IDebugCustomViewer::DisplayValue` przedstawia widok tylko do odczytu danych. Aby zezwolić na zmiany danych, EE musi implementować niestandardowy interfejs, który obsługuje dane zmiany obiektu właściwości. `IDebugCustomViewer::DisplayValue` Metoda używa tego niestandardowy interfejs obsługuje zmiany danych. Metoda szuka niestandardowy interfejs `IDebugProperty2` interfejsu przekazany jako `pDebugProperty` argumentu.  
  
## <a name="supporting-both-type-visualizers-and-custom-viewers"></a>Obsługa zarówno wpisz Wizualizatorów i niestandardowych przeglądarki  
 EE może obsługiwać zarówno wizualizatorach typu, jak i niestandardowe przeglądarki w [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) i [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) metody. Najpierw EE dodaje do wartości zwracanej przez liczbę niestandardowych przeglądarek, które udostępnia on [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) metody. Po drugie, dołącza EE `CLSID`s własne niestandardowe przeglądarki do listy zwróconych przez [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) metody.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie zadań](../../extensibility/debugger/debugging-tasks.md)   
 [Wizualizator typów i przeglądarka niestandardowa](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)