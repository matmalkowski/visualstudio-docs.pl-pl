---
title: IDebugApplicationThread110::IsThreadCallable | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugApplicationThread110::IsThreadCallable
ms.assetid: 2a75a366-801d-47e0-bba3-51aa669e03a7
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b34e2c45d7e94c72ade62780f46f4b5c7c22405e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationthread110isthreadcallable"></a>IDebugApplicationThread110::IsThreadCallable
Określa, czy ten wątek jest w stanie, który będzie przetwarzać wywołań za pomocą wątku PDM przełączanie funkcjom, takim jak SynchronousCallInThread.  
  
> [!IMPORTANT]
>  [Interfejs IDebugApplicationThread110](../../winscript/reference/idebugapplicationthread110-interface.md) jest implementowany przez PDM v11.0 i większa. Znajduje się w zestawie activdbg100.h.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT IsThreadCallable([out, annotation("_Out_")] BOOL * pfIsCallable);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pfIsCallable`  
 [out] `true` Jeśli wątek jest można wywołać, w przeciwnym razie `false`.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugApplicationThread110](../../winscript/reference/idebugapplicationthread110-interface.md)