---
title: IActiveScriptProfilerCallback2::OnFunctionEnterByName | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerCallback2::OnFunctionEnterByName
ms.assetid: 24b1593a-97fc-4d70-9b85-ec86fb59f987
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ea74d9e9e00485c86d26bb01c486992f85ffeb8f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793414"
---
# <a name="iactivescriptprofilercallback2onfunctionenterbyname"></a>IActiveScriptProfilerCallback2::OnFunctionEnterByName
Powiadamia obiektu profilera, który aparat skryptów ma wykonać wywołanie funkcji modelu DOM (Document Object).  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT OnFunctionEnterByName(  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] PROFILER_SCRIPT_TYPE scriptType);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pwszFunctionName`  
 [in] Nazwa funkcji, który przechodzi przez aparat skryptów do wykonania.  
  
 `scriptType`  
 [in] Typ funkcji. Aby uzyskać opis prawidłowych wartości, zobacz [wyliczenie profiler_script_type Enumeration](../../winscript/reference/profiler-script-type-enumeration.md).  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwracana wartość ta metoda jest ignorowana przez aparat skryptów.  
  
## <a name="remarks"></a>Uwagi  
 Dla wywołań modelu DOM, aparat skryptów wywołuje tę metodę, zamiast wywoływać metodę [IActiveScriptProfilerCallback::OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md). Jest to spowodowane dużą liczbę unikatowych metody i właściwości w modelu DOM.  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)   
 [Interfejs IActiveScriptProfilerCallback2](../../winscript/reference/iactivescriptprofilercallback2-interface.md)