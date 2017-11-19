---
title: Wyliczenie PROFILER_EVENT_MASK | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: PROFILER_EVENT_MASK
apilocation: scrobj.dll
ms.assetid: c2168408-f4f6-4600-971d-f15b4edf4ca2
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 68547fcb1fd2cd34b18a3d204baefd24d9da936b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="profilereventmask-enumeration"></a>Wyliczenie PROFILER_EVENT_MASK
Określa typy zdarzeń, które powinny być profilowane.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum {  
    PROFILER_EVENT_MASK_TRACE_SCRIPT_FUNCTION_CALL = 0x00000001,  
    PROFILER_EVENT_MASK_TRACE_NATIVE_FUNCTION_CALL = 0x00000002,  
    PROFILER_EVENT_MASK_TRACE_DOM_FUNCTION_CALL    = 0x00000004,  
    PROFILER_EVENT_MASK_TRACE_ALL =  
    PROFILER_EVENT_MASK_TRACE_SCRIPT_FUNCTION_CALL |  
    PROFILER_EVENT_MASK_TRACE_NATIVE_FUNCTION_CALL,  
    PROFILER_EVENT_MASK_TRACE_ALL_WITH_DOM = PROFILER_EVENT_MASK_TRACE_ALL |  
    PROFILER_EVENT_MASK_TRACE_DOM_FUNCTION_CALL  
} PROFILER_EVENT_MASK;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|PROFILER_EVENT_MASK_TRACE_SCRIPT_FUNCTION_CALL|Profile funkcje, które są zdefiniowane w skrypt zapisane przez użytkownika i kod dynamicznych.|  
|PROFILER_EVENT_MASK_TRACE_NATIVE_FUNCTION_CALL|Profile natywnego funkcje zdefiniowane przez aparat skryptów.|  
|PROFILER_EVENT_MASK_TRACE_ALL|Profile wszystkie funkcje zdefiniowane przez użytkownika i skryptów aparatu, z wyłączeniem wywołania do modelu DOM (Document Object).|  
|PROFILER_EVENT_MASK_TRACE_DOM_FUNCTION_CALL|Funkcje profilów, które wywołują modelu DOM.|  
|PROFILER_EVENT_MASK_TRACE_ALL_WITH_DOM|Profile wszystkich funkcji, w tym wywołania do modelu DOM.|  
  
## <a name="see-also"></a>Zobacz też  
 [Stałe profilera aktywnego skryptu, wyliczenia i struktury](../../winscript/reference/active-script-profiler-constants-enumerations-and-structures.md)   
 [IActiveScriptProfilerControl::SetProfilerEventMask](../../winscript/reference/iactivescriptprofilercontrol-setprofilereventmask.md)   
 [IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md)