---
title: IJsDebugDataTarget::FreeVirtualMemory — metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.FreeVirtualMemory
apilocation:
- jscript9diag.dll
ms.assetid: ea54bad3-9ae3-436b-974d-70fc7fffefd6
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3b53d7f80227a1c4eb0ef0293093543c09c5a367
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794776"
---
# <a name="ijsdebugdatatargetfreevirtualmemory-method"></a>IJsDebugDataTarget::FreeVirtualMemory — Metoda
Zwalnia i/lub decommits obszaru pamięci w wirtualnej przestrzeni adresowej procesu docelowego.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT FreeVirtualMemory(  
   UINT64 address,  
   DWORD size,  
   DWORD freeType  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `address`  
 [in] Adresów, w którym zwolniona pamięć procesu docelowego.  
  
 `size`  
 [in] Liczba bajtów do zrzeka się. Aby zwolnić obszaru pamięci, ta wartość musi być zero.  
  
 `freeType`  
 [in] Wskazuje typ wolnego operacji do wykonania. Jest to zazwyczaj wartości MEM_RELEASE (0x8000), które zwalnia określonego regionu stron. Po wykonaniu operacji strony są w stanie wolnym. MEM_DECOMMIT (0x4000) można zamiast tego zrzeka stron bez ich zwolnienie.  
  
## <a name="return-value"></a>Wartość zwracana  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać dodatkowe informacje Zobacz VirtualFree Win32 API.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jscript9diag.h  
  
## <a name="see-also"></a>Zobacz też  
 [Ijsdebugdatatarget — interfejs](../../winscript/reference/ijsdebugdatatarget-interface.md)