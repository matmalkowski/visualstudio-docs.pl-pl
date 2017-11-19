---
title: IActiveScriptProfilerCallback::ScriptCompiled | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptProfilerCallback.ScriptCompiled
apilocation: scrobj.dll
ms.assetid: 1bb8e9be-cbb1-4a61-b36c-805127a56ac7
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7ea1823087b323f2acc9b87edfce48bbe9f924bd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercallbackscriptcompiled"></a>IActiveScriptProfilerCallback::ScriptCompiled
Powiadamia profilera dla obiekt, który aparat skryptów skompilowany skryptu. Ta metoda jest wywoływana dla każdego skryptu, który ma być kompilowana.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT ScriptCompiled(  
    [in] PROFILER_TOKEN scriptId,  
    [in] PROFILER_SCRIPT_TYPE type,  
    [in] IUnknown *pIDebugDocumentContext);  
```  
  
#### <a name="parameters"></a>Parametry  
 `scriptId`  
 [in] Unikatowy identyfikator skrypt, który został skompilowany. Ten identyfikator jest przypisywany przez aparat skryptów.  
  
 `type`  
 [in] Typ skryptu, który został skompilowany. Wartości są zdefiniowane w [wyliczenie profiler_script_type Enumeration](../../winscript/reference/profiler-script-type-enumeration.md).  
  
 `pIDebugDocumentContext`  
 [in] Jeśli jest dostępna, wskaźnik do `IUnknown` interfejs, który należy wyszukać profilera [interfejs IDebugDocumentContext](../../winscript/reference/idebugdocumentcontext-interface.md) wskaźnika. W przeciwnym razie wartość będzie pusta.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwracana wartość ta metoda jest ignorowana przez aparat skryptów.  
  
## <a name="remarks"></a>Uwagi  
 Aparat skryptów zapewniają kontekstu dokumentu, tylko wtedy, gdy jest to obsługiwane przez hosta.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md)