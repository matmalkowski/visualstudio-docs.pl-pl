---
title: IDebugExpressionEvaluator2::SetCallback | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugExpressionEvaluator2::SetCallback
- SetCallback
ms.assetid: 31e3a99e-e784-44a3-8b19-cc5ef31ed546
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a4860418edf2c0dcd4e9d0f6c98ea44db425034e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugexpressionevaluator2setcallback"></a>IDebugExpressionEvaluator2::SetCallback
Umożliwia ewaluatora wyrażenia (EE) określić interfejs wywołania zwrotnego, który aparat debugera (DE) będzie używany do odczytu ustawień metryki.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetCallback (  
   IDebugSettingsCallback2* pCallback  
);  
```  
  
```csharp  
int SetCallback (  
   IDebugSettingsCallback2 pCallback  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pCallback`  
 [in] Interfejs na potrzeby wywołania zwrotnego ustawienia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zapewnia interfejs do menedżera sesji debugowania, służącego do odczytu ustawień metryki ewaluatora wyrażeń. Jest on przydatny do zdalnego debugowania odczytać metryki na [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] komputera.  
  
## <a name="example"></a>Przykład  
 W poniższych przykładach przedstawiono sposób zaimplementować tę metodę do **CEE** obiekt ujawniający [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md) interfejsu.  
  
```cpp  
HRESULT CEE::SetCallback(IDebugSettingsCallback2* in_pCallback)  
{  
    // precondition  
    INVARIANT( this );  
  
    // function body  
    if (NULL != this->m_LanguageSpecificUseCases.pfSetCallback)  
    {  
        EEDomain::fSetCallback DomainVal =  
        {  
            in_pCallback  
        };  
  
        BOOL bSuccess = (*this->m_LanguageSpecificUseCases.pfSetCallback)(DomainVal);  
        ENSURE( bSuccess );  
    }  
  
    // postcondition  
    INVARIANT( this );  
  
    return S_OK;  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)