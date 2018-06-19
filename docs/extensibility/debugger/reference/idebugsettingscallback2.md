---
title: IDebugSettingsCallback2 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugSettingsCallback2 interface
ms.assetid: 7e525d0b-7d7a-4d1c-8b78-e1398fa922f2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 54724d3e7652df6f7b5b61099136286257fca954
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31122408"
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
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
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