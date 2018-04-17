---
title: IDebugCustomViewer | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCustomViewer
helpviewer_keywords:
- IDebugCustomViewer interface
ms.assetid: 7aca27d3-c7b8-470f-b42c-d1e9d9115edd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3fb70365304883abe99a87cfec5e78bbed89f2dd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="idebugcustomviewer"></a>IDebugCustomViewer
Ten interfejs umożliwia ewaluatora wyrażeń (EE), aby wyświetlić wartość właściwości w dowolnie wybrany format jest konieczne.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugCustomViewer : IUknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 EE implementuje ten interfejs, aby wyświetlić wartość właściwości w niestandardowym formacie.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Wywołania modelu COM `CoCreateInstance` funkcja tworzy wystąpienie tego interfejsu. `CLSID` Przekazany do `CoCreateInstance` są uzyskiwane z rejestru. Wywołanie [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) uzyskuje lokalizacji w rejestrze. Zobacz uwagi szczegółowe informacje, jak również w przykładzie.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 Ten interfejs implementuje następującą metodę:  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Się pozycje DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md)|Nie, niezależnie od jest niezbędne do wyświetlania podanej wartości.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs jest używany, gdy wartość właściwości nie można wyświetlić w normalny sposób — na przykład z tabelą danych lub inny typ właściwości złożonej. Podglądu niestandardowego, reprezentowane przez `IDebugCustomViewer` interfejsu, jest inny niż typ wizualizatora, czyli programu zewnętrznego do wyświetlania danych o typie określonym niezależnie od EE. EE implementuje podglądu niestandardowego, które są specyficzne dla tego EE. Użytkownik wybiera typ wizualizatora do użycia, wizualizatora typu i podglądu niestandardowego. Zobacz [Visualizing i wyświetlanie danych](../../../extensibility/debugger/visualizing-and-viewing-data.md) szczegółowe informacje na temat tego procesu.  
  
 Podglądu niestandardowego jest zarejestrowany w taki sam sposób jak EE i dlatego wymaga języka identyfikator GUID i identyfikator GUID dostawcy. Dokładne metryki (lub nazwa wpisu rejestru) jest znany tylko EE. Ta metryka jest zwracany w [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) struktury, która z kolei jest zwracany przez wywołanie do [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md). Wartość przechowywana we metryka jest `CLSID` przekazanego do modelu COM `CoCreateInstance` funkcji (Zobacz przykład).  
  
 [Pomocników zestawu SDK dla debugowania](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) funkcji `SetEEMetric`, można użyć do zarejestrowania podglądu niestandardowego. W sekcji "Ewaluatorów wyrażeń" rejestru `Debugging SDK Helpers` dla kluczy rejestru, który wymaga podglądu niestandardowego. Należy pamiętać, że podglądu niestandardowego wymaga tylko jedna metryka, (która jest definiowana za pomocą implementujący EE) ewaluatora wyrażeń wymaga kilku predefiniowane metryki.  
  
 Zwykle podglądu niestandardowego udostępnia widok tylko do odczytu danych, ponieważ [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) interfejs dostarczony do [się pozycje DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) nie ma żadnych metod w przypadku zmiany wartości właściwości z wyjątkiem jako ciąg. Aby zapewnić obsługę zmiana dowolnego bloki danych, EE implementuje interfejs niestandardowe dla tego samego obiektu, który implementuje `IDebugProperty3` interfejsu. Ten niestandardowy interfejs będzie dostarczać metody zmiany dowolnego bloku danych.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="example"></a>Przykład  
 Ten przykład przedstawia, jak uzyskać pierwszy podglądu niestandardowego z właściwości, jeśli wszystkie niestandardowe podglądy tej właściwości.  
  
```cpp  
IDebugCustomViewer *GetFirstCustomViewer(IDebugProperty2 *pProperty)  
{  
    // This string is typically defined globally.  For this example, it  
    // is defined here.  
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";  
    IDebugCustomViewer *pViewer = NULL;  
    if (pProperty != NULL) {  
        CComQIPtr<IDebugProperty3> pProperty3(pProperty);  
        if (pProperty3 != NULL) {  
            HRESULT hr;  
            ULONG viewerCount = 0;  
            hr = pProperty3->GetCustomViewerCount(&viewerCount);  
            if (viewerCount > 0) {  
                ULONG viewersFetched = 0;  
                DEBUG_CUSTOM_VIEWER viewerInfo = { 0 };  
                hr = pProperty3->GetCustomViewerList(0,  
                                                     1,  
                                                     &viewerInfo,  
                                                     &viewersFetched);  
                if (viewersFetched == 1) {  
                    CLSID clsidViewer = { 0 };  
                    CComPtr<IDebugCustomViewer> spCustomViewer;  
                    // Get the viewer's CLSID from the registry.  
                    ::GetEEMetric(viewerInfo.guidLang,  
                                  viewerInfo.guidVendor,  
                                  viewerInfo.bstrMetric,  
                                  &clsidViewer,  
                                  strRegistrationRoot);  
                    if (!IsEqualGUID(clsidViewer,GUID_NULL)) {  
                        // Instantiate the custom viewer.  
                        spCustomViewer.CoCreateInstance(clsidViewer);  
                        if (spCustomViewer != NULL) {  
                            pViewer = spCustomViewer.Detach();  
                        }  
                    }  
                }  
            }  
        }  
    }  
    return(pViewer);  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy Core](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)   
 [Pomocnicy zestawu SDK do debugowania](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)