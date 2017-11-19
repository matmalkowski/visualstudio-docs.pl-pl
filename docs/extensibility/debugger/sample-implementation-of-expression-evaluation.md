---
title: "Przykładowe implementacji Szacowanie wyrażeń | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
- expression evaluation, examples
ms.assetid: 2a5f04b8-6c65-4232-bddd-9093653a22c4
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2cae1e8d697ba8079b29fa2188f0fb2f8b9a40e6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="sample-implementation-of-expression-evaluation"></a>Przykładowe zastosowanie Szacowanie wyrażeń
> [!IMPORTANT]
>  W programie Visual Studio 2015 ten sposób wdrażania ewaluatorów wyrażeń jest przestarzały. Aby uzyskać informacje dotyczące wdrożenia ewaluatorów wyrażeń CLR, zobacz [Ewaluatorów wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane próbki ewaluatora wyrażenia](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Dla **czujki** wyrażenia okna, wywołań Visual Studio [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) do produkcji [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) obiektu. `IDebugExpressionContext2::ParseText`tworzy wystąpienie ewaluatora wyrażeń (EE) i wywołania [przeanalizować](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) uzyskanie [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) obiektu.  
  
 Ta implementacja `IDebugExpressionEvaluator::Parse` wykonuje następujące zadania:  
  
1.  [Tylko C++] Analizuje wyrażenie, aby wyszukać błędy.  
  
2.  Tworzy wystąpienie klasy (nazywane `CParsedExpression` w tym przykładzie), który zawiera `IDebugParsedExpression` interfejsu i są przechowywane w klasie wyrażenie, które ma zostać przeanalizowany.  
  
3.  Zwraca `IDebugParsedExpression` interfejsu z `CParsedExpression` obiektu.  
  
> [!NOTE]
>  W przykładach, które należy wykonać i w przykładowym MyCEE Ewaluator wyrażeń nie oddzielne analizowania z oceny.  
  
## <a name="managed-code"></a>Zarządzany kod  
 Jest to implementacja `IDebugExpressionEvaluator::Parse` w kodzie zarządzanym. Należy pamiętać, że ta wersja metody różni się analizy do [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) jako kod analizy ocenia się również w tym samym czasie (zobacz [obliczenia wyrażenia czujki](../../extensibility/debugger/evaluating-a-watch-expression.md)).  
  
```csharp  
namespace EEMC  
{  
    public class CParsedExpression : IDebugParsedExpression  
    {  
        public HRESULT Parse(  
                string                 expression,   
                uint                   parseFlags,  
                uint                   radix,  
            out string                 errorMessage,   
            out uint                   errorPosition,   
            out IDebugParsedExpression parsedExpression)  
        {   
            errorMessage = "";  
            errorPosition = 0;  
  
            parsedExpression =  
                new CParsedExpression(parseFlags, radix, expression);  
            return COM.S_OK;  
        }  
    }  
}  
```  
  
## <a name="unmanaged-code"></a>Niezarządzany kod  
 Jest to implementacja `IDebugExpressionEvaluator::Parse` za pomocą kodu niezarządzanego. Ta metoda wywołuje funkcję Pomocnika `Parse`, można przeanalizować wyrażenia i sprawdź, czy błędy, ale ta metoda ignoruje wynikowej wartości. Posiadanie oceny została odroczona do [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) gdy wyrażenie jest analizowana podczas, gdy wartość jest szacowana (zobacz [obliczenia wyrażenia czujki](../../extensibility/debugger/evaluating-a-watch-expression.md)).  
  
```cpp  
STDMETHODIMP CExpressionEvaluator::Parse(  
        in    LPCOLESTR                 pszExpression,  
        in    PARSEFLAGS                flags,  
        in    UINT                      radix,  
        out   BSTR                     *pbstrErrorMessages,  
        inout UINT                     *perrorCount,  
        out   IDebugParsedExpression  **ppparsedExpression  
    )  
{  
    if (pbstrErrorMessages == NULL)  
        return E_INVALIDARG;  
    else  
        *pbstrErrormessages = 0;  
  
    if (pparsedExpression == NULL)  
        return E_INVALIDARG;  
    else  
        *pparsedExpression = 0;  
  
    if (perrorCount == NULL)  
        return E_INVALIDARG;  
  
    HRESULT hr;  
    // Look for errors in the expression but ignore results  
    hr = ::Parse( pszExpression, pbstrErrorMessages );  
    if (hr != S_OK)  
        return hr;  
  
    CParsedExpression* pparsedExpr = new CParsedExpression( radix, flags, pszExpression );  
    if (!pparsedExpr)  
        return E_OUTOFMEMORY;  
  
    hr = pparsedExpr->QueryInterface( IID_IDebugParsedExpression,  
                                      reinterpret_cast<void**>(ppparsedExpression) );  
    pparsedExpr->Release();  
  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Obliczenie wyrażenia okno czujki](../../extensibility/debugger/evaluating-a-watch-window-expression.md)   
 [Obliczenie wyrażenia czujki](../../extensibility/debugger/evaluating-a-watch-expression.md)