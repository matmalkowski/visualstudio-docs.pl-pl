---
title: IDebugApplicationThread110::AsynchronousCallIntoThread | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 06b3031a-4aec-4a47-afaa-04642a4c4870
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0d4275d42ec102557cce12127f47a33a53c4dba6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793990"
---
# <a name="idebugapplicationthread110asynchronouscallintothread"></a>IDebugApplicationThread110::AsynchronousCallIntoThread
Powoduje, że wywołanie asynchroniczne w głównym wątku.  
  
> [!IMPORTANT]
>  [Interfejs IDebugApplicationThread110](../../winscript/reference/idebugapplicationthread110-interface.md) jest implementowany przez PDM v11.0 i większa. Znajduje się w zestawie activdbg100.h.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT AsynchronousCallInMainThread([in] IDebugThreadCall* pptc, [in] DWORD_PTR dwParam1, [in] DWORD_PTR dwParam2, [in] DWORD_PTR dwParam3);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pptc`  
 [Interfejs IDebugThreadCall](../../winscript/reference/idebugthreadcall-interface.md) obiekt do wywołania.  
  
 `dwParam1`  
 Pierwszy parametr wywołania.  
  
 `dwParam1`  
 Pierwszy parametr wywołania.  
  
 `dwParam2`  
 Drugi parametr wywołania.  
  
 `dwParam3`  
 Trzeci parametr wywołania.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugApplication110](../../winscript/reference/idebugapplication110-interface.md)