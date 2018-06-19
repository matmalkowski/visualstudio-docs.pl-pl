---
title: IActiveScriptProfilerCallback::FunctionCompiled | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerCallback.FunctionCompiled
apilocation:
- scrobj.dll
ms.assetid: a7e9ef17-3891-4731-9d08-c37bc489be61
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 797476d4892224ad0b27c9caf579c0704693c835
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793369"
---
# <a name="iactivescriptprofilercallbackfunctioncompiled"></a>IActiveScriptProfilerCallback::FunctionCompiled
Powiadamia profilera dla obiekt, który aparat skryptów napotkał funkcji podczas kompilowania skryptu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT FunctionCompiled(  
    [in] PROFILER_TOKEN functionId,  
    [in] PROFILER_TOKEN scriptId,  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] [string] const WCHAR *pwszFunctionNameHint,  
    [in] IUnknown *pIDebugDocumentContext);  
```  
  
#### <a name="parameters"></a>Parametry  
 `functionId`  
 [in] Unikatowy identyfikator funkcji. Ten identyfikator jest przypisywany przez aparat skryptów.  
  
 `scriptId`  
 [in] Unikatowy identyfikator skryptu, który jest ona częścią.  
  
 `pwszFunctionName`  
 [in] Nazwa funkcji, lub wartość null dla funkcji anonimowej.  
  
 `pwszFunctionNameHint`  
 [in] Wywnioskowane nazwę funkcji lub wartość null, jeśli aparat skryptów nie są rozpoznawane przez dowolną nazwę.  
  
 `pIDebugDocumentContext`  
 [in] Jeśli jest dostępna, wskaźnik do `IUnknown` interfejs, który należy wyszukać profilera [interfejs IDebugDocumentContext](../../winscript/reference/idebugdocumentcontext-interface.md) wskaźnika. W przeciwnym razie wartość null.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwracana wartość ta metoda jest ignorowana przez aparat skryptów.  
  
## <a name="remarks"></a>Uwagi  
 Aparat skryptów zapewniają kontekstu dokumentu, tylko wtedy, gdy jest to obsługiwane przez hosta.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md)