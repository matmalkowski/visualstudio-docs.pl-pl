---
title: IActiveScriptProfilerCallback::Shutdown | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptProfilerCallback.Shutdown
apilocation: scrobj.dll
ms.assetid: 1281bf3c-d7d8-4ff5-9d8a-d1761fdb262e
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ec47cd5f581c36abb60b662983c6d806a4732f47
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercallbackshutdown"></a>IActiveScriptProfilerCallback::Shutdown
Wywołuje się, by informuje obiektu profilera zawsze, gdy profilowania jest zatrzymana na aparatu skryptów. W ten sposób obiektu profilera można wywołać jej procedury czyszczenia, jeśli jest to wymagane. Ta metoda jest również wywoływany przez aparat skryptów, gdy trwa wyłączanie aparatu skryptów lub gdy wywołanie [IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md) nie powiedzie się.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Shutdown(  
    [in] HRESULT hrReason);  
```  
  
#### <a name="parameters"></a>Parametry  
 `hrReason`  
 [in] Przyczyna zamykanie. Jeśli aparat skryptów jest zamykany, `S_OK` została przekazana. Jeśli wywołanie [IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md) zwraca błąd HRESULT, HRESULT została przekazana. W przeciwnym razie ta wartość jest pobierana z [IActiveScriptProfilerControl::StopProfiling](../../winscript/reference/iactivescriptprofilercontrol-stopprofiling.md).  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwracana wartość ta metoda jest ignorowana przez aparat skryptów.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md)