---
title: Wyliczenie profiler_script_type Enumeration | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- PROFILER_SCRIPT_TYPE
apilocation:
- scrobj.dll
ms.assetid: 3ab6633a-6241-44f0-b837-14336f70c71e
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 279969ec0b50f705e39d2e29e700adc1e833ead3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24796390"
---
# <a name="profilerscripttype-enumeration"></a>Wyliczenie PROFILER_SCRIPT_TYPE Enumeration
Określa typ skryptu.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum {  
    PROFILER_SCRIPT_TYPE_USER,  
    PROFILER_SCRIPT_TYPE_DYNAMIC,  
    PROFILER_SCRIPT_TYPE_NATIVE,  
    PROFILER_SCRIPT_TYPE_DOM  
} PROFILER_SCRIPT_TYPE;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|PROFILER_SCRIPT_TYPE_USER|Określa kod skryptu zapisane przez użytkownika.|  
|PROFILER_SCRIPT_TYPE_DYNAMIC|Określa kod skryptu, który jest generowany dynamicznie podczas wykonywania.|  
|PROFILER_SCRIPT_TYPE_NATIVE|Określa typ skryptu funkcje natywne i obiektów zdefiniowanych przez aparat skryptów.|  
|PROFILER_SCRIPT_TYPE_DOM|Określa wywołania do modelu DOM (Document Object) programu Internet Explorer, na przykład wywołanie `document.getElementById` metody.|  
  
## <a name="see-also"></a>Zobacz też  
 [Stałe profilera aktywnego skryptu, wyliczenia i struktury](../../winscript/reference/active-script-profiler-constants-enumerations-and-structures.md)   
 [IActiveScriptProfilerCallback::ScriptCompiled](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)   
 [IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)   
 [IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)