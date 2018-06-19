---
title: IDebugApplication110::SynchronousCallInMainThread | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplication110::SynchronousCallInMainThread
ms.assetid: 57475ae5-1520-45ef-800d-ccfc6235a5d1
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ef52ebfe8bfccecc0eea2383787a5b2698a5ce5f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793894"
---
# <a name="idebugapplication110synchronouscallinmainthread"></a>IDebugApplication110::SynchronousCallInMainThread
Wykonuje synchroniczne wywołania w głównym wątku.  
  
> [!IMPORTANT]
>  [Interfejs IDebugApplication110](../../winscript/reference/idebugapplication110-interface.md) jest implementowany przez PDM v11.0 i większa. Znajduje się w zestawie activdbg100.h.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SynchronousCallInMainThread([in] IDebugThreadCall* pptc, [in] DWORD_PTR dwParam1, [in] DWORD_PTR dwParam2, [in] DWORD_PTR dwParam3);  
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