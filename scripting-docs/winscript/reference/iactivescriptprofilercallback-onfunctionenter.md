---
title: IActiveScriptProfilerCallback::OnFunctionEnter | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptProfilerCallback.OnFunctionEnter
apilocation: scrobj.dll
ms.assetid: 12dab2b4-df4e-444d-99cb-25e1c278e6e8
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d9af9dc5ce1f4cb0eb5c328c90c20184111afd9b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercallbackonfunctionenter"></a>IActiveScriptProfilerCallback::OnFunctionEnter
Powiadamia obiektu profilera, które ma wykonać wywołania funkcji, która nie jest wywołaniem do modelu DOM (Document Object) aparatu skryptów.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT OnFunctionEnter(  
    [in] PROFILER_TOKEN scriptId,   
    [in] PROFILER_TOKEN functionId);  
```  
  
#### <a name="parameters"></a>Parametry  
 `scriptId`  
 [in] Unikatowy identyfikator skryptu, który jest ona częścią. Ten identyfikator jest przypisywany przez aparat skryptów.  
  
 `functionId`  
 [in] Unikatowy identyfikator funkcji. Ten identyfikator jest przypisywany przez aparat skryptów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwracana wartość ta metoda jest ignorowana przez aparat skryptów.  
  
## <a name="remarks"></a>Uwagi  
 Dla wywołań modelu DOM, aparat skryptów wywołuje [IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md) zamiast `IActiveScriptProfilerCallback::OnFunctionEnter`. Jest to spowodowane dużą liczbę unikatowych metody i właściwości w modelu DOM.  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)   
 [Interfejs IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md)