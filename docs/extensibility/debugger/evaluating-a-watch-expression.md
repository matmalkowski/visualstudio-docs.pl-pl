---
title: Obliczenie wyrażenia czujki | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, watch expressions
- watch expressions
ms.assetid: 8317cd52-6fea-4e8f-a739-774dc06bd44b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5d86b94a457934547037f2428e6284f20de1660d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="evaluating-a-watch-expression"></a>Obliczenie wyrażenia czujki
> [!IMPORTANT]
>  W programie Visual Studio 2015 ten sposób wdrażania ewaluatorów wyrażeń jest przestarzały. Aby uzyskać informacje dotyczące wdrożenia ewaluatorów wyrażeń CLR, zobacz [Ewaluatorów wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane próbki ewaluatora wyrażenia](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Gdy program Visual Studio jest gotowy do wyświetlenia wartości wyrażenia czujki, wywołuje [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) które z kolei wywołuje [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). Spowoduje to utworzenie [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) obiekt, który zawiera wartości i typ wyrażenia.  
  
 W tej implementacji `IDebugParsedExpression::EvaluateSync`, wyrażenie jest analizowana i oceniane w tym samym czasie. Ta implementacja wykonuje następujące zadania:  
  
1.  Analizuje i ocenia wyrażenie, tak aby utworzyć obiekt ogólnego, który przechowuje wartości i jej typie. W języku C# jest reprezentowane jako `object` podczas w języku C++ jest reprezentowane jako `VARIANT`.  
  
2.  Tworzy wystąpienie klasy (nazywane `CValueProperty` w tym przykładzie), który zawiera `IDebugProperty2` interfejsu i są przechowywane w klasie wartość zwracaną.  
  
3.  Zwraca `IDebugProperty2` interfejsu z `CValueProperty` obiektu.  
  
## <a name="managed-code"></a>Zarządzany kod  
 Jest to implementacja `IDebugParsedExpression::EvaluateSync` w kodzie zarządzanym. Metoda pomocnicza `Tokenize` analizuje wyrażenia na drzewo analizy. Funkcja Pomocnika `EvalToken` konwertuje wartość tokenu. Funkcja Pomocnika `FindTerm` rekursywnie jest przesyłany w drzewie analizy wywoływania `EvalToken` dla każdego węzła reprezentujący wartość i stosowania żadnych operacji (dodawania lub odejmowania) w wyrażeniu.  
  
```csharp  
namespace EEMC  
{  
    public class CParsedExpression : IDebugParsedExpression  
    {  
        public HRESULT EvaluateSync(  
            uint evalFlags,  
            uint timeout,  
            IDebugSymbolProvider provider,  
            IDebugAddress address,  
            IDebugBinder binder,  
            string resultType,  
            out IDebugProperty2 result)  
        {  
            HRESULT retval = COM.S_OK;  
            this.evalFlags = evalFlags;  
            this.timeout = timeout;  
            this.provider = provider;  
            this.address = address;  
            this.binder = binder;  
            this.resultType = resultType;  
  
            try  
            {  
                IDebugField field = null;  
                // Tokenize, then parse.  
                tokens = Tokenize(expression);  
                result = new CValueProperty(  
                             expression,  
                             (int) FindTerm(EvalToken(tokens[0], out field),1),  
                             field,  
                             binder);  
            }  
            catch (ParseException)  
            {  
                result = new CValueProperty(expression, "Huh?");  
                retval = COM.E_INVALIDARG;  
            }  
            return retval;  
        }  
    }  
}  
```  
  
## <a name="unmanaged-code"></a>Niezarządzany kod  
 Jest to implementacja `IDebugParsedExpression::EvaluateSync` za pomocą kodu niezarządzanego. Funkcja Pomocnika `Evaluate` analizuje i ocenia wyrażenie zwracające `VARIANT` zawierający wynikowej wartości. Funkcja Pomocnika `VariantValueToProperty` pakiety `VARIANT` do `CValueProperty` obiektu.  
  
```  
[C++]  
STDMETHODIMP CParsedExpression::EvaluateSync(   
    in  DWORD                 evalFlags,  
    in  DWORD                 dwTimeout,  
    in  IDebugSymbolProvider* pprovider,  
    in  IDebugAddress*        paddress,  
    in  IDebugBinder*         pbinder,  
    in  BSTR                  bstrResultType,  
    out IDebugProperty2**     ppproperty )  
{  
    // dwTimeout parameter is ignored in this implementation.  
    if (pprovider == NULL)  
        return E_INVALIDARG;  
  
    if (paddress == NULL)  
        return E_INVALIDARG;  
  
    if (pbinder == NULL)  
        return E_INVALIDARG;  
  
    if (ppproperty == NULL)  
        return E_INVALIDARG;  
    else  
        *ppproperty = 0;  
  
    HRESULT hr;  
    VARIANT value;  
    BSTR    bstrErrorMessage = NULL;  
    hr = ::Evaluate( pprovider,  
                     paddress,  
                     pbinder,  
                     m_expr,  
                     &bstrErrorMessage,  
                     &value );  
    if (hr != S_OK)  
    {  
        if (bstrErrorMessage == NULL)  
            return hr;  
  
        //we can display better messages ourselves.  
        HRESULT hrLocal = S_OK;  
        VARIANT varType;  
        VARIANT varErrorMessage;  
  
        VariantInit( &varType );  
        VariantInit( &varErrorMessage );  
        varErrorMessage.vt      = VT_BSTR;  
        varErrorMessage.bstrVal = bstrErrorMessage;  
  
        CValueProperty* valueProperty = new CValueProperty();  
        if (valueProperty != NULL)  
        {  
            hrLocal = valueProperty->Init(m_expr, varType, varErrorMessage);  
            if (SUCCEEDED(hrLocal))   
            {  
                hrLocal = valueProperty->QueryInterface( IID_IDebugProperty2,  
                        reinterpret_cast<void**>(ppproperty) );  
            }  
        }  
  
        VariantClear(&varType);  
        VariantClear(&varErrorMessage); //frees BSTR  
        if (!valueProperty)  
            return hr;  
        valueProperty->Release();  
        if (FAILED(hrLocal))  
            return hr;  
    }  
    else  
    {  
        if (bstrErrorMessage != NULL)  
            SysFreeString(bstrErrorMessage);  
  
        hr = VariantValueToProperty( pprovider,  
                                     paddress,  
                                     pbinder,  
                                     m_radix,  
                                     m_expr,  
                                     value,  
                                     ppproperty );  
        VariantClear(&value);  
        if (FAILED(hr))  
            return hr;  
    }  
  
    return S_OK;  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Obliczenie wyrażenia okno czujki](../../extensibility/debugger/evaluating-a-watch-window-expression.md)   
 [Przykład implementacji oceny wyrażenia](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md)