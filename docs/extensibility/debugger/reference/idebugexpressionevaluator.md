---
title: IDebugExpressionEvaluator | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugExpressionEvaluator
helpviewer_keywords:
- IDebugExpressionEvaluator interface
ms.assetid: 0636d8c3-625a-49fa-94b6-516f22b7e1bc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d5a4b7061b5de50162bd04e033a983987ab4f35f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31117465"
---
# <a name="idebugexpressionevaluator"></a>IDebugExpressionEvaluator
> [!IMPORTANT]
>  W programie Visual Studio 2015 ten sposób wdrażania ewaluatorów wyrażeń jest przestarzały. Aby uzyskać informacje dotyczące wdrożenia ewaluatorów wyrażeń CLR, zobacz [Ewaluatorów wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane próbki ewaluatora wyrażenia](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Ten interfejs reprezentuje ewaluatora wyrażenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugExpressionEvaluator : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Ewaluator wyrażeń musi zawierać implementację tego interfejsu.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Aby uzyskać ten interfejs, wystąpienia ewaluatora wyrażenia, za pomocą `CoCreateInstance` metody za pomocą klasy ewaluatora identyfikator (CLSID). Zapoznaj się z przykładem.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 W poniższej tabeli przedstawiono metody `IDebugExpressionEvaluator`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[analizy](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)|Konwertuje ciąg wyrażenia przeanalizowany wyrażenia.|  
|[GetMethodProperty](../../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)|Pobiera zmienne lokalne, argumentów i inne właściwości metody.|  
|[GetMethodLocationProperty](../../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodlocationproperty.md)|Konwertuje metody lokalizacji i Przesunięcie na adres pamięci.|  
|[SetLocale](../../../extensibility/debugger/reference/idebugexpressionevaluator-setlocale.md)|Określa język utworzyć wyniki do druku.|  
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugexpressionevaluator-setregistryroot.md)|Ustawia katalog główny rejestru. Używane do debugowania side-by-side.|  
  
## <a name="remarks"></a>Uwagi  
 W przypadku typowej aparat debugowania (DE) tworzy ewaluatora wyrażenia (EE) w wyniku wywołania [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md). Ponieważ DE zna język i dostawcy EE chce używać, DE pobiera EE CLSID z rejestru ( [pomocników zestawu SDK dla debugowania](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) funkcji `GetEEMetric`, ułatwia to pobieranie).  
  
 Po EE zostanie uruchomiony, DE wywołuje [przeanalizować](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) można przeanalizować wyrażenia i umieszczenie go w [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) obiektu. Później wywołanie [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) oblicza wyrażenie.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pokazano, jak można utworzyć ewaluatora wyrażenia, podany adres i dostawcy symbol w kodzie źródłowym. W tym przykładzie użyto funkcji `GetEEMetric`, z [pomocników zestawu SDK dla debugowania](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) biblioteki, dbgmetric.lib.  
  
```cpp  
IDebugExpressionEvaluator GetExpressionEvaluator(IDebugSymbolProvider pSymbolProvider,  
                                                 IDebugAddress *pSourceAddress)  
{  
    // This is typically defined globally but is specified here just  
    // for this example.  
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";  
  
    IDebugExpressionEvaluator *pEE = NULL;  
    if (pSymbolProvider != NULL && pSourceAddress != NULL) {  
        HRESULT hr         = S_OK;  
        GUID  languageGuid = { 0 };  
        GUID  vendorGuid   = { 0 };  
  
        hr = pSymbolProvider->GetLanguage(pSourceAddress,  
                                          &languageGuid,  
                                          &vendorGuid);  
        if (SUCCEEDED(hr)) {  
            CLSID clsidEE      = { 0 };  
            CComPtr<IDebugExpressionEvaluator> spExpressionEvaluator;  
            // Get the expression evaluator's CLSID from the registry.  
            ::GetEEMetric(languageGuid,  
                          vendorGuid,  
                          metricCLSID,  
                          &clsidEE,  
                          strRegistrationRoot);  
            if (!IsEqualGUID(clsidEE,GUID_NULL)) {  
                // Instantiate the expression evaluator.  
                spExpressionEvaluator.CoCreateInstance(clsidEE);  
            }  
            if (spExpressionEvaluator != NULL) {  
                pEE = spExpressionEvaluator.Detach();  
            }  
        }  
    }  
    return pEE;  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy Obliczanie wyrażenia](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)   
 [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [Pomocnicy zestawu SDK do debugowania](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)