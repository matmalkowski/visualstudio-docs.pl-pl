---
title: IActiveScriptProfilerControl::StartProfiling | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptProfilerControl.StartProfiling
apilocation: scrobj.dll
ms.assetid: 56a7b3b7-8c21-43d0-9d8b-53bbc19fabb9
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d5362eaba439ff7a645a8323c4eed5d9496f6d88
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercontrolstartprofiling"></a>IActiveScriptProfilerControl::StartProfiling
Uruchamia profilowanie na aparatu skryptów. Aparat skryptów tworzy wystąpienie obiektu profilera poprzez wywołanie [wywołanie funkcji CoCreateInstance](http://msdn.microsoft.com/en-us/7295a55b-12c7-4ed0-a7a4-9ecee16afdec).  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT StartProfiling(  
    [in] REFCLSID clsidProfilerObject,  
    [in] DWORD dwEventMask,  
    [in] DWORD dwContext);  
```  
  
#### <a name="parameters"></a>Parametry  
 `clsidProfilerObject`  
 [in] Klasy identyfikator (CLSID) do utworzenia obiektu profilera.  
  
 `dwEventMask`  
 [in] Maska bitów do 4-bajtowych, który określa typy zdarzeń. Bity są zdefiniowane w [wyliczenie PROFILER_EVENT_MASK](../../winscript/reference/profiler-event-mask-enumeration.md).  
  
 `dwContext`  
 [in] Wartość 4-bajtowych, która została przekazana do obiektu profilera.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość HRESULT. Dopuszczalne są następujące wartości:  
  
|Wartość zwracana|Znaczenie|  
|------------------|-------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`ACTIVPROF_E_PROFILER_PRESENT`|Profilowanie jest już włączony.|  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IActiveScriptProfilerControl](../../winscript/reference/iactivescriptprofilercontrol-interface.md)