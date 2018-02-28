---
title: IRemoteDebugApplication110::GetMainThread | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplication110::GetMainThread
ms.assetid: 9982acc9-3d35-4dcf-8ca9-662469de4072
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2dc420f3c59a59373c6e3a2be9e7254eea451585
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iremotedebugapplication110getmainthread"></a>IRemoteDebugApplication110::GetMainThread
Zwraca wątku głównego dla hostów, które wywołują [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439), w przeciwnym razie zwraca E_FAIL.  
  
> [!IMPORTANT]
>  [Interfejs IRemoteDebugApplication](../../winscript/reference/iremotedebugapplication-interface.md) jest implementowany przez PDM v11.0 i większa. Znajduje się w zestawie activdbg100.h.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetMainThread([out] IRemoteDebugApplicationThread **ppThread);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppThread`  
 [out] Głównym [interfejs IRemoteDebugApplicationThread](../../winscript/reference/iremotedebugapplicationthread-interface.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IRemoteDebugApplication](../../winscript/reference/iremotedebugapplication-interface.md)   
 [Interfejs IRemoteDebugApplication110](../../winscript/reference/iremotedebugapplication110-interface.md)