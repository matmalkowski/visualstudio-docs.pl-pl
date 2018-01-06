---
title: IDebugBreakpointErrorEvent2::GetErrorBreakpoint | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugBreakpointErrorEvent2::GetErrorBreakpoint
helpviewer_keywords: IDebugBreakpointErrorEvent2::GetErrorBreakpoint
ms.assetid: e5acfd19-ac17-47f3-a31a-b2aa8baca36d
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 0d4989fb601c45ad6e44e976b2c68756335ecf9b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugbreakpointerrorevent2geterrorbreakpoint"></a>IDebugBreakpointErrorEvent2::GetErrorBreakpoint
Pobiera [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) obiekt, który podano również uzasadnienie, dlaczego nie został powiązany punkt przerwania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetErrorBreakpoint(   
   IDebugErrorBreakpoint2** ppErrorBP  
);  
```  
  
```csharp  
int GetErrorBreakpoint(   
   out IDebugErrorBreakpoint2 ppErrorBP  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppErrorBP`  
 [out] Zwraca [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) obiektu, który opisuje ostrzeżenia lub błędu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Po `IDebugErrorBreakpoint2` interfejsu są uzyskiwane, należy wywołać [GetBreakpointResolution](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) metodę, aby pobrać [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md) obiektu. Następnie przy użyciu [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) metoda pozwala ustalić nieprawidłową lokalizację, to nieprawidłowe wyrażenie lub z przyczyn, dlaczego oczekującym punktem przerwania nie został powiązany, takie jak kod nie załadowano jeszcze i tak dalej.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób zaimplementować tę metodę do **CBreakpointSetDebugEventBase** obiekt ujawniający [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) interfejsu.  
  
```cpp  
STDMETHODIMP CBreakpointErrorDebugEventBase::GetErrorBreakpoint(  
    IDebugErrorBreakpoint2 **ppbp)  
{  
    HRESULT hRes = E_FAIL;  
  
    if ( ppbp )  
    {  
        if ( m_pError )  
        {  
            *ppbp = m_pError;  
  
            m_pError->AddRef();  
  
            hRes = S_OK;  
        }  
        else  
            hRes = E_FAIL;  
    }  
    else  
        hRes = E_INVALIDARG;  
  
    return ( hRes );  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)   
 [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)   
 [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)