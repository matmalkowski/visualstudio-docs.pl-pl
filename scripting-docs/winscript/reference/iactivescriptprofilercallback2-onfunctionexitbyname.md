---
title: IActiveScriptProfilerCallback2::OnFunctionExitByName | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerCallback2::OnFunctionExitByName
ms.assetid: a6ddead4-e66d-4789-b778-84e5c343f908
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dd26ab1cf36378c0f037d78a3c079c58e004006d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercallback2onfunctionexitbyname"></a>IActiveScriptProfilerCallback2::OnFunctionExitByName
Powiadamia profilera dla obiekt, który aparat skryptów zamknięte wywołanie funkcji modelu DOM (Document Object).  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT OnFunctionExitByName(  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] PROFILER_SCRIPT_TYPE scriptType);  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `pwszFunctionName`  
 [in] Nazwa funkcji zakończenie działania aparatu skryptów.  
  
 `scriptType`  
 [in] Typ funkcji. Aby uzyskać opis prawidłowych wartości, zobacz [wyliczenie profiler_script_type Enumeration](../../winscript/reference/profiler-script-type-enumeration.md).  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwracana wartość ta metoda jest ignorowana przez aparat skryptów.  
  
## <a name="remarks"></a>Uwagi  
 Dla wywołań modelu DOM, aparat skryptów wywołuje tę metodę, zamiast wywoływać metodę [IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md). Jest to spowodowane dużą liczbę unikatowych metody i właściwości w modelu DOM.  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)   
 [Interfejs IActiveScriptProfilerCallback2](../../winscript/reference/iactivescriptprofilercallback2-interface.md)