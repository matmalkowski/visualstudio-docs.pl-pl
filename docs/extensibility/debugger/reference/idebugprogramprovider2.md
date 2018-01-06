---
title: IDebugProgramProvider2 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgramProvider2
helpviewer_keywords: IDebugProgramProvider2 interface
ms.assetid: a9ec7b3e-a59c-4069-b2ee-6f45916eeb78
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 37771a5ea9f35075200cd5d5309bc5836afd11bc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogramprovider2"></a>IDebugProgramProvider2
Ten interfejs zarejestrowanych umożliwia sesji debugowania (SDM), aby uzyskać informacje o programach "opublikowane" za pośrednictwem Menedżera [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md) interfejsu.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugProgramProvider2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Aparat debugowania (DE) implementuje ten interfejs, aby podać informacje o debugowane programy. Ten interfejs jest zarejestrowany w sekcji DE rejestru za pomocą metryki `metricProgramProvider`, zgodnie z opisem w [pomocników zestawu SDK dla debugowania](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md).  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Wywołania modelu COM `CoCreateInstance` działać z `CLSID` dostawcy program, który jest uzyskany z rejestru. Zapoznaj się z przykładem.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)|Pobiera informacje o programach uruchomiony, filtrować na wiele sposobów.|  
|[GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)|Pobiera węzeł program podany identyfikator określonego procesu.|  
|[WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)|Ustanawia wywołanie zwrotne uwagę na zdarzenia dostawcy skojarzonego z określonych rodzajów procesów.|  
|[SetLocale](../../../extensibility/debugger/reference/idebugprogramprovider2-setlocale.md)|Określa ustawienia regionalne dla wszystkich wymaganych przez DE zasobów specyficzne dla języka.|  
  
## <a name="remarks"></a>Uwagi  
 Zwykle proces używa tego interfejsu, aby uzyskać informacje na temat programów uruchomionych w tym procesie.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="example"></a>Przykład  
  
```cpp  
IDebugProgramProvider2 *GetProgramProvider(GUID *pDebugEngineGuid)  
{  
    // This is typically defined globally.  For this example, it is  
    // defined here.  
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";  
    IDebugProgramProvider2 *pProvider = NULL;  
    if (pDebugEngineGuid != NULL) {  
        CLSID clsidProvider = { 0 };  
        ::GetMetric(NULL,  
                    metrictypeEngine,  
                    *pDebugEngineGuid,  
                    metricProgramProvider,  
                    &clsidProvider,  
                    strRegistrationRoot);  
        if (!IsEqualGUID(clsidProvider,GUID_NULL)) {  
            CComPtr<IDebugProgramProvider2> spProgramProvider;  
            spProgramProvider.CoCreateInstance(clsidProvider);  
            if (spProgramProvider != NULL) {  
                pProvider = spProgramProvider.Detach();  
            }  
        }  
    }  
    return(pProvider);  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy Core](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)   
 [Pomocnicy zestawu SDK do debugowania](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)