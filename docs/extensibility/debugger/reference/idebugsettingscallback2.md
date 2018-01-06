---
title: IDebugSettingsCallback2 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugSettingsCallback2 interface
ms.assetid: 7e525d0b-7d7a-4d1c-8b78-e1398fa922f2
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 779550509dd6d30b16f30a47c1b9a2879d5034ab
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugsettingscallback2"></a>IDebugSettingsCallback2
Włącza debugowanie aparaty można odczytać ustawień metryki zdalnie.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugSettingsCallback2D : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Ten interfejs jest implementowany przez metodę wywołania zwrotnego zdarzeń Menedżera sesji debugowania i używane przez aparaty debugowania. Również zostać wykorzystana lokalnie zamiast .lib Dbgmetric [d].  
  
## <a name="methods"></a>Metody  
 W poniższej tabeli przedstawiono metody `IDebugSettingsCallback2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[EnumEEs](../../../extensibility/debugger/reference/idebugsettingscallback2-enumees.md)|Wylicza oceniających dostępne wyrażenie podane identyfikatorów języka i dostawcy.|  
|[GetEELocalObject](../../../extensibility/debugger/reference/idebugsettingscallback2-geteelocalobject.md)|Pobiera wyrażenie ewaluatora obiektu lokalnego podane metryki.|  
|[GetEEMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricdword.md)|Pobiera wartość, która odpowiada określonym Metryka ewaluatora wyrażenia.|  
|[GetEEMetricFile](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricfile.md)|Pobiera plik metryki ewaluatora wyrażenia, daną nazwę lub metryki.|  
|[GetEEMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricguid.md)|Pobiera unikatowy identyfikator dla podanej nazwy metryki ewaluatora wyrażenia.|  
|[GetEEMetricString](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricstring.md)|Pobiera ciąg wartość metryki ewaluatora wyrażenia, jego nazwę.|  
|[GetMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricdword.md)|Pobiera wartość metryki otrzymuje jej nazwę.|  
|[GetMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricguid.md)|Pobiera unikatowy identyfikator metryki otrzymuje jej nazwę.|  
|[GetMetricString](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricstring.md)|Pobiera ciąg wartość metryki otrzymuje jej nazwę.|  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia funkcję, która przyjmuje **IDebugSettingsCallback2** obiektu jako parametr.  
  
```cpp  
HRESULT GetDebugSettingsCallback (IDebugSettingsCallback2 **ppCallback)  
{  
    HRESULT hRes = E_FAIL;  
  
    if ( ppCallback )  
   {  
        if ( EVAL(m_pdec) )  
            hRes = m_pdec->QueryInterface(IID_IDebugSettingsCallback2, (void **)ppCallback);  
        else  
            hRes = E_FAIL;  
    }  
    else  
        hRes = E_INVALIDARG;  
  
    return ( hRes );  
}  
```