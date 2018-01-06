---
title: Implementowanie GetMethodProperty | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GetMethodProperty method
- IDebugExpressionEvaluator2 property
ms.assetid: 6305874f-a2c4-4432-834c-07530ea84bff
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 09dacf87e672b584fb4c19012567d4caaaf38f7d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-getmethodproperty"></a>Implementowanie GetMethodProperty
> [!IMPORTANT]
>  W programie Visual Studio 2015 ten sposób wdrażania ewaluatorów wyrażeń jest przestarzały. Aby uzyskać informacje dotyczące wdrożenia ewaluatorów wyrażeń CLR, zobacz [Ewaluatorów wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane próbki ewaluatora wyrażenia](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Visual Studio wymaga aparatu debugowania (DE) [GetDebugProperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md), który z kolei wywołuje [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) Aby uzyskać informacje o bieżącej metody w ramce stosu.  
  
 Ta implementacja `IDebugExpressionEvaluator::GetMethodProperty` wykonuje następujące zadania:  
  
1.  Wywołania [GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md), przekazując [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) obiektu. Zwraca symbol dostawcy [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) reprezentujący metodę, która zawiera określony adres.  
  
2.  Uzyskuje [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) z `IDebugContainerField`.  
  
3.  Tworzy wystąpienie klasy (nazywane `CFieldProperty` w tym przykładzie), który zawiera [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interfejsu i zawiera `IDebugMethodField` zwróciła obiekt PS.  
  
4.  Zwraca `IDebugProperty2` interfejsu z `CFieldProperty` obiektu.  
  
## <a name="managed-code"></a>Zarządzany kod  
 Ten przykład przedstawia implementację `IDebugExpressionEvaluator::GetMethodProperty` w kodzie zarządzanym.  
  
```csharp  
namespace EEMC  
{  
    [GuidAttribute("462D4A3D-B257-4AEE-97CD-5918C7531757")]  
    public class EEMCClass : IDebugExpressionEvaluator  
    {  
        public HRESULT GetMethodProperty(  
                IDebugSymbolProvider symbolProvider,  
                IDebugAddress        address,  
                IDebugBinder         binder,  
                int                  includeHiddenLocals,  
            out IDebugProperty2      property)   
        {  
            IDebugContainerField containerField = null;  
            IDebugMethodField methodField       = null;  
            property = null;  
  
            // Get the containing method field.  
            symbolProvider.GetContainerField(address, out containerField);  
            methodField = (IDebugMethodField) containerField;  
  
            // Return the property of method field.  
            property = new CFieldProperty(symbolProvider, address, binder, methodField);  
            return COM.S_OK;  
        }  
    }  
}  
```  
  
## <a name="unmanaged-code"></a>Niezarządzany kod  
 Ten przykład przedstawia implementację `IDebugExpressionEvaluator::GetMethodProperty` za pomocą kodu niezarządzanego.  
  
```  
[CPP]  
STDMETHODIMP CExpressionEvaluator::GetMethodProperty(  
        in IDebugSymbolProvider *pprovider,  
        in IDebugAddress        *paddress,  
        in IDebugBinder         *pbinder,  
        in BOOL                  includeHiddenLocals,  
        out IDebugProperty2    **ppproperty  
    )  
{  
    if (pprovider == NULL)  
        return E_INVALIDARG;  
  
    if (ppproperty == NULL)  
        return E_INVALIDARG;  
    else  
        *ppproperty = 0;  
  
    HRESULT hr;  
    IDebugContainerField* pcontainer = NULL;  
  
    hr = pprovider->GetContainerField(paddress, &pcontainer);  
    if (FAILED(hr))  
        return hr;  
  
    IDebugMethodField*    pmethod    = NULL;  
    hr = pcontainer->QueryInterface( IID_IDebugMethodField,  
            reinterpret_cast<void**>(&pmethod));  
    pcontainer->Release();  
    if (FAILED(hr))  
        return hr;  
  
    CFieldProperty* pfieldProperty = new CFieldProperty( pprovider,  
                                                         paddress,  
                                                         pbinder,  
                                                         pmethod );  
    pmethod->Release();  
    if (!pfieldProperty)  
        return E_OUTOFMEMORY;  
  
    hr = pfieldProperty->Init();  
    if (FAILED(hr))  
    {  
        pfieldProperty->Release();  
        return hr;  
    }  
  
    hr = pfieldProperty->QueryInterface( IID_IDebugProperty2,  
            reinterpret_cast<void**>(ppproperty));  
    pfieldProperty->Release();  
  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady implementacji zmiennych lokalnych](../../extensibility/debugger/sample-implementation-of-locals.md)